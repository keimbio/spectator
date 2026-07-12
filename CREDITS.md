# Credits & third-party notices — Spectator

Spectator is released under the MIT License (see `LICENSE`). It is an original implementation,
but it stands on knowledge and one piece of data from the open-source community.

## Embedded material (attribution required)

- **Procreate brush-parameter schema** — adapted from
  [aumlette-lab/procreate-brush-decoder](https://github.com/aumlette-lab/procreate-brush-decoder)
  (MIT License). A trimmed version of its parameter map (setting names, archive paths, and value
  formulas) is embedded to label decoded brush parameters. Used under the MIT License.

## Runtime libraries (loaded from CDN, not bundled)

- **JSZip** — MIT License. https://stuk.github.io/jszip/
- **jsPDF** — MIT License. https://github.com/parallax/jsPDF

If you self-host these instead of loading them from a CDN, include their MIT notices alongside
the copies you distribute.

## Format & technique references (no code copied — acknowledged with thanks)

File formats and techniques are facts/ideas rather than copyrightable expression, so these
projects' licenses do not attach to Spectator. Credited out of respect.

- [jaromvogel/prospect](https://github.com/jaromvogel/prospect) (GPLv3) — the macOS Procreate
  viewer that inspired this tool; demonstrated the `QuickLook/Thumbnail.png` preview approach.
- [tohsakrat/Brush-Converter](https://github.com/tohsakrat/Brush-Converter) (CC BY-NC-SA 4.0) —
  reverse-engineering write-up that aided understanding of the Photoshop `.abr` sampled-brush
  layout, and confirmed the `Reset/` + `Sub01/` brushset folder semantics.
- [aredridel/mkbrushset](https://github.com/aredridel/mkbrushset) (AGPLv3) — reference for the
  Procreate `.brushset` packaging method.
- [joanroig/palette-studio](https://github.com/joanroig/palette-studio) (GPLv3) — reference for
  the overall UI structure.

Photoshop `.abr` parsing is based on the publicly documented format
(http://fileformats.archiveteam.org/wiki/Photoshop_brush) and Adobe's file-format specification.
