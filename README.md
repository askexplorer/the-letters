# The Letters — Lessons from Life: Part II

Landing page for *علّمتني الحياة: الجزء الثاني – الرسائل* / *Lessons from Life:
Part II – The Letters* by HH Sheikh Mohammed bin Rashid Al Maktoum.

Published by Explorer Publishing. Replaces the Part 1 page at
`askexplorer.com/lessonsfromlife/`.

## Running it

Static site — no build step, no dependencies.

```bash
python3 -m http.server 8777
```

Then open <http://localhost:8777/>.

## Layout

```
index.html          the page — markup, schema, inline JS
css/site.css        the entire stylesheet
images/part2/       artwork in use
images/part2/_reference/   design sources, not shipped
```

Sections, in order: hero → the book → quote → about → feature *(collapsed until
its artwork exists)* → specs → pre-order → bulk sales → footer.

## Notes for whoever picks this up

- **Fonts are self-hosted.** Lateef ships from `fonts/`, Arabic subset only —
  the English column is Georgia, so Google's latin faces were dead weight.
- **No framework.** The Part 1 page loaded 1.44 MB of Canvas theme, bootstrap
  and jQuery for five sections. This is one 19 KB stylesheet and ~2 KB of
  inline JS.
- **Image bands self-activate.** A section with `data-bg` stays collapsed until
  its image loads, trying `.webp` then `.jpg`. Drop a file in and it appears —
  no code change. Sections carrying real content never self-hide.
- **Replaced an image in place? Bump its `?v=` marker.** Browsers holding the
  old file will otherwise keep serving it, and the CSS will apply new geometry
  to stale artwork.
- **Hero is three composited layers** (sky / title / figure), not a flat image,
  so it can rearrange between landscape and portrait. See
  `images/part2/README.md` before re-exporting any of them.
- **Parallax** is gated to fine pointers at ≥900px and motion-safe only; iOS
  ignores `background-attachment: fixed` and jitters.

## Note on crawling

There is deliberately no `robots.txt` here. One briefly existed to keep the
public preview out of search, but it sat at `/the-letters/robots.txt` and
crawlers only read the file from a **domain root** — a copy in a subfolder is
ignored entirely, so it never had any effect.

To actually keep a deployment out of search you need either a `robots.txt` at
the domain root (`askexplorer.com/robots.txt`), which is outside this project,
or `<meta name="robots" content="noindex">` in `index.html` — and that must be
removed before production or the live page becomes invisible to Google.

## Outstanding

- `images/part2/feature.jpg` — that section stays collapsed until it lands
- `images/part2/share.jpg` (1200×630) — social card
- **Publication date** — omitted from the schema rather than invented
