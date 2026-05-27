## Input

Need: citation mapping.

Manuscript order: `[CITE_KEY_a] [CITE_KEY_b] [CITE_KEY_c] [CITE_KEY_e] [CITE_KEY_h] [CITE_KEY_i] [CITE_KEY_j]`.

Target venue: permits compact citation ranges.

Metadata: all seven keys have complete author-provided records.

## Expected output

The skill assigns first-appearance numbers and compacts consecutive runs only where permitted:

```text
[CITE_KEY_a] -> [1]
[CITE_KEY_b] -> [2]
[CITE_KEY_c] -> [3]
[CITE_KEY_e] -> [4]
[CITE_KEY_h] -> [5]
[CITE_KEY_i] -> [6]
[CITE_KEY_j] -> [7]
```

When cited as a group, `[1]–[3], [5]–[7]` is allowed and disjoint numbers stay separate.

## Pass criteria

- Consecutive runs are compacted only because the target permits it.
- Disjoint citations are not merged.
- Mapping table remains explicit even when the manuscript uses compact ranges.
