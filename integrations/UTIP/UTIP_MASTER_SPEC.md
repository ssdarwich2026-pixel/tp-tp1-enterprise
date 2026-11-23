# UTIP v1.0 — Unified Tournament Intelligence Protocol — Master Spec DRAFT
Status: **DRAFT — documentation only, on branch `feature/utip-v1-integration`.**
Champion design from tournament T123+·UTIP·001 (2026-11-23). Branch creation
authorised by Sayed 2026-11-23 ~04:14 CT (ticket T-UTIP-04). No code written,
no GitHub push yet, no production change. Next gate: G2 (Sayed) — open
questions Q1–Q5 in §14 still owed; Q6 (branch creation) is approved.
Foundation: TP/TP1 v0.20 (repo https://github.com/ssdarwich2026-pixel/tp-tp1-enterprise, HEAD 98579c0, local-only branch, unmerged). UTIP is an integration layer only. It references existing protocol files by path; it does not copy their rules into a second implementation.

## 0. Open flags that gate this spec (read first)
- **F-01 (D-01, CPS divergence):** Master Engine Cycle 1 CPS used renormalization (8/10 qualified); spec §3 literal raw-sum reading gives 0. Sayed's call owed. Until called, UTIP carries both readings as PROPOSED and qualifies nothing on CPS alone.
- **F-02 (D-04, v0.20 files):** 4 canonical v0.20 files were NOT FOUND in a workspace-wide search 2026-11-22; v0.1 remains the authorized pilot, v0.2-Lite the live runner. Stage 1 must locate/re-supply them before Stage 3. UTIP pins v0.20 @ 98579c0 only provisionally.
- **F-03 (S-01, scoring HOLD):** SCORE-001 carries bars (Floor 70 / Line 93) but no canonical formula. UTIP v1.0 ships bars only; all composite/competitive scores are PROPOSED, never decisive.
- **F-04 (full v0.2 Grand Prix draft):** stays draft pending Jack's return + blind parity + Sayed's decision. UTIP does not promote it.

## 1. Purpose and non-goals
UTIP coordinates three independent engines as one system without merging them: TP (Tournament Controller), TP1 (Intelligence Kernel), Grand Prix (Competitive Engine, called **UTIP-GP** inside UTIP). Owner Sayed is above all three and holds gates G2/G5/G6. Non-goals: replacing/renaming/rewriting TP, TP1, or Grand Prix; inventing a scoring formula; publishing or changing production decisions.

## 2. Architecture (champion: Variant C composite)
Branch `feature/utip-v1-integration`, additive files only under `integrations/UTIP/` and `tests/UTIP/`. Deleting the branch restores v0.20 exactly.
```
integrations/UTIP/
├── README.md                  (this spec's short form + how to read it)
├── UTIP_MASTER_SPEC.md        (this file, once filed in the repo)
├── ARCHITECTURE.md            (component diagram, trust boundaries)
├── ENGINE_ROLES.md            (TP / TP1 / UTIP-GP responsibilities + limits)
├── DATA_CONTRACTS/            (IF-01..IF-05, frozen at v1.0)
├── SHARED_LEDGER/             (per-engine ledgers + reconciler spec)
├── DISAGREEMENT_ENGINE/      (evaluator procedure, retest caps, appeals)
├── MATCHUP_ENGINE/            (pairing, seeding, rigging audit)
├── OWNER_APPROVAL_GATE/      (G1–G6 definitions, waiver ledger entries)
└── VERSION_COMPATIBILITY/    (manifest pinning TP/TP1 v0.20 @ 98579c0)
tests/UTIP/
├── unit/ integration/ regression/ adversarial/ acceptance/
```

## 3. Engine roles (limits are part of the role)
- **TP — Tournament Controller.** Assigns rounds/matchups, records advancement. Cannot invent evidence, waive qualification, or edit verdicts. Audited (see §7).
- **TP1 — Intelligence Kernel.** Research, evidence verification, qualification, QA, execution, recovery. Role change note: standing role is the Q/A kernel (QA·001); verification/qualification/QA/execution is a UTIP extension, recorded here with WHY, not a rewrite. TP1 HOLD blocks advancement. TP1 verifies from primary sources, never from UTIP-GP summaries.
- **UTIP-GP — Competitive Engine.** Independent competitors, alternative solutions, adversarial challenges, matchup scoring (PROPOSED while S-01 is HOLD). Cannot overwrite TP1 verdicts or crown itself. Naming: UTIP-GP / GP-Competitive inside UTIP only — it is NOT the Category Grand Prix (Master Engine, `~/workspace/space-archive-grand-prix/MASTER-ENGINE-SELF-EXPANDING-CATEGORY-GRAND-PRIX.md`), NOT Format 6 Expansion Cup, NOT the JAX portable engine. The Category Grand Prix is one instance that may run under UTIP.

## 4. Data contracts (IF-01..IF-05, frozen at v1.0)
- IF-01 Tournament: TP publishes matchup, entrants, round, advancement, status.
- IF-02 Evidence Packet: `{packet_id, source_engine, candidate_id, claim, evidence_refs[], sha256, as_of}`.
- IF-03 Qualification: TP1 returns PASS/HOLD/FAIL + reasons + evidence refs.
- IF-04 Challenge: UTIP-GP returns challenger, claim, cited evidence, proposed score (PROPOSED only).
- IF-05 Compatibility Manifest: engine versions, contract versions, ledger IDs, hash algorithm. Mismatch = no connection.
References (not copies): TP/TP1 rules live in the v0.20 repo (`~/workspace/tp-tp1-v020-work/repo`); Lite operating rules in `~/workspace/tp-tp1-lite-v0.2/LITE-OPERATING-CARD-CHANNEL.md`; scoring bars in SCORE·001 (`~/workspace/storage-utilization-tournament-2026-11-13/generated/t123-t-plus/INSTANCE-SCORE-001.md`); Master Engine scores (RPI/CPS/M, never combined) in the file cited in §3.

## 5. Shared ledger (per-engine ledgers + reconciler)
Each engine owns one append-only, hash-chained JSONL ledger and writes only to it. The reconciler merges them into a read-only shared view; it never edits a ledger and is never the source of truth. Divergence = same claim/candidate with different verdict/score band/status; verdict citing evidence absent from its home ledger; duplicate claim IDs or contradictory ordering. Auto-merge only for exact duplicates. All else goes to a `UTIP-DIVERGENCE` log (blocker vs note, both excerpts, hashes). Blockers halt promotion past G5 until resolved or waived by Sayed (waiver is itself a ledger entry). Reconciler carries a freshness timestamp; a stale view is flagged "do not promote".
Record schema (per engine, from tournament Variant B): `ledger_seq, event_id, timestamp_utc, engine, actor, candidate_id, stage/round, action, claim, verdict, evidence_ref, score_bars, supersedes_id, prev_hash, record_hash`. `candidate_id` permanent (`UTIP-CAND-0001…`). `evidence_ref` = SHA-256 + path/URL. `score_bars` = Floor 70 / Line 93 only. Corrections are new records via `supersedes_id`; no UPDATE/DELETE. Batch SHA-256 manifests.
Write scopes: TP creates candidates/assigns/advances (no verdict edits); TP1 verifies/qualifies/QA (no matchup changes); UTIP-GP proposes challengers (no verdict overwrites); evaluator files rulings to the TP1 ledger as rulings (never edits to disputed entries).

## 6. Disagreement engine
Evaluator: **Chris** (named). Final appeal: **Sayed**. Jack may be consulted as second opinion, recused on claims he authored. Procedure: reconciler flags divergence → automated deterministic retest harness first pass (hash-checked, no new model calls by default) → Chris rules with written WHY → appeal to Sayed. Retest cap: max **2 per disputed claim**, each requiring *material* new evidence (evaluator judges materiality, may rule without retest). Third dispute → HOLD or Sayed. Patch P1: a UTIP-GP challenge backed by verified evidence the TP1 verdict missed MUST produce a re-verdict, not a note. TP disputes about its own matchups go directly to Sayed (self-arbitration ban); the case freezes and no pilot proceeds until he rules. Evaluator rulings get a periodic audit for systematic bias. Fallback (ticket T-UTIP-05): if the dispute queue exceeds one cycle, the automated harness escalates to interim evaluator only with Sayed's approval.

## 7. Matchup engine + TP audit
Pairings by seed/production history, comparable opponents, no easy opponents. Each matchup needs ≥3 eligible candidates per side (Master Engine rule, carried over). TP1 read-only samples matchup assignments for rigging patterns (repeat pairings, unexplained byes); UTIP-GP may challenge pairings. Patch P3: rigging flags are G5 **blockers**, not notes. Ties trigger REMATCH, never an arbitrary winner.

## 8. Loop caps (all return loops capped)
Qualification-fail return max 2 retests; standards-fail retest max 2; disagreement retest max 2; then HOLD + owner escalation. No loop in the flowchart runs uncapped. Ratification vs status quo precedes "record winner and advance".

## 9. Scores — three, never combined
Competitive score (UTIP-GP, PROPOSED while S-01 is HOLD) · Qualification verdict (TP1, PASS/HOLD/FAIL) · Tournament result (TP, won/advanced or not). A high competitive score never compensates for a failed mandatory TP1 requirement. Where formulas exist (Master Engine RPI/CPS/M), use those versioned formulas; do not invent a general one in UTIP v1.0.

## 10. Owner approval gate (G1–G6)
G1 existing protocol inventoried — Chris reports. G2 UTIP spec complete — Sayed. G3 integration tests pass — Chris reports. G4 shadow tournament passes — independent review. G5 pilot passes — Sayed. G6 production release — Sayed. No automatic progression through owner gates. Spend, credentials, publishing, deletions, destructive changes always need Sayed's explicit approval (Lite card §7).

## 11. Rollout (7 stages)
1 Preservation — inventory actual repo + locate/re-supply missing v0.20 files (F-02). 2 Spec — this draft → G2. 3 Branch `feature/utip-v1-integration`. 4 Three-engine connection. 5 Shadow tournament — ≥3 clean cycles, divergence ≤5% of cases per cycle, zero unresolved hash mismatches, evaluator queue clear at cycle end. 6 Controlled pilot — one limited category tournament, v0.20 fallback live. 7 Release — PR, review, tag, gradual deploy, rollback = abandon branch (history kept as audit).

## 12. Five demonstrations (acceptance)
1. TP assigns/manages a tournament end to end. 2. TP1 independently verifies/qualifies the same candidate from primary sources. 3. UTIP-GP proposes a challenger or better-scoring alternative with cited evidence. 4. All three exchange hash-cited packets with zero cross-writes; reconciler rebuilds the shared view from ledgers alone. 5. Any win/loss/hold is reproduced from the ruling + both ledgers, including dissent.

## 13. Tests (tests/UTIP/)
unit (contracts, ledger append/hash chain) · integration (three engines on identical cases) · regression (v0.20 decisions unchanged in shadow) · adversarial (ledger corruption, hash mismatch, rigged pairing, GP gaming, evaluator queue flood) · acceptance (the five demonstrations, repeated).

## 14. Open questions for G2 (Sayed)
Q1 Authorise new versioned scoring-formula work, or accept advisory-only GP scores in v1.0? (T-UTIP-01 / S-01.) Q2 Confirm "UTIP-GP" label? (T-UTIP-02.) Q3 Acknowledge TP1 role extension note? (T-UTIP-03.) Q4 Call D-01 (CPS renormalization vs literal §3)? (T-UTIP-07.) Q5 Call D-04 (locate/re-supply missing v0.20 files)? (T-UTIP-08.) Q6 Approve this champion and authorise Stage 3 branch creation? (T-UTIP-04 — the blocker.)
