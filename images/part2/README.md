# Part 2 artwork

## Hero — delivered ✅

Three layers, all sharing one 2000 × 1306 frame and pre-aligned by the
designer. They are composited in CSS, not flattened.

| File | Role | Content bbox | Size |
|---|---|---|---|
| `hero-sky.jpg` | back — sky plate | full frame | 320 KB → 12 KB webp |
| `hero-title.png` | middle — "The LETTERS / الرسائل" lockup, white on transparent | x 248–832, y 404–900 | 42 KB → 18 KB webp |
| `hero-figure.png` | front — HH Sheikh Mohammed cutout | x 964–1900, y 88–1304 | 1545 KB → 156 KB webp |

WebP versions are generated and wired with PNG/JPEG fallback via `image-set()`.
**1.9 MB → 186 KB, 90% smaller**, alpha preserved, verified visually
indistinguishable at 132% zoom.

### Rules if these are ever re-exported

- **Keep all three on the identical 2000 × 1306 frame.** The title and figure
  are rendered at the same size and position so the lockup cannot separate.
  Trimming either one to its bounding box breaks the alignment.
- **Layers 2 and 3 must stay PNG with a real alpha channel.** As JPEG they
  gain a white box and occlude everything beneath.
- Only the sky is allowed to move (subtle scroll drift). The title and figure
  carry no transform.
- Nothing is drawn on top of the art — the page title lives in the HTML as a
  visually hidden `<h1>`, so search and screen readers still get it.
- Re-run the WebP pass after any re-export, or the CSS will point at a stale
  `.webp`. Both formats must change together.

### ⚠️ A portrait crop is still needed

The artwork is a 1.53:1 landscape lockup with the title hard left and the
figure hard right. A phone viewport is ~0.46:1. Cropping to fill would cut off
*both* the title and the figure, so the lockup is currently scaled to fit
inside the width with a 5% gutter — it occupies only **~33% of the hero
height** on a phone, floating in sky.

It is correct and nothing is clipped, but it is not the impact the desktop
composition has. **A portrait re-composition (title stacked above the figure,
roughly 1600 × 2100) would fix it properly.** Save as:

- `hero-sky-mobile.jpg`
- `hero-title-mobile.png`
- `hero-figure-mobile.png`

## Still outstanding

| File | Size (px) | Used for |
|---|---|---|
| `cover.jpg` | 2400 × 1600 | Book cover band |
| `cover-mobile.jpg` | 1600 × 1600 | Same, under 900px |
| `feature.jpg` | 2400 × 1100 | Wide feature band below the copy |
| `feature-mobile.jpg` | 1600 × 1200 | Same, under 900px |
| `share.jpg` | 1200 × 630 | Social sharing card (OG / Twitter) |
| `../apple-touch-icon.png` | 180 × 180 | iOS home screen |

**Send these as plain `.jpg`.** The loader tries `.webp` first and falls back
to `.jpg` on its own, so a JPEG-only delivery works immediately and picks up
the WebP automatically once the optimisation pass has run.

- `cover.jpg` and `feature.jpg` are `background-attachment: fixed` on desktop,
  so keep the subject clear of the extreme top and bottom edges.
- Palette: navy `#1E3E69`, deep navy `#16304F`, gold `#A08F69`, light gold
  `#A89875`.
- `images/logo.png` is still the Part 1 file at 209 × 115; a 2× or SVG version
  would sharpen it on retina.
