---
name: ieee-venue-selector
version: 0.1.1
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

This skill recommends an IEEE-aligned venue from a curated matrix of 12 journals and 8 conferences while making every constraint visible. This skill recommends only IEEE-published or IEEE-cosponsored venues; ACM/Springer/Elsevier/Nature requests are explicitly rejected. It anchors general venue discovery to the IEEE Author Center at https://journals.ieeeauthorcenter.ieee.org/ and venue-specific rows to the verified URLs in [references/journal-matrix.csv](references/journal-matrix.csv) and [references/conference-matrix.csv](references/conference-matrix.csv). The engineering constraint is transparent ranking: every recommendation must show hard filters, score components, and any `未确认` field rather than hiding uncertainty.

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

1. Intake topic, contribution type, page count, data/code status, preferred publication type, open-access preference, and timeline, and emit `AUTHOR_INPUT_NEEDED: manuscript topic, page count, contribution type, data/code status, and venue preference` if any decisive intake field is missing.
2. If the user explicitly names a non-IEEE venue (ACM SIGCOMM, MobiCom, Springer, Elsevier, Nature, etc.) as the target, emit `NON_IEEE_VENUE_REQUEST: <named venue>`, refer the user to that ecosystem's author tools, and stop further venue ranking for this request.
3. Load `references/journal-matrix.csv` and `references/conference-matrix.csv` before recommending any venue.
4. If the manuscript topic does not match any matrix row's `scope_keywords`, emit `AUTHOR_INPUT_NEEDED: topic does not match curated IEEE venue set; please provide additional keywords or describe contribution type`.
5. Filter out venues whose scope keywords do not match the manuscript topic or target community, and keep ACM-sponsored rows only as labeled non-IEEE comparisons when comparing ecosystems.
6. Apply hard constraints for page limit, abstract limit, blind type, submission system, supplementary policy, sponsor, fees, and `未确认` fields.
7. If a matrix row has a decision-critical `未确认` field, emit `AUTHOR_INPUT_NEEDED: <venue>.<field> not on official page; please check manually` and exclude that field from scoring instead of guessing.
8. Score each remaining IEEE or IEEE/CVF venue with topic fit 0-5, page-budget fit 0-3, evidence/reproducibility fit 0-2, audience fit 0-3, and submission-friction fit 0-2.
9. Penalize rows with decisive `未确认` fields and surface those fields in the venue card.
10. Return the top three venue cards with name, URL, sponsor, page limit, abstract limit, blind type, overlength fee, submission system, supplementary material policy, score breakdown, and rationale.
11. If no IEEE venue fits, state that no matrix venue fits and tell the user to seek venues outside this skill's scope.
12. Recommend follow-on skills: `ieee-writing` for page-budget drafting, `ieee-template` for IEEEtran conversion, and `ieee-academic-search` for related-work coverage.

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
4. TPDS CSDL journal page: https://www.computer.org/csdl/journal/td (see [references/TPDS.url.txt](references/TPDS.url.txt)).
5. TMLCN journal page: https://www.comsoc.org/publications/journals/ieee-tmlcn (see [references/TMLCN.url.txt](references/TMLCN.url.txt)).
6. TWC journal page: https://www.comsoc.org/publications/journals/ieee-twc (see [references/TWC.url.txt](references/TWC.url.txt)).
7. TCOM journal page: https://www.comsoc.org/publications/journals/ieee-tcom (see [references/TCOM.url.txt](references/TCOM.url.txt)).
8. TSP journal page: https://signalprocessingsociety.org/publications-resources/ieee-transactions-signal-processing (see [references/TSP.url.txt](references/TSP.url.txt)).
9. TPAMI CSDL journal page: https://www.computer.org/csdl/journal/tp (see [references/TPAMI.url.txt](references/TPAMI.url.txt)).
10. TAC journal page: https://www.ieeecss.org/publication/transactions-automatic-control (see [references/TAC.url.txt](references/TAC.url.txt)).
11. TVT journal page: https://vtsociety.org/publication/ieee-transactions-vehicular-technology (see [references/TVT.url.txt](references/TVT.url.txt)).
12. TII journal page: https://www.ieee-ies.org/pubs/transactions-on-industrial-informatics (see [references/TII.url.txt](references/TII.url.txt)).
13. IEEE Access: https://ieeeaccess.ieee.org/ (see [references/TAccess.url.txt](references/TAccess.url.txt)).
14. INFOCOM author CFP page: https://infocom2026.ieee-infocom.org/call-papers (see [references/INFOCOM.url.txt](references/INFOCOM.url.txt)).
15. GLOBECOM conference page: https://globecom2026.ieee-globecom.org/ (see [references/GLOBECOM.url.txt](references/GLOBECOM.url.txt)).
16. ICRA final paper instructions: https://2026.ieee-icra.org/contribute/final-paper-submission-instructions/ (see [references/ICRA.url.txt](references/ICRA.url.txt)).
17. Journal matrix: [references/journal-matrix.csv](references/journal-matrix.csv).
18. Conference matrix: [references/conference-matrix.csv](references/conference-matrix.csv).
19. Decision flowchart: [references/decision-flowchart.md](references/decision-flowchart.md).
20. Companion skills: [../ieee-writing](../ieee-writing), [../ieee-template](../ieee-template), [../ieee-academic-search](../ieee-academic-search).

> **Disclaimer**: IEEE venue policies change. Verify against the official Author Info page on submission day.

## Integration

`ieee-venue-selector` emits `target_venue`, `sponsor`, `page_budget`, `blind_type`, `template_hint`, and `constraints[]` for `ieee-writing` and `ieee-template`. It can request `ieee-academic-search` when the venue card shows related-work depth as weak, and it can use `ieee-reader` outputs when comparing a user's manuscript against recent IEEE papers in the same venue family.
