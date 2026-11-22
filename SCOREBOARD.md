# TP/TP1 Scoreboard — progress you can check, not a number you have to trust

**Status:** live board, 2026-11-21. Sayed's call: a scoreboard keeps the system moving instead of bogged down. This board shows verified counts per dimension. It never shows a single overall score — there is no canonical scoring formula yet (challenge S-01, HOLD), and an invented score would be gamed and trusted as if it were real.

## The rule

A number on this board moves **only** when evidence lands (a test run, a filed artifact, a verified flip, a ratified ledger line). Nothing here is estimated, averaged, or guessed. If a row is empty, it means no evidence yet — not zero effort.

## The board (as of 2026-11-21, evening CT)

| Dimension | What we count | Now | Evidence |
|---|---|---|---|
| Candidate build tests | Tests passing | **24 / 24** | Re-run live 2026-11-21, Python 3.12.3, 0.08s |
| Foundation tests | Tests passing | **10 / 10** | Re-run 2026-11-21 |
| Math challenges (M) | Lines closed | **0 / 6** | Ledger, all OPEN |
| Novel-theorem challenges (N) | Lines closed | **0 / 6** | Ledger, all OPEN |
| Scoring / Grand Prix (S) | Lines closed | **0 / 4** | Ledger, all OPEN — S-01 formula still missing |
| Build / evidence (B) | Lines closed | **0 / 5** | Ledger, all OPEN — B-01 v0.20 map not done |
| Credit (A) | Lines closed | **0 / 4** | Ledger, all OPEN |
| Release readiness | Verdict | **READY WITH BLOCKERS** | `RELEASE-READINESS.md` |
| Release blockers | Blockers open | **6** | License draft · owner confirmation · GitHub destination · contact inbox · secrets sweep · B-01 map |
| Pack | Shipped artifacts | **Pack 0.1, 78K, 49 files** | Distribution zip, hashes in `SHA256SUMS.txt` |
| Instructions | Quick start | **Written + verified** | `QUICKSTART.md`, run live 2026-11-21 |

## What this board is for

- **Seeing what's stuck.** Right now the board says: the code runs, the paperwork is ready, and the math and scoring are the stuck part. That's the truth, and it tells us where the next push goes.
- **Keeping momentum.** Every time evidence lands — a test run, a challenge answer, a ratified line — a number moves the same day. Progress you can see is what keeps a system from bogging down.
- **The bridge.** Sayed's word for it: the board is the bridge between "the system is built to give better results" and "it actually is." Design alone doesn't yield results; visible, checkable progress does.

## What this board never does

- No overall score, no percentage-complete on the math, no champion, no ranking. Those need the S-01 formula first.
- No counting a thing twice, no padding, no "almost done." A line is open until evidence + ratification close it.
- No hiding a stuck row. A row that hasn't moved in a week is the most important row on the board.
