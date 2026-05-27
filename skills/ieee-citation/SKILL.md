---
name: ieee-citation
version: 0.1.0
description: Handle IEEEtran.bst BibTeX and IEEE Reference Guide numeric [N] citations for IEEE LaTeX manuscripts.
author: XiansenWu954
status: Stable
tags:
  - ieee
  - citation
  - bibtex
  - ieee-latex
license: MIT
---

## Purpose

This skill converts source references into IEEE numeric `[N]` citations and BibTeX entries compatible with IEEEtran.bst. It follows the IEEE Reference Guide, current March 2025 revision, and CTAN's current IEEEtran package metadata. Its authority comes from the IEEE Reference Guide official redirect at https://journals.ieeeauthorcenter.ieee.org/wp-content/uploads/sites/7/IEEE_Reference_Guide.pdf and CTAN IEEEtran at https://ctan.org/pkg/ieeetran.

## When to use

- The user has DOI strings, RIS exports, plain-text references, or a rough `.bib` file and needs IEEE-ready BibTeX.
- The manuscript contains `[CITE_KEY]` placeholders that must become numbered `[N]` citations.
- The user needs a first-appearance citation mapping table for Markdown or LaTeX.
- The reference list needs IEEE month abbreviations, author initials, journal abbreviations, DOI, URL, or page-range cleanup.

## Input contract

- Accepts BibTeX, RIS, DOI lists, plain-text reference lists, or Markdown/LaTeX manuscripts with citation placeholders.
- Requires enough metadata to identify each source: DOI, title plus authors, or author-provided bibliographic record.
- Requires manuscript citation order when assigning `[N]`; otherwise outputs BibTeX only and asks for citation order.
- Accepts optional target venue, Crossref lookup availability, journal abbreviation preferences, and existing citation keys.
- Does not accept requests to fabricate missing references or to output a non-IEEE reference style.

## Workflow

1. Confirm the input type as BibTeX, RIS, DOI list, plain-text references, or manuscript placeholders.
2. Confirm whether the user needs `.bib` only, `[N]` mapping only, or both artifacts.
3. Resolve each DOI or bibliographic record through Crossref when internet is available, or use author-provided metadata when lookup is unavailable.
4. Emit `AUTHOR_INPUT_NEEDED` for any unresolved DOI, missing title, missing year, missing venue, or ambiguous duplicate.
5. Normalize each entry into IEEEtran-compatible `@article`, `@inproceedings`, `@book`, `@techreport`, `@misc`, or another justified BibTeX type.
6. Enforce IEEE Reference Guide conventions for initials, author count handling, abbreviated months, journal abbreviations, DOI or URL placement, and page ranges with en dash normalization where required.
7. Assign `[N]` numbers by first appearance in the manuscript and keep the same number for repeated citations.
8. Apply compact numeric ranges only when the target venue permits them; otherwise list citation numbers explicitly.
9. Output `references.bib` and, when requested, `citation-map.md` with `[CITE_KEY] -> [N]` replacements.

## Output contract

- Creates or modifies `references.bib` with IEEEtran.bst-compatible BibTeX entries.
- Optionally creates `citation-map.md` with first-appearance order, old keys, new `[N]` numbers, and unresolved items.
- Optionally returns patched manuscript text replacing `[CITE_KEY]` placeholders with `[N]` citations.
- Done means every reference is either normalized with traceable metadata or marked `AUTHOR_INPUT_NEEDED` without fabricated fields.

## Scope boundary

### ✓ In scope

- Converting DOI, RIS, plain-text, and rough BibTeX references to IEEEtran-compatible BibTeX.
- Assigning numeric `[N]` citations by first appearance.
- Cleaning months, page ranges, author initials, DOI fields, URL fields, and journal abbreviations.
- Producing an explicit mapping table for manuscript replacement.

### ✗ Out of scope

- Searching for sources that the author has not identified.
- Ranking literature, writing related work, or judging whether a citation is scientifically appropriate.
- Applying non-IEEE reference styles or venue systems outside IEEE.
- Treating raw `\cite{}` keys as sufficient final output when the user requested actionable BibTeX.

### 🚩 Red lines (NEVER do these)

- Never fabricate a citation, DOI, author, title, venue, year, page range, or URL.
- Never silently drop unresolved references; emit `AUTHOR_INPUT_NEEDED` instead.
- Never output only `\cite{}` keys when the requested artifact is a `.bib` file.
- Never convert IEEE numeric citations to name-date parenthetical citations.

## References

1. IEEE Reference Guide official redirect, current revision March 2025: https://journals.ieeeauthorcenter.ieee.org/wp-content/uploads/sites/7/IEEE_Reference_Guide.pdf
2. CTAN IEEEtran package, current v1.8b: https://ctan.org/pkg/ieeetran
3. Local reference stubs: [references/RG.url.txt](./references/RG.url.txt), [references/IT-BST.url.txt](./references/IT-BST.url.txt), [references/IEEEtran.bst.url.txt](./references/IEEEtran.bst.url.txt)
4. Local aids: [references/month-abbreviations.txt](./references/month-abbreviations.txt), [references/citation-templates.bib](./references/citation-templates.bib), [references/compaction-rules.md](./references/compaction-rules.md)
5. Companion skills: [ieee-writing](../ieee-writing), [ieee-polishing](../ieee-polishing), [ieee-template](../ieee-template), [ieee-academic-search](../ieee-academic-search)

> **Disclaimer**: IEEE policies (page limits, fees, formatting rules) change. Always verify against the official URL above on submission day.

## Integration

`ieee-writing` -> emits `manuscript.md` with `[CITE_KEY]` placeholders -> `ieee-citation` emits `references.bib`, `citation-map.md`, and patched `[N]` citations.

`ieee-citation` -> emits IEEEtran-compatible BibTeX -> `ieee-polishing` checks citation surface text and `ieee-template` compiles with `IEEEtran.bst`; `ieee-academic-search` may supply DOI metadata when the author asks for source discovery.
