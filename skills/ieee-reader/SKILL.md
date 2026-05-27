---
name: ieee-reader
version: 0.1.0
description: Convert IEEE PDF or IEEE Xplore pages into structured Markdown with IEEE Reference Guide citation mapping and bilingual ZH/EN handoff.
author: XiansenWu954
status: Stable
tags:
  - ieee
  - reader
  - xplore
  - bilingual
license: MIT
---

## Purpose

This skill turns IEEE PDFs, IEEE Xplore pages, or pasted IEEE article text into auditably structured Markdown without changing the source order or meaning. It derives extraction constraints from IEEE Xplore article structure at https://ieeexplore.ieee.org/ and IEEE editorial section/caption conventions documented by the IEEE Author Center at https://journals.ieeeauthorcenter.ieee.org/your-role-in-article-production/ieee-editorial-style-manual/ . The core engineering constraint is traceability: every extracted heading, caption, equation marker, and citation marker must map back to the source location or be flagged `AUTHOR_INPUT_NEEDED`.

## When to use

- When the user provides an IEEE PDF and asks for Markdown sections, captions, references, or reading notes.
- When the user provides an IEEE Xplore URL and needs title, abstract, keywords, sections, figures, tables, and citation markers preserved.
- When the user pastes a two-column IEEE article chunk whose section order or citation numbering must survive cleanup.
- When the user asks for a Chinese-English parallel summary of an IEEE paper after extraction.
- When downstream `ieee-academic-search` or `ieee-writing` needs reliable related-work notes from an existing IEEE article.

## Input contract

- Accept a local PDF path, an IEEE Xplore URL, OCR text, or pasted article text.
- Require the user to state whether output should be extract-only or include a bilingual ZH/EN summary.
- Preserve article identifiers if present: DOI, IEEE Xplore document number, title, venue, year, authors, and ORCID lines.
- Treat missing pages, failed OCR, paywalled content, broken tables, and inaccessible figures as `AUTHOR_INPUT_NEEDED`.
- Do not accept a request to paraphrase the source as if it were extracted text.

## Workflow

1. Identify the input type as PDF path, IEEE Xplore URL, OCR text, or pasted article text.
2. Extract title, authors, venue metadata, abstract, index terms, section headings, acknowledgments, references, appendices, and biographies in source order.
3. Preserve IEEE-style section numbering such as `I.`, `II.`, `A.`, and appendix labels exactly as seen.
4. Extract figure captions, table captions, equation labels, footnotes, and callouts into separate Markdown tables while preserving `Fig. N`, `Table N`, and `(N)` numbering.
5. Extract every numeric citation marker `[N]` from body text and map it to the matching reference-list entry.
6. Mark any missing caption, ambiguous OCR token, broken citation range, or unmatched reference as `AUTHOR_INPUT_NEEDED`.
7. If bilingual output is requested, write a section-by-section ZH/EN parallel summary after the extract and keep technical terms in their source language unless the user supplies a glossary.
8. Emit the structured Markdown artifact, caption table, citation mapping table, and optional bilingual summary with a short extraction log.

## Output contract

- Produce one Markdown artifact named by the user or default to `ieee-reader-output.md`.
- Include sections in this order: `# Metadata`, `# Extracted Markdown`, `# Captions`, `# Citation Mapping`, `# Extraction Log`, and optional `# ZH/EN Parallel Summary`.
- Use Markdown tables for captions and citation mappings, with source page or source section where available.
- Define done as complete extraction, no reordered source content, and every uncertain element marked `AUTHOR_INPUT_NEEDED`.

## Scope boundary

### ✓ In scope

- Extracting IEEE article structure from PDF, IEEE Xplore HTML, OCR, or pasted text.
- Preserving IEEE numbering for sections, figures, tables, equations, and citations.
- Producing bilingual ZH/EN summaries only after a faithful extraction layer exists.
- Preparing Markdown notes for related-work analysis and citation follow-up.

### ✗ Out of scope

- Circumventing paywalls or downloading restricted IEEE full text without user-provided access.
- Rewriting, compressing, or polishing the source paper.
- Creating BibTeX entries; hand citation candidates to `ieee-citation`.
- Judging novelty, venue fit, or acceptance probability.

### 🚩 Red lines (NEVER do these)

- Never paraphrase source text in the extract-only layer.
- Never reorder sections, captions, references, or biographies for readability.
- Never invent missing reference entries, page numbers, DOI values, captions, or equations.
- Never translate technical terms unilaterally; flag ambiguous terminology as `AUTHOR_INPUT_NEEDED`.
- Never recommend non-authoritative sources as citation authority.

## References

1. IEEE Xplore Digital Library: https://ieeexplore.ieee.org/ (see [references/XPL.url.txt](references/XPL.url.txt)).
2. IEEE Editorial Style Manual page: https://journals.ieeeauthorcenter.ieee.org/your-role-in-article-production/ieee-editorial-style-manual/ (see [references/ESM.url.txt](references/ESM.url.txt)).
3. IEEE Reference Guide: https://journals.ieeeauthorcenter.ieee.org/wp-content/uploads/sites/7/IEEE_Reference_Guide.pdf (see [references/RG.url.txt](references/RG.url.txt)).
4. Extraction protocol: [references/pdf-to-md-protocol.md](references/pdf-to-md-protocol.md).
5. Bilingual handoff format: [references/bilingual-handoff.md](references/bilingual-handoff.md).
6. Companion skills: [../ieee-academic-search](../ieee-academic-search), [../ieee-citation](../ieee-citation), [../ieee-writing](../ieee-writing).

> **Disclaimer**: IEEE policies (page limits, fees, formatting rules) change. Always verify against the official URL above on submission day.

## Integration

`ieee-reader` extracts structured Markdown and citation markers from existing IEEE papers, then passes DOI/reference gaps to `ieee-academic-search` as `missing_metadata[]` and passes verified reference entries to `ieee-citation` as numbered citation candidates. It also supports `ieee-writing` by producing related-work notes in a stable section format: `source_id`, `section`, `verbatim_extract`, `caption_refs`, `citation_refs`, and optional `zh_en_summary`.
