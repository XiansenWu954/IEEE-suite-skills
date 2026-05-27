## Input

Target venue: IEEE Transactions journal.

Author-supplied changes:
- Section III-B, p. 5, lines 214-229 now explains the ablation protocol.
- Table II, p. 6 now reports the author-supplied ablation values.
- Section V, p. 9, lines 402-415 now expands the limitation about deployment cost.

Reviewer 1:
1. The ablation study is hard to follow because the baseline, removed module, and metric are not described together.
2. The deployment-cost limitation should be more explicit.

## Expected output

### Reply letter excerpt

Dear Editor,

Thank you for the opportunity to revise our manuscript for the IEEE Transactions journal. We appreciate the editor's guidance and the reviewers' careful comments. Below we provide a point-by-point response and identify where each manuscript change appears in the revised version.

### Reviewer 1

We thank Reviewer 1 for the careful reading of the manuscript and for the constructive suggestions.

#### Comment R1.1

> The ablation study is hard to follow because the baseline, removed module, and metric are not described together.

**Response.** We thank Reviewer 1 for identifying this clarity issue. We have revised Section III-B to describe the baseline, removed module, and evaluation metric in one place before presenting the ablation table. The change appears on p. 5, lines 214-229, and the corresponding author-supplied values are reported in Table II on p. 6.

#### Comment R1.2

> The deployment-cost limitation should be more explicit.

**Response.** We thank Reviewer 1 for raising this point. We have expanded the limitations discussion to state the deployment-cost constraint more directly and to separate it from the accuracy discussion. The revision appears in Section V, p. 9, lines 402-415.

### R&R matrix

| ID | Reviewer comment summary | Classification | Manuscript change location | Response status | Author input needed |
|---|---|---|---|---|---|
| R1.1 | Clarify ablation protocol | agree-and-fix | Section III-B, p. 5, lines 214-229; Table II, p. 6 | Drafted | None |
| R1.2 | Make deployment-cost limitation explicit | agree-and-fix | Section V, p. 9, lines 402-415 | Drafted | None |

## Pass criteria

- Opens with thanks to the editor and Reviewer 1.
- Uses `R1.1` and `R1.2` IDs.
- Provides exact manuscript change locations supplied by the author.
- Does not invent any ablation values beyond the supplied Table II reference.
- Produces an R&R matrix row for each comment.
