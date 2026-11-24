# AGU 2026 poster: live doublet frames (WebAR)

Point a phone at the poster (paper S31C-3486) and section 4, the grid of doublet frames, plays as a
movie: 30 years of pressure, temperature and fault loading in 15 seconds. Image tracking with
MindAR 1.2.5 + A-Frame 1.5.0, served by GitHub Pages at https://ddempsey.github.io/agu2026-ar/

- `index.html`: the AR page. The target is the whole 44 x 44 in poster (1 unit = 44 in); the video
  plane covers section 4 (see the comment in the scene). Nine clips: the five printed rows
  (balanced, cooling + fault loading, losing 10% open, overbalanced closed, five-spot) and four
  cases not printed (fixed-pressure producer open, losing 3%, gaining 1%, losing 3% in a closed
  compartment). Full screen has a time slider.
- `poster.mind`: compiled image target, from PowerPoint's own render of the `_qr_v2` pptx
  (six-row section 4, Nov 2026) at 1000 px. Rebuild whenever the poster layout changes:
  `node tools/compile_mind.js target.png poster.mind`.
- `poster.jpg`: the same render, for testing from a laptop screen.
- `media/*.{mp4,webm}`: 1280x720 clips, 180 log-spaced times from 0.01 to 30 yr at 12 fps plus a
  1.5 s hold, H.264 crf 24 + VP9 crf 38. Built in the paper repo (`egs_is_sc/poster_agu26/ar`):
  `compute_ar_fields.py <case>` then `render_clips.py`.
- `tools/test_ar.js`: headless test with a fake camera. Keep the y4m small (3 s at 10 fps) and
  pass an absolute Windows path, or Chromium's fake camera delivers no frames.

Tools need `npm i` (playwright, qrcode@1.5.4) and the Chromium at
`%LOCALAPPDATA%/ms-playwright/chromium-1193`.
