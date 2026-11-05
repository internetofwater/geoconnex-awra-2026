# Linking the Fabric: Persistent Identifiers and the Geoconnex Knowledge Graph

Slides for the 2026 AWRA Annual Water Resources Conference (Philadelphia, Nov 9-11), built with [Slidev](https://sli.dev). The talk covers how Geoconnex mints persistent identifiers for water features, links data across agencies, and how organizations can contribute.

## Run it

Requires Node 20.19+ (22 recommended).

```bash
npm install
npm run dev      # present / edit at http://localhost:3030
npm run build    # static site in dist/
npm run export   # PDF export (needs: npx playwright-chromium install chromium)
```

## Layout

| Path | What it is |
| --- | --- |
| `slides.md` | All slides |
| `style.css` | CGS brand colors, fonts, shared card styles |
| `layouts/hero.vue` | Gradient title/closing layout with the graph motif |
| `components/WaterIcon.vue` | Icon set (gage, dam, river, aquifer, ...) used in the diagrams |
| `global-top.vue` | Co-brand footer on content slides (set `footer: false` in a slide's frontmatter to hide it) |
| `public/` | Headshot and logos (CGS, USGS, Internet of Water, agencies) |
| `.claude/skills/` | CGS design and Geoconnex reference skills used while authoring |

## Deploy

Every push to `main` builds the deck and publishes it to GitHub Pages via `.github/workflows/deploy.yml`. One-time setup: Settings → Pages → Source: **GitHub Actions**.

## Notes

- Brand colors and typography follow the CGS guidelines (District Pro / Aptos, with fallbacks if not installed).
- Agency and organization logos belong to their respective owners.
