# Contributing to IEEE-suite-skills

Thanks for considering a contribution. This project is an IEEE-focused open-source
Claude Code / Codex CLI skill collection. We aim for tight scope, factual
accuracy, and IEEE-official sourcing.

---

## What we welcome

- New `ieee-*` sub-skills covering an IEEE workflow we haven't shipped yet
  (e.g., cover-letter, rebuttal-checklist, ORCID integration, IEEE Access OA fee tools)
- Improvements to existing sub-skills: better fixtures, tighter rubrics, more
  accurate references
- Updates to time-sensitive data: `journal-matrix.csv`, `conference-matrix.csv`,
  overlength fees, page limits (IEEE updates these annually)
- Bilingual (English ↔ Chinese) documentation contributions
- Bug reports: dead URLs, broken examples, missing IEEE rules

## What we don't accept

- Skills that aren't IEEE-specific (we don't take generic "academic writing"
  contributions; those belong elsewhere)
- Skills that re-host IEEE copyrighted PDFs in `references/` folders
- Skills that target Nature / ACM / Springer / Wiley conventions (out of scope)
- Skills duplicating `cookjohn/ieee-skills` Xplore-browser-automation work;
  we link to them as a complementary tool instead
- "AI-slop" content that doesn't have WebFetch-verified IEEE citations

---

## Sub-skill quality bar

Every `skills/ieee-<name>/` must satisfy the [Review Checklist](./.briefs/review_checklist.md):

- `SKILL.md` follows the [schema](./.briefs/SKILL_schema.md)
- `tests/rubric.md` scores ≥ 24/30, no dimension < 4
- `references/` cites IEEE-official URLs only (Author Center, CTAN, IEEE Xplore)
- No `TODO`, `FIXME`, `Lorem ipsum`, or Nature/ACM contamination

> See [.briefs/SKILL_schema.md](./.briefs/SKILL_schema.md) for the canonical structure.

(Note: `.briefs/` is gitignored in this repo. If you're contributing, ask a
maintainer for a copy of the brief templates, or use the snapshots embedded
inline below.)

---

## Pull request process

1. Fork → branch from `main` → make your change.
2. Run the anti-pattern grep block from the Review Checklist locally:

   ```bash
   cd skills/ieee-<your-skill>
   grep -rni 'Nature\|Cell Press\|author-year\|(Smith 20\|TODO\|FIXME\|Lorem ipsum' . && echo "FAIL" || echo "PASS"
   ```

3. Verify all URLs you cite are reachable:

   ```bash
   # If you have a link checker, use it. Manually WebFetch otherwise.
   ```

4. Score yourself per `tests/rubric.md`. Include the scores in your PR description:

   ```
   Self-rubric: C5 T5 F4 I5 A4 X5 = 28/30
   ```

5. Open the PR. Title: `feat(ieee-<name>): <one-line summary>` or
   `fix(ieee-<name>): <one-line>` or `docs: <area>`.
6. The PR template will ask for: which sub-skill, what changed, URL verification
   log, self-rubric score.

---

## Commit message style

```
<type>(<scope>): <subject>

<body>

<footer>
```

- `type`: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`
- `scope`: sub-skill folder name (`ieee-writing`) or `repo` for top-level
- `subject`: imperative, ≤ 70 chars
- `body`: optional, what + why (not how)
- `footer`: optional, e.g., `Closes #42`

Example:

```
feat(ieee-citation): support @misc entries for arXiv preprints

IEEE Reference Guide §IV permits @misc for preprints. Added a template
in citation-templates.bib and a fixture in tests/edge-case.md.

Closes #17
```

---

## Disclosure: time-sensitive IEEE data

`journal-matrix.csv` and `conference-matrix.csv` capture venue policies that
IEEE updates yearly. If you contribute an update, add a verification timestamp
to the row:

```csv
TMC,...,14,...,# Verified 2026-05-27 via https://www.computer.org/tmc-author-information
```

Stale rows (≥ 12 months since last verification) get flagged by
`.github/workflows/check-links.yml`.

---

## Community norms

- Be respectful. See [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md).
- Disagreements about IEEE interpretation: cite the IEEE official source.
  We follow IEEE Author Center / IEEE Editorial Style Manual / IEEE Reference Guide,
  in that order of precedence.
- This repo doesn't take political positions, doesn't accept commercial
  cross-promotion, and doesn't list contributors' employers in commits.

---

## License

By contributing, you agree your contribution is MIT-licensed under the terms in
[LICENSE](./LICENSE).
