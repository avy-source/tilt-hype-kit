# Tilt Hype Kit

A self-serve marketing asset builder for Tilt sellers. Sellers enter their handle, pick a language and purpose, optionally upload a profile photo, and generate branded, share-ready graphics for Instagram, TikTok, Facebook, Discord, and more — then download them as PNGs.

This is a **UX/UI prototype** (a single self-contained HTML file) intended for feedback and engineering handoff, not production code.

## View it

- **Live (GitHub Pages):** once published, visit `https://<your-username>.github.io/<repo-name>/`
- **Locally:** just open `index.html` in any modern browser (Chrome, Safari, Edge). No build step, no server needed.

### Publish to GitHub Pages
1. Create a repo and upload `index.html` (keep that filename so it loads at the root URL).
2. **Settings → Pages → Build and deployment** → Source: *Deploy from a branch*, Branch: `main`, folder: `/ (root)`.
3. Wait ~1 minute, then share the Pages URL.

## What's in it

**Two views**
- **Landing / Get Started** — Hype Kit hero, a short form (Language, Tilt handle, Logo/avatar, Purpose), and an "Enter Studio" key.
- **Studio** — the editor. A "← Back" button returns to the landing.

**Four templates (purposes)**
- Discount / referral
- Live announcement
- New drop hype
- Community invite

**Sizes / platforms**
- Square 1:1 (Instagram · Facebook)
- Portrait 4:5 (Instagram · Facebook)
- Portrait 9:16 (Instagram Stories & Reels)
- Portrait 9:16 (TikTok)
- Landscape 16:9 (Discord · X · YouTube)

**Features**
- Live preview that updates as you type.
- Light / Dark mode toggle for the asset; Aurora glow toggle.
- Profile photo: drag to reposition, zoom to scale (click the circle to open the controls).
- Localisation: US English, UK English, Italian, Spanish, Polish — with currency (`$ / £ / € / zł`) and per-locale phrasing.
- The promo code auto-derives as the uppercased handle (no separate field).
- Export: **Download PNG** (current size), **Download all sizes**, and **Batch view** (see all sizes at once, with per-size download and a dark/light + aurora toggle).
- Content is laid out inside the current platform safe zones.

## Notes for engineering

- **Single file.** Everything is inlined — no external assets except the `html-to-image` library (loaded from a CDN) used for PNG export.
- **Typeface:** Aspekta (weights 500 + 650 only), embedded as base64 woff2. The source files shipped without kerning, so a `kern` feature was generated and injected for loose uppercase/lowercase pairs.
- **Brand assets:** Tilt wordmark, the Live pill, and the App Store / Google Play badges are the official SVGs, inlined. The landing keycaps and "Enter Studio" key are the supplied transparent PNGs.
- **Export approach:** each poster renders at true pixel size (e.g. 1080×1080); the preview is only visually scaled via a CSS transform, so exports are pixel-exact.
- **Safe zones** live in a single `SAFE_ZONES` object — tune per platform there.
- **Two views** are toggled by show/hide in one file. For production, map them to real routes/components in the seller portal (e.g. `/hype-kit` and `/hype-kit/studio`) so browser back/forward and deep links work natively.
- **Localised copy** lives in the `STRINGS` object; templates and their sample copy live in `TEMPLATES`.

## Feedback

Open it, click through the templates and sizes, try light/dark + aurora, upload a photo and reposition it, and run Batch view. Notes welcome on copy, layout, and which formats matter most.
