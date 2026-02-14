# Copilot Instructions — Herrild Health

## Project Overview
Static GitHub Pages site at `health.herrild.net`. Single `index.html` with CSS-only
tab navigation. No JavaScript frameworks, no build tools. Deployed automatically on
push to `main` via GitHub Actions.

## Visual Style
- **Font:** Poppins (Google Fonts) — weights 300, 400, 500, 600, 700
- **Layout:** Centered single-column, max-width 640px
- **Cards:** White background, 24px border-radius, soft box-shadow (`0 18px 40px rgba(0,0,0,0.10)`)
- **Gradients:** Subtle green gradient background (`#e8f5e9` → `#c8e6c9`)
- **Accent color:** `#2e7d52` (deep green) with soft variant at 10% opacity
- **Mobile:** Responsive at 480px breakpoint — smaller padding, fonts, radii

## CSS Architecture
- All styles are inline in `<style>` within `index.html` (no external CSS files)
- CSS custom properties (`:root` variables) for all colors
- Tab navigation uses hidden radio inputs + `:checked` sibling selectors (pure CSS, no JS)
- BEM-lite naming: `.tab-nav`, `.tab-panel`, `.section-list`, `.site-header`, `.site-footer`

## Components

### Tag (`.tag`)
Status pill with dot indicator. Used to show section status (e.g., "In Progress").

### Card (`.card`)
Main content container. Has subtle radial gradient accent in top-right corner via `::before`.

### Section List (`.section-list`)
Bordered list items for upcoming content placeholders. Uses `<ul>` with `<li>` items.

### Tab Navigation (`.tab-nav`)
Pill-style nav bar with radio button toggle. Labels are `<label for="tab-*">`.
Panels use `.panel-home`, `.panel-supplements`, `.panel-exercise` class selectors.

## Content Guidelines
- Tone: Personal, informational, not medical advice
- Structure: Each tab is a self-contained section
- "In Progress" tags should be removed when content is added
- Keep it concise — this is a reference, not a blog post

## Deployment
- Push to `main` triggers `.github/workflows/static.yml`
- GitHub Actions deploys entire repo root to GitHub Pages
- Custom domain: `health.herrild.net` (configured via `CNAME` file)

## File Structure
```
index.html                     # The entire site
CNAME                          # Custom domain
README.md                      # Repo overview
.github/workflows/static.yml  # Deploy workflow
.github/copilot_instructions.md  # This file
prd/                           # Product requirement docs
```
