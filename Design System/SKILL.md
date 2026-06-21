---
name: ai-code-academy-design
description: Use this skill to generate well-branded interfaces and assets for AI Code Academy, either for production or throwaway prototypes/mocks/slides. Contains essential design guidelines, colors, type, fonts, assets, and UI kit components for prototyping.
user-invocable: true
---

Read the `readme.md` file within this skill, and explore the other available files.

If creating visual artifacts (slides, mocks, throwaway prototypes, etc), copy assets out and create static HTML files for the user to view. If working on production code, you can copy assets and read the rules here to become an expert in designing with this brand.

If the user invokes this skill without any other guidance, ask them what they want to build or design, ask some questions, and act as an expert designer who outputs HTML artifacts _or_ production code, depending on the need.

## Quick reference

- **Brand:** AI Code Academy — clean, modern, friendly teaching/course materials.
- **Colors:** navy `#224289` (primary), teal `#61cbc8` (secondary), amber `#fcb600` (accent). Navy-tinted slate neutrals.
- **Type:** Rubik (rounded geometric sans, 700–800 display / 400–500 body) + JetBrains Mono for code.
- **Voice:** second person, encouraging, sentence case, plain language, no emoji.
- **Look:** rounded corners, soft navy-tinted shadows, flat fills, brand "blobs" + amber dot, two-column slides.

## Files
- `styles.css` — link this for all tokens + fonts.
- `tokens/` — color, type, spacing, font tokens (CSS custom properties).
- `guidelines/` — foundation specimen cards.
- `components/core/` — Button, Badge, Card, Callout (tip=green / warning=amber / dont=red / note=navy), CodeBlock.
- `components/media/` — MaterialCard, ImageFrame, ScreenshotCard, VideoCard (load `_ds_bundle.js`, read from `window.DesignSystem_df7c10`).
- `slides/` — 1280×720 slide templates + `slide-frame.css` (fixed header / head block / footer).
- `assets/` — logos, course PNG icons, hardware photos, Rubik fonts. See
  `assets/assets.md` for a catalog of every asset (what each looks like + when to use it).
- `skills/` — bundled export skills (see below).

## Exporting lesson slides

Bundled export skills live in `skills/` and ship with this system so they travel
with it. Build lesson slides from `templates/lesson-deck/` first, then run these against
the saved `.html`:

- `skills/export-deck-pdf/` — `python skills/export-deck-pdf/export_pdf.py
  <deck.html>` → a clean 16:9 PDF (one slide per page, real selectable text,
  clickable links), via headless Edge/Chrome print-to-PDF driven by the deck's
  `@media print` rules.
- `skills/export-deck-pptx-screenshot/` — `python
  skills/export-deck-pptx-screenshot/build_pptx.py <deck.html>` → a 16:9 `.pptx`
  where each slide is a pixel-perfect image, with the slides' speaker notes and
  clickable link hotspots preserved (needs `python-pptx` + `pymupdf`). Slide text
  is a rendered image, not editable text boxes — the fidelity/editability
  trade-off.
