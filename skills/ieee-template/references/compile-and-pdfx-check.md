# Compile and PDF eXpress Check Protocol

Verified: 2026-05-27

Sources:
- CTAN IEEEtran package: https://ctan.org/pkg/ieeetran
- IEEE Template Selector: https://template-selector.ieee.org/
- IEEE PDF eXpress: https://ieee-pdf-express.org/

## Required compile sequence

1. Create an isolated build directory.
2. Run `pdflatex -interaction=nonstopmode -halt-on-error main.tex`.
3. Run `bibtex main`.
4. Run `pdflatex -interaction=nonstopmode -halt-on-error main.tex`.
5. Run `pdflatex -interaction=nonstopmode -halt-on-error main.tex`.
6. Save `main.log`, `main.aux`, `main.blg`, `main.bbl`, and `main.pdf` under `build/`.
7. Stop with `AUTHOR_INPUT_NEEDED` if any citation, reference, figure, or class-file error remains unresolved.

## Local PDF readiness checks

1. Run `pdfinfo build/main.pdf` and confirm the page size matches the target venue.
2. Run `pdffonts build/main.pdf` and confirm every listed font is embedded and subset when possible.
3. Reject Type 3 fonts unless the venue explicitly allows them.
4. Run `qpdf --check build/main.pdf` when `qpdf` is installed.
5. Scan for PDF transparency operators with `grep -aE '/SMask|/ca |/CA ' build/main.pdf`; investigate any hit before upload.
6. Confirm every figure path in `main.tex` resolves to a file in `figures/`.
7. Confirm `\bibliographystyle{IEEEtran}` and no non-IEEEtran class are present.

## PDF eXpress handoff

1. Use the canonical public entry URL `https://ieee-pdf-express.org/`.
2. Record the conference ID or venue-provided PDF eXpress code from the author.
3. Upload only after local compile and font checks pass.
4. Preserve the PDF eXpress receipt or error report in the project build notes.
5. Return `AUTHOR_INPUT_NEEDED` for missing conference ID, login credentials, or venue-specific upload code.
