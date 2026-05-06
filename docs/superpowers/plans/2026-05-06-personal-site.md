# Personal Site Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a one-page personal presentation site (name, tagline, bio, GitHub/LinkedIn/email links) and deploy it to GitHub Pages at `https://cristianmanoliu.github.io`.

**Architecture:** Pure static HTML + CSS, no build step. Single `index.html` with semantic markup, single `style.css` with auto light/dark mode via `prefers-color-scheme`, one inline `favicon.svg`. Hosted on GitHub Pages via the `cristianmanoliu.github.io` user-site repo (root of `main` branch deploys automatically).

**Tech Stack:** HTML5, CSS3, SVG. No JS, no frameworks, no build tools. Git + GitHub Pages for deployment.

**Reference spec:** `docs/superpowers/specs/2026-05-06-personal-site-design.md`

---

## File Structure

Working directory: `/Users/cristianmanoliu/Main/source.code/github/cristianmanoliu.github.io`

```
cristianmanoliu.github.io/
├── .gitignore           # macOS/editor noise
├── README.md            # repo description
├── LICENSE              # MIT
├── index.html           # the page
├── style.css            # all styling
├── favicon.svg          # CM monogram
└── docs/                # already exists (spec + this plan)
    └── superpowers/...
```

Each file has one responsibility. No partials, no shared state. The repo is git-initialized already (commit `d49da72` has the spec). All paths below are relative to the repo root unless stated otherwise.

---

## Task 1: Add `.gitignore` and `README.md`

**Files:**
- Create: `.gitignore`
- Create: `README.md`
- Create: `LICENSE`

- [ ] **Step 1: Create `.gitignore`**

Write this file at `/Users/cristianmanoliu/Main/source.code/github/cristianmanoliu.github.io/.gitignore`:

```
# macOS
.DS_Store

# Editors
.vscode/
.idea/
*.swp

# OS
Thumbs.db
```

- [ ] **Step 2: Create `README.md`**

Write this file at `/Users/cristianmanoliu/Main/source.code/github/cristianmanoliu.github.io/README.md`:

```markdown
# cristianmanoliu.github.io

Personal presentation site — one page, plain HTML + CSS, hosted on GitHub Pages.

Live at: https://cristianmanoliu.github.io

## Local preview

Open `index.html` directly in a browser, or serve the directory:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy

Pushes to `main` are auto-deployed by GitHub Pages.
```

- [ ] **Step 3: Create `LICENSE` (MIT)**

Write this file at `/Users/cristianmanoliu/Main/source.code/github/cristianmanoliu.github.io/LICENSE`:

```
MIT License

Copyright (c) 2026 Cristian Manoliu

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

- [ ] **Step 4: Verify files exist**

Run from `/Users/cristianmanoliu/Main/source.code/github/cristianmanoliu.github.io`:

```bash
ls -1 .gitignore README.md LICENSE
```

Expected output (three lines, in any order):
```
.gitignore
LICENSE
README.md
```

- [ ] **Step 5: Commit**

```bash
git add .gitignore README.md LICENSE
git commit -m "chore: add gitignore, README, and MIT license"
```

---

## Task 2: Build `index.html` (markup only, no styling yet)

**Files:**
- Create: `index.html`

- [ ] **Step 1: Write `index.html`**

Write this file at `/Users/cristianmanoliu/Main/source.code/github/cristianmanoliu.github.io/index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Cristian Manoliu — Senior Software Engineer</title>
  <meta name="description" content="Senior Software Engineer with 15+ years of experience designing and delivering high-performance, scalable, and mission-critical systems.">
  <meta name="author" content="Cristian Manoliu">
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
    <p class="bio">Senior Software Engineer with 15+ years of experience designing and delivering high-performance, scalable, and mission-critical systems. Deeply experienced in event-driven systems, performance optimizations, and secure data processing at massive scale.</p>
    <nav class="links" aria-label="Profile links">
      <a href="https://github.com/cristianmanoliu" target="_blank" rel="noopener noreferrer">GitHub</a>
      <span class="sep" aria-hidden="true">·</span>
      <a href="https://www.linkedin.com/in/cristianmanoliu/" target="_blank" rel="noopener noreferrer">LinkedIn</a>
      <span class="sep" aria-hidden="true">·</span>
      <a href="mailto:cristian.manoliu@gmail.com">Email</a>
    </nav>
    <footer>© 2026 Cristian Manoliu</footer>
  </main>
</body>
</html>
```

- [ ] **Step 2: Verify markup loads in a browser**

Open the file:

```bash
open /Users/cristianmanoliu/Main/source.code/github/cristianmanoliu.github.io/index.html
```

Expected: page renders with unstyled content — name as a large heading (browser default), tagline + bio as paragraphs, three links separated by `·`, and the footer line. Links should be clickable. Page will look plain because `style.css` doesn't exist yet — that's expected; the file is created in Task 3.

- [ ] **Step 3: Validate HTML structure**

Run:

```bash
curl -s -F "out=text" -F "content=<index.html" https://validator.w3.org/nu/ | head -40
```

Expected: no `Error:` lines in output. (Warnings about `og:` properties may appear — those are fine.)

If the W3C validator is unavailable from CLI, instead open https://validator.w3.org/nu/#textarea in a browser, paste the file contents, and confirm no errors.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add index.html with semantic markup"
```

