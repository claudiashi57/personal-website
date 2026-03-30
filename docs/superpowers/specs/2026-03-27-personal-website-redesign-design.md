# Personal Website Redesign — Design Spec

## Goal

Migrate claudiashi.com from Owlstown (paid) to GitHub Pages (free) with a redesigned, modern minimal static site.

## Constraints

- Free hosting (GitHub Pages)
- Custom domain: www.claudiashi.com (canonical), with apex redirect
- No build step, no external dependencies
- Plain HTML/CSS only
- Semantic HTML (`<nav>`, `<main>`, `<header>`, `<footer>`) for accessibility

## Pages

### Home (`index.html`)

- Header: site title (name), horizontal nav (Home, Publications, CV)
- Bio: Name, title (Research Scientist at Meta FAIR, NYC, AI and Society team), research focus (alignment, safety, and governance of LLMs), PhD from Columbia under David Blei
- Links: Email, Twitter (@causalclaudia), GitHub, Google Scholar — external links open in new tab
- Footer: copyright line
- No headshot photo

### Publications (`publications.html`)

- Same header/nav/footer as Home
- Chronological list (newest first), each entry:
  - Paper title (linked to URL if available, opens in new tab)
  - Authors
  - Venue/year
- Manually maintained — edit HTML to add new papers
- **Data source:** Scrape current Owlstown site during implementation to populate initial list

### CV (`cv.html`)

- Same header/nav/footer as Home
- Link/button to download CV PDF from `assets/cv.pdf`

## File Structure

```
personal_website/
├── index.html
├── publications.html
├── cv.html
├── 404.html
├── style.css
├── CNAME
└── assets/
    └── cv.pdf
```

## Styling

- **Font:** System font stack (`-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif`)
- **Layout:** Centered content, max-width ~700px, generous padding
- **Colors:** Near-black text (#1a1a1a) on white (#ffffff), gray (#666) for secondary text, blue (#2563eb) for links
- **Responsive:** CSS media queries for mobile (adjust padding)
- **No JavaScript**

## HTML Head (all pages)

- `<title>` per page (e.g., "Claudia Shi", "Publications — Claudia Shi")
- `<meta name="description">` per page
- `<meta name="viewport">` for responsive
- `<link rel="icon">` — simple favicon
- Open Graph tags (`og:title`, `og:description`) for link previews

## Deployment

1. Create public GitHub repo
2. Enable GitHub Pages on `main` branch
3. Add `CNAME` file containing exactly: `www.claudiashi.com`
4. DNS configuration at domain registrar:
   - CNAME record: `www` → `<github-username>.github.io`
   - A records for apex (`claudiashi.com`):
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
5. Enable "Enforce HTTPS" in GitHub Pages settings

## Tech Decisions

| Decision | Choice | Rationale |
|----------|--------|-----------|
| Hosting | GitHub Pages | Free, reliable, supports custom domains |
| Tech stack | Plain HTML/CSS | No build step, no dependencies, easy to maintain |
| Font | System font stack | No external requests, consistent with "no dependencies" |
| Publications | Manual HTML | Simple, full control, low maintenance for small list |
| CV | PDF link | Already maintained as PDF, avoids duplication |
| CSS framework | None | 3 pages don't justify a dependency |
| Design | Modern minimal | Sans-serif, whitespace, clean academic look |
| Accent color | Blue (#2563eb) | Standard, accessible, professional |
