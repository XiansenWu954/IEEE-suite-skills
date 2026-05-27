## Input

Find citation candidates for an IEEE Transactions manuscript on ultra-wideband indoor localization with neural-network-aided ranging. Prefer 2022-2026 and return DOI-backed IEEE or signal-processing papers.

## Expected output

```markdown
# Ranked Citation Candidates

| Rank | Total | Score breakdown | Title | Authors | Venue | Year | DOI | IEEE Xplore URL | DBLP key | Crossref status | Rationale |
|---:|---:|---|---|---|---|---:|---|---|---|---|---|
| 1 | 11/12 | relevance 5; venue 3; recency 2; metadata 1 | ... | ... | IEEE ... | 2025 | 10.... | <IEEE Xplore URL> | ... | matched | Direct UWB-ranging / neural-aided localization overlap |

# Search Log

1. IEEE Xplore query: ...
2. DBLP query: ...
3. Crossref query: ...

# BibTeX Handoff

- DOI: 10....
  title: ...
  target: ieee-citation
```

## Pass criteria

- Searches IEEE Xplore first.
- Shows score components.
- Includes DOI or stable IEEE Xplore URL for each candidate.
- Provides a handoff to `ieee-citation`.
