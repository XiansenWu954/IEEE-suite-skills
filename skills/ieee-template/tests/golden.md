## Input

User request: "Convert `paper.md`, `references.bib`, and `figures/latency.pdf` into an IEEE conference project for PDF eXpress. The author block and conference title are supplied."

## Expected output

- Creates `main.tex` with `\documentclass[conference]{IEEEtran}`.
- Copies `references.bib` without changing entries.
- Links or copies `figures/latency.pdf` into `figures/`.
- Runs `pdflatex`, `bibtex`, `pdflatex`, `pdflatex`.
- Produces `build/main.pdf`, compile logs, conversion deltas, and `build/pdf-express-readiness.md`.

## Pass criteria

- The skill uses IEEEtran and `\bibliographystyle{IEEEtran}`.
- The compile sequence is complete and logged.
- The readiness report includes font embedding and PDF structure checks.
