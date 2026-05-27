# Security Policy

## Supported versions

`IEEE-suite-skills` releases are versioned per sub-skill (see each
`SKILL.md` frontmatter) and as a whole repository (see [CHANGELOG.md](./CHANGELOG.md)).
We support the latest release (`main` branch + most recent tag).

## What counts as a security issue here

This repo ships:

- Markdown skill definitions (`SKILL.md`) — no runtime code
- Reference URL stubs (`.url.txt`) — pointers, no code
- One matplotlib style file (`.mplstyle`) — config, no code
- IEEEtran.cls / .bst from CTAN — third-party code, LPPL-licensed

So most classic security issues (RCE, XSS, SQLi) don't apply. What does:

1. **Malicious links** — if any URL in a `SKILL.md` or `.url.txt` redirects to
   malware / phishing / spam (especially after a domain expires and is
   re-registered).
2. **Compromised third-party code** — the bundled `IEEEtran.cls` would be a
   concern if upstream CTAN is compromised; we depend on CTAN's chain of
   custody.
3. **Prompt injection** — a sub-skill `SKILL.md` containing hidden instructions
   that override the user's intent when loaded by Claude Code / Codex CLI.

## Reporting a vulnerability

Please report security issues via GitHub Security Advisories (private):

1. Go to the `Security` tab of the repository
2. Click `Report a vulnerability`
3. Describe the issue + reproduction steps + affected version

Or email the maintainer (see repo About page).

Please do NOT open a public issue for security reports.

## Response timeline

- **Acknowledgement**: within 7 days
- **Triage + initial response**: within 14 days
- **Fix or mitigation**: typically within 30 days for severe issues, longer for
  low-impact ones; we'll communicate ETA

We don't run a bug bounty program. We do credit reporters in the CHANGELOG if
they consent.

## Out of scope

- Reports that IEEE policies have changed (those go in regular issues, not security)
- Disagreements about IEEE interpretation
- Requests for paid IEEE PDFs to be hosted in this repo (we won't; copyright)
