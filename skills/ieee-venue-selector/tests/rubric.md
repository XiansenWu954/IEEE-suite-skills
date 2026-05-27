# Quality Rubric

## 6 Evaluation Dimensions

### 1. Completeness (0-5)

Every claim made in `SKILL.md` is operationally enforceable. The skill leaves no unfinished placeholders.

- **5** - Every workflow step executes with no human gap-filling.
- **3** - One or two steps require external clarification.
- **1** - Skill is a stub.

### 2. Traceability (0-5)

Every IEEE rule cited in the skill maps to a specific authoritative source.

- **5** - Every constraint links to an IEEE official source or a local verified reference file.
- **3** - Cites a document but not the relevant local protocol.
- **1** - Uses vague claims with no source.

### 3. Factuality (0-5)

The skill enforces the never-fabricate rule downstream.

- **5** - Missing inputs produce `AUTHOR_INPUT_NEEDED`; tests cover this path.
- **3** - Notes the rule but does not enforce it in workflow.
- **1** - Fills in plausible-looking unverified values.

### 4. IEEE-fit (0-5)

The skill is unambiguously IEEE and preserves numeric `[N]` citations.

- **5** - Uses IEEE-specific article, citation, venue, or submission constraints.
- **3** - Mostly IEEE but some generic academic guidance slips in.
- **1** - Could apply to any paper with no IEEE-specific constraints.

### 5. Actionability (0-5)

Output is immediately usable.

- **5** - Output is a copy-pasteable artifact with concrete fields and logs.
- **3** - Output is mainly a checklist.
- **1** - Output is meta-advice.

### 6. Cross-skill integration (0-5)

The skill names sibling `ieee-*` skills and concrete handoff formats.

- **5** - Names at least 2 sibling skills with sample handoff fields.
- **3** - Names siblings but no handoff format.
- **1** - Lives in isolation.

## Tests Folder Fixtures

Each fixture contains `## Input`, `## Expected output`, and `## Pass criteria`. The required fixtures are `golden.md`, `edge-case.md`, and `red-line.md`.

## Scoring Procedure

1. Read `SKILL.md` end-to-end and score Completeness plus IEEE-fit.
2. Execute one fixture mentally and score Traceability, Factuality, and Actionability.
3. Read `Integration` and score Cross-skill integration.
4. Pass threshold is total score at least 24/30 with no dimension below 4.
