# cristianmanoliu.github.io

Personal presentation site — one page, plain HTML + CSS, hosted on GitHub Pages.

**Live:** https://cristianmanoliu.github.io

## Stack

- HTML5 + CSS3, no JavaScript
- No build step, no framework, no dependencies
- System font stack (no Google Fonts)
- Auto-deployed by GitHub Pages on push to `main`

## Files

| Path | Purpose |
| --- | --- |
| `index.html` | Page markup and meta tags |
| `style.css` | All styling (theme tokens, layout, responsive rules) |
| `avatar.jpg` | Profile photo (320×320) |
| `matrix-bg.jpg` | Background image (1920×1080) |
| `favicon.svg` | Browser-tab icon (CM monogram) |
| `docs/` | Design spec and implementation plan |

## Local preview

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

Or just open `index.html` directly in a browser.

## Deploy

```bash
git push
```

GitHub Pages rebuilds automatically; the new content is live in ~30 seconds.

## License

MIT — see [LICENSE](LICENSE).