---

## Task 3: Write `style.css` — base typography and layout

**Files:**
- Create: `style.css`

- [ ] **Step 1: Write the base stylesheet**

Write this file at `/Users/cristianmanoliu/Main/source.code/github/cristianmanoliu.github.io/style.css`:

```css
/* Reset */
*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

/* Theme tokens (light mode default) */
:root {
  --bg: #fafafa;
  --fg: #111111;
  --muted: #666666;
  --accent: #2563eb;
}

/* Base */
html {
  font-size: 16px;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  background: var(--bg);
  color: var(--fg);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
}

/* Layout */
main {
  max-width: 640px;
  width: 100%;
}

/* Typography */
h1 {
  font-size: 2.5rem;
  font-weight: 600;
  letter-spacing: -0.02em;
  margin-bottom: 0.5rem;
}

.tagline {
  color: var(--muted);
  font-size: 1rem;
  margin-bottom: 2rem;
}

.bio {
  font-size: 1rem;
  line-height: 1.6;
  margin-bottom: 2rem;
}

/* Links row */
.links {
  margin-bottom: 3rem;
}

.links a {
  color: var(--fg);
  text-decoration: none;
  transition: color 120ms ease;
}

.links a:hover,
.links a:focus-visible {
  color: var(--accent);
  text-decoration: underline;
}

.links .sep {
  color: var(--muted);
  margin: 0 0.75rem;
}

/* Footer */
footer {
  color: var(--muted);
  font-size: 0.85rem;
}
```

- [ ] **Step 2: Reload and verify in a browser**

Reload `index.html` in the browser (Cmd+R). Expected:
- Off-white background (`#fafafa`)
- Name large and semi-bold
- Tagline in muted gray, sitting just under the name
- Bio paragraph with comfortable line-height
- Links horizontal, separated by muted middle-dots
- Hover on a link → text turns blue and underlines
- Footer small and muted at the bottom of the content
- Whole content vertically and horizontally centered in the viewport

If anything looks off, fix the CSS before continuing. Take a screenshot and verify against the spec.

- [ ] **Step 3: Commit**

```bash
git add style.css
git commit -m "feat: add base stylesheet — typography, layout, links"
```

---

## Task 4: Add dark mode and mobile responsive rules

**Files:**
- Modify: `style.css` (append rules at the end)

- [ ] **Step 1: Append dark mode rules**

Add to the end of `style.css`:

```css
/* Dark mode (auto via OS setting) */
@media (prefers-color-scheme: dark) {
  :root {
    --bg: #0f0f10;
    --fg: #eaeaea;
    --muted: #888888;
    /* --accent stays the same blue */
  }
}

/* Mobile */
@media (max-width: 480px) {
  body {
    padding: 1.25rem;
  }
  h1 {
    font-size: 2rem;
  }
  .tagline {
    margin-bottom: 1.5rem;
  }
  .bio {
    margin-bottom: 1.5rem;
  }
  .links {
    margin-bottom: 2rem;
  }
  .links .sep {
    margin: 0 0.5rem;
  }
}
```

- [ ] **Step 2: Verify dark mode in browser**

In the browser, toggle the OS to dark mode (System Settings → Appearance → Dark on macOS) and reload. Expected:
- Background near-black (`#0f0f10`)
- Text light gray (`#eaeaea`)
- Tagline / footer muted gray (`#888888`)
- Link hover still produces the same blue accent

Toggle back to light mode and reload — colors should revert.

Alternatively, use Chrome DevTools: open DevTools → ⋮ → More tools → Rendering → "Emulate CSS media feature prefers-color-scheme" → set to `dark`.

- [ ] **Step 3: Verify mobile layout**

In Chrome DevTools, toggle device toolbar (Cmd+Shift+M) and set width to 375px (iPhone SE). Expected:
- Page padding shrinks to ~1.25rem
- Name shrinks to ~2rem
- Spacing tightens but layout stays single-column and readable
- Middle-dot separators between links remain visible with smaller margins

- [ ] **Step 4: Commit**

```bash
git add style.css
git commit -m "feat: add dark mode and mobile responsive rules"
```

---

## Task 5: Create `favicon.svg` (CM monogram)

**Files:**
- Create: `favicon.svg`

- [ ] **Step 1: Write the favicon**

Write this file at `/Users/cristianmanoliu/Main/source.code/github/cristianmanoliu.github.io/favicon.svg`:

```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
  <text x="50%" y="50%"
        text-anchor="middle"
        dominant-baseline="central"
        font-family="-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif"
        font-size="18"
        font-weight="700"
        fill="#2563eb">CM</text>
</svg>
```

- [ ] **Step 2: Verify in browser**

Reload `index.html`. Expected: the browser tab shows a small blue `CM` icon. (On some browsers you may need a hard reload — Cmd+Shift+R — to refresh the favicon cache.)

