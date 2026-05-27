## Input

Need: `.bib` and citation mapping.

Manuscript order: `[CITE_KEY_alpha]`, `[CITE_KEY_beta]`, `[CITE_KEY_alpha]`.

Metadata: two complete DOI records with authors, title, venue, pages, month, year, and DOI.

## Expected output

The skill writes `references.bib` with two IEEEtran-compatible entries and `citation-map.md` with:

```text
[CITE_KEY_alpha] -> [1]
[CITE_KEY_beta] -> [2]
```

Repeated citations of `CITE_KEY_alpha` remain `[1]`.

## Pass criteria

- Numbering follows first appearance.
- BibTeX entries include required fields and no fabricated metadata.
- Month names use the local month abbreviation list.
- Output can be handed to `ieee-template` for IEEEtran.bst compilation.
