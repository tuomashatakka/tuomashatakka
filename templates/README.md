# Templates

This directory contains template files used by the GitHub Action to generate repository visualizations.

## Files

### `index.html`
HTML template with handlebars-style placeholders:
- `{{REPO_COUNT}}` - Total number of repositories
- `{{TOTAL_STARS}}` - Total stars across all repos
- `{{TOTAL_FORKS}}` - Total forks across all repos
- `{{REPOS_DATA}}` - JSON array of repository data

### `repos.svg`
SVG template that wraps the HTML content:
- `{{SVG_HEIGHT}}` - Calculated height based on repo count
- `{{HTML_CONTENT}}` - The generated HTML from index.html

## How It Works

The GitHub Action workflow:
1. Fetches repository data from GitHub API
2. Calculates statistics (count, stars, forks)
3. Replaces placeholders in `templates/index.html` → `public/index.html`
4. Embeds the HTML into `templates/repos.svg` → `public/repos.svg`
5. Commits the generated files in `public/` directory

The SVG uses `<foreignObject>` to embed rich HTML content, making it displayable on GitHub.