Also open `favicon.svg` directly: `open /Users/cristianmanoliu/Main/source.code/github/cristianmanoliu.github.io/favicon.svg`. Expected: a square showing "CM" in blue, centered.

- [ ] **Step 3: Commit**

```bash
git add favicon.svg
git commit -m "feat: add CM monogram favicon"
```

---

## Task 6: Full-page acceptance check before deploy

**Files:** none (verification only)

This task confirms the spec's success criteria are met before pushing to GitHub.

- [ ] **Step 1: Local preview via http server**

From `/Users/cristianmanoliu/Main/source.code/github/cristianmanoliu.github.io`, run:

```bash
python3 -m http.server 8000
```

Open `http://localhost:8000` in a browser. Expected: page loads identically to `file://` open, all assets resolve (200 status for `style.css`, `favicon.svg`).

Stop the server with Ctrl+C when done.

- [ ] **Step 2: Verify all three links work**

In the browser:
- Click `GitHub` → opens `https://github.com/cristianmanoliu` in a new tab
- Click `LinkedIn` → opens `https://www.linkedin.com/in/cristianmanoliu/` in a new tab
- Click `Email` → triggers the OS mail client to compose to `cristian.manoliu@gmail.com`

- [ ] **Step 3: Lighthouse audit**

In Chrome DevTools (with the site served at `http://localhost:8000`), open the Lighthouse panel, select all four categories (Performance, Accessibility, Best Practices, SEO), choose "Desktop", and run the audit.

Expected: all four scores ≥ 95.

If any score is below 95, read the suggested fixes and address them before continuing. Common issues for static pages:
- SEO: missing `meta description` (already present — verify)
- Accessibility: insufficient color contrast (test with the configured colors)
- Best Practices: console errors (should be none)

- [ ] **Step 4: HTML validation**

Open https://validator.w3.org/nu/, paste the contents of `index.html`, and confirm zero errors.

- [ ] **Step 5: CSS validation**

Open https://jigsaw.w3.org/css-validator/, paste the contents of `style.css`, and confirm zero errors. (Vendor-prefix warnings for `-webkit-font-smoothing` and `-moz-osx-font-smoothing` are acceptable.)

- [ ] **Step 6: Commit any fixes (if needed)**

If steps 3-5 surfaced fixes, commit them:

```bash
git add -A
git commit -m "fix: address lighthouse/validator findings"
```

If no fixes were needed, skip this commit.

---

## Task 7: Create the GitHub repo and deploy

**Files:** none (deployment only)

- [ ] **Step 1: Verify `gh` CLI is authenticated**

Run:

```bash
gh auth status
```

Expected: shows logged-in account `cristianmanoliu` (or whatever account owns the GitHub Pages user site).

If not authenticated, the engineer should run `gh auth login` in their own terminal — do not perform the auth flow inside this plan.

- [ ] **Step 2: Create the public GitHub repo**

From `/Users/cristianmanoliu/Main/source.code/github/cristianmanoliu.github.io`, run:

```bash
gh repo create cristianmanoliu.github.io \
  --public \
  --source=. \
  --description "Personal presentation site" \
  --remote=origin
```

Expected output: confirmation that the repo was created at `https://github.com/cristianmanoliu/cristianmanoliu.github.io` and that `origin` was added as a remote.

If the repo already exists, instead run:

```bash
git remote add origin https://github.com/cristianmanoliu/cristianmanoliu.github.io.git
```

- [ ] **Step 3: Push `main` to origin**

```bash
git branch -M main
git push -u origin main
```

Expected: push succeeds, `main` tracking `origin/main`.

- [ ] **Step 4: Verify GitHub Pages is enabled**

Run:

```bash
gh api repos/cristianmanoliu/cristianmanoliu.github.io/pages 2>/dev/null || echo "pages-not-enabled"
```

If the response includes a `status` and `html_url`, Pages is already enabled (which is automatic for `*.github.io` user-site repos). If you see `pages-not-enabled`, enable it manually in the repo's Settings → Pages → Source: `Deploy from a branch` → `main` / `/ (root)`.

- [ ] **Step 5: Confirm the live site**

Wait ~30-60 seconds for the first deploy, then run:

```bash
curl -sI https://cristianmanoliu.github.io | head -3
```

Expected: `HTTP/2 200`. If you get `404`, wait another minute and retry; first deploys can take longer.

Then open `https://cristianmanoliu.github.io` in a browser. Expected: the page renders identically to local preview, with the favicon showing in the tab.

- [ ] **Step 6: Done**

No further commits required. Future content edits land via normal `git commit` + `git push`; GitHub Pages redeploys automatically.

---

## Notes for the implementer

- **No build step.** Don't add npm, no `package.json`, no bundler. If you find yourself wanting one, stop and reconsider.
- **No JavaScript.** The page should work with JS disabled.
- **No tracking, no analytics, no fonts from CDN.** The page must make zero third-party requests.
- **Commit cadence:** one commit per task, as written. Don't squash; the small history is fine.
- **If you change the bio or links,** update them in `index.html` *and* in the spec (`docs/superpowers/specs/2026-05-06-personal-site-design.md`) so the spec stays accurate.
