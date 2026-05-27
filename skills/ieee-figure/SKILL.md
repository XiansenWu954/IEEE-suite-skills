---
name: ieee-figure
version: 0.1.0
description: Create IEEE figures for IEEE journal and IEEE Transactions submissions with IEEE Graphics dimensions, DPI, and fonts.
author: XiansenWu954
status: Stable
tags:
  - ieee
  - figure
  - graphics
license: MIT
---

## Purpose

This skill generates or validates figures against IEEE Graphics Requirements before the figures enter an IEEE journal, IEEE Transactions, or IEEE conference manuscript. It derives width and raster-resolution constraints from the IEEE Author Center Resolution and Size page (https://journals.ieeeauthorcenter.ieee.org/create-your-ieee-journal-article/create-graphics-for-your-article/resolution-and-size/) and file-format/font rules from the IEEE Author Center File Formatting page (https://journals.ieeeauthorcenter.ieee.org/create-your-ieee-journal-article/create-graphics-for-your-article/file-formatting/). Caption references are checked against IEEE Editorial Style Manual guidance, current revision March 2025 per the project freshness policy.

## When to use

- A user has PDF, PNG, TIFF, or SVG figures and needs an IEEE compliance report before submission.
- A user has data plus a plot intent and needs a one-column or two-column IEEE-ready figure.
- A user needs Matplotlib or TikZ/PGFPlots code that recreates a figure at IEEE dimensions.
- A user needs captions normalized to `Fig. N.` references for handoff to `ieee-writing`.

## Input contract

- Accept existing figure files in PDF, EPS, PS, SVG, PNG, or TIFF, or accept source data with a requested plot type.
- Require target context: IEEE journal, IEEE Transactions, or IEEE conference; requested column span; figure number; caption draft; and output directory.
- Accept optional context: target venue, print-vs-online needs, color palette constraints, source plotting code, and required file naming convention.
- Return `AUTHOR_INPUT_NEEDED` when source data, figure number, caption meaning, or target column span is missing.
- Treat measured dimensions, DPI, font embedding, and font sizes as evidence, not as values to infer from filenames.

## Workflow

1. Confirm the target is an IEEE journal, IEEE Transactions, or IEEE conference submission, and stop with `AUTHOR_INPUT_NEEDED` if the venue family is unclear.
2. Classify the request as validation or generation, and record the requested column span, figure number, caption, source data, and output path.
3. For validation, measure width, height, raster DPI, embedded fonts, visible font sizes, and file format using structured tools such as `pdfinfo`, `pdffonts`, ImageMagick, or SVG metadata.
4. Compare each figure against single-column: 88.9mm, double-column: 182mm, line art: >=600 DPI, color or grayscale raster: >=300 DPI, and fonts: >=8pt.
5. For generation, produce Matplotlib code that loads `assets/matplotlib-ieee-style.mplstyle` or produce TikZ/PGFPlots code when LaTeX-native vector text is required.
6. Save vector PDF for line art and plots, and use TIFF or PNG only for true raster images without placing raster artwork inside vector PDF.
7. Use perceptually ordered or categorical palettes, grayscale-safe encodings, direct labels, and no decorative gradient backgrounds.
8. Emit a compliance table, regenerated figure path, source code path when created, and a caption beginning `Fig. N.`.

## Output contract

- Produce `figures/<slug>.pdf` for vector output or `figures/<slug>.tif` / `figures/<slug>.png` for true raster output.
- Produce `figures/<slug>.py` or `figures/<slug>.tex` when a figure is generated from data or plotting instructions.
- Produce a Markdown compliance report with measured width, height, DPI, font status, file format, caption status, and pass/fail result.
- Produce a caption block that starts with `Fig. N.` and contains no fabricated result or statistic.
- Define done as: every requested figure is either compliant, regenerated to spec, or blocked with `AUTHOR_INPUT_NEEDED` plus the missing input.

## Scope boundary

### ✓ In scope

- Validate dimensions, DPI, font sizes, font embedding, and accepted graphics file types.
- Generate IEEE-ready Matplotlib or TikZ/PGFPlots figures from supplied data and explicit plot intent.
- Normalize figure captions and in-text figure references to `Fig. N.` form.
- Select palettes and encodings that remain interpretable in grayscale.

### ✗ Out of scope

- Invent data, statistical results, experimental labels, or figure captions.
- Rewrite manuscript prose outside figure captions and figure callouts.
- Decide venue-specific page budgets without chaining to `ieee-venue-selector`.
- Recreate proprietary artwork when the user lacks source data or permission.

### 🚩 Red lines (NEVER do these)

- Never fabricate citations, statistics, measurements, or figure content.
- Never use rainbow colormaps for scalar data or decorative gradient backgrounds.
- Never place raster image data inside vector PDF output.
- Never produce figures with axis, tick, legend, or annotation fonts below 8pt.
- Never replace `Fig. N.` with long-form numbered figure callouts in IEEE text.

## References

1. IEEE Graphics Resolution and Size: https://journals.ieeeauthorcenter.ieee.org/create-your-ieee-journal-article/create-graphics-for-your-article/resolution-and-size/
2. IEEE Graphics File Formatting: https://journals.ieeeauthorcenter.ieee.org/create-your-ieee-journal-article/create-graphics-for-your-article/file-formatting/
3. IEEE Editorial Style Manual page: https://journals.ieeeauthorcenter.ieee.org/your-role-in-article-production/ieee-editorial-style-manual/
4. Local numeric spec: [references/figure-spec.md](references/figure-spec.md)
5. One-column examples: [references/EXAMPLES-single-col.md](references/EXAMPLES-single-col.md)
6. Two-column examples: [references/EXAMPLES-double-col.md](references/EXAMPLES-double-col.md)
7. Color guidance: [references/IEEE-color-vs-grayscale.md](references/IEEE-color-vs-grayscale.md)
8. Companion skills: [../ieee-writing](../ieee-writing), [../ieee-template](../ieee-template), [../ieee-citation](../ieee-citation)

> **Disclaimer**: IEEE policies (page limits, fees, formatting rules) change. Always verify against the official URL above on submission day.

## Integration

`ieee-writing` supplies figure callouts and captions as Markdown, `ieee-figure` returns compliant `figures/*.pdf` or raster assets plus a caption block, and `ieee-template` embeds those files into IEEEtran LaTeX. `ieee-citation` supplies numeric `[N]` references used inside captions, and `ieee-venue-selector` resolves venue-specific limits before figure generation changes manuscript layout.
