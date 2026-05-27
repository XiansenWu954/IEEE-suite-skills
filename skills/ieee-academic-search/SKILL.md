---
name: ieee-academic-search
version: 0.1.0
description: Orchestrate IEEE Xplore, DBLP, and Crossref for IEEE related work, DOI metadata, and IEEE arXiv preprint policy checks.
author: XiansenWu954
status: Stable
tags:
  - ieee
  - search
  - xplore
  - citations
license: MIT
---

## Purpose

This skill orchestrates IEEE Xplore, DBLP, and Crossref searches to produce citation candidates that are traceable enough for IEEE manuscript work. It prioritizes IEEE Xplore at https://ieeexplore.ieee.org/ for IEEE venue manuscripts, uses DBLP at https://dblp.org for computer-science venue coverage, and validates DOI metadata through Crossref at https://www.crossref.org . It also surfaces IEEE Author Center preprint rules from https://journals.ieeeauthorcenter.ieee.org/become-an-ieee-journal-author/publishing-ethics/guidelines-and-policies/submission-and-peer-review-policies/ when a user's own arXiv or TechRxiv preprint is involved.

## When to use

- When the user has an IEEE manuscript section with weak or missing related-work citations.
- When the user provides topic keywords and wants IEEE-first citation candidates with DOI metadata.
- When the user gives one seed paper and asks for sibling papers by venue, author, method, or DOI.
- When the user needs a ranked candidate list before handing entries to `ieee-citation` for BibTeX formatting.
- When the user asks whether a current-work arXiv preprint can be declared during IEEE submission.

## Input contract

- Accept topic keywords, an abstract, a related-work section, a DOI, an IEEE Xplore URL, a DBLP record, or a Crossref result.
- Require enough scope to distinguish method, domain, task, and venue family; otherwise ask for `AUTHOR_INPUT_NEEDED`.
- Accept optional constraints: year range, target venue, must-include authors, exclude self-citations, or preferred source mix.
- Require verifiable metadata for returned candidates: title, authors, venue, year, DOI or IEEE Xplore URL, and source.
- Reject requests to fabricate DOIs, infer missing author lists, or cite unverifiable search results.

## Workflow

1. Parse the user's query into topic terms, field synonyms, seed papers, venue constraints, and exclusion rules.
2. Search IEEE Xplore first for IEEE venue manuscripts and record the exact query string used.
3. Search DBLP for computer-science conference and journal coverage using venue, author, and title variants.
4. Search Crossref for DOI validation, publisher metadata, and broader interdisciplinary matches.
5. Deduplicate candidates by DOI, normalized title, author-year tuple, and IEEE Xplore document number.
6. Reject candidates without a verifiable DOI or stable IEEE Xplore URL unless the user explicitly asks for exploratory leads.
7. Rank candidates with a transparent score: relevance 0-5, venue fit 0-3, recency 0-2, and metadata completeness 0-2.
8. If the user has an own arXiv or TechRxiv preprint of the current work, state that IEEE allows preprints but requires declaration of the posting URL and that the preprint should not be used as the main peer-reviewed reference for the same work.
9. Output a ranked citation-candidate table plus a handoff block for `ieee-citation`.

## Output contract

- Produce a Markdown ranked list or table named by the user or default to `ieee-academic-search-results.md`.
- Include columns: rank, score breakdown, title, authors, venue, year, DOI, IEEE Xplore URL if available, DBLP key if available, Crossref status, abstract snippet, and rationale.
- Include a `Search Log` section with query strings, source order, date, and deduplication decisions.
- Include a `BibTeX Handoff` section containing DOI/title metadata ready for `ieee-citation`.
- Define done as no fabricated DOI values, all candidate sources named, and every unverifiable candidate either removed or marked `AUTHOR_INPUT_NEEDED`.

## Scope boundary

### ✓ In scope

- IEEE-first literature search orchestration across IEEE Xplore, DBLP, and Crossref.
- DOI and metadata verification before citation handoff.
- Transparent ranking for related-work candidate selection.
- IEEE preprint-policy reminders for current-work arXiv or TechRxiv postings.

### ✗ Out of scope

- Browser automation of IEEE Xplore search sessions; use `cookjohn/ieee-skills` for that lower-level operation.
- Formatting final BibTeX entries; hand candidates to `ieee-citation`.
- Writing the related-work prose for the user without verified references.
- Treating non-peer-reviewed preprints as primary evidence when a published version exists.

### 🚩 Red lines (NEVER do these)

- Never fabricate DOI values, IEEE Xplore document numbers, abstracts, venues, or author lists.
- Never return AI-summarized search hits that lack a verifiable DOI or stable IEEE Xplore URL.
- Never demote IEEE Xplore for IEEE venue manuscripts unless the user explicitly targets a non-IEEE corpus.
- Never suggest citing crowd-edited encyclopedia pages, blogs, or forum posts as scholarly authority.
- Never hide score components; always show why a candidate ranked above another.

## References

1. IEEE Xplore Digital Library: https://ieeexplore.ieee.org/ (see [references/XPL.url.txt](references/XPL.url.txt)).
2. DBLP computer science bibliography: https://dblp.org (see [references/dblp.url.txt](references/dblp.url.txt)).
3. Crossref: https://www.crossref.org (see [references/crossref.url.txt](references/crossref.url.txt)).
4. IEEE Submission and Peer Review Policies: https://journals.ieeeauthorcenter.ieee.org/become-an-ieee-journal-author/publishing-ethics/guidelines-and-policies/submission-and-peer-review-policies/ (see [references/SUB.url.txt](references/SUB.url.txt)).
5. Search protocol: [references/search-protocol.md](references/search-protocol.md).
6. IEEE arXiv and TechRxiv policy notes: [references/arxiv-policy.md](references/arxiv-policy.md).
7. Companion skills: [../ieee-reader](../ieee-reader), [../ieee-citation](../ieee-citation), [../ieee-writing](../ieee-writing).

> **Disclaimer**: IEEE policies (page limits, fees, formatting rules) change. Always verify against the official URL above on submission day.

## Integration

`ieee-reader` can feed extracted citation gaps as `missing_metadata[]`; `ieee-academic-search` returns DOI-backed candidates; `ieee-citation` converts those candidates into IEEE numeric BibTeX entries; `ieee-writing` uses the verified list to repair related-work coverage. The complementary project `cookjohn/ieee-skills` at https://github.com/cookjohn/ieee-skills handles IEEE Xplore browser automation, while this skill handles higher-level source orchestration, deduplication, ranking, and IEEE-policy checks.
