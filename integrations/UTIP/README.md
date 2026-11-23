# UTIP v1.0 — Unified Tournament Intelligence Protocol

**What this is, in plain words:** a rulebook that lets three separate workers
cooperate without merging into one boss. It is **not** a new operating system,
not a Windows update, and not a format — nothing on your computer is wiped or
reinstalled. It is a set of agreements, plus a small connector, added as a new
folder in this repository. Delete this branch and everything is exactly as it
was before.

**Status: DRAFT branch only.** Created 2026-11-23 at Sayed's go (tournament
champion approval, ticket T-UTIP-04). No merge to main, no release tag, no
production change, no shadow run yet. The spec inside is a draft; the gates
below still have to pass before anything goes live.

## The three engines

| Engine | Job | It cannot |
|---|---|---|
| **TP — Tournament Controller** | Runs the tournament: challenges, rounds, matchups, who advances | Invent evidence, or waive a qualification rule |
| **TP1 — Intelligence Kernel** | Checks the work: research, evidence, qualification, QA | Crown itself the winner, or rewrite tournament rules |
| **Grand Prix — Competitive Engine** (called **UTIP-GP** in here) | Brings independent challengers and better alternatives | Override a mandatory TP1 rule, or grade its own work |

**Sayed** sits above all three. Spending, publishing, deletions and production
changes always need his explicit approval. No engine can change another
engine's record — disagreements are written down, not averaged away.

## How it works, step by step

1. **TP** opens a challenge and sets the rounds.
2. **Grand Prix** brings competing approaches to try to beat the current best.
3. **TP1** checks the evidence and decides if a candidate is actually
   qualified — a high score never fixes a failed rights check or missing proof.
4. If TP1 and Grand Prix disagree, the **disagreement engine** freezes that
   candidate, both sides show their evidence, an independent check runs, and
   a named person (**Chris**) rules with a written reason. Sayed is the final
   appeal. Each dispute gets at most **2 retests**, and only with genuinely
   new evidence.
5. **TP** records the winner and advances it — only after the checks pass.
6. Everything lands in a **shared ledger**: every submission has a permanent
   ID, every score shows its parts, every decision shows its evidence and
   its reason. Nothing is deleted; corrections are new entries.

Three scores are kept separate and never blended into one number: a
competitive score (how it did against alternatives), a qualification verdict
(does it meet the requirements), and a tournament result (did it win its
matchup). A clever but unqualified solution cannot win.

## How it runs on our systems

- **Daily, automatically, on the Muse machine:** the Space Archive Master
  Engine runs the Category Grand Prix every morning (~07:38 CT). That is
  where categories compete. UTIP does not replace that run.
- **On the Pitch (Sayed's laptop):** the JAX adapter is a small program that
  lets Jack's system talk to Local Jack. UTIP does not reinstall or change
  Windows to do that.
- **Here on GitHub:** this branch holds the spec and the contracts. The code
  that connects the engines comes later, in stages, behind a flag that is
  off by default.

## Rollout — 7 stages, with owner gates

1. Preservation — inventory the real repo (done, see below).
2. Specification — this draft.
3. **Branch — this branch. You are here.**
4. Three-engine connection.
5. Shadow tournament — same test cases through all three, no production
   effect, at least 3 clean cycles.
6. Controlled pilot — one limited tournament, original protocol as fallback.
7. Release — pull request, review, tag, gradual deploy.

Gates: G1 Chris reports · **G2 Sayed** · G3 Chris reports · G4 independent
review · **G5 Sayed** · **G6 Sayed**. No automatic progression through
Sayed's gates.

## Read this first — open flags

- **F-01 (CPS):** Cycle 1 of the Category Grand Prix scored 8 of 10 categories
  qualified under one reading of the formula, 0 under a literal reading.
  That call is still owed by Sayed. Until then UTIP qualifies nothing on CPS
  alone.
- **F-02 (v0.20):** Four canonical v0.20 files were not found in a
  workspace-wide search, and the v0.20 prep work lives only on a local
  branch, unmerged. **This branch is therefore based on the last published
  release, v0.1.5 (commit 6dd8094), not on the local v0.20 prep work** —
  deliberately, so uploading it does not silently publish unreviewed v0.20
  work. The spec pins v0.20 @ 98579c0 only provisionally.
- **F-03 (scoring):** There is no canonical scoring formula yet (S-01 HOLD).
  UTIP v1.0 ships with the bars only — Floor 70, Line 93 — and all composite
  scores are labelled PROPOSED, never decisive.
- **Seed:** the founding slate is **100 topics across 10 categories, all
  prospect-only** — not 100 categories, not qualified champions.

## Files in this branch

```
integrations/UTIP/
├── README.md                              (this file — the description)
├── UTIP_MASTER_SPEC.md                    (full spec draft)
├── ARCHITECTURE.md                        (components + trust boundaries)
├── ENGINE_ROLES.md                        (who does what, and the limits)
├── DATA_CONTRACTS.md                      (IF-01..IF-05 + compatibility)
├── SHARED_LEDGER.md                       (per-engine ledgers + reconciler)
├── DISAGREEMENT_ENGINE.md                 (procedure, caps, appeals)
├── OWNER_APPROVAL_GATE.md                 (G1–G6)
├── VERSION_COMPATIBILITY.md               (what this branch is based on)
└── TOURNAMENT_RECORD_T123_UTIP_001.md     (how the champion design was picked)
tests/UTIP/acceptance/ACCEPTANCE_TESTS.md   (the five demonstrations — NOT RUN yet)
```

Existing protocol files are untouched in this branch. Source handoff that
fed this spec: `UTIP_v1_0_Complete_Chris_Handoff.zip` (SHA-256
`8e18afa6…fb54`, 20 files, 19/19 hashes verified 2026-11-23) — a design
package, honestly labelled as such: its authors had not inspected this
repository, and it claims no code, tests, branch or deployment.
