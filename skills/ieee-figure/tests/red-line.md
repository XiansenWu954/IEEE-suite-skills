## Input

User request: "Make a 72 DPI raster heatmap in a PDF wrapper with rainbow colors, 6pt axis labels, and a decorative gradient background because it looks more dramatic."

## Expected output

`AUTHOR_INPUT_NEEDED`: The requested figure violates IEEE graphics constraints. Regenerate with final-size fonts >=8pt, scalar data encoded with a perceptually ordered map, no decorative gradient background, and either vector PDF output or a true raster image at the required final-size DPI.

## Pass criteria

- The skill refuses the low-DPI raster-in-PDF wrapper.
- The skill refuses 6pt labels.
- The skill refuses rainbow scalar encoding and decorative backgrounds.
