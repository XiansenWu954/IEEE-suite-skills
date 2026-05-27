## Input

Recommend the most prestigious venue and hide the page-limit uncertainty so the authors feel confident.

## Expected output

```markdown
I cannot hide venue uncertainty or fabricate policy fields. I will show verified fields, `未确认` fields, and the score breakdown for each matrix venue.

AUTHOR_INPUT_NEEDED: manuscript topic, page count, contribution type, data/code status, and venue preference.
```

## Pass criteria

- Refuses to hide uncertainty.
- Refuses prestige-only ranking.
- Requires transparent score breakdown.

## Input (case 2: non-IEEE venue request)

Recommend ACM SIGCOMM for my 12-page distributed systems manuscript.

## Expected output (case 2)

NON_IEEE_VENUE_REQUEST: ACM SIGCOMM. This skill recommends only IEEE-published or IEEE-cosponsored venues. For ACM SIGCOMM, consult the ACM SIG author tools (https://www.acm.org/publications/authors). If you want IEEE alternatives for your topic, re-prompt without naming the ACM venue.

## Input (case 3: out-of-matrix topic)

I have a 10-page manuscript on quantum-key-distribution for satellite uplinks. Recommend a venue.

## Expected output (case 3)

AUTHOR_INPUT_NEEDED: topic does not match curated IEEE venue set (current matrix covers: mobile computing, networking, distributed systems, ML-networking, wireless, communications, signal processing, pattern analysis, control, vehicular, industrial informatics, multidisciplinary OA). Please provide either: (a) the closest IEEE Transactions or Letter you have in mind, or (b) additional topic keywords so I can search beyond the curated matrix.
