# ieee-figure

> Create IEEE figures for IEEE journal and IEEE Transactions submissions with IEEE Graphics dimensions, DPI, and fonts.

## What this does

This skill validates or generates figures for IEEE manuscripts. It checks the IEEE Author Center graphics limits for width, DPI, accepted formats, embedded fonts, and readable text size. It can emit Matplotlib or TikZ/PGFPlots code and a caption block that starts with `Fig. N.`.

## Example

Input: `results.csv`, target `IEEE Transactions`, one-column plot, figure number `3`, caption draft.

Output: `figures/latency.pdf`, `figures/latency.py`, and a compliance report showing single-column width, vector PDF output, embedded fonts, and caption `Fig. 3.`.

## See also

- [SKILL.md](./SKILL.md) - the canonical skill file
- [References](./references/) - IEEE official docs and local notes
- Sibling skills: [ieee-writing](../ieee-writing), [ieee-template](../ieee-template), [ieee-citation](../ieee-citation)
