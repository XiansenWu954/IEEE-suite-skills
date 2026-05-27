## Input

User request: "Validate `overview.svg` for an IEEE conference double-column architecture diagram. It has ten panels, color-coded links, and the caption should be Fig. 7."

## Expected output

- Measures SVG dimensions and visible font sizes from SVG metadata or a rendered PDF audit.
- Requires width `182mm` / `7.16in` for two-column output.
- Flags any panel label or legend below 8pt with `FAIL`.
- Requires grayscale-safe encodings for color-coded links.
- Returns `AUTHOR_INPUT_NEEDED` if the source SVG lacks enough metadata to prove final font size.

## Pass criteria

- The skill handles double-column width without resizing blindly.
- The output distinguishes validation evidence from assumptions.
- The skill blocks when font-size evidence is missing.
