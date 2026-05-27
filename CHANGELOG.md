# Changelog

All notable changes to **IEEE-suite-skills** are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

Per-sub-skill versions are tracked in each `skills/ieee-*/SKILL.md` frontmatter
(`version:` field) and may advance independently between repo releases.

---

## [Unreleased]

### Added
- Initial repository scaffold: 10 sub-skill subdirectories, plugins manifest,
  governance docs (LICENSE / CONTRIBUTING / CODE_OF_CONDUCT / SECURITY),
  GitHub Actions for dead-link checking.
- Ten v0.1.0 sub-skill deliveries: SKILL.md (8-section schema-conformant) +
  README + references (URL stubs + paraphrased cheatsheets) + tests (rubric +
  golden / edge-case / red-line fixtures), each scoring ≥ 27/30 on the 6-dimension
  quality rubric.

### Audit
- Cleanliness audit pass: 2026-05-27 by repository maintainer (Tiers 1–6).
- Zero AURA-style / private-path / private-tooling leakage in tracked content.
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
