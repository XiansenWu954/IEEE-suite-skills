## Input

Target venue: generic IEEE Transactions.

Stage: first draft.

Content: A 220-word abstract, six index terms, sections for introduction, method, evaluation, discussion, and conclusion, two equations, three figures, and citation placeholders `[CITE_KEY_scheduler]` and `[CITE_KEY_trace]`.

## Expected output

The skill returns a revised `manuscript.md` with IEEE-style title block, abstract, index terms, numbered main sections, equation callouts `(1)` and `(2)`, `Fig. 1` through `Fig. 3` callouts, and an `IEEE_HANDOFF` block.

The `IEEE_HANDOFF` block lists:

- target: generic IEEE Transactions
- next skills: `ieee-polishing`, `ieee-citation`, `ieee-figure`, `ieee-template`
- unresolved: none

## Pass criteria

- Workflow confirms target venue and manuscript stage before drafting.
- Abstract remains at or below 250 words.
- Six index terms are retained.
- Citation placeholders are preserved for `ieee-citation`.
- No unsupported data or claims are added.
