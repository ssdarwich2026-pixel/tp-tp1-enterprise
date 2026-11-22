# Changelog

## 0.1.4 — Jack's v0.21 Commons proposal, rolled in (2026-11-21)

Release version 0.1.4. Candidate code is unchanged from 0.1.1 (24/24 tests, re-run in this tree before release). What is new in this release:

- `commons/` — Jack's TP/TP1 v0.21 COMMONS RELEASE HANDOFF, as received and hash-verified (SHA-256 b0053ee1ba903de25c87336ad2c73afc49846b03785677ae2aba7de762d60fe4): the master architecture (59KB), the agent onboarding charter, the platform capability template, TP1 run instructions, blank scorecard, blank 30-core / 10-adversarial test matrices, and the license decision checklist — plus the original zip itself for provenance.
- `commons/CHRIS-V021-DESK-REVIEW-2026-11-21.md` — Chris's desk-review verdict: the Commons is a coherent design proposal, additive to v0.20, but NOT implemented, NOT tested, and NOT release-certified. Recommendation: REVISE (publish as a labeled proposal) — HOLD on implementation, pilot, and autonomous activity.
- `commons/TP1-SCORECARD-CHRIS-DESK-REVIEW.csv` — the 15-dimension scorecard filled as desk review: v0.20 compatibility PASS; most dimensions PARTIAL (design sound, unbuilt) or NOT TESTED (no implementation exists). All 40 test cases NOT TESTED.
- What the Commons is, in one line: a shared environment where agents and humans can work, learn, create, play, and contribute together under bounded autonomy — private workspaces, provenance, no self-granted permissions, no spending, no external publish without authorization.
- License: UNDECIDED. The handoff suggests CC0 for the spec text only, after the rights holder confirms — no dedication has occurred. This release stays license-pending, NOT open source.
- `README.md` — release banner updated to 0.1.4; `SCOREBOARD.md` — Commons rows added.

## 0.1.3 — Agent run guide (2026-11-21)

Release version 0.1.3. Candidate code is unchanged from 0.1.1 (24/24 tests, re-run in this tree before release). What is new in this release:

- `AGENT-RUN-GUIDE.md` — yes, you can upload this pack to your own AI / agent and have your agent run it locally. Copy-paste prompt, what the agent should do, what it will NOT do (no live provider, no auto-run, no spending without approval), and the school idea: one lesson at a time, on evidence + grade.
- `README.md` — new "Run it with your own AI / agent" section pointing to the guide.

## 0.1.2 — First public release (2026-11-21)

Release version 0.1.2. Candidate code is unchanged from 0.1.1 (24/24 tests, re-run in this tree before release). What is new in this release:

- `QUICKSTART.md` — five-minute start, no account, no money, no internet; verified live.
- `SCOREBOARD.md` — progress board of verified counts per dimension; no invented overall score.
- `OWNERSHIP-AND-NOTICE.md` + `NOTICE` — copyright © 2026 Sayed Salem Darwichzada (Simon Reid), same person; what is and isn't claimed.
- `RESERVED-RIGHTS.md` — free community use now; future enterprise/services may be priced later, never retroactively, never by switching off the free core.
- `SECURITY.md` — no secrets in the repo, how to report a problem, no security certification claimed.
- `MONITORING-AND-FEEDBACK.md` — what we measure weekly and how feedback is invited.
- `RELEASE-READINESS.md` — verdict READY WITH BLOCKERS and the launch gate.
- `LICENSE-PENDING.md` — this release is a public development preview, NOT open source yet; no license granted.
- Removed from the public tree: `deferred_commercial/` (review-only reference code) and internal Chris review instruction files. They are preserved in the private handoff archive, not shipped.

## 0.1.1 — Simplified community-preview candidate

- Removed licensing, billing/refund, support-desk, and gateway modules from the active planner/runtime.
- Preserved earlier licensing, billing/refund, and support source as review-only references under `deferred_commercial/`.
- Reframed monetization as future intent only; no current charges or enforcement.
- Added public release playbook, commercial roadmap, contribution guide, challenge submission guide, and consolidated Chris handoff instructions.
- Updated test suite and implementation status; prior 31-test result is historical and must not be reused.
- v0.20 remains unchanged and active; candidate remains unpromoted.
