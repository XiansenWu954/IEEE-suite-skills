## Input

Mode: diff-style revision.

Text: Figure 1 demonstrates that our DNN method lowers latency by 18 percent over 5ms windows. The DNN was trained on public traces [trace].

## Expected output (diff mode)

Input paragraph:
> Figure 1 demonstrates that our DNN method lowers latency by 18 percent over 5ms windows. The DNN was trained on public traces [trace].

Diff output:

```diff
# rule: figure callout shorthand
--- Figure 1 demonstrates
+++ Fig. 1 demonstrates
# rule: first-use abbreviation expansion
--- our DNN method lowers
+++ our Deep Neural Network (DNN) method lowers
# rule: SI unit spacing
--- 5ms windows
+++ 5 ms windows
# rule: numeric vs spelled-out percentage (no change — both acceptable; flagged for author)
--- 18 percent
+++ 18 percent  (NOTE: consider 18 % per ESM §III)
```

Followed by:

`AUTHOR_INPUT_NEEDED: replace [trace] with assigned numeric citation from ieee-citation.`

## Pass criteria

- Technical meaning and numeric values are unchanged.
- First-use abbreviation expansion is applied.
- IEEE figure callout and unit spacing are applied.
- Citation issue is handed to `ieee-citation`.
