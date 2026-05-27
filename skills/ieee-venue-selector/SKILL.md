---
name: ieee-venue-selector
version: 0.1.0
description: Recommend IEEE journal, IEEE Transactions, or IEEE conference venues with blind-review policy and transparent score breakdowns.
author: XiansenWu954
status: Stable
tags:
  - ieee
  - venue
  - journals
  - conferences
license: MIT
---

## Purpose

This skill recommends an IEEE-aligned venue from a curated matrix of 12 journals and 8 conferences while making every constraint visible. It anchors general venue discovery to the IEEE Author Center at https://journals.ieeeauthorcenter.ieee.org/ and venue-specific rows to the verified URLs in [references/journal-matrix.csv](references/journal-matrix.csv) and [references/conference-matrix.csv](references/conference-matrix.csv). The engineering constraint is transparent ranking: every recommendation must show hard filters, score components, and any `未确认` field rather than hiding uncertainty.

## When to use

- When the user has a manuscript topic and asks which IEEE journal or IEEE conference fits best.
- When the user needs a page-budget check before drafting or shortening an IEEE manuscript.
- When the user is choosing between TMC, TON, TPDS, TWC, TCOM, TPAMI, TAC, TVT, TII, IEEE Access, INFOCOM, ICC, GLOBECOM, CVPR, ICCV, or ICRA, with ACM rows used only as labeled comparisons.
- When the user wants to know whether journal, conference, or open-access routing is more practical.
- When a manuscript may not fit any IEEE venue and needs an explicit no-fit outcome.

## Input contract

- Accept topic, contribution type, manuscript length, figure/table count, data/code availability, target audience, urgency, and author preference.
- Require page count in IEEE double-column equivalent when applying page-budget filters.
- Accept optional preferences: journal vs conference, open access, rapid review, audience, and willingness to pay APC or overlength charges.
- Treat any missing decisive field as `AUTHOR_INPUT_NEEDED`.
- Use only rows in `journal-matrix.csv` and `conference-matrix.csv`; do not invent venues.

## Workflow

1. Intake topic, contribution type, page count, data/code status, preferred publication type, open-access preference, and timeline.
2. Load `references/journal-matrix.csv` and `references/conference-matrix.csv` before recommending any venue.
3. Filter out venues whose scope keywords do not match the manuscript topic or target community, and keep ACM-sponsored rows only as labeled non-IEEE comparisons unless the user explicitly asks for them.
4. Apply hard constraints for page limit, abstract limit, blind type, submission system, supplementary policy, sponsor, fees, and `未确认` fields.
5. Score each remaining IEEE or IEEE/CVF venue with topic fit 0-5, page-budget fit 0-3, evidence/reproducibility fit 0-2, audience fit 0-3, and submission-friction fit 0-2.
6. Penalize rows with decisive `未确认` fields and surface those fields in the venue card.
7. Return the top three venue cards with name, URL, sponsor, page limit, abstract limit, blind type, overlength fee, submission system, supplementary material policy, score breakdown, and rationale.
8. If no IEEE venue fits, state that no matrix venue fits and tell the user to seek venues outside this skill's scope.
9. Recommend follow-on skills: `ieee-writing` for page-budget drafting, `ieee-template` for IEEEtran conversion, and `ieee-academic-search` for related-work coverage.

## Output contract

- Produce a Markdown recommendation report named by the user or default to `ieee-venue-selector-report.md`.
- Include `# Intake`, `# Hard Filters`, `# Score Breakdown`, `# Top 3 Venue Cards`, `# Unverified Fields`, and `# Next Skills`.
- Show each score component, not only the final rank.
- Include the official venue URL from the matrix row in every venue card.
- Define done as a transparent recommendation or explicit no-fit result with no fabricated policy fields.

## Scope boundary

### ✓ In scope

- Recommending IEEE and IEEE/CVF venues from the matrix, with ACM rows shown only as explicit comparisons.
- Comparing topic fit, page budget, blind-review constraints, fees, systems, and supplementary material policies.
- Flagging `未确认` fields and telling the user to verify on submission day.
- Distinguishing IEEE, IEEE/CVF, and ACM-sponsored rows without changing their sponsorship labels.

### ✗ Out of scope

- Recommending venues outside the provided matrix.
- Estimating acceptance probability or impact factor beyond the matrix tier labels.
- Submitting a manuscript or creating camera-ready files.
- Treating old CFPs, forum posts, or unofficial pages as venue authority.

### 🚩 Red lines (NEVER do these)

- Never recommend an ACM-sponsored row as an IEEE venue.
- Never invent page limits, fees, blind policy, submission systems, or supplementary-material rules.
- Never conflate ACM-sponsored SIGCOMM or MobiCom with IEEE-sponsored conferences; they are ACM-sponsored and double-blind.
- Never hide `未确认` fields from the user.
- Never output a ranked list without score breakdowns.

## References

1. IEEE Author Center: https://journals.ieeeauthorcenter.ieee.org/ (see [references/AC.url.txt](references/AC.url.txt)).
2. TMC Author Information: https://www.computer.org/tmc-author-information (see [references/TMC.url.txt](references/TMC.url.txt)).
3. TON/TNET Author Information: https://www.comsoc.org/publications/journals/ieee-tnet/policies-guidelines (see [references/TON.url.txt](references/TON.url.txt)).
4. Journal matrix: [references/journal-matrix.csv](references/journal-matrix.csv).
5. Conference matrix: [references/conference-matrix.csv](references/conference-matrix.csv).
6. Decision flowchart: [references/decision-flowchart.md](references/decision-flowchart.md).
7. Companion skills: [../ieee-writing](../ieee-writing), [../ieee-template](../ieee-template), [../ieee-academic-search](../ieee-academic-search).

> **Disclaimer**: IEEE venue policies change. Verify against the official Author Info page on submission day.

## Integration

`ieee-venue-selector` emits `target_venue`, `sponsor`, `page_budget`, `blind_type`, `template_hint`, and `constraints[]` for `ieee-writing` and `ieee-template`. It can request `ieee-academic-search` when the venue card shows related-work depth as weak, and it can use `ieee-reader` outputs when comparing a user's manuscript against recent IEEE papers in the same venue family.
