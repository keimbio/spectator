# ₊°˖.⟡ ݁. Spectator – Brush Studio⋆°.⊹ ݁₊*。݁

A single-file, client-side previewer & packager for Procreate (`.brush`, `.brushset`) and
Photoshop (`.abr`) brushes. Everything runs in your browser — files are never uploaded.

## Deploy
Drop `index.html` in a repo and enable GitHub Pages, or just open it locally. Identical
capability either way (pure client-side). No build step.

Edit two constants near the top of the `<script>` to point the footer at your repo:
`REPO_URL` and `APP_VERSION`.

## Features
- Batch-load `.brush`, `.brushset`, `.abr` — click the Brushes box or drag & drop onto it.
- **Dual brushes** are kept intact (not split); their secondary shape/grain show in the info panel.
- Brushset brush **names and order** come straight from the set's `brushset.plist`.
- Grid / Stack views with adjustable column count.
- Info panel: name, source, dates, decoded Procreate parameters, plus Preview / Shape / Grain
  (and Secondary shape/grain for dual brushes), each with its own Save link.
- Export previews — Separate (zip) / Stacked / Strip / Grid, as PNG / JPEG / WEBP / TIFF / PDF,
  with an optional name caption.
- Export shape + grain PNGs; split a `.brushset` into individual `.brush` files; package selected
  Procreate brushes into a new `.brushset`.
- `.abr` tips → PNG (reliable Photoshop route) and an experimental `.abr` → `.brush` converter.

## Notes
- Writing real `.abr` files isn't reliably possible in-browser (the newer format isn't fully
  documented); use the PNG-tip route for Photoshop. See `CREDITS.md`.
- License: MIT (see `LICENSE`). Attribution for the embedded parameter schema is in `CREDITS.md`.
