# Changelog

All notable changes to Foundry Studio are recorded here.
Format follows Keep a Changelog. Versioning follows Semantic Versioning.

## [5.0.0] - 2026-07-13

### Changed
- **Motion engine is now SMIL instead of CSS keyframes.** CSS keyframes
  on SVG text are not dependable in WebKit, and CSS filter on SVG does
  not render on iOS at all. Every animation is now `<animate>` or
  `<animateTransform>`, which the SVG engine runs directly.
- Exported SVGs now satisfy a hard rule: **the static markup is the
  finished picture.** Strip every animation out and the image is still
  correct. "Anim: off" in the canvas header previews exactly that.
- Toolbar is grouped into ADD, EXPORT, and PROJECT, each with its own
  rail color and button shape.

### Fixed
- Text never appeared, or appeared in the wrong position, on iOS Safari.
  The entrance animation parked on its first keyframe.
- The color cycle rendered nothing on any iPhone. It used
  `filter: hue-rotate`, which iOS Safari does not apply to SVG.
- Typing looked like a stroke being drawn rather than typing. It now
  reveals whole glyphs, and has an optional blinking caret.
- `draw` could render a thick line as a dotted comb where a renderer
  ignored `pathLength`. It now uses the real outline length.
- 8-digit hex (`#RRGGBBAA`) could render as black in renderers that
  only speak SVG 1.1. It is now normalized to `none`.

### Added
- Blinking caret toggle for typing text.

### Compatibility
- v4 project files load and are migrated on open.
