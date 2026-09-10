# Part 2 artwork slots

Drop files here using these exact names. The CSS picks them up automatically —
no code change needed. Until a file exists, the section falls back to a
designed navy gradient, so the page never looks broken.

| File | Size (px) | Used for |
|---|---|---|
| `layer-1-sky.jpg` | 2400 × 1600 | Hero layer 1 — sky plate (back) |
| `layer-2.png` | 2400 × 1600 | Hero layer 2 — wash / haze (middle) |
| `layer-3-figure.png` | 2400 × 1600 | Hero layer 3 — figure cutout (front) |
| `layer-1-sky-mobile.jpg` | 1600 × 2100 | Hero layer 1, portrait crop under 900px |
| `layer-2-mobile.png` | 1600 × 2100 | Hero layer 2, portrait crop |
| `layer-3-figure-mobile.png` | 1600 × 2100 | Hero layer 3, portrait crop |
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

## The hero is three stacked layers

The hero is composited in CSS, not flattened. The three files stack in order
(sky → wash → figure) and drift at different rates on scroll for depth.

- **Layers 2 and 3 must be PNG with a real alpha channel.** Exported as JPEG
  they gain a white box and hide everything beneath them.
- **Layer 3 (the figure) is anchored bottom-right** and scaled to the frame
  height on desktop, bottom-centre at 78% height on mobile. Export it on a
  fully transparent canvas at the same 2400 × 1600 frame as the other two —
  do not trim to the figure's bounding box, or the alignment shifts.
- All three share one frame size, so they line up automatically.
- Nothing is drawn on top of the art. The page title exists in the HTML but is
  visually hidden, so search and screen readers still get it.

## Notes for the designer

- **No overlay is applied to the hero any more** — what you export is what
  renders, so bake the final contrast and tone into the layers themselves.
- `cover.jpg` and `feature.jpg` are `background-attachment: fixed` on desktop,
  so keep the subject away from the extreme top and bottom edges.
- Palette in use: navy `#1E3E69`, deep navy `#16304F`, gold `#A08F69`,
  light gold `#A89875`.

## Also still needed

- `images/apple-touch-icon.png` — 180 × 180
- `images/logo.png` — currently the Part 1 file at 209 × 115; a 2× or SVG
  version would sharpen it on retina.
