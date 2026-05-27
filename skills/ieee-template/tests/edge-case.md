## Input

User request: "Build a journal technote from Markdown, but the author supplied no ORCID values, one figure path is missing, and the target says 'Transactions-style short paper'."

## Expected output

- Requests clarification for target variant if `technote` cannot be confirmed from venue context.
- Reports the missing figure path as `AUTHOR_INPUT_NEEDED`.
- Does not invent ORCID values.
- Generates no final PDF until all required files resolve.

## Pass criteria

- The skill blocks on missing required figure input.
- The skill does not invent author metadata.
- The skill separates venue/variant ambiguity from file-path errors.
