# Search Protocol

## Query Construction

1. Build one IEEE Xplore query from exact technical phrases, core synonyms, and target venue keywords.
2. Build one DBLP query from title words, author surnames, acronym venues, and year bounds.
3. Build one Crossref query from normalized title strings or DOI prefixes.
4. Keep quoted phrases for exact concepts and avoid broad single-word queries unless paired with venue or method terms.

## Deduplication

Use this priority order:

1. Exact DOI match.
2. Exact IEEE Xplore document number match.
3. Normalized title match after lowercasing, punctuation removal, and whitespace compaction.
4. Same first author, same year, and title similarity above a high threshold.

## Ranking Score

| Component | Range | Meaning |
|---|---:|---|
| Relevance | 0-5 | Direct match to method, task, and domain |
| Venue fit | 0-3 | IEEE target fit or strong sibling community |
| Recency | 0-2 | Current enough for the user's field |
| Metadata completeness | 0-2 | DOI, venue, year, authors, abstract snippet present |

Always display the component values and total.

## Failure Handling

- Use `AUTHOR_INPUT_NEEDED` when the user supplies only vague topic words.
- Drop or quarantine candidates with missing DOI and no stable IEEE Xplore URL.
- State which source returned each candidate.
