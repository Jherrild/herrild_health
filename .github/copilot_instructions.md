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

### Dev-Only Tabs
Tabs with `dev_only: true` in their front matter are **excluded from production builds**
(`JEKYLL_ENV=production`, which `actions/jekyll-build-pages` sets by default). They appear
only when running `bundle exec jekyll serve` locally. Use this for UX previews, design
experiments, or staging content that isn't ready for the public site.

### Visual Style
- **Font:** Poppins (Google Fonts) — weights 300, 400, 500, 600, 700
- **Layout:** Centered single-column, max-width 640px
- **Cards:** White background, 24px border-radius, soft box-shadow (`0 18px 40px rgba(0,0,0,0.10)`)
- **Gradients:** Subtle green gradient background (`#e8f5e9` → `#c8e6c9`)
- **Accent color:** `#2e7d52` (deep green) with soft variant at 10% opacity
- **Accent hover:** `#1b5e3b`
- **Mobile:** Responsive at 480px breakpoint — smaller padding, fonts, radii
- All CSS is inline in `_layouts/default.html` `<style>` block (no external stylesheets)
- CSS custom properties (`:root` variables) for all colors

### Interactive Features
- **FAQ cross-links:** Supplement items can link to specific FAQ entries using an
  `onclick` handler that: checks the FAQ radio button, opens the `<details>` element,
  adds a `.highlight` class (green pulse animation), and smooth-scrolls to it.
- **Collapsible research notes:** Supplement items with a `note` field render as a
  collapsed `<details>` element with a "📋 More info & research" toggle. This keeps
  the stack scannable on mobile while preserving full citations.
- **FAQ IDs:** Each FAQ `<details>` gets an auto-generated `id` from the slugified
  question text (e.g., `faq-is-10-g-of-creatine-too-much`). These are stable
  anchor targets for cross-links.

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
  faq-list.html                     # FAQ accordion from data array (auto-generates IDs)
  staging-list.html                 # Numbered staging protocol

_tabs/                              # Tab content (Jekyll collection, output: false)
  home.md                           # Welcome / intro
  supplements.md                    # Uses Liquid to loop over _data files
  exercise.md                       # Markdown content (coming soon)
  faq.md                            # Uses faq-list.html include
  ux-examples.md                    # Dev-only UX preview tab (dev_only: true)

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
Each item has: `name`, `dose`, `detail`, and optionally `note` (for collapsible
research callouts with citations).
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
The FAQ item automatically gets an `id` attribute from the slugified question
(e.g., `faq-can-i-take-creatine-on-an-empty-stomach`) for cross-linking.

### Link a supplement item to a specific FAQ
In the supplement's `detail` field, add an inline link using this pattern:
```html
<a href="#faq-SLUG"
   onclick="document.getElementById('tab-faq').checked=true;
            var el=document.getElementById('faq-SLUG');
            el.open=true;
            el.classList.remove('highlight');
            void el.offsetWidth;
            el.classList.add('highlight');
            el.scrollIntoView({behavior:'smooth'});
            return false;">link text</a>
```
Replace `SLUG` with the slugified FAQ question. Be tasteful — link naturally from
existing text (e.g., "Must be the *glycinate form*") rather than adding explicit
"see FAQ" callouts for every item.

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

## UX Preview Protocol

When presenting UX/design options for the owner to evaluate:

1. **Create examples in `_tabs/ux-examples.md`** (already exists, `dev_only: true`).
   Do not create new files — reuse this page, replacing previous examples.
2. **Show real component context** — render each option inside an actual
   `supplement-item` card (or whatever component is being styled) so it's
   evaluated in situ, not in isolation.
3. **Label each option clearly** with an `<h3>Option N: Name</h3>` heading.
4. **Use scoped CSS** — define option-specific styles in a `<style>` block at the
   bottom of the UX preview file using unique class names (e.g., `.ux-pill`,
   `.ux-strip`). Never modify `_layouts/default.html` CSS for preview options.
5. **Keep options self-contained** — each option's CSS class should override the
   base `.note-toggle` styles so the owner can compare them side by side.
6. **Include hover/open states** — design is interactive; static screenshots miss
   half the picture.
7. **Tell the owner to run `bundle exec jekyll serve`** and check the "UX Preview"
   tab locally. This tab never ships to production.
8. **After a choice is made**, apply the chosen CSS to `_layouts/default.html`,
   remove the preview styles from `ux-examples.md`, and leave the page ready
   for the next round of UX experiments.

## Content Conventions
- **Tone:** Personal, informational, not medical advice
- **Notes/callouts:** Use `note` field in YAML data. HTML `<a>` tags are allowed
  for citations. Notes render as collapsible yellow-bordered callout boxes.
- **Fact-checking:** When adding health claims, include inline citations as
  `<a href="..." target="_blank">` in the `note` field. Verify claims via web search.
  Prefer systematic reviews and RCTs over individual studies. Note when a claim is
  emerging/preliminary vs well-established.
- **Tags:** Use `tag` in front matter to show section status. Remove or change to
  "Active Protocol" when content is complete. Do not use "In Progress" for finished sections.

## Local Development
```bash
# Requires Ruby (Homebrew: brew install ruby)
cd ~/repos/herrild_health
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"
bundle install            # first time only
bundle exec jekyll serve  # preview at http://127.0.0.1:4000 (auto-reloads)
bundle exec jekyll build  # one-shot build → _site/
```

Dev-only tabs (like UX Preview) appear locally but are excluded from production.
To simulate a production build locally:
```bash
JEKYLL_ENV=production bundle exec jekyll build
```

## Deployment
- Push to `main` triggers `.github/workflows/static.yml`
- `actions/jekyll-build-pages@v1` builds with `JEKYLL_ENV=production` (excludes dev-only tabs)
- `actions/deploy-pages@v4` publishes `_site/` to GitHub Pages
- Custom domain: `health.herrild.net` (configured via `CNAME` file)

## Key Components

### supplement-item.html
Renders a single supplement card. Parameters passed via `include`:
- `item.name` — supplement name
- `item.dose` — dosage string
- `item.detail` — description text (supports inline HTML for FAQ links)
- `item.note` — (optional) collapsible research callout with yellow styling

### faq-list.html
Renders `<details>` accordion items with auto-generated `id` attributes.
Pass `items` array where each has `question` and `answer` keys. The `id` is
the slugified question (e.g., `faq-do-i-still-need-melatonin-if-i-sleep-fine`).
Supports `.highlight` class for green pulse animation on cross-link navigation.

### staging-list.html
Renders a bordered step list. Pass `stages` array where each has
`label` and `items` keys.

## References & Research Standards
- Supplement notes should cite peer-reviewed sources where possible
- Use `target="_blank"` on all external links
- Prefer systematic reviews and RCTs over individual studies
- Note when a claim is emerging/preliminary vs well-established
- Include links directly in the YAML `note` field as HTML `<a>` tags
