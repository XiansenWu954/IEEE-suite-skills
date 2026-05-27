## Input

The user provides one title with no DOI: "Learning over unreliable edge links" and asks for sibling papers.

## Expected output

The skill searches title variants and returns only candidates with verified DOI or stable IEEE Xplore URL. If several near-duplicates exist, it emits:

```markdown
AUTHOR_INPUT_NEEDED: multiple records match the supplied title. Provide one of: DOI, author list, year, or venue.
```

## Pass criteria

- Does not pick a near-duplicate silently.
- Does not invent a DOI.
- Records source queries and deduplication decisions.
