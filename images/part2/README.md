# Part 2 artwork slots

Drop files here using these exact names. The CSS picks them up automatically —
no code change needed. Until a file exists, the section falls back to a
designed navy gradient, so the page never looks broken.

| File | Size (px) | Used for |
|---|---|---|
| `hero.jpg` | 2400 × 1600 | Full-screen opening band |
| `hero-mobile.jpg` | 1600 × 2100 | Same, portrait crop under 900px |
| `cover.jpg` | 2400 × 1600 | Book cover band |
| `cover-mobile.jpg` | 1600 × 1600 | Same, square-ish crop under 900px |
| `feature.jpg` | 2400 × 1100 | Wide feature band below the copy |
| `feature-mobile.jpg` | 1600 × 1200 | Same, under 900px |
| `share.jpg` | 1200 × 630 | Social sharing card (OG / Twitter) |

**JPEG only for now.** Hand over plain `.jpg` files — do not add `.webp`
yourself. WebP versions get generated in the optimisation pass, which also
switches the CSS over to `image-set()` at the same time. (If the CSS points at
a WebP that does not exist, the browser leaves the slot blank rather than
falling back to the JPEG, so the two have to change together.)

## Notes for the designer

- **Leave the type off `hero.jpg`.** The title, Arabic title, series line and
  "coming soon in English" badge are all live HTML text sitting on top of it —
  that is what fixes the SEO and screen-reader problems the Part 1 page had.
  A clean photographic or textured plate is what this slot wants.
- A dark overlay (navy, ~30–62% top to bottom) is applied over the hero
  automatically, so the art can be lighter than the finished result looks.
- `cover.jpg` and `feature.jpg` are `background-attachment: fixed` on desktop,
  so keep the subject away from the extreme top and bottom edges.
- Palette in use: navy `#1E3E69`, deep navy `#16304F`, gold `#A08F69`,
  light gold `#A89875`.

## Also still needed

- `images/apple-touch-icon.png` — 180 × 180
- `images/logo.png` — currently the Part 1 file at 209 × 115; a 2× or SVG
  version would sharpen it on retina.
