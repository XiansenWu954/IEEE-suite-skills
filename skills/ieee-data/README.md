# ieee-data

> Draft IEEE Research Reproducibility data/code availability statements with DOI hosting for IEEE journal submissions.

## What this does

`ieee-data` turns artifact notes into IEEE-ready data and code availability statements. It chooses among DOI-capable hosts, separates code and data licensing, and preserves restrictions rather than weakening them. It refuses personal cloud links as archival hosts and flags missing DOI, license, and access-policy facts with `AUTHOR_INPUT_NEEDED`.

## Example

Input: open dataset on Zenodo with DOI, code release on Zenodo with DOI, code license MIT, data license CC BY 4.0.

Output:

`Data and code availability: The dataset and analysis code supporting this study are available in [repository] under DOI: [DOI]. The data are licensed under CC BY 4.0, and the code is licensed under MIT.`

The same workflow can produce restricted-data, no-data, and hybrid statements.

## See also

- [SKILL.md](./SKILL.md) - the canonical skill file
- [References](./references/) - IEEE reproducibility guidance, repository stubs, and license matrix
- Sibling skills: [ieee-writing](../ieee-writing), [ieee-template](../ieee-template), [ieee-response](../ieee-response)
