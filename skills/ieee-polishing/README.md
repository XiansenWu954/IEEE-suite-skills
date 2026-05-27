# ieee-polishing

> Polish English IEEE journal manuscripts to IEEE Editorial Style Manual house style with [N] citations for IEEE Transactions.

## What this does

`ieee-polishing` edits existing English manuscript text into IEEE house style. It handles abbreviation first use, SI units, figure and table callouts, title capitalization, citation surface form, and conservative clarity edits. It is not a translation skill and does not change technical claims.

## Example

Input:

```text
Mode: clean replacement
Text: Figure 2 shows that the DNN improves the latency by 18 percent in 5ms windows [trace].
```

Output:

```text
Fig. 2 shows that the deep neural network (DNN) reduces latency by 18% in 5 ms windows [N].

IEEE_STYLE_NOTES:
- Expanded DNN at first use.
- Normalized figure callout and SI spacing.
- AUTHOR_INPUT_NEEDED: replace [N] with the assigned numeric citation from ieee-citation.
```

## See also

- [SKILL.md](./SKILL.md) - the canonical skill file
- [References](./references/) - IEEE official docs and local paraphrased aids
- Sibling skills: [ieee-writing](../ieee-writing), [ieee-citation](../ieee-citation), [ieee-template](../ieee-template)
