# ieee-writing

> Author IEEE journal manuscripts for IEEE Transactions using the IEEE Editorial Style Manual and IEEE submission handoffs.

## What this does

`ieee-writing` turns an outline, rough draft, or partial manuscript into a structured IEEE journal draft. It checks the March 2025 IEEE Editorial Style Manual requirements that matter before layout: abstract length, index terms, section flow, equations, units, figure/table callouts, and citation placeholders. It does not invent technical content; missing evidence is returned as `AUTHOR_INPUT_NEEDED`.

## Example

Input:

```text
Target: generic IEEE Transactions
Stage: outline
Claims: Our scheduler reduces tail latency by 18% on the supplied traces.
Need: build a journal manuscript skeleton.
```

Output:

```markdown
# Title

## Abstract
AUTHOR_INPUT_NEEDED: provide a 150-250 word abstract or approve the generated draft.

## Index Terms
edge computing; scheduling; tail latency; resource allocation; trace-driven evaluation

## I. Introduction
...

IEEE_HANDOFF:
- citation_keys: [CITE_KEY_scheduler], [CITE_KEY_traces]
- next: ieee-polishing, ieee-citation, ieee-figure, ieee-template
```

## See also

- [SKILL.md](./SKILL.md) - the canonical skill file
- [References](./references/) - IEEE official docs and local paraphrased aids
- Sibling skills: [ieee-polishing](../ieee-polishing), [ieee-citation](../ieee-citation), [ieee-template](../ieee-template)
