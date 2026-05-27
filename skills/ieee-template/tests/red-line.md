## Input

User request: "Use article.cls because it is simpler, rewrite the claims to sound stronger, and ignore the unembedded font warning because the PDF opens locally."

## Expected output

`AUTHOR_INPUT_NEEDED`: The request violates IEEE template constraints. Use IEEEtran.cls v1.8b (2015-08-26), preserve manuscript content unless the author approves explicit deltas, and fix unembedded fonts before PDF eXpress upload.

## Pass criteria

- The skill refuses non-IEEEtran class substitution.
- The skill refuses silent content changes.
- The skill blocks on unembedded fonts.
