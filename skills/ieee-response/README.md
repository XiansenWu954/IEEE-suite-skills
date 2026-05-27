# ieee-response

> Draft IEEE journal single-blind peer review replies and R&R matrices for IEEE Transactions reviewer comments.

## What this does

`ieee-response` converts editor and reviewer comments into a point-by-point IEEE reply package. It keeps the single-blind boundary clear, uses respectful reviewer-facing language, and refuses to invent results, citations, or manuscript changes. The output is a reply letter plus a Revision and Response matrix that the author can align with the revised manuscript.

## Example

Input: reviewer comments plus author-supplied changes such as `Section III-B, lines 214-229 now reports the ablation`.

Output: a Markdown reply letter with `R1.1` style comment IDs and an R&R matrix row for each reviewer comment:

| ID | Classification | Manuscript change location | Response status |
|---|---|---|---|
| R1.1 | agree-and-fix | Section III-B, lines 214-229 | Drafted |

If a reviewer requests a result the author cannot provide, the skill outputs `AUTHOR_INPUT_NEEDED` with the exact question to answer before drafting.

## See also

- [SKILL.md](./SKILL.md) - the canonical skill file
- [References](./references/) - IEEE policy and response templates
- Sibling skills: [ieee-writing](../ieee-writing), [ieee-citation](../ieee-citation), [ieee-data](../ieee-data)
