# Quality Rubric - ieee-data

The skill is shippable when all six dimensions score at least 4 out of 5 and the total score is at least 24 out of 30.

## 1. Completeness (0-5)

- 5: Every data, code, model, and documentation artifact has status, host, DOI plan, access terms, and license or restriction note.
- 3: Most artifacts are handled, but one artifact type has an incomplete DOI or license decision.
- 1: The output is a generic availability paragraph.

## 2. Traceability (0-5)

- 5: Repository and license recommendations link to verified sources and state why each choice fits the artifact.
- 3: Recommendations name repositories and licenses but give limited rationale.
- 1: Recommendations are unsupported or cite informal sources.

## 3. Factuality (0-5)

- 5: Missing DOI, access policy, ownership, restriction, or license facts trigger `AUTHOR_INPUT_NEEDED`.
- 3: The skill warns about missing facts but still drafts uncertain claims.
- 1: The skill invents DOIs, repository records, citations, statistics, or public-access claims.

## 4. IEEE Fit (0-5)

- 5: The output follows IEEE Research Reproducibility guidance and uses DOI-capable repositories suitable for IEEE submissions.
- 3: The output is broadly scholarly but only lightly IEEE-specific.
- 1: The output recommends nonpersistent personal storage or ignores IEEE reproducibility context.

## 5. Actionability (0-5)

- 5: The output includes paste-ready data and code availability statements, hosting rationale, and license table.
- 3: The output gives a useful checklist but leaves the final statement unwritten.
- 1: The output is only advice about sharing data.

## 6. Cross-Skill Integration (0-5)

- 5: The output names handoffs to `ieee-writing`, `ieee-template`, and `ieee-response` with concrete artifacts.
- 3: The output mentions sibling skills without handoff detail.
- 1: The skill cannot feed the manuscript or revision workflow.

## Scoring Procedure

1. Read `SKILL.md` and score completeness plus IEEE fit.
2. Execute one fixture mentally and score traceability, factuality, and actionability.
3. Check the integration section and score cross-skill integration.
4. Confirm no red-line behavior appears in the output.
