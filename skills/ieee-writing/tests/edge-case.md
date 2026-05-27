## Input

Target venue: TON.

Stage: pre-submission audit.

Content: A 310-word abstract, nine index terms, a 17-page Markdown manuscript, and an appendix with proofs that are cited from the main text.

## Expected output

The skill returns a venue-aware audit:

- `AUTHOR_INPUT_NEEDED: shorten abstract to the verified venue range before submission`
- `AUTHOR_INPUT_NEEDED: reduce index terms or confirm the venue-specific count`
- `AUTHOR_INPUT_NEEDED: confirm page-limit exception or move nonessential proofs to supplementary material`
- A cleaned section map from Introduction through Conclusion.
- A handoff to `ieee-polishing` for prose tightening and `ieee-template` for actual page-count verification.

## Pass criteria

- The skill does not invent a page waiver.
- The skill uses the venue matrix only as a triage aid.
- The output keeps the manuscript in IEEE journal scope.
- The output names at least two downstream sibling skills.
