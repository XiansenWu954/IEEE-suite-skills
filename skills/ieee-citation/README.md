# ieee-citation

> Handle IEEEtran.bst BibTeX and IEEE Reference Guide numeric [N] citations for IEEE LaTeX manuscripts.

## What this does

`ieee-citation` converts DOI lists, RIS exports, plain references, or rough BibTeX into IEEEtran-compatible `.bib` entries. It can also assign numeric `[N]` citations by first appearance and create a citation mapping table. Missing metadata is never guessed; unresolved sources become `AUTHOR_INPUT_NEEDED`.

## Example

Input:

```text
Need: references.bib and citation-map.md
Order: [CITE_KEY_sched], [CITE_KEY_trace], [CITE_KEY_sched]
Metadata: DOI for CITE_KEY_sched, plain-text record for CITE_KEY_trace
```

Output:

```text
references.bib
citation-map.md

[CITE_KEY_sched] -> [1]
[CITE_KEY_trace] -> [2]
```

## See also

- [SKILL.md](./SKILL.md) - the canonical skill file
- [References](./references/) - IEEE official docs and local citation aids
- Sibling skills: [ieee-writing](../ieee-writing), [ieee-polishing](../ieee-polishing), [ieee-template](../ieee-template)
