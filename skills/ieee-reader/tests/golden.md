## Input

Read `./papers/tmc-edge-paper.pdf` and produce structured Markdown, caption table, citation mapping, and a ZH/EN summary.

## Expected output

```markdown
# Metadata

| Field | Value |
|---|---|
| Source type | PDF |
| Venue | IEEE Transactions on Mobile Computing |
| DOI | AUTHOR_INPUT_NEEDED if not visible |

# Extracted Markdown

## Abstract

<verbatim abstract text>

## I. Introduction

<verbatim section text with [1], [2] preserved>

# Captions

| Type | Number | Caption | Source |
|---|---:|---|---|
| Figure | Fig. 1 | <verbatim caption> | p. 2 |

# Citation Mapping

| Marker | Reference entry | First seen |
|---|---|---|
| [1] | <verbatim reference 1> | I. Introduction |

# ZH/EN Parallel Summary

| Section | English summary | 中文摘要 | Terms kept in source language | Ambiguities |
|---|---|---|---|---|
| I. Introduction | ... | ... | edge computing |  |
```

## Pass criteria

- Keeps IEEE section order and citation markers unchanged.
- Extracts captions verbatim into a table.
- Adds ZH/EN summary only after extraction.
- Uses `AUTHOR_INPUT_NEEDED` for missing DOI or unreadable PDF text.
