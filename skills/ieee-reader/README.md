# ieee-reader

> Convert IEEE PDF or IEEE Xplore pages into structured Markdown with IEEE Reference Guide citation mapping and bilingual ZH/EN handoff.

## What this does

`ieee-reader` extracts IEEE paper structure without rewriting it. It preserves section numbering, `Fig. N` and `Table N` captions, equation markers, and numeric citation markers so a user can inspect or reuse the paper as structured Markdown. It can add a ZH/EN parallel summary after extraction while keeping source terminology stable.

## Example

Input:

```text
Read ./papers/example-ieee.pdf and produce structured Markdown plus a Chinese-English section summary.
```

Output:

```text
ieee-reader-output.md
- Metadata
- Extracted Markdown
- Captions
- Citation Mapping
- Extraction Log
- ZH/EN Parallel Summary
```

## See also

- [SKILL.md](./SKILL.md) - canonical skill file
- [References](./references/) - source URL stubs and extraction protocols
- Sibling skills: [ieee-academic-search](../ieee-academic-search), [ieee-citation](../ieee-citation), [ieee-writing](../ieee-writing)
