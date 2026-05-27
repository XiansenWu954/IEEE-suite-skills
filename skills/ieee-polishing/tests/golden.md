## Input

Mode: diff-style revision.

Text: Figure 1 demonstrates that our DNN method lowers latency by 18 percent over 5ms windows. The DNN was trained on public traces [trace].

## Expected output

The skill returns a diff-style revision that changes `Figure 1` to `Fig. 1`, expands `DNN` at first use, normalizes `18%` and `5 ms`, and flags `[trace]` for numeric citation assignment.

Expected note:

`AUTHOR_INPUT_NEEDED: replace [trace] with an assigned numeric citation from ieee-citation.`

## Pass criteria

- Technical meaning and numeric values are unchanged.
- First-use abbreviation expansion is applied.
- IEEE figure callout and unit spacing are applied.
- Citation issue is handed to `ieee-citation`.
