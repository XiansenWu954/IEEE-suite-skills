# Bilingual ZH/EN Handoff

Use this only after the extract-only Markdown is complete.

## Output Format

```markdown
# ZH/EN Parallel Summary

| Section | English summary | 中文摘要 | Terms kept in source language | Ambiguities |
|---|---|---|---|---|
| I. Introduction | ... | ... | edge computing; federated learning | AUTHOR_INPUT_NEEDED: ... |
```

## Rules

1. Keep formulas, algorithm names, datasets, protocol names, and venue names in the source language unless the user provides a glossary.
2. Translate claims conservatively and preserve uncertainty markers.
3. Do not translate a citation marker or caption number.
4. Use `AUTHOR_INPUT_NEEDED` for ambiguous technical terms, OCR artifacts, or missing context.
