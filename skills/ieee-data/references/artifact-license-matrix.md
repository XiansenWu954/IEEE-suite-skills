# Artifact License Matrix

This matrix is guidance for drafting IEEE availability statements, not legal advice. Confirm funder, institution, collaborator, and venue requirements before finalizing.

URL verification: All license URLs in this matrix were WebFetch-verified on 2026-05-27.

## License Source Links

| SPDX ID | Verified license URL | Typical artifact | Trade-off |
|---|---|---|---|
| MIT | https://spdx.org/licenses/MIT.html | Small research code and scripts | Simple and permissive; no explicit patent grant. |
| Apache-2.0 | https://spdx.org/licenses/Apache-2.0.html | Software libraries, reusable tools, model-serving code | Permissive with patent language; longer notice requirements. |
| BSD-3-Clause | https://spdx.org/licenses/BSD-3-Clause.html | Academic software and reference implementations | Permissive with endorsement restriction; no explicit patent grant. |
| CC-BY-4.0 | https://spdx.org/licenses/CC-BY-4.0.html and https://creativecommons.org/licenses/by/4.0/ | Open datasets, documentation, benchmark metadata | Allows broad reuse with attribution; users must preserve attribution. |
| CC0-1.0 | https://spdx.org/licenses/CC0-1.0.html and https://creativecommons.org/publicdomain/zero/1.0/ | Public-domain-style metadata or non-sensitive factual datasets | Maximizes reuse; attribution is not required by the waiver. |
| CC-BY-NC-4.0 | https://spdx.org/licenses/CC-BY-NC-4.0.html and https://creativecommons.org/licenses/by-nc/4.0/ | Data whose owners allow research reuse but not commercial reuse | Narrows reuse; confirm funder and venue acceptance before choosing. |

## Recommendation Matrix

| Artifact type | Use case | Recommended license path | Notes for statement |
|---|---|---|---|
| Code | Minimal scripts where commercial reuse is acceptable | MIT or BSD-3-Clause | Use a DOI-backed release and list dependencies. |
| Code | Reusable package where patent clarity matters | Apache-2.0 | Include notice file requirements in the repository. |
| Data | Open data where attribution should be required | CC-BY-4.0 | Pair with repository citation and DOI. |
| Data | Public metadata or facts where maximum reuse is desired | CC0-1.0 | Confirm authors are allowed to waive rights. |
| Data | Research-only reuse requested by data owner | CC-BY-NC-4.0 or restricted access | Explain reduced reuse and confirm policy acceptance. |
| Data | Human-subject, proprietary, or third-party restricted data | No open license without authorization | Use restricted statement with access pathway and approval terms. |
| Models | Weights intended for broad reuse | Match training-data and code constraints | Do not apply a license that conflicts with data or model-provider terms. |
| Documentation | Methods docs and metadata | CC-BY-4.0 | Use with attribution and DOI citation. |

## Persistent Host Rule

A personal cloud folder or personal repository without a DOI-backed release is not a persistent archival host for IEEE availability statements. Archive the final version in a DOI-capable repository and cite the DOI in the manuscript.
