# rahullamba.com

Personal website of Rahul Lamba — SRE, DevSecOps, and infrastructure engineer based in Abu Dhabi.

Built with [Hugo](https://gohugo.io/). Deployed via GitHub Actions to GitHub Pages.

## Stack

- **Hugo** — static site generator
- **Space Grotesk + Inter** — typography
- **Plain CSS** — no frameworks, custom design system with dark mode via `prefers-color-scheme`
- **Umami** — privacy-friendly analytics

## Structure

```
content/
  projects/       # project write-ups (markdown)
layouts/
  _default/       # base, list, single templates
  partials/       # navbar, hero, footer
  index.html      # homepage
assets/css/
  style.css       # all styles
static/
  images/         # photos
  favicon.svg     # rocket emoji favicon
```

## Local development

```bash
hugo server
```

## Adding a project

Create a markdown file in `content/projects/`:

```bash
hugo new content/projects/my-project.md
```

Frontmatter fields:

```yaml
---
title: "project-name"
date: 2025-01-01
description: "One-line description."
github: "https://github.com/..."
status: "active"
tags: ["python", "aws"]
---
```

## Deployment

Pushes to `main` trigger the GitHub Actions workflow which builds and deploys to GitHub Pages.
