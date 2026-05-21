# Personal Presentation Site — Design

## Goal

A minimal one-page personal presentation site for Cristian Manoliu, hosted on GitHub Pages, presenting name, role, short bio, and links to GitHub, LinkedIn, and email.

## Repository & Deployment

- **Repo name:** `cristianmanoliu.github.io` (GitHub's "user site" convention — content at root auto-deploys to `https://cristianmanoliu.github.io`)
- **Local path:** `/Users/cristianmanoliu/Main/code/active/cristianmanoliu.github.io`
- **Branch:** `main` (default GitHub Pages source for user sites)
- **No build step** — pure static HTML + CSS, served as-is
- **Custom domain:** out of scope for v1 (can be added later via `CNAME` file)

## File Structure

```
cristianmanoliu.github.io/
├── index.html
├── style.css
├── favicon.svg
├── README.md
├── LICENSE          (MIT, optional)
└── .gitignore
```

That's it. No `node_modules`, no config files, no framework artifacts.

## Page Structure

Single column, single viewport. No scroll on a typical laptop. Centered horizontally and vertically using flexbox on the `<body>`. Max content width ~640px.

Vertical order:

1. **Name** — `Cristian Manoliu` — `<h1>`, ~2.5rem, semi-bold (600)
2. **Tagline** — `Senior Software Engineer · High-Performance Distributed Systems` — `<p>`, ~1rem, muted color
3. **Bio** — full bio paragraph (`<p>`), comfortable line-height (1.6), normal weight
4. **Links row** — horizontal `<nav>` with three text links separated by a small middle-dot `·` (rendered in muted color, with `~0.75rem` horizontal margin on each side): `GitHub`, `LinkedIn`, `Email`
5. **Footer** — small (`<footer>`), very muted: `© 2026 Cristian Manoliu`

### Content (final)

- **Name:** Cristian Manoliu
- **Tagline:** Senior Software Engineer · High-Performance Distributed Systems
- **Bio:** Senior Software Engineer with 15+ years of experience designing and delivering high-performance, scalable, and mission-critical systems. Deeply experienced in event-driven systems, performance optimizations, and secure data processing at massive scale.
- **GitHub:** https://github.com/cristianmanoliu
- **LinkedIn:** https://www.linkedin.com/in/cristianmanoliu/
- **Email:** cristian.manoliu@gmail.com (rendered as `mailto:` link)

## Visual Style

**Typography**
- Font stack: `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif`
- Base size: 16px (browser default), `1rem` units throughout
- Font smoothing: `-webkit-font-smoothing: antialiased; -moz-osx-font-smoothing: grayscale`

**Colors — Light mode (default)**
- Background: `#fafafa`
- Primary text: `#111111`
- Muted text: `#666666` (tagline, footer)
- Accent: `#2563eb` (link hover)

**Colors — Dark mode (via `@media (prefers-color-scheme: dark)`)**
- Background: `#0f0f10`
- Primary text: `#eaeaea`
- Muted text: `#888888`
- Accent: `#2563eb` (same)

No manual toggle — respects OS setting.

**Spacing**
- Body line-height: 1.6 on bio paragraph
- Vertical rhythm: ~2rem between the major blocks (name → tagline → bio → links → footer has more breathing room)
- Page padding: 2rem on the viewport edges

**Links**
- Default: underline on hover only, color matches text
- Hover: accent blue, underline appears
- External links: `target="_blank"` and `rel="noopener noreferrer"`
- Email: `mailto:cristian.manoliu@gmail.com`

**Responsive**
- Single breakpoint at `max-width: 480px`: name reduces to ~2rem, padding reduces to 1.25rem
- No tablet-specific breakpoint needed

**Favicon**
- `favicon.svg` — simple monogram `CM` in accent blue on transparent background, ~32×32 viewBox

## HTML Skeleton (illustrative)

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cristian Manoliu — Senior Software Engineer</title>
  <meta name="description" content="Senior Software Engineer with 15+ years of experience in high-performance, scalable, mission-critical systems.">
  <!-- Open Graph tags for link previews -->
  <meta property="og:title" content="Cristian Manoliu">
  <meta property="og:description" content="Senior Software Engineer · High-Performance Distributed Systems">
  <meta property="og:type" content="website">
  <meta property="og:url" content="https://cristianmanoliu.github.io">
  <link rel="icon" type="image/svg+xml" href="favicon.svg">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <main>
    <h1>Cristian Manoliu</h1>
    <p class="tagline">Senior Software Engineer · High-Performance Distributed Systems</p>
    <p class="bio">Senior Software Engineer with 15+ years of experience...</p>
    <nav class="links">
      <a href="https://github.com/cristianmanoliu" target="_blank" rel="noopener noreferrer">GitHub</a>
      <a href="https://www.linkedin.com/in/cristianmanoliu/" target="_blank" rel="noopener noreferrer">LinkedIn</a>
      <a href="mailto:cristian.manoliu@gmail.com">Email</a>
    </nav>
    <footer>© 2026 Cristian Manoliu</footer>
  </main>
</body>
</html>
```

## Meta Tags

- `<title>`: `Cristian Manoliu — Senior Software Engineer`
- `<meta name="description">`: shortened bio for search engines
- Open Graph: `og:title`, `og:description`, `og:type`, `og:url` so LinkedIn/Twitter previews look clean
- No Twitter card tags needed beyond OG (Twitter falls back to OG)

## Out of Scope (for v1)

- Custom domain
- Profile photo / avatar
- Project list, blog, or additional pages
- Analytics
- Contact form
- Resume PDF link
- SVG link icons (text-only links chosen for minimalism)
- Dark mode toggle button (auto-only)

## Success Criteria

- Page loads at `https://cristianmanoliu.github.io` after `git push` to `main`
- Lighthouse score ≥ 95 across all four categories (Performance, Accessibility, Best Practices, SEO)
- Renders correctly in current Chrome, Safari, Firefox on macOS
- Renders correctly at 375px width (iPhone SE) and 1440px (laptop)
- Dark mode activates when OS is in dark mode
- All three links work: GitHub opens new tab, LinkedIn opens new tab, Email opens default mail client
- HTML and CSS pass W3C validators with no errors

## Open Questions

None at this time. Ready for implementation planning.
