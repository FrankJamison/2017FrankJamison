# 2017 Frank Jamison Resume Site (Static HTML/CSS)

This project is a responsive, multi-page resume website built with semantic HTML5 and a single shared CSS stylesheet. It showcases a consistent layout system, a mobile-first responsive strategy, and a navigation pattern that uses icon states (default/current/hover) to reinforce location within the site.

It is intentionally “framework-free”: no build step, no JavaScript, and no external dependencies beyond Google Fonts.

## Quick take (for recruiters & hiring managers)

This site demonstrates:

1. **Clean, semantic HTML5** — consistent use of `header`, `nav`, `main`, `article`, `section`, `aside`, `footer`, and `address`.
2. **Mobile-first responsive design** — layout and content density scale progressively through defined breakpoints.
3. **Design system thinking** — shared components (header/nav/contact/footer) and page-specific content areas.
4. **Attention to usability** — clear information hierarchy, scannable lists, readable typography, and touch-friendly navigation.
5. **Practical accessibility basics** — descriptive `alt` text, phone/email links, and decorative imagery marked with `aria-hidden="true"`.

## Tech stack

- **HTML5** (static pages)
- **CSS3** (single stylesheet: `css/myStyles.css`)
- **Google Fonts**
  - Cantarell (body)
  - Cardo (headings)
  - Exo 2 (loaded; not heavily used)

No JavaScript, no package manager, no build pipeline.

## Site map

- **Home / About** — `index.html`
- **Employment** — `employment.html`
- **Education** — `education.html`
- **Skills** — `skills.html`
- **Awards** — `awards.html`
- **Organizations** — `organizations.html`

## Layout architecture (shared across all pages)

Each page follows the same structural pattern:

1. **Header top** (`#headerTop`)
   - Logo + name + subtitle.
2. **Banner** (`#pageBanner`)
   - Background image plus page title overlay.
   - Hidden on small screens; enabled at larger widths.
3. **Primary navigation** (`#siteNav`)
   - Icon-backed section links.
   - Current page indicated by a `current` class on the relevant link.
4. **Content area** (`#contentContainer`)
   - `article` contains the section-specific resume content.
   - `aside#contactInfo` is the contact/social sidebar.
5. **Footer**
   - Simple copyright notice.

This consistent structure makes the pages easy to extend or restyle without changing markup patterns.

## Responsive design & breakpoints (developer-focused)

The stylesheet is **mobile-first**: the default rules target small screens, then media queries progressively enhance layout.

Breakpoints (from `css/myStyles.css`):

- **≥ 513px**
  - Banner becomes visible.
  - Navigation switches from single-column to wrapped rows.
  - Contact layout shifts to a two-column flex layout.
  - Skills list becomes two columns.
- **≥ 769px**
  - Page container becomes centered with a reduced width.
  - Navigation switches to a 3-column layout with icon + label + “phrase” text visible.
  - Main content becomes a two-column layout (`article` + `aside`).
  - Skills list returns to single-column for readability in the sidebar layout.
- **≥ 1025px**
  - Wider container with max-width.
  - Navigation becomes a single row with top-aligned icons.
  - Home page portrait floats left and enables caption.
  - Skills list becomes two columns again.
- **≥ 1200px**
  - Skills list becomes three columns.

## Navigation design (icon states + “current page”)

Navigation links are built with semantic anchors and enhanced with CSS background icons:

- Each nav item has a class like `navHome`, `navEmployment`, etc.
- The active page adds the `current` class (e.g., `class="navLink navHome current"`).
- Each icon has 3 assets (default/current/hover) in `images/`.

This keeps markup simple while still delivering rich, visually communicative navigation.

## Styling approach (CSS organization)

The stylesheet is organized in clear sections:

- **Limited reset + HTML5 display rules** for consistent baseline rendering.
- **Global typography and layout defaults** (font stacks, spacing, shadows).
- **Component blocks**: header, banner, navigation, content container.
- **Page-specific blocks**: home, employment, education, skills, awards, organizations.
- **Contact sidebar**: card-like container, icon-backed social links.
- **Media queries**: progressive enhancements at defined breakpoints.

Notable implementation details:

- Uses **Flexbox** for key layout containers (`#headerTop`, `#siteNav ul`, `#contentContainer`, and contact content areas).
- Uses a simple “card” UI for contact info via background color + border radius.
- Uses `box-sizing: border-box` globally.

## Accessibility & UX notes

- Decorative banner background image is marked with `aria-hidden="true"`.
- Portrait image includes meaningful `alt` text.
- Uses `tel:` and `mailto:` links for direct action from mobile devices.
- Uses an `address` element for address content.
- Uses `wbr` in the email address for improved wrapping on small screens.

## Local viewing / development

### Option A: Open directly

Open `index.html` in any browser and navigate via the top menu.

### Option B: Run a local web server (recommended)

Running a local server avoids potential `file://`-mode quirks.

Python (Windows):

```bat
cd /d d:\Websites\2026FCJamison\projects\2017FrankJamison
py -m http.server 8000
```

Then open `http://127.0.0.1:8000/`.

### Option C: VS Code task

This repo includes a VS Code task to open a local domain in Chrome:

- Task definition: `.vscode/tasks.json`
- Target URL: `http://2017frankjamison.localhost/`

Note: that domain typically requires local DNS/hosts configuration and a local web server/virtual host.

## Deployment

This is a static site: deploy by copying the folder contents to any static host so that `index.html` is at the web root and the `css/` and `images/` folders remain alongside it.

## Customization guide

- **Update content**: edit the relevant page’s `article` section.
- **Update shared header/nav/contact/footer**: apply the same change across all HTML files (no templating/includes in this project).
- **Update which nav item is active**: ensure exactly one link has the `current` class on each page.
- **Replace icons/images**: keep filenames stable where possible to avoid repeated markup updates.

## Potential next improvements (optional)

- Fill in `meta name="description"` on each page.
- Add `rel="noopener noreferrer"` to external links that use `target="_blank"`.
- Consider extracting shared markup into templates (server-side includes or a static site generator) to reduce duplication.
