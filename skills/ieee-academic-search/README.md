# ieee-academic-search

> Orchestrate IEEE Xplore, DBLP, and Crossref for IEEE related work, DOI metadata, and IEEE arXiv preprint policy checks.

## What this does

`ieee-academic-search` turns topic keywords, seed papers, or weak citation areas into a ranked list of citation candidates. It searches IEEE Xplore first for IEEE manuscripts, expands with DBLP, verifies metadata through Crossref, and reports a score breakdown instead of a black-box ranking. It also reminds authors how to handle their own arXiv or TechRxiv preprint during IEEE submission.

## Example

Input:

```text
Find recent IEEE and networking papers related to federated learning over edge networks. Prefer 2022-2026 and return DOI-backed candidates.
```

Output:

```text
ieee-academic-search-results.md
- Ranked citation candidates
- Score breakdown
- DOI / Xplore / DBLP / Crossref metadata
- Search log
- BibTeX handoff for ieee-citation
```

## See also

- [SKILL.md](./SKILL.md) - canonical skill file
- [References](./references/) - source URL stubs and search policies
- Sibling skills: [ieee-reader](../ieee-reader), [ieee-citation](../ieee-citation), [ieee-writing](../ieee-writing)
