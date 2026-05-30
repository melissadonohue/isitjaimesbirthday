# Asset manifest

## In place
- `cursors/crab-open.svg` — default crab cursor. CSS hotspot ~ `6 4`.
- `cursors/crab-pinch.svg` — active/click state (claws pinched).
- `img/dog-placeholder.svg` — cobalt dachshund-in-circle. **Placeholder** — swap for the real photo.
- `vendor/anime.umd.min.js` — anime.js v4.4.1 (global `anime`). For final deploy, inline into index.html.

## Still needed from Melissa
1. **Faffin Medium .ttf** — the JKK display face. The prior session's embedded base64 was lost
   when temp files cleared. Re-source the licensed file; we'll base64-embed it. (Public domain
   hosting needs a webfont license or a free display fallback — flagged in CLAUDE.md.)
2. **Dog photo** — the transparent dachshund cutout (from `IMG_5031.heic`). Re-upload; we'll
   clean the fringe and bake it into the dog-rain in place of the placeholder.
3. *(optional)* a photo of the two of them, to sit inside the cobalt circle.

## Usage notes
- Cursor: `cursor: url(assets/cursors/crab-open.svg) 6 4, auto;` then swap to crab-pinch on `:active`.
- Real dog: replace `CONFIG.dogPhoto` with a `data:image/png;base64,...` or path; the rain
  generator clones it.
