# site-generator-speed

[![make.fun · site-generator-speed-01-run-20261122](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/maharani212/site-generator-speed/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/maharani212/site-generator-speed/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122?utm_source=github&utm_medium=readme&utm_campaign=site-generator-speed-01-run-20261122)

A faster drop-in for make.fun's makefun-site 1.0.0, written from its README
specification and reference behaviour. It answers byte-identically to
makefun-site on every input.

Run: `node main.ts` (Node 22). It reads every case from `/input/cases.json`
and writes `/output/answers.json`, one answer per case in order.
`MAKEFUN_INPUT_DIR` / `MAKEFUN_OUTPUT_DIR` override the paths.

Speed comes from: a manual-loop HTML escaper (no regex callback), an
ASCII fast path plus a per-build cache for slugs, index-based front-matter
parsing (no full-body split), a Markdown inline renderer that escapes plain
runs in bulk, first-character dispatch in the block lexer, a manual word
count, and a template renderer that reuses scope objects and the root scope
across renders.

Practice set: 3/3 cases byte-identical to the reference; ~1.6x faster than
the house baseline (trimmed mean CPU ~0.83s vs ~1.30s on this machine).
