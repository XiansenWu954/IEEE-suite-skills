## Input

The user pastes OCR text from a two-column IEEE article where `Fig. 2` appears before `Fig. 1`, equation `(3)` is unreadable, and references `[7]` and `[8]` are merged.

## Expected output

The skill emits Markdown in source order, keeps the figure numbering as observed, and records:

```markdown
# Extraction Log

- AUTHOR_INPUT_NEEDED: Equation (3) contains unreadable OCR tokens.
- AUTHOR_INPUT_NEEDED: References [7] and [8] appear merged; user must provide the reference-list image or cleaner text.
```

## Pass criteria

- Does not renumber figures.
- Does not invent equation content.
- Does not split a merged reference without evidence.
- Keeps the source's section order even when captions appear out of numeric order.
