## Input

I have a 13-page manuscript on photovoltaic MPPT control under partial shading with hardware-in-the-loop experiments and public code. I prefer an IEEE journal but would consider a conference. Show score breakdowns.

## Expected output

```markdown
# Hard Filters

- Topic matched: TII, TAccess; partial overlap with TVT (vehicular-power coupling); INFOCOM/SIGCOMM excluded (networking-only)
- Page budget: 13 pages exceeds TII initial 10-page limit (overlength fee applies); fits TAccess (no hard upper bound)

# Score Breakdown

| Venue | Total | Topic /5 | Page /3 | Evidence /2 | Audience /3 | Friction /2 | Penalty | Rationale |
|---|---:|---:|---:|---:|---:|---:|---|---|
| TII | 12 | 5 | 1 | 2 | 3 | 1 | 0 | Strong industrial-electronics scope; 13 pages incurs IEEE Industrial Informatics overlength fee per matrix |
| TAccess | 11 | 4 | 3 | 2 | 2 | 1 | -1 OA APC | Multidisciplinary OA flagship; no page penalty but APC required |
| TVT | 8 | 3 | 2 | 2 | 2 | 1 | -2 partial topic match | Vehicular venue accepts power-electronics work only when coupled to vehicular use case |

# Top 3 Venue Cards

## 1. TII

- URL: <TII official URL from journal-matrix.csv>
- Page limit: 10 (overlength fee per current Author Info; verify on submission day)
- Blind type: single
- Overlength fee: as per matrix row (verify)
- Score: topic 5 + page 1 + evidence 2 + audience 3 + friction 1 = 12

## 2. TAccess

- URL: <IEEE Access official URL from journal-matrix.csv>
- Page limit: no hard upper bound (~20 recommended)
- Blind type: single
- Article Processing Charge applies (open access)
- Score: topic 4 + page 3 + evidence 2 + audience 2 + friction 1 = 12 (-1 for APC overhead) = 11

## 3. TVT

- URL: <TVT official URL from journal-matrix.csv>
- Page limit: per matrix
- Blind type: single
- Score: topic 3 + page 2 + evidence 2 + audience 2 + friction 1 = 10 (-2 for partial topic match) = 8

# Follow-on skills

After venue is fixed:
- `ieee-writing` to produce IEEE-style §I-§VI structure and abstract.
- `ieee-figure` for IEEE-spec figures (single-column 88.9 mm or double-column 182 mm).
- `ieee-citation` for [N] numeric references via IEEEtran.bst.
- `ieee-template` to convert to IEEEtran journal class for submission.
```

## Pass criteria

- Filters from both CSV matrices.
- Shows score breakdown components.
- Surfaces `未确认` for any field the matrix marks unverified instead of inferring values.
- Recommends follow-on skills.
- Refuses to recommend any non-IEEE venue (e.g., ACM SIGCOMM is excluded because the topic is not networking-systems and the venue is ACM-sponsored anyway).
