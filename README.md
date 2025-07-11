# Broken Link Checker GitHub Actions

This repository contains GitHub Actions workflows that automatically check your website or documentation for broken links using lychee.

## Workflows

### 1. Basic Link Checker (`broken-link-checker.yml`)
- Runs on push to main/master branches
- Runs on pull requests
- Runs daily at 2 AM UTC
- Checks links in your repository files
- Comments on PRs with results
- Uploads results as artifacts

### 2. Advanced Link Checker (`broken-link-checker-advanced.yml`)
- All features from basic workflow
- Manual trigger with custom URLs
- Creates GitHub issues for broken links on scheduled runs
- More detailed reporting

### 3. GitHub Pages Link Checker (`github-pages-link-checker.yml`)
- Specifically designed for GitHub Pages sites
- Automatically detects your GitHub Pages URL
- Runs daily at 6 AM UTC
- Creates issues for broken links

## Configuration Files

### `.lycheeignore`
Exclude specific URLs and patterns from checking:
```
# Ignore localhost and private networks
http://localhost
http://127.0.0.1

# Ignore mailto and tel links
mailto:
tel:

# Ignore anchor links
^#
```

### `.lychee.toml`
Advanced configuration for lychee behavior:
```toml
[output]
format = "markdown"
file = "lychee-results.md"

[input]
max_concurrent = 10
max_retries = 3
timeout = 10
```

## Usage

1. Copy the desired workflow file to `.github/workflows/` in your repository
2. Customize the `.lycheeignore` file for your needs
3. Update the `.lychee.toml` configuration if needed
4. Push to trigger the workflow

## Features

- **Automatic scheduling**: Daily checks via cron
- **PR integration**: Comments on pull requests with results
- **Issue creation**: Automatically creates issues for broken links
- **Artifact upload**: Results saved as downloadable artifacts
- **Customizable**: Exclude patterns and configure behavior
- **GitHub Pages support**: Specialized workflow for Pages sites

## Manual Trigger

Use the Advanced Link Checker to manually check specific URLs:
1. Go to Actions tab in your repository
2. Select "Advanced Broken Link Checker"
3. Click "Run workflow"
4. Enter URLs to check (one per line)
5. Add exclude patterns if needed
6. Click "Run workflow"