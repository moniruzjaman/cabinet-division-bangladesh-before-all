# Fertilizer Management: Walking The Path towards nationalism to Bloom 🌾
Self-contained interactive landing page for the Ministry of Agriculture briefing (Sept 2026).
Single `index.html` — no build step, no CDN, no external assets.

## Deploy to GitHub Page from workflows deploy.yml

## Icons (zero binary files in repo)
- **Favicon:** inline SVG data-URI of a golden panicle of rice (works with JS disabled).
- **Apple touch icon:** generated at runtime on a `<canvas>` and attached as a **JPEG data-URI**
  (`link rel="apple-touch-icon"`), with a PNG fallback link for legacy browsers.
- Want a static file? Open the page, run `copy(window.__iconDataURL)` in the console,
  save as `apple-touch-icon.jpg` at the repo root, and replace the empty `href` in `<head>`.
