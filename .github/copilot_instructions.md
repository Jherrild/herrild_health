# Copilot Instructions — Herrild Health

## Project Overview
Jekyll-powered static site at `health.herrild.net`. Single-page app with CSS-only
tab navigation. Content is authored in YAML data files and Markdown tab files.
Deployed automatically on push to `main` via GitHub Actions (`jekyll-build-pages`).

## Architecture & Design Decisions

### Why Jekyll
- **Native GitHub Pages support** — `actions/jekyll-build-pages` builds the site;
  no custom Node/Python/Go build scripts to maintain.
- **Data-driven content** — Supplements, FAQ, staging, and timing live in `_data/*.yml`.
  Edit YAML, push, done. No HTML knowledge needed for content changes.
- **Standard and documented** — Liquid templating, kramdown markdown, YAML front matter
  are all well-documented with large communities. No custom parsing conventions.
- **Alternatives considered** — Hugo (overkill, Go templates less intuitive), 11ty
  (requires CI build step), Astro (way overkill for a zero-JS single page), custom
  Node.js build script (fragile custom conventions, maintenance burden).

### CSS-Only Tabs (No JavaScript)
The site uses hidden `<input type="radio">` elements with `:has()` CSS selectors to
toggle tab panels. This is a deliberate choice — zero JS means zero runtime failures.
The `:has()` selectors are dynamically generated from the `_tabs/` collection at build time.

### Visual Style
- **Font:** Poppins (Google Fonts) — weights 300, 400, 500, 600, 700
- **Layout:** Centered single-column, max-width 640px
- **Cards:** White background, 24px border-radius, soft box-shadow (`0 18px 40px rgba(0,0,0,0.10)`)
- **Gradients:** Subtle green gradient background (`#e8f5e9` → `#c8e6c9`)
- **Accent color:** `#2e7d52` (deep green) with soft variant at 10% opacity
- **Mobile:** Responsive at 480px breakpoint — smaller padding, fonts, radii
- All CSS is inline in `_layouts/default.html` `<style>` block (no external stylesheets)
- CSS custom properties (`:root` variables) for all colors

## File Structure
```
index.html                          # Jekyll entry point (just front matter + layout ref)
CNAME                               # Custom domain: health.herrild.net
_config.yml                         # Jekyll config, collections, excludes
Gemfile                             # Ruby deps (jekyll, webrick)

_layouts/
  default.html                      # Full page template: CSS, nav, tab panels, footer

_includes/
  supplement-item.html              # Single supplement card (name, dose, detail, note)
  faq-list.html                     # FAQ accordion from data array
  staging-list.html                 # Numbered staging protocol

_tabs/                              # Tab content (Jekyll collection, output: false)
  home.md                           # Welcome / intro
  supplements.md                    # Uses Liquid to loop over _data files
  exercise.md                       # Markdown content (coming soon)
  faq.md                            # Uses faq-list.html include

_data/                              # Structured content (edit these to update the site)
  supplements.yml                   # Core daily stack items
  optional_supplements.yml          # Optional items (NAC / GlyNAC)
  staging.yml                       # 3-stage onboarding protocol
  timing.yml                        # Morning / evening timing slots
  faq.yml                           # FAQ question/answer pairs

prd/                                # Product requirement docs (excluded from build)
.github/
  workflows/static.yml              # GitHub Actions: jekyll-build-pages → deploy
  copilot_instructions.md           # This file
```

## How to Make Common Changes

### Add a new supplement
Edit `_data/supplements.yml` (core) or `_data/optional_supplements.yml` (optional).
Each item has: `name`, `dose`, `detail`, and optionally `note` (for fact-check callouts).
```yaml
- name: Vitamin D3
  dose: 5,000 IU/day
  detail: >
    Take with a fat-containing meal for absorption.
  note: >
    📋 Note: Upper safe limit is 4,000 IU/day per NIH, though many
    researchers consider 5,000 IU safe for adults with low baseline levels.
```

### Add a new FAQ
Append to `_data/faq.yml`:
```yaml
- question: Can I take creatine on an empty stomach?
  answer: >
    Yes. Creatine monohydrate absorbs well regardless of food intake.
```

### Add a new tab
1. Create `_tabs/newtab.md` with front matter:
   ```yaml
   ---
   title: New Tab Title
   tab_label: Tab Name
   tag: In Progress
   order: 5
   ---
   ```
2. Write content as markdown or Liquid. The layout auto-discovers it from the
   `_tabs` collection, generates the nav radio button, CSS `:has()` selector,
   and tab panel. No template changes needed.

### Update timing or staging
Edit `_data/timing.yml` or `_data/staging.yml` — simple label/detail pairs.

### Change the layout or CSS
Edit `_layouts/default.html`. All CSS is in the `<style>` block at the top.
Component-level styles are grouped with comment headers (`/* ── Supplement Groups ── */`).

## Content Conventions
- **Tone:** Personal, informational, not medical advice
- **Notes/callouts:** Use `note` field in YAML data. HTML `<a>` tags are allowed
  for citations. Notes render as yellow-bordered callout boxes.
- **Fact-checking:** When adding health claims, include inline citations as
  `<a href="..." target="_blank">` in the `note` field. Verify claims via research.
- **Tags:** Use `tag` in front matter to show section status. Remove or change to
  "Active Protocol" when content is complete. Do not use "In Progress" for finished sections.

## Local Development
```bash
# Requires Ruby (Homebrew: brew install ruby)
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
bundle install          # first time only
bundle exec jekyll serve  # preview at http://localhost:4000
bundle exec jekyll build  # one-shot build → _site/
```

## Deployment
- Push to `main` triggers `.github/workflows/static.yml`
- `actions/jekyll-build-pages@v1` builds the site
- `actions/deploy-pages@v4` publishes `_site/` to GitHub Pages
- Custom domain: `health.herrild.net` (configured via `CNAME` file)

## Key Components

### supplement-item.html
Renders a single supplement card. Parameters passed via `include`:
- `item.name` — supplement name
- `item.dose` — dosage string
- `item.detail` — description text
- `item.note` — (optional) fact-check/note callout with yellow styling

### faq-list.html
Renders `<details>` accordion items. Pass `items` array where each has
`question` and `answer` keys.

### staging-list.html
Renders a bordered step list. Pass `stages` array where each has
`label` and `items` keys.

## References & Research Standards
- Supplement notes should cite peer-reviewed sources where possible
- Use `target="_blank"` on all external links
- Prefer systematic reviews and RCTs over individual studies
- Note when a claim is emerging/preliminary vs well-established
