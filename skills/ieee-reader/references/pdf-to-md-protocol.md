# PDF / Xplore to Markdown Protocol

## Extraction Order

1. Capture source metadata before body text: title, authors, venue, year, DOI, IEEE Xplore document number, and license notes if visible.
2. Reconstruct the reading order by column, page, and heading hierarchy before emitting Markdown.
3. Preserve headings exactly, including roman numerals, lettered subsections, appendices, acknowledgments, references, and biographies.
4. Extract display equations with their labels; use `AUTHOR_INPUT_NEEDED` for unreadable symbols.
5. Extract captions verbatim into a caption table and leave figure/table callouts in the body.
6. Extract references as numbered entries and map all body citation markers to those entries.
7. Record extraction uncertainty in `# Extraction Log`.

## Markdown Skeleton

```markdown
# Metadata

| Field | Value |
|---|---|
| Title | ... |
| DOI | ... |

# Extracted Markdown

## Abstract

...

## I. Introduction

...

# Captions

| Type | Number | Caption | Source |
|---|---:|---|---|

# Citation Mapping

| Marker | Reference entry | First seen |
|---|---|---|

# Extraction Log

- ...
```

## Handling Two-Column Layout

- Prefer native PDF text extraction when it preserves column order.
- If OCR is needed, run page-level OCR and manually check headings, equations, and caption boundaries.
- Never merge the left column of one section with the right column of another section.
- Treat marginal footnotes, author affiliations, copyright notices, and biographies as separate blocks.
