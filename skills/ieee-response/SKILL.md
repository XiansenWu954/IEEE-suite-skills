---
name: ieee-response
version: 0.1.0
description: Draft IEEE journal single-blind peer review replies and R&R matrices for IEEE Transactions reviewer comments.
author: XiansenWu954
status: Stable
tags:
  - ieee
  - response
  - peer-review
license: MIT
---

## Purpose

This skill turns IEEE reviewer comments into a respectful point-by-point response letter and a Revision and Response traceability matrix. It enforces IEEE peer-review ethics and confidentiality expectations from the IEEE Submission and Peer Review Policies: <https://journals.ieeeauthorcenter.ieee.org/become-an-ieee-journal-author/publishing-ethics/guidelines-and-policies/submission-and-peer-review-policies/>. IEEE journal review is treated as single-blind by default: author identity is visible to reviewers, reviewer identity is anonymous to authors, and responses must never speculate about reviewer identity.

## When to use

- A user has raw IEEE journal, IEEE Transactions, or IEEE conference reviewer comments and needs a point-by-point reply.
- A revised manuscript already has page, section, line, figure, table, or appendix locations to cite in responses.
- The editor requested a resubmission package with a reply letter and a change matrix.
- Reviewer comments ask for experiments, citations, clarifications, or limitations that must be classified before drafting.

## Input contract

- Accepts reviewer comments copied from ScholarOne, IEEE author portal text, email, PDF review text, Markdown, or plain text.
- Requires the target IEEE venue or article type when available; if absent, use generic IEEE journal language and mark venue-specific policy checks as `AUTHOR_INPUT_NEEDED`.
- Requires author-provided change locations before claiming that a manuscript change was made.
- Accepts optional revised-manuscript excerpts, diff summaries, new result descriptions, new citations, and constraints on what the authors cannot provide.
- Treats missing experimental evidence, missing citations, or unavailable data as blocking facts that require `AUTHOR_INPUT_NEEDED`.

## Workflow

1. Confirm that the target is an IEEE journal, IEEE Transactions, or IEEE conference and stop with a venue-mismatch note if it is not.
2. Parse the editor and reviewer text into atomic comments and auto-assign IDs such as `R1.1`, `R1.2`, and `R2.1`.
3. Preserve the IEEE single-blind boundary by naming reviewers only as Reviewer 1, Reviewer 2, or Editor and never inferring identity.
4. Classify each comment as `agree-and-fix`, `partially-agree`, `respectfully-disagree`, or `clarification-needed`.
5. Draft every response with a respectful opening that starts from "We thank Reviewer N for ..." or an equivalent editor-facing phrase.
6. Attach a manuscript change location for each claimed fix, using page, section, line, figure, table, appendix, or supplemental-material identifiers supplied by the author.
7. Build respectfully-disagree responses from new evidence, clarified assumptions, or cited manuscript text instead of restating the old wording.
8. Emit `AUTHOR_INPUT_NEEDED: <clear question>` before drafting any response that would require unavailable results, unsupported citations, unverified statistics, or changes the author has not approved.
9. Produce a full Markdown reply letter, an R&R matrix, and a separate list of every `AUTHOR_INPUT_NEEDED` item.

## Output contract

- Produces a Markdown reply letter with editor greeting, reviewer-by-reviewer sections, comment IDs, quoted comment summaries, and response paragraphs.
- Produces an R&R matrix as a Markdown table or CSV with columns `ID`, `Reviewer comment summary`, `Classification`, `Manuscript change location`, `Response status`, and `Author input needed`.
- Produces a flagged-input section containing each `AUTHOR_INPUT_NEEDED` token and the exact question for the author.
- Done means every reviewer comment maps to exactly one matrix row and every factual claim is either grounded in supplied manuscript material or flagged for author input.

## Scope boundary

### ✓ In scope

- Drafting point-by-point IEEE reviewer replies with respectful, evidence-first language.
- Structuring R&R traceability matrices for IEEE resubmission packages.
- Classifying reviewer comments and identifying missing author facts.
- Rewriting defensive or vague replies into specific author-facing responses.

### ✗ Out of scope

- Deciding whether the manuscript should be accepted.
- Inventing new experiments, data, citations, reviewer identities, or editorial policy.
- Applying non-IEEE resubmission conventions unless the user explicitly changes venue.
- Editing the whole manuscript outside the locations needed for the reply package.

### 🚩 Red lines (NEVER do these)

- Never fabricate citations, statistics, figures, experiments, or experimental data.
- Never agree to changes that contradict the manuscript without flagging the conflict to the author.
- Never use sarcasm, condescension, or blame.
- Never disclose, infer, or speculate about reviewer identity in IEEE single-blind review.
- Never write that a result was added unless the author supplied the result and manuscript location.

## References

1. IEEE Submission and Peer Review Policies: https://journals.ieeeauthorcenter.ieee.org/become-an-ieee-journal-author/publishing-ethics/guidelines-and-policies/submission-and-peer-review-policies/ (verified 2026-05-27).
2. [SUB.url.txt](./references/SUB.url.txt) records the verification stamp for the IEEE peer-review policy source.
3. [rebuttal-templates.md](./references/rebuttal-templates.md) provides reusable point-by-point reply and R&R matrix scaffolds.
4. [tone-guide.md](./references/tone-guide.md) defines the IEEE single-blind tone and anonymity boundary.
5. [red-flags.md](./references/red-flags.md) lists phrases to avoid in reviewer responses.
6. Companion skills: [ieee-writing](../ieee-writing), [ieee-citation](../ieee-citation), and [ieee-data](../ieee-data).

> **Disclaimer**: IEEE policies (page limits, fees, formatting rules) change. Always verify against the official URL above on submission day.

## Integration

`ieee-writing` supplies the revised manuscript sections and line references that this skill cites in responses. `ieee-citation` supplies validated numeric `[N]` citations when a reviewer requests new prior work. `ieee-data` supplies data and code availability wording when reviewer comments request reproducibility artifacts, and this skill maps those changes into the reply letter and R&R matrix.
