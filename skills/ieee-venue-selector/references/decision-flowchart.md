# Decision Flowchart

1. Ask whether the user prefers journal, conference, open access, or no preference.
2. Ask for IEEE double-column page count, abstract word count, topic keywords, and contribution type.
3. If the topic is primarily mobile, networking, wireless, communications, vision, robotics, control, industrial informatics, signal processing, vehicular systems, or multidisciplinary IEEE scope, continue.
4. If the topic does not match any matrix scope keyword, return no-fit inside this skill.
5. Filter by page budget and mark any overlength or `未确认` fee risk.
6. Filter by blind-review constraints only when the user's anonymity needs conflict with the venue row.
7. Score topic fit, page-budget fit, evidence fit, audience fit, and submission friction.
8. Return top three cards with official URL and score breakdown.
9. Hand the selected target to `ieee-writing`, `ieee-template`, and `ieee-academic-search`.

## Score Template

```markdown
| Venue | Total | Topic fit /5 | Page fit /3 | Evidence fit /2 | Audience fit /3 | Friction fit /2 | Penalties | Rationale |
|---|---:|---:|---:|---:|---:|---:|---|---|
```
