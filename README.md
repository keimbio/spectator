# ₊°˖.⟡ ݁. Spectator – Brush Studio⋆°.⊹ ݁₊*。݁

A single-file, client-side previewer & packager for Procreate (`.brush`, `.brushset`) and Photoshop (`.abr`) brushes. Nothing is uploaded — every file is read and written in your browser.

## Deploy
- **GitHub Pages:** drop `index.html` in a repo, enable Pages, done. Works identically opened as a local file (`file://`) — it's pure client-side, so there's no functional difference between the two.
- No build step, no dependencies to install. JSZip and jsPDF load from cdnjs.

## What it does

**Solid / validated**
- Batch-load any mix of `.brush`, `.brushset`, `.abr`. Each brush becomes a card.
- Select individually, **Select all**, **Clear**, or **Only Procreate**.
- **Info panel** (the `i` button): name, source file, file-modified date, decoded Procreate parameters (135-setting schema with GUI-value formulas), plus the **shape** and **grain** images — each with its own save link.
- **Export previews as images:** layout = Separate (zipped) / Stacked ↓ / Strip → / Grid; format = **PNG / JPEG / WEBP / TIFF / PDF**; optional **name caption** (top-left); tile size, gap, white-bg toggle.
- **Export shape + grain PNGs** for the selection (zipped).
- **Package → `.brushset`** from selected Procreate brushes — preserves each original `Brush.archive`, shape, grain and thumbnail, and writes a valid binary `brushset.plist`.
- **Split → individual `.brush`** files (from `.brushset` members).

**Beta (heuristic, verify against your files)**
- `.abr` tip-bitmap extraction & preview. Targets v6+ sampled brushes; some versions/records may not decode, in which case the card is flagged.
- `.abr` → `.brush` (experimental): transfers the tip into a Procreate brush using a loaded `.brush` as a parameter **template**. Load one Procreate brush first; behavior parameters come from the template, not the source `.abr`.

**Reliable Photoshop route (instead of writing `.abr`)**
- `.abr` tips → PNG. In Photoshop: **Edit ▸ Define Brush Preset**.

## What it deliberately does NOT do
Writing real `.abr` files (`.brush` → `.abr`, or compiling a new `.abr`) is **not done**, because the newer `.abr` write format isn't fully reverse-engineered — the most thorough open decoder states it can unpack but not repack `.abr`, and the commercial converters run a server backend for this. Producing fake `.abr` files that Photoshop silently rejects would be worse than not offering it. Use the PNG-tip route above, or run a local Python backend for true `.abr` authoring (can be added separately).

## Notes
- Procreate brushes generally don't store created/modified dates internally, so the panel shows the file's modified time; any date fields found in the archive are surfaced too.
- Verified in-engine: the binary-plist reader (against Apple-format plists), the `brushset.plist` writer (round-trips through `plistlib`), the parameter formula evaluator, and the TIFF encoder. The Procreate archive decode and ABR parser should be validated against your own files.
