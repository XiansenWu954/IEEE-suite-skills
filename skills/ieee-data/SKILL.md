---
name: ieee-data
version: 0.1.0
description: Draft IEEE Research Reproducibility data/code availability statements with DOI hosting for IEEE journal submissions.
author: XiansenWu954
status: Stable
tags:
  - ieee
  - data
  - reproducibility
license: MIT
---

## Purpose

This skill drafts IEEE Research Reproducibility-aligned data and code availability statements with persistent repository hosting. It follows the IEEE Research Reproducibility guidance at https://journals.ieeeauthorcenter.ieee.org/create-your-ieee-journal-article/research-reproducibility/, which encourages authors to share data, code, methods, and research outputs as openly as possible. It enforces a persistent DOI requirement and prevents personal cloud links from becoming the archival source for IEEE submissions.

## When to use

- A user needs a data availability or code availability statement for an IEEE journal, IEEE Transactions, or IEEE conference manuscript.
- A reviewer, editor, or venue asks for reproducibility artifacts, dataset links, or code links.
- Authors need to choose among IEEE DataPort, Zenodo, Figshare, or Harvard Dataverse for DOI-based hosting.
- Authors need license recommendations for code, data, models, documentation, or mixed artifacts.

## Input contract

- Accepts descriptions of datasets, code, trained models, documentation, protocols, and supplementary reproducibility artifacts.
- Requires current public/private status for each artifact and any legal, IRB, consent, export-control, proprietary, embargo, or data-use-agreement restrictions.
- Requires target IEEE venue when known and article section target when known, such as Methods, Acknowledgments, appendix, or supplementary material.
- Accepts existing repository links only if they are persistent records with a DOI or an approved plan to mint one before submission.
- Treats unknown restrictions, missing DOI, missing license, or unclear data ownership as `AUTHOR_INPUT_NEEDED` rather than guessing.

## Workflow

1. Confirm that the target is an IEEE journal, IEEE Transactions, or IEEE conference and stop with a venue-mismatch note if it is not.
2. Inventory every data, code, model, documentation, and protocol artifact needed to verify or reproduce the work.
3. Classify each artifact as open, restricted, embargoed, proprietary, third-party, not generated, or not applicable.
4. Select a DOI-capable host from IEEE DataPort, Zenodo, Figshare, Harvard Dataverse, or a venue-approved repository based on artifact size, access controls, community fit, and submission integration.
5. Reject Dropbox, personal Google Drive, and personal GitHub repositories without a DOI-backed release as final persistent hosts.
6. Recommend artifact licenses by separating code licenses from data licenses and naming trade-offs for reuse, attribution, patent terms, commercial use, and restriction policy.
7. Draft a data availability statement that names the repository, DOI status, access terms, restriction rationale, and any required approval pathway.
8. Draft a separate code availability statement that names the repository, release or DOI, license, dependency notes, and execution scope.
9. Emit `AUTHOR_INPUT_NEEDED: <clear question>` for any missing DOI, license choice, repository decision, or restriction detail needed before submission.

## Output contract

- Produces a hosting decision rationale comparing DOI-capable repositories and rejecting nonpersistent personal storage.
- Produces a license recommendation table for code, data, models, and documentation with verified license URLs.
- Produces data availability and code availability statements ready to paste into the manuscript section specified by the user.
- Produces one of four boilerplate variants from [data-availability-statement-templates.md](./references/data-availability-statement-templates.md): open code plus open data, restricted data, no data, or hybrid.
- Done means every artifact has a status, host decision, DOI plan, license recommendation or restriction note, and no unsupported availability claim.

## Scope boundary

### ✓ In scope

- Drafting IEEE Research Reproducibility-aligned data and code availability statements.
- Selecting DOI-capable repositories such as IEEE DataPort, Zenodo, Figshare, and Harvard Dataverse.
- Recommending open-source and open-data licenses with trade-offs and verified license URLs.
- Flagging missing DOI, license, access, ownership, or restriction facts for author input.

### ✗ Out of scope

- Giving legal advice or overriding institutional, IRB, consent, export-control, or proprietary restrictions.
- Uploading datasets, minting DOIs, or accepting repository terms on behalf of authors.
- Claiming data or code are public before the author supplies a DOI-capable public record or release plan.
- Replacing venue-specific data policy checks when a journal has stricter instructions.

### 🚩 Red lines (NEVER do these)

- Never recommend Dropbox, personal Google Drive, or personal GitHub without a DOI-backed release as a persistent host.
- Never fabricate dataset identifiers, DOIs, access dates, licenses, statistics, citations, or experimental data.
- Never override the author's stated restriction policy; if data are proprietary, use the restricted-data statement path.
- Never make a license recommendation without naming trade-offs and linking the verified license source.
- Never imply that restricted human-subject, proprietary, or third-party data can be opened without authorization.

## References

1. IEEE Research Reproducibility: https://journals.ieeeauthorcenter.ieee.org/create-your-ieee-journal-article/research-reproducibility/ (verified 2026-05-27).
2. IEEE DataPort public landing page: https://info.ieee-dataport.org/home (verified 2026-05-27).
3. Zenodo: https://zenodo.org/ (verified 2026-05-27).
4. Figshare: https://figshare.com/ (verified 2026-05-27).
5. Harvard Dataverse information page: https://library.harvard.edu/services-tools/harvard-dataverse (verified 2026-05-27).
6. [REP.url.txt](./references/REP.url.txt), [dataport.url.txt](./references/dataport.url.txt), [zenodo.url.txt](./references/zenodo.url.txt), [figshare.url.txt](./references/figshare.url.txt), and [dataverse.url.txt](./references/dataverse.url.txt) record verification stamps.
7. [data-availability-statement-templates.md](./references/data-availability-statement-templates.md) provides the four boilerplate statement variants.
8. [artifact-license-matrix.md](./references/artifact-license-matrix.md) maps artifacts and use cases to license recommendations.
9. Companion skills: [ieee-writing](../ieee-writing), [ieee-template](../ieee-template), and [ieee-response](../ieee-response).

> **Disclaimer**: IEEE policies (page limits, fees, formatting rules) change. Always verify against the official URL above on submission day.

## Integration

`ieee-writing` receives the final data and code availability statements for insertion into Methods, Acknowledgments, appendix, or supplementary material. `ieee-template` converts the accepted statement into IEEEtran LaTeX and preserves DOI text in the final manuscript. `ieee-response` uses this skill's DOI, access, and license decisions when reviewers ask for reproducibility artifacts during revision.
