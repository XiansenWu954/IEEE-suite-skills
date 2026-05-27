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
