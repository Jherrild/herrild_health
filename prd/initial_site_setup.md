# PRD: Herrild Health — Initial Site Setup

## Summary
Single-page static site for `health.herrild.net` built as a GitHub Pages deployment.
Serves as a personal health knowledge base documenting supplement protocols, exercise
routines, and wellness research.

## What Was Implemented

### Site Structure
- **Single `index.html`** with all HTML, CSS, and layout inline
- **CSS-only tab navigation** using radio inputs and `:checked` selectors — no JavaScript
- Three tabs: **Home**, **Supplement Stack**, **Exercise**
- All tabs show "In Progress" placeholder content

### Visual Design (matching sunday-coffee style)
- Poppins font family with multiple weights
- Card-based layout with 24px rounded corners and soft shadows
- Subtle green gradient background
- Accent color theming via CSS custom properties
- Mobile-responsive at 480px breakpoint
- Status tag pills with dot indicators

### Infrastructure
- Private GitHub repo under `jherrild/herrild_health`
- GitHub Actions workflow (`.github/workflows/static.yml`) deploys on push to `main`
- `CNAME` file configured for `health.herrild.net`
- README with project overview and live link

### Documentation
- `.github/copilot_instructions.md` — style guide and component reference
- This PRD in `/prd`

---

## Next Steps

### Content: Supplement Stack Tab
- [ ] Document current daily supplement protocol (names, dosages, timing)
- [ ] Add cycling protocols (what rotates on/off and why)
- [ ] Include references and sources for each supplement choice
- [ ] Consider a table or structured format for easy scanning

### Content: Exercise Tab
- [ ] Document current weekly training split
- [ ] Detail cardio approach (Zone 2 training, frequency, duration)
- [ ] Add mobility and recovery practices
- [ ] Consider embedding workout structure as a visual schedule

### Content: Home Tab
- [ ] Write a brief personal intro / philosophy on health
- [ ] Add a "last updated" timestamp to reinforce living-document nature
- [ ] Consider a changelog or "what's new" section

---

## Proposed Optimizations

### Content & Structure
1. **Add a "Sleep" or "Recovery" tab** — Sleep protocols, HRV tracking, and recovery
   practices are a natural complement to supplements and exercise.
2. **Structured data format** — Move supplement/exercise data to a JSON file and
   render via lightweight JS templating. Makes updates easier and enables future
   features (filtering, search).
3. **Last-updated footer per section** — Auto-generate from git commit dates or
   add manual timestamps to each tab section.

### Site Operations
4. **Add a `.gitignore`** — Exclude OS files (`.DS_Store`, `Thumbs.db`).
5. **Open Graph meta tags** — Add `og:title`, `og:description`, `og:image` for
   better link previews when sharing on social media.
6. **Favicon** — Add a simple health/wellness themed favicon.
7. **Lighthouse CI** — Add a GitHub Action to run Lighthouse on PRs to ensure
   performance and accessibility stay high.
8. **Print stylesheet** — Add `@media print` styles so the page prints cleanly
   (useful for sharing protocols offline).

### Future Features
9. **Dark mode toggle** — Add a CSS-only or minimal-JS dark mode using
   `prefers-color-scheme` media query.
10. **Anchor links / URL hash routing** — Allow direct linking to tabs
    (`#supplements`, `#exercise`) for shareability.
11. **RSS or changelog feed** — If content updates become frequent, an RSS feed
    or visible changelog adds transparency.
