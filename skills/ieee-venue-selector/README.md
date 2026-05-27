# ieee-venue-selector

> Recommend IEEE journal, IEEE Transactions, or IEEE conference venues with blind-review policy and transparent score breakdowns.

## What this does

`ieee-venue-selector` compares a manuscript against 12 IEEE journal rows and 8 IEEE/ACM conference rows, with ACM rows labeled as comparisons rather than IEEE recommendations. It filters by scope, page budget, review policy, fees, submission system, supplementary-material policy, and author preference. It returns top venue cards with score breakdowns and calls out `未确认` fields instead of guessing.

## Example

Input:

```text
I have a 13-page wireless edge-learning manuscript with experiments and code. Recommend an IEEE venue and show the score breakdown.
```

Output:

```text
ieee-venue-selector-report.md
- Hard filters
- Score breakdown table
- Top 3 venue cards
- Unverified fields
- Next skills: ieee-writing, ieee-template, ieee-academic-search
```

## See also

- [SKILL.md](./SKILL.md) - canonical skill file
- [References](./references/) - venue matrices and URL stubs
- Sibling skills: [ieee-writing](../ieee-writing), [ieee-template](../ieee-template), [ieee-academic-search](../ieee-academic-search)
