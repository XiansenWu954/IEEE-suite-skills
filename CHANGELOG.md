# Changelog

All notable changes to **IEEE-suite-skills** are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Per-sub-skill versions are tracked in each `skills/ieee-*/SKILL.md` frontmatter
(`version:` field) and may advance independently between repo releases.

---

## [Unreleased]

## [0.1.1] — 2026-05-27

### Changed
- **ieee-venue-selector** raised from 23/30 to 28/30 on independent 6-dimension review:
  - Added 13 new per-venue reference stubs (TPDS, TMLCN, TWC, TCOM, TSP, TPAMI,
    TAC, TVT, TII, IEEE Access, INFOCOM, GLOBECOM, ICRA) with `Verified: 2026-05-27`
    stamps and live WebFetch confirmations. Traceability now spans every venue
    in the matrix, not just the seed three.
  - Workflow step 2 hardened: explicit `NON_IEEE_VENUE_REQUEST` abort for any
    user-named non-IEEE venue (ACM SIGCOMM, MobiCom, Springer, Elsevier, Nature),
    with redirection to that ecosystem's tools.
  - `AUTHOR_INPUT_NEEDED` paths added at two more workflow decision points
    (missing matrix field for ranking; topic outside curated matrix).
  - `tests/red-line.md` extended with cases for non-IEEE venue and out-of-matrix
    topic.
  - Purpose section now states "IEEE-published or IEEE-cosponsored venues only"
    as a hard contract.

- **ieee-polishing** raised from 26/30 to 28/30:
  - Workflow step 5 replaced abstract "normalize house style" with five concrete
    sub-rules: passive-voice ratio target (≤40% in paragraphs >120 words),
    first-use abbreviation expansion, SI unit spacing (e.g., `5 ms` not `5ms`),
    `Fig. N`/`Table N` callout shorthand, en-dash for numeric ranges.
  - Output contract specifies unified-diff format with `---`/`+++` markers and
    rule-rationale lines; alternative clean-replacement mode produces an
    accompanying issue list with rule references.
  - `tests/golden.md` expanded with a complete diff-mode example demonstrating
    the new format.

- **ieee-data** raised from 26/30 to 28/30:
  - Workflow step 2 hardened: explicit `NON_IEEE_VENUE_REQUEST` abort when the
    target venue is outside IEEE (journals, IEEE-cosponsored conferences, or
    IEEE Letters).
  - `tests/red-line.md` extended with three new cases: non-IEEE venue redirect,
    proprietary data without persistent DOI plan, and missing IRB approval
    declaration for human-subjects research.

### Audit
- Iteration 1 review pass: every revised sub-skill scores ≥ 27/30 on the
  6-dimension rubric, with no dimension below 4. Independent Lead review
  confirms the worker self-rubric within ±1 point.
- Anti-pattern grep over revised sub-skills returns only the expected
  intentional mentions of non-IEEE publishers (inside `NON_IEEE_VENUE_REQUEST`
  handlers as redirect targets), with no leakage into IEEE-authority claims.

## [0.1.0] — 2026-05-27

### Added
- Initial repository scaffold: 10 sub-skill subdirectories, plugins manifest,
  governance docs (LICENSE / CONTRIBUTING / CODE_OF_CONDUCT / SECURITY),
  GitHub Actions for dead-link checking.
- Ten v0.1.0 sub-skill deliveries: SKILL.md (8-section schema-conformant) +
  README + references (URL stubs + paraphrased cheatsheets) + tests (rubric +
  golden / edge-case / red-line fixtures), each scoring ≥ 27/30 on the 6-dimension
  quality rubric (per worker self-evaluation; subsequent independent review
  led to v0.1.1 revisions of three sub-skills — see above).

### Audit
- Cleanliness audit pass: 2026-05-27 by repository maintainer (Tiers 1–6).
- Zero leakage of unrelated-project identifiers, private filesystem paths, or
  private tooling references in tracked content.
- All fixture inputs use fictional or domain-generic IEEE topics; no
  manuscript content from any specific in-flight project.
- Maintainer identity set to `XiansenWu954`; all `author:` fields and
  repository URLs reference this GitHub account.

### Sub-skill versions
| Sub-skill | Version | Status |
|---|---|---|
| ieee-writing | 0.1.0 | Stable (target) |
| ieee-polishing | 0.1.0 | Stable (target) |
| ieee-figure | 0.1.0 | Stable (target) |
| ieee-citation | 0.1.0 | Stable (target) |
| ieee-response | 0.1.0 | Stable (target) |
| ieee-reader | 0.1.0 | Beta (target) |
| ieee-academic-search | 0.1.0 | Beta (target) |
| ieee-data | 0.1.0 | Beta (target) |
| ieee-template | 0.1.0 | Beta (target) |
| ieee-venue-selector | 0.1.0 | Beta (target) |

---

## [0.1.0] — TBD (v0.1.0 release pending)

First public release. Ships 10 sub-skills covering the end-to-end IEEE
manuscript workflow:

- **Writing**: `ieee-writing`, `ieee-polishing`, `ieee-citation`
- **Figures & LaTeX**: `ieee-figure`, `ieee-template`
- **Submission & review**: `ieee-response`, `ieee-data`
- **Information & discovery**: `ieee-reader`, `ieee-academic-search`, `ieee-venue-selector`

Inspired in structure by [`Yuan1z0825/nature-skills`](https://github.com/Yuan1z0825/nature-skills);
content is entirely IEEE-focused and authored independently.

### Notes
- Complementary to [`cookjohn/ieee-skills`](https://github.com/cookjohn/ieee-skills),
  which automates IEEE Xplore browsing. We orchestrate at the manuscript level;
  they operate at the website level. Both can coexist.
