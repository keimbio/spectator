# Changelog

All notable changes to Spectator are documented here.
Format based on [Keep a Changelog](https://keepachangelog.com/); versioning follows [SemVer](https://semver.org/).

## [1.0.1] - 2026-07-12

### Fixed
- **Brushes from a `.brushset` now load in the set's real order.** `brushset.plist` is written in
  two different shapes: a plain plist (`{name, brushes:[...]}`) and an `NSKeyedArchiver` archive
  (where `brushes` is an `NS.objects` array of UID references). Only the first shape was handled,
  so archived sets silently fell back to ZIP central-directory order — which is arbitrary, and
  showed brushes shuffled (e.g. 4, 2, 1, 3). Both shapes are now parsed, and UID entries are
  dereferenced to their folder names.
- `brushset.plist` is now located case-insensitively.
- Brush folders present in the archive but missing from `brushset.plist` are appended at the end
  instead of being dropped.
- If the order can't be read, a warning is logged to the console rather than failing silently.

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
