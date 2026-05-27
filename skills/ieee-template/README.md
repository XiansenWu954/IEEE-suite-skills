# ieee-template

> Build IEEEtran.cls IEEE LaTeX projects for IEEE journal and IEEE conference submissions with PDF eXpress checks.

## What this does

This skill turns a manuscript package into an IEEEtran LaTeX project. It selects the correct IEEEtran variant, preserves the author's content, runs the standard LaTeX/BibTeX compile cycle, and checks the PDF for PDF eXpress readiness risks. It ships IEEEtran.cls v1.8b as a redistributable LPPL reference file.

## Example

Input: `paper.md`, `references.bib`, `figures/latency.pdf`, and target `IEEE conference`.

Output: `main.tex`, `references.bib`, `figures/` links, `build/main.pdf`, compile logs, a conversion-delta report, and `build/pdf-express-readiness.md`.

## See also

- [SKILL.md](./SKILL.md) - the canonical skill file
- [References](./references/) - CTAN and IEEE official docs this skill is based on
- Sibling skills: [ieee-writing](../ieee-writing), [ieee-citation](../ieee-citation), [ieee-figure](../ieee-figure)
