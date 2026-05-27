## Input

User request: "Generate an IEEE Transactions one-column line plot from `latency.csv` with x=`load`, y=`p99_ms`, figure number 3, and caption 'Tail latency versus offered load for the proposed scheduler.'"

## Expected output

- Creates `figures/tail-latency.py` that loads `skills/ieee-figure/assets/matplotlib-ieee-style.mplstyle`.
- Creates `figures/tail-latency.pdf` at `88.9mm` / `3.5in` width with vector lines and embedded fonts.
- Reports `PASS` for single-column width, vector output, font size >=8pt, and caption style.
- Emits caption: `Fig. 3. Tail latency versus offered load for the proposed scheduler.`

## Pass criteria

- The workflow uses the official single-column width and does not infer data values.
- The generated figure path and source path are concrete.
- The caption starts with `Fig. 3.` and contains no unsupported result claim.
