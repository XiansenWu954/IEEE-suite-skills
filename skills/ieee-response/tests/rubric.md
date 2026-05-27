# Quality Rubric - ieee-response

The skill is shippable when all six dimensions score at least 4 out of 5 and the total score is at least 24 out of 30.

## 1. Completeness (0-5)

- 5: Every reviewer comment is parsed, classified, answered or flagged, and entered into the R&R matrix.
- 3: Most comments are handled, but one or two need manual regrouping.
- 1: The output is a generic response-letter outline.

## 2. Traceability (0-5)

- 5: Every claimed fix maps to a page, section, line, figure, table, appendix, or supplied manuscript location.
- 3: Claimed fixes cite broad sections but not exact locations.
- 1: Responses claim changes without traceable manuscript anchors.

## 3. Factuality (0-5)

- 5: Missing evidence, unavailable results, unsupported citations, and contradictory author constraints trigger `AUTHOR_INPUT_NEEDED`.
- 3: The skill warns about missing facts but still drafts some uncertain language.
- 1: The skill invents plausible experiments, citations, statistics, or data.

## 4. IEEE Fit (0-5)

- 5: The response assumes IEEE single-blind review, uses reviewer numbers only, and cites IEEE peer-review policy.
- 3: The response is mostly IEEE-compatible but could fit many publishers.
- 1: The response ignores IEEE review context or uses incompatible citation and formatting conventions.

## 5. Actionability (0-5)

- 5: The output is a ready-to-review reply letter plus a complete R&R matrix and flagged-input list.
- 3: The output gives good suggestions but requires the author to build the final artifacts.
- 1: The output is only advice about how to respond.

## 6. Cross-Skill Integration (0-5)

- 5: The output names handoffs to `ieee-writing`, `ieee-citation`, and related skills with concrete artifacts.
- 3: The output mentions siblings without handoff details.
- 1: The skill stands alone and cannot feed a resubmission workflow.

## Scoring Procedure

1. Read `SKILL.md` and score completeness plus IEEE fit.
2. Execute one fixture mentally and score traceability, factuality, and actionability.
3. Check the integration section and score cross-skill integration.
4. Confirm no red-line behavior appears in the output.
