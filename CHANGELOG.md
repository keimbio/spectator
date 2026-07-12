# Changelog

All notable changes to Spectator are documented here.
Format based on [Keep a Changelog](https://keepachangelog.com/); versioning follows [SemVer](https://semver.org/).

## [3.2.1] - 2026-07-12

### Fixed
- **Brushes from a `.brushset` now load in the set's true order.** Procreate writes
  `brushset.plist` as an **XML** plist, while `Brush.archive` inside each brush folder is a
  **binary** plist. Spectator only had a binary-plist reader, so parsing `brushset.plist` threw,
  the brush order silently fell back to ZIP central-directory order (which is arbitrary), and
  brushes appeared shuffled. Brush *names* still worked, which masked the failure — they come
  from the binary `Brush.archive`, not the manifest.
- Added an XML plist parser. `brushset.plist` is now sniffed by header (`bplist00` vs `<?xml`)
  and read with the appropriate parser, so both formats are handled.

### Added
- Logo displayed beneath the site credit in the footer.

### Changed
- Version bumped to 3.2.1.

## [1.0.1] - 2026-07-12

### Fixed
- Handled `NSKeyedArchiver`-wrapped `brushset.plist` (where `brushes` is an `NS.objects` array of
  UID references) in addition to the plain form; case-insensitive manifest lookup; brush folders
  missing from the manifest are appended rather than dropped.

## [1.0.0] - 2026-06-14

### Added
- Initial release: Procreate `.brush` / `.brushset` and Photoshop `.abr` preview, inspection,
  export and packaging. Runs entirely client-side.
- Grid / Stack views with adjustable column count; click-or-drop import.
- Info panel with decoded Procreate parameters, shape, grain, and dual-brush secondary sources.
- Preview export (PNG / JPEG / WEBP / TIFF / PDF), shape+grain export, `.brushset` split and package.

### Fixed
- NSKeyedArchiver `UID` values were resolved against the wrong object table, which erased brush
  names and all decoded parameters.
- `Reset/` and `Sub01/` subfolders were treated as separate brushes, splitting dual brushes in two.
