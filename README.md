# Herrild Health

Personal health knowledge base — supplements, exercise, and wellness protocols.

🔗 **Live at [health.herrild.net](https://health.herrild.net)**

## About

A simple, single-page site for documenting my current supplement stack, exercise
routines, and evolving understanding of health and wellness. Built as a static
GitHub Pages site with CSS-only tab navigation.

## Structure

```
index.html          # Single-page site with CSS tab navigation
CNAME               # Custom domain config (health.herrild.net)
.github/workflows/  # GitHub Actions for auto-deploy on push to main
prd/                # Product requirement documents
```

## Development

Edit `index.html` and push to `main` — GitHub Actions will auto-deploy to
GitHub Pages. No build step required.

## Custom Domain

DNS should have a CNAME record pointing `health.herrild.net` to
`jherrild.github.io`.
