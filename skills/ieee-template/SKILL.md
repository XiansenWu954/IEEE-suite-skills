---
name: ieee-template
version: 0.1.0
description: Build IEEEtran.cls IEEE LaTeX projects for IEEE journal and IEEE conference submissions with PDF eXpress checks.
author: XiansenWu954
status: Stable
tags:
  - ieee
  - template
  - latex
  - pdf-express
license: MIT
---

## Purpose

This skill converts an author's manuscript package into a compilable IEEEtran LaTeX project and reports whether the resulting PDF is ready for IEEE PDF eXpress. It uses IEEEtran.cls v1.8b (2015-08-26), the current canonical IEEEtran class version per CTAN as of 2026-05-27 (https://ctan.org/pkg/ieeetran), plus the IEEE Template Selector (https://template-selector.ieee.org/) for template selection. PDF eXpress readiness is based on the live IEEE PDF eXpress entry URL (https://ieee-pdf-express.org/) and local checks for page size, embedded fonts, compile errors, and PDF structure.

## When to use

- A user has Markdown, BibTeX, and figure files and needs an IEEEtran journal or conference project.
- A user needs to choose between IEEEtran `journal`, `conference`, and `technote` class options.
- A user needs a reproducible compile sequence and a PDF eXpress readiness report.
- A user needs generated `main.tex` that preserves manuscript content and surfaces conversion deltas.

## Input contract

- Require a Markdown manuscript, a `.bib` file from `ieee-citation`, figure file paths from `ieee-figure`, and a target variant: journal, conference, or technote.
- Accept optional context: target publication name, author affiliations, ORCID values, funding footnote, corresponding author, keywords, and supplementary files.
- Require all citations to resolve to BibTeX keys and all figure paths to exist or be explicitly marked pending.
- Return `AUTHOR_INPUT_NEEDED` when target variant, bibliography, figure paths, author block, or required venue metadata is missing.
- Preserve manuscript content during conversion and report every non-formatting change as a diff for author approval.

## Workflow

1. Confirm the target is an IEEE journal, IEEE Transactions, IEEE conference, or IEEE technote submission, and stop with `AUTHOR_INPUT_NEEDED` if the target is unclear.
2. Select the IEEEtran class option `journal`, `conference`, or `technote` from the user-provided target and venue context.
3. Create a self-contained project directory containing `main.tex`, `references.bib`, `figures/`, `build/`, and a conversion-delta report.
4. Copy or symlink supplied figure files into `figures/` and preserve the paths expected by `ieee-figure`.
5. Use IEEEtran.cls v1.8b (2015-08-26) and `\bibliographystyle{IEEEtran}` without substituting another LaTeX class or bibliography style.
6. Convert Markdown sections, equations, tables, citations, and `Fig. N.` callouts to LaTeX without silently changing manuscript meaning.
7. Run `pdflatex main`, `bibtex main`, `pdflatex main`, and `pdflatex main`, and save logs under `build/`.
8. Check the compiled PDF with `pdfinfo`, `pdffonts`, `qpdf --check` when available, and a transparency scan before PDF eXpress upload.
9. Emit the PDF path, compile log path, unresolved warnings, conversion deltas, and a PDF eXpress readiness statement.

## Output contract

- Produce `main.tex` using IEEEtran class options that match the selected target variant.
- Produce `references.bib` copied from the verified `ieee-citation` handoff.
- Produce `figures/` links or copies and a manifest mapping source paths to LaTeX paths.
- Produce `build/main.pdf`, `build/main.log`, `build/main.blg`, and `build/pdf-express-readiness.md` when local compilation succeeds.
- Define done as: the project compiles cleanly or reports exact blocking errors with `AUTHOR_INPUT_NEEDED`.

## Scope boundary

### ✓ In scope

- Generate IEEEtran journal, conference, and technote LaTeX project structures.
- Preserve author content while converting Markdown, BibTeX, and figure references into LaTeX.
- Run local compile and PDF readiness checks.
- Include IEEEtran.cls v1.8b (2015-08-26) as a redistributable LPPL reference file.

### ✗ Out of scope

- Rewrite scientific claims, results, references, or conclusions during template conversion.
- Choose a journal or conference venue without chaining to `ieee-venue-selector`.
- Perform the actual authenticated PDF eXpress upload for the author.
- Guarantee acceptance by a venue or by IEEE production systems after policies change.

### 🚩 Red lines (NEVER do these)

- Never fabricate citations, author metadata, funding text, or venue requirements.
- Never use a non-IEEEtran LaTeX class for an IEEE manuscript.
- Never ship a PDF with unembedded fonts, Type 3 fonts, invalid page size, or known transparency problems.
- Never silently change manuscript content during conversion.
- Never replace numeric IEEE citations `[N]` with name/date citations.

## References

1. CTAN IEEEtran package: https://ctan.org/pkg/ieeetran
2. CTAN IEEEtran source directory: https://ctan.org/tex-archive/macros/latex/contrib/IEEEtran
3. IEEE Template Selector: https://template-selector.ieee.org/
4. IEEE Article Templates page: https://journals.ieeeauthorcenter.ieee.org/create-your-ieee-journal-article/authoring-tools-and-templates/tools-for-ieee-authors/ieee-article-templates/
5. IEEE PDF eXpress public entry URL: https://ieee-pdf-express.org/
6. Local compile protocol: [references/compile-and-pdfx-check.md](references/compile-and-pdfx-check.md)
7. Journal example: [references/latex-journal-example.tex](references/latex-journal-example.tex)
8. Conference example: [references/latex-conference-example.tex](references/latex-conference-example.tex)
9. Companion skills: [../ieee-writing](../ieee-writing), [../ieee-citation](../ieee-citation), [../ieee-figure](../ieee-figure)

> **Disclaimer**: IEEE policies (page limits, fees, formatting rules) change. Always verify against the official URL above on submission day.

## Integration

`ieee-writing` provides the Markdown manuscript, `ieee-citation` provides `references.bib` with numeric `[N]` citation intent, and `ieee-figure` provides compliant `figures/*.pdf` or raster assets. `ieee-template` converts those handoffs into `main.tex`, compiles `build/main.pdf`, and sends unresolved venue decisions back to `ieee-venue-selector`.
