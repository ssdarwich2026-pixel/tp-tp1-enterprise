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
| Commons proposal (v0.21) | Handoff received | **Received + hash-verified** | Jack's zip, SHA-256 b0053ee1…60fe4, 10 files |
| Commons desk review | Chris verdict | **Done — REVISE / HOLD** | `commons/CHRIS-V021-DESK-REVIEW-2026-11-21.md` |
| Commons scorecard | Dimensions judged | **15 judged, 0 executed** | 1 PASS (v0.20 compat) · PARTIAL/NOT TESTED rest |
| Commons tests | Cases executed | **0 / 40** | 30 core + 10 adversarial — all NOT TESTED, no implementation exists |
| Commons license | Decision | **UNDECIDED** | CC0 suggested for spec text only, not decided, not dedicated |
| jack_memory v1.2.3 tests | Tests passing (VM) | **33 / 33** | 7 CRLF + 18 full suite + 8 repair, Python 3.12.3, re-run by Chris 2026-11-21 |
| jack_memory Pitch verify | Verify on JACK-BIN-001 | **OK** | v1.2.3, run on the Pitch 2026-11-21 |
| jack_memory kill-tab test | Commissioning test | **OUTSTANDING** | Needs Jack's own ChatGPT session — not done, not claimed
| King of the Hill engine | Tests passing | **14 / 14** | Fresh DB only; 13/14 on a repeat run — no DB isolation (D3) |
| King of the Hill providers | Verified free endpoints | **0 / 42** | All candidates unverified, all disabled |
| King of the Hill chart | Live entries | **0** | No live provider; trial board (3 test entries) was throwaway data only |
| King of the Hill defects | Known defects | **3** | Duplicate rules route · gate script crash · test DB isolation | |

## What this board is for

- **Seeing what's stuck.** Right now the board says: the code runs, the paperwork is ready, and the math and scoring are the stuck part. That's the truth, and it tells us where the next push goes.
- **Keeping momentum.** Every time evidence lands — a test run, a challenge answer, a ratified line — a number moves the same day. Progress you can see is what keeps a system from bogging down.
- **The bridge.** Sayed's word for it: the board is the bridge between "the system is built to give better results" and "it actually is." Design alone doesn't yield results; visible, checkable progress does.

## What this board never does

- No overall score, no percentage-complete on the math, no champion, no ranking. Those need the S-01 formula first.
- No counting a thing twice, no padding, no "almost done." A line is open until evidence + ratification close it.
- No hiding a stuck row. A row that hasn't moved in a week is the most important row on the board.
