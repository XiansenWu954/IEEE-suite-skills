# Numeric Citation Compaction Rules

Source basis: IEEE Reference Guide, March 2025 revision, plus IEEEtran.bst behavior notes, paraphrased for this skill.

## Ordering

- Assign numbers by first appearance in the manuscript.
- Reuse the same number for repeated citations of the same source.
- Keep the reference list in numeric order, not alphabetical order.

## Compact Ranges

- If the target venue permits compact ranges, convert three or more consecutive citation numbers into a range such as `[1]–[5]`.
- Keep two consecutive citations explicit unless the author or venue requests range compaction.
- Do not compact nonconsecutive citations: use `[1], [3], [5]`.
- If the current venue guide requires every number to be written separately, follow the venue guide and add an `IEEE_STYLE_NOTES` entry.

## Mixed Groups

- Use ranges only for consecutive runs inside a larger group: `[1]–[3], [5], [8]–[10]`.
- Keep page or theorem locators attached to a single source, such as `[3, pp. 5-10]`.
- Do not merge separate references into one numbered item.

## Failure Cases

- Mark missing source metadata as `AUTHOR_INPUT_NEEDED`.
- Mark ambiguous duplicate sources as `AUTHOR_INPUT_NEEDED` until the author confirms whether they are identical.
