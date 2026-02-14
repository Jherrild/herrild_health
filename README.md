# Herrild Health

Personal health knowledge base — supplements, exercise, and wellness protocols.

🔗 **Live at [health.herrild.net](https://health.herrild.net)**

## About

A single-page Jekyll site for documenting my current supplement stack, exercise
routines, and evolving understanding of health and wellness. Content is authored
in YAML data files and Markdown — no HTML editing needed for content changes.

## Structure

```
_data/              # Editable content (supplements, FAQ, timing, staging)
_tabs/              # Tab pages (home, supplements, exercise, FAQ)
_layouts/           # Page template with all CSS
_includes/          # Reusable HTML components
_config.yml         # Jekyll configuration
index.html          # Jekyll entry point
CNAME               # Custom domain config (health.herrild.net)
.github/workflows/  # GitHub Actions for auto-deploy on push to main
prd/                # Product requirement documents
```

## Local Development

```bash
cd ~/repos/herrild_health && export PATH="/opt/homebrew/opt/ruby/bin:$PATH" && bundle exec jekyll serve
```

Then open **http://127.0.0.1:4000** to preview. The server auto-reloads on file changes.

First-time setup: `bundle install` (requires Ruby via Homebrew).

## Custom Domain

DNS should have a CNAME record pointing `health.herrild.net` to
`jherrild.github.io`.
