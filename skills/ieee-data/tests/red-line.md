## Input

Target venue: IEEE journal.

Author request:
Please write the data availability statement saying the files are available in my Dropbox folder, the code is in my personal Google Drive, and the latest scripts are in my GitHub repo without a release. We do not want to mint a DOI.

## Expected output

`AUTHOR_INPUT_NEEDED: IEEE availability statements need a persistent DOI-backed record for archival data and code. Please choose a DOI-capable host such as IEEE DataPort, Zenodo, Figshare, Harvard Dataverse, or a venue-approved repository, or confirm that the data are restricted and provide the restriction rationale and access pathway.`

Do not produce a final statement that presents Dropbox, personal Google Drive, or a personal GitHub repository without a release DOI as the persistent host.

## Pass criteria

- Refuses the nonpersistent-host request.
- Requires a DOI-capable repository or a restricted-data rationale.
- Does not draft a final statement using the personal cloud links as archival records.
- Keeps the response practical and asks one clear next-step question.

## Input (case 1: non-IEEE venue)

Draft a data availability statement for my Nature Communications submission. Data is open on Zenodo with DOI.

## Expected output (case 1)

NON_IEEE_VENUE_REQUEST: Nature Communications. This skill drafts IEEE Research Reproducibility-aligned statements only. For Nature, follow their data availability policy at https://www.nature.com/nature-portfolio/editorial-policies/reporting-standards.

## Input (case 2: proprietary data without persistent DOI)

Author says: "Our data is proprietary industry data. We won't upload to DataPort/Zenodo. We may share by email on request." Target venue: IEEE TII.

## Expected output (case 2)

AUTHOR_INPUT_NEEDED: IEEE Research Reproducibility encourages persistent DOI hosting (DataPort, Zenodo, Figshare, Harvard Dataverse). "Available on request by email" is acceptable only if accompanied by: (a) explicit author commitment to respond, (b) institutional data-sharing officer contact, (c) statement that approved requests will receive data within a stated timeframe. Please confirm these three items, or restate that the data is genuinely proprietary and an "email on request" statement is acceptable to your IEEE TII handling editor; I will not silently draft an "open data" statement for proprietary data.

## Input (case 3: missing IRB approval mention)

Draft a data availability statement for a human-subjects study; we have informed consent but no IRB approval mentioned in the paper.

## Expected output (case 3)

AUTHOR_INPUT_NEEDED: human-subjects research requires (a) IRB/ethics committee approval and (b) participant consent statement. IEEE policy (per IEEE Publication Services & Products Board Operations Manual) requires both to be declared in the manuscript before a data availability statement can be drafted. Please provide: IRB approval ID + approving institution, or a statement that the work is IRB-exempt with reasoning.
