# Quality Rubric — All Sub-skills MUST Pass

> **For Codex workers**: Copy this file verbatim to `skills/ieee-<topic>/tests/rubric.md`
> as the evaluation framework. Add 3+ fixture cases per skill in the same `tests/` folder.
>
> **For Lead**: A sub-skill is shippable when all 6 dimensions score ≥ 4/5.
> If any dimension is < 4/5, the sub-skill goes back to its worker for fix.

---

## 6 Evaluation Dimensions

### 1. Completeness (0–5)

Every claim made in `SKILL.md` is operationally enforceable. The skill leaves
no unfinished markers, "fill in later" text, or unresolved appendix pointers.

- **5** — Every step in `Workflow` executes with no human gap-filling.
- **3** — One or two steps require external clarification (acceptable for niche venues).
- **1** — Skill is a stub.

### 2. Traceability (0–5)

Every IEEE rule cited in the skill maps to a specific section of an IEEE
official document. No floating "IEEE says..." claims.

- **5** — Every constraint links to IEEE Editorial Style Manual / Reference Guide / venue Author Info, with section or page anchor.
- **3** — Cites the document but not the specific section.
- **1** — Vague "IEEE recommends..." with no citation.

### 3. Factuality (0–5)

The skill enforces the "never fabricate" rule downstream. When data/results
are missing, the skill outputs an `AUTHOR_INPUT_NEEDED` token rather than
guessing.

- **5** — Skill explicitly handles missing inputs with named tokens; tests cover this path.
- **3** — Skill notes the rule but doesn't enforce it in workflow.
- **1** — Skill happily fills in plausible-looking but unverified numbers.

### 4. IEEE-fit (0–5)

The skill is unambiguously IEEE. It refuses to apply non-IEEE publisher conventions.

- **5** — Workflow has explicit "if user is targeting non-IEEE venue, abort and recommend that ecosystem" branch; numeric `[N]` references; double-column metrics; single-blind defaults.
- **3** — Mostly IEEE but some generic academic advice slips in.
- **1** — Could be applied to any journal; nothing IEEE-specific.

### 5. Actionability (0–5)

Output is immediately usable. No "consider revising" hedging — concrete diffs,
LaTeX, BibTeX entries, prose paragraphs.

- **5** — Output is a copy-pasteable artifact; user takes it and moves on.
- **3** — Output is a checklist or suggestion; user still has to write the artifact.
- **1** — Output is meta-advice ("you should think about X").

### 6. Cross-skill integration (0–5)

The skill names its upstream and downstream `ieee-*` siblings explicitly. The
`Integration` section traces concrete handoffs.

- **5** — Names at least 2 sibling skills, with sample input/output handoff format.
- **3** — Names siblings but no handoff format.
- **1** — Lives in isolation, no integration plan.

---

## Tests folder — required fixtures

Beside `rubric.md`, each `skills/ieee-<topic>/tests/` MUST contain **at least 3** fixture cases:

| Fixture filename | Purpose |
|---|---|
| `golden.md` | A textbook-correct input → ideal output. Demonstrates the happy path. |
| `edge-case.md` | A boundary input (e.g., overlength manuscript, missing data table, multi-author). |
| `red-line.md` | An input that should trigger a refusal or `AUTHOR_INPUT_NEEDED` — verifies the skill enforces its Red Lines. |

Optional but encouraged:
- `cross-venue.md` — same input targeted at TMC vs TPAMI vs INFOCOM, verifies the venue-selector chain works.
- `multilingual.md` — Chinese-input → English-output handoff (the repo supports zh+en use cases).

Each fixture is a Markdown file with three sections:

```markdown
## Input
<verbatim user request or manuscript chunk>

## Expected output
<verbatim ideal skill output>

## Pass criteria
<bullet list of what reviewer should check>
```

---

## Scoring procedure (used by Lead in review)

1. Read `SKILL.md` end-to-end without running anything. Score Completeness + IEEE-fit.
2. Pick 1 fixture from `tests/`. Mentally execute the workflow on it. Score Traceability + Factuality + Actionability.
3. Read `Integration` section. Cross-check that named sibling skills exist. Score Cross-skill integration.
4. Total = sum of 6 dimensions, max 30. Ship threshold: ≥ 24 AND no single dimension < 4.
5. Sub-threshold sub-skills get a fix list (specific line numbers + expected change) and one revision cycle. Two revision cycles max; if still failing, escalate to Lead for redesign.
