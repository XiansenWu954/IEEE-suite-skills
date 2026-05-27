---
name: ieee-writing
version: 0.1.0
description: Author IEEE journal manuscripts for IEEE Transactions using the IEEE Editorial Style Manual and IEEE submission handoffs.
author: XiansenWu954
status: Stable
tags:
  - ieee
  - writing
  - journal
  - manuscript
license: MIT
---

## Purpose

This skill creates or audits IEEE journal manuscripts against the IEEE Editorial Style Manual for Authors, current March 2025 revision, and the IEEE Author Center journal workflow, including the §I Introduction through §VI Conclusion core structure. It enforces structure, abstract and keyword constraints, math and unit style, and numeric citation handoffs before the manuscript reaches layout or submission. Its authority comes from the IEEE Author Center and the current Editorial Style Manual page: https://journals.ieeeauthorcenter.ieee.org/your-role-in-article-production/ieee-editorial-style-manual/.

## When to use

- The user has an outline and needs a structured IEEE Transactions-style manuscript draft.
- The user has a partial Markdown or LaTeX draft and wants section-level conformance before polishing.
- The user needs an abstract, keywords, and main section skeleton checked before IEEE submission.
- The target venue is known or can be selected by `ieee-venue-selector`.

## Input contract

- Accepts Markdown, LaTeX, plain-text outlines, section notes, tables, equations, and user-supplied figure captions.
- Requires a target venue or an explicit "generic IEEE Transactions" target; otherwise call `ieee-venue-selector`.
- Requires author-provided technical claims, data, methods, limitations, and experimental results; missing evidence must be marked `AUTHOR_INPUT_NEEDED`.
- Accepts optional constraints such as page target, article type, blind-review mode, supplementary-material plan, and source `.bib` file; defaults to single-blind unless the verified venue states otherwise.
- Assumes the user wants an English IEEE journal manuscript, not a conference paper or a non-IEEE publisher template.

## Workflow

1. Confirm the target venue, using `ieee-venue-selector` first if the user does not provide TMC, TON, TPDS, or another IEEE journal target.
2. Confirm the manuscript stage as outline, first draft, revision, or pre-submission audit.
3. Reject a non-IEEE target with `AUTHOR_INPUT_NEEDED: target venue is outside IEEE scope`.
4. Produce or check the §I Introduction through §VI Conclusion core structure, adding discipline-specific Related Work, Method, Results, and Discussion sections only when supported by the author content.
5. Enforce an abstract not exceeding 250 words and require 5-8 index terms unless the verified venue page states a different limit.
6. Check section headings, equation numbering, italic variables, roman operators, SI units, figure/table callouts, and appendix placement against the Editorial Style Manual.
7. Preserve every technical claim exactly unless the author provides evidence for a change, marking unsupported claims as `AUTHOR_INPUT_NEEDED`.
8. Send prose-level edits to `ieee-polishing` and citation placeholders or source references to `ieee-citation`.
9. Output a structured Markdown manuscript with `[CITE_KEY]` placeholders and handoff notes for `ieee-figure` and `ieee-template`.

## Output contract

- Creates or modifies `manuscript.md` or the user-named Markdown/LaTeX file.
- Produces IEEE-style sections, abstract, index terms, equation labels, figure/table callouts, and citation placeholders.
- Emits a handoff block named `IEEE_HANDOFF` listing unresolved author inputs, citation keys, figures, venue assumptions, and template needs.
- Done means the manuscript can move directly to `ieee-polishing`, `ieee-citation`, `ieee-figure`, and `ieee-template` without unresolved structural questions except explicit `AUTHOR_INPUT_NEEDED` items.

## Scope boundary

### ✓ In scope

- Drafting or restructuring IEEE journal manuscripts from author-provided content.
- Checking abstract length, index terms, section order, equations, units, captions, and citation placeholders.
- Marking missing data, missing venue details, or unsupported claims as `AUTHOR_INPUT_NEEDED`.
- Preparing a clean Markdown handoff for downstream IEEE skills.

### ✗ Out of scope

- Selecting a venue without using `ieee-venue-selector` or an author-specified target.
- Creating figures, BibTeX entries, final LaTeX layout, cover letters, or reviewer responses.
- Translating non-English manuscripts as a standalone task.
- Guaranteeing acceptance, peer-review outcome, page-charge waiver, or production decisions.

### 🚩 Red lines (NEVER do these)

- Never apply non-IEEE journal-family or conference-family structure to an IEEE manuscript.
- Never invent numbers, statistics, datasets, limitations, author affiliations, or funding statements.
- Never use name-date parenthetical citations; IEEE manuscript drafts use numbered `[N]` citations downstream.
- Never proceed on a non-IEEE venue request; refer the user to that venue's ecosystem.

## References

1. IEEE Author Center Journals: https://journals.ieeeauthorcenter.ieee.org/
2. IEEE Editorial Style Manual page, current revision March 2025: https://journals.ieeeauthorcenter.ieee.org/your-role-in-article-production/ieee-editorial-style-manual/
3. IEEE Reference Guide official redirect, current revision March 2025: https://journals.ieeeauthorcenter.ieee.org/wp-content/uploads/sites/7/IEEE_Reference_Guide.pdf
4. Local reference stubs: [references/AC.url.txt](./references/AC.url.txt), [references/ESM.url.txt](./references/ESM.url.txt), [references/RG.url.txt](./references/RG.url.txt)
5. Local cheatsheets: [references/CHEATSHEET-math-formatting.md](./references/CHEATSHEET-math-formatting.md), [references/journal-page-limits.csv](./references/journal-page-limits.csv)
6. Companion skills: [ieee-polishing](../ieee-polishing), [ieee-citation](../ieee-citation), [ieee-figure](../ieee-figure), [ieee-template](../ieee-template)

> **Disclaimer**: IEEE policies (page limits, fees, formatting rules) change. Always verify against the official URL above on submission day.

## Integration

`ieee-venue-selector` -> emits `venue_profile.yaml` with target journal, page limits, blind mode, and verified URL -> `ieee-writing` uses it to shape `manuscript.md`.

`ieee-writing` -> emits `manuscript.md` with `[CITE_KEY]`, `Fig. N`, `Table N`, and `IEEE_HANDOFF` -> `ieee-polishing` returns revised prose, `ieee-citation` returns `references.bib` plus `[N]` mapping, `ieee-figure` returns compliant artwork, and `ieee-template` converts the manuscript into IEEEtran LaTeX.
