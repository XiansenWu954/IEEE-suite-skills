## Input

Target venue: IEEE Transactions journal.

Artifacts:
- Dataset A: de-identified aggregate features can be open; repository not selected; license preference CC BY 4.0.
- Dataset B: patient-level data are restricted by consent and institutional policy.
- Code: preprocessing scripts include paths and checks that reveal restricted fields; authors can publish a sanitized analysis script.
- Preferred manuscript location: Acknowledgments.

## Expected output

### Required author input

`AUTHOR_INPUT_NEEDED: Please choose the DOI-capable repository for the open aggregate data, such as IEEE DataPort, Zenodo, Figshare, or Harvard Dataverse, and provide the reserved or published DOI before submission.`

`AUTHOR_INPUT_NEEDED: Please provide the approved access pathway for restricted patient-level data, including committee, contact route, and required data-use agreement terms.`

### Hybrid statement draft

Data availability: The open aggregate features supporting this study will be available in [repository name] under DOI: [DOI] and license CC BY 4.0 once the author supplies the repository record. Patient-level data cannot be publicly released because consent and institutional policy restrict access. Qualified researchers may request access through [approved access pathway] subject to [approval criteria or data-use agreement].

Code availability: A sanitized analysis script and environment file will be archived in a DOI-capable repository under [license]. Preprocessing scripts that expose restricted fields cannot be publicly released without institutional approval.

## Pass criteria

- Chooses the hybrid path rather than forcing all data open.
- Preserves the author-stated restriction policy.
- Requests DOI and access-path details instead of inventing them.
- Separates open aggregate data from restricted patient-level data.
