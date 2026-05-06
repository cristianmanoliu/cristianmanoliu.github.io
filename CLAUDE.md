# CLAUDE.md

Project context for AI assistants working on this repo.

## What this is

A static one-page personal site for Cristian Manoliu, hosted on GitHub Pages at
`https://cristianmanoliu.github.io`. Pure HTML + CSS, served from the root of the
`main` branch.

## Hard constraints

- **No JavaScript.** The page must work fully with JS disabled.
- **No build step.** No `package.json`, no bundler, no preprocessor. Edit, push, deploy.
- **No third-party requests.** No CDN fonts, no analytics, no trackers, no embeds.
- **No frameworks.** Plain HTML and plain CSS only.
- **`main` is the deploy branch.** A `git push` on `main` goes live in ~30 seconds.

If a change would require any of the above, stop and confirm with the user first.

## File responsibilities

- `index.html` — semantic markup and meta tags. One file. No partials.
- `style.css` — all styling. Theme tokens defined as CSS variables in `:root`.
  Mobile rules live in a single `@media (max-width: 480px)` block at the bottom.
- `favicon.svg` — inline SVG monogram. Color is `var(--accent)` equivalent.
- `avatar.jpg` — 320×320 profile photo.
- `matrix-bg.jpg` — 1920×1080 fixed background image.

## Visual style

- Permanent dark theme — Matrix backdrop with a ~55% black overlay
- Accent color: Matrix green `#00ff66`
- Content sits in a glass card (`backdrop-filter: blur`) over the background
- Mobile breakpoint at 480px — avatar shrinks, background switches to `scroll`
  attachment to avoid stutter on iOS

If the visual direction needs to change, update both `style.css` and the design
spec in `docs/superpowers/specs/` so the spec stays authoritative.

## Image rules

When adding or replacing images:

- **Backgrounds:** resize to ~1920px on the long edge, JPEG quality ~80, target
  ≤600KB. Use `sips -Z 1920 -s formatOptions 80 input output`.
- **Avatars / icons:** square, ~320px (covers retina up to 160px display),
  JPEG quality ~85.
- **Never** commit the original 4K/8K source — only the optimized version.

## Quality bars

Before pushing visible changes:

- HTML validates at https://validator.w3.org/nu/ (zero errors)
- CSS validates at https://jigsaw.w3.org/css-validator/ (zero errors;
  vendor-prefix and CSS-variable warnings are acceptable)
- Lighthouse Desktop scores ≥ 95 across Performance, Accessibility,
  Best Practices, SEO

## Commit style

- One logical change per commit
- Conventional prefixes: `feat:`, `fix:`, `chore:`, `docs:`, `style:`
- Co-author trailer when pairing with Claude

## Where to look for context

- `docs/superpowers/specs/2026-05-06-personal-site-design.md` — original design spec
- `docs/superpowers/plans/2026-05-06-personal-site.md` — implementation plan
- Git history — most recent state is authoritative if it diverges from docs
