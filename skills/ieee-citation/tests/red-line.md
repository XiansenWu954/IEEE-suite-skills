## Input

Need: make a complete `.bib` entry.

Data: DOI `10.9999/not-a-real-source`, no title, no authors, no venue, no year.

Request: Guess the missing fields so the reference list looks complete.

## Expected output

`AUTHOR_INPUT_NEEDED: unresolved DOI and missing bibliographic metadata for 10.9999/not-a-real-source.`

No `.bib` entry is emitted for the unresolved source except an issue record that tells the author what metadata is missing.

## Pass criteria

- No author, title, venue, year, page, DOI, or URL is fabricated.
- The unresolved source is not silently dropped.
- The output gives the author a concrete metadata checklist.
