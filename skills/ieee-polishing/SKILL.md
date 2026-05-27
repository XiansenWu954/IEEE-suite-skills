---
name: ieee-polishing
version: 0.1.0
description: Polish English IEEE journal manuscripts to IEEE Editorial Style Manual house style with [N] citations for IEEE Transactions.
author: XiansenWu954
status: Stable
tags:
  - ieee
  - polishing
  - style
  - manuscript
license: MIT
---

## Purpose

This skill polishes existing English IEEE manuscripts without changing the author's technical meaning. It applies IEEE Editorial Style Manual for Authors, current March 2025 revision, to prose, abbreviations, units, figure/table references, titles, and citation surface form. Its authority comes from the IEEE Editorial Style Manual page: https://journals.ieeeauthorcenter.ieee.org/your-role-in-article-production/ieee-editorial-style-manual/.

## When to use

- The user has English Markdown, LaTeX, or plain text that already contains the intended technical claims.
- The user wants IEEE house-style cleanup beyond grammar correction.
- The draft mixes inconsistent abbreviations, units, figure callouts, capitalization, or citation syntax.
- The user asks for either diff-style edits or clean replacement text for an IEEE manuscript section.

## Input contract

- Accepts Markdown, LaTeX, or plain English manuscript chunks.
- Requires the user to specify whether output should be a diff-style revision or clean replacement text.
- Requires enough surrounding context to resolve first-use abbreviations; otherwise mark `AUTHOR_INPUT_NEEDED`.
- Accepts optional target venue, preferred English variant, protected terminology, and no-change technical terms.
- Does not accept translation-only requests or requests to alter claims without author-supplied evidence.

## Workflow

1. Confirm that the input is an English IEEE manuscript chunk in Markdown, LaTeX, or plain text.
2. Confirm whether the user wants diff-style revisions or clean replacement text.
3. Preserve technical claims, numeric values, equations, citations, and limitations unless the author explicitly changes them.
4. Expand abbreviations at first use and keep later uses consistent, marking unresolved first uses as `AUTHOR_INPUT_NEEDED`.
5. Normalize passive-voice balance, SI units, ranges, capitalization, hyphenation, contractions, and dash usage to IEEE house style.
6. Replace non-IEEE surface forms with IEEE forms, including `Fig. 1`, `Table I`, equation `(1)`, and numeric `[N]` citations.
7. Flag unsupported prose flourishes, overclaims, missing references, or unverified comparisons with `AUTHOR_INPUT_NEEDED`.
8. Return the requested diff-style revision or clean replacement text plus a compact issue list.
9. Hand off unresolved citation metadata to `ieee-citation` and structure-level problems to `ieee-writing`.

## Output contract

- Produces revised Markdown, LaTeX, or plain text in the same format as the input unless the user requests another format.
- Emits either a diff-style block or clean replacement block, followed by `IEEE_STYLE_NOTES`.
- Lists each `AUTHOR_INPUT_NEEDED` item with the exact phrase, location, and reason.
- Done means the prose can be returned to `ieee-writing` or passed to `ieee-template` without unresolved style-only issues.

## Scope boundary

### ✓ In scope

- IEEE house-style polishing of existing English manuscript text.
- Abbreviation expansion, SI unit cleanup, figure/table/equation references, title capitalization, and numeric citation surface checks.
- Diff-style or clean replacement output.
- Conservative wording changes that improve clarity without changing technical meaning.

### ✗ Out of scope

- Translating non-English text into English.
- Rewriting the paper's technical claims, methods, results, limitations, or conclusions.
- Resolving bibliographic metadata, creating figures, compiling LaTeX, or choosing venues.
- Enforcing American or British spelling unless the user specifies the preference.

### 🚩 Red lines (NEVER do these)

- Never change a technical claim, number, theorem, dataset description, or result without explicit author evidence.
- Never translate languages; send mixed-language drafting needs to `ieee-writing` with `AUTHOR_INPUT_NEEDED` for author approval.
- Never impose a spelling variant when the user has not specified one.
- Never convert IEEE numeric citations to name-date parenthetical citations.

## References

1. IEEE Editorial Style Manual page, current revision March 2025: https://journals.ieeeauthorcenter.ieee.org/your-role-in-article-production/ieee-editorial-style-manual/
2. Local reference stub: [references/ESM.url.txt](./references/ESM.url.txt)
3. Local cheatsheets: [references/CHEATSHEET-style-rules.md](./references/CHEATSHEET-style-rules.md), [references/bad-examples.md](./references/bad-examples.md)
4. Companion skills: [ieee-writing](../ieee-writing), [ieee-citation](../ieee-citation), [ieee-template](../ieee-template)

> **Disclaimer**: IEEE policies (page limits, fees, formatting rules) change. Always verify against the official URL above on submission day.

## Integration

`ieee-writing` -> emits `manuscript.md` with author-approved claims -> `ieee-polishing` returns `manuscript.polished.md` plus `IEEE_STYLE_NOTES`.

`ieee-polishing` -> flags unresolved `[CITE_KEY]`, malformed `[N]`, and reference-list issues -> `ieee-citation` returns `references.bib` and citation mapping; `ieee-template` then receives polished IEEEtran-ready text.
