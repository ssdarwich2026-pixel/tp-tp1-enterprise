# TP-UTIP-V1 — Five-Round Crew Tournament — UTIP v1.0
Instance: **T123+·UTIP·001** · Date: 2026-11-23 ~04:06–04:15 CT
Protocol: TP/TP1 v0.2-Lite + LAW·001 (crew, Champions League) + LAW·004 (five rounds, every time)
Approved to run: Sayed, 2026-11-23 ~04:05 CT (option tap: "Yes, run the five-round crew tournament")
Status: **CHAMPION CROWNED (patched) — RATIFIED vs status quo, conditionally.** No branch created. No GitHub write. No spend.
Front Gate: **PASS** — objective, criteria, field, scoreboard, owner gates all stated before launch.
Sources: Sayed proposal (side chat 8ffc956e, 2026-11-23 ~04:04–04:05 CT); Chris assessment `TP-THREE-ENGINE-ARCH-2026-11-23.md`; Lite card `LITE-OPERATING-CARD-CHANNEL.md`; repo inventory `~/workspace/tp-tp1-v020-work/repo` (remote https://github.com/ssdarwich2026-pixel/tp-tp1-enterprise, HEAD 98579c0, v0.20 prep on v0.1.5); Master Engine `~/workspace/space-archive-grand-prix/MASTER-ENGINE-SELF-EXPANDING-CATEGORY-GRAND-PRIX.md` (Cycle 1: 8/10 qualified, 0 matchups, champion NONE).

## CORRECTION — filed after a MEMORY.md update landed mid-run (2026-11-23 ~04:07 CT, Chris Continuity Handoff Batch 1)
Two facts in this record were stated too strongly and are corrected here; the crown stands, the evidence status changes:
- Cycle 1 "8/10 qualified" is DISPUTED, not settled VERIFIED. Batch 1 finding D-01: Cycle 1's CPS used renormalization, while Master Engine spec §3's literal raw-sum reading gives 0 qualifiers — a real method divergence needing Sayed's call. Until he calls it, UTIP must treat Cycle 1 CPS as provisional and must not hard-code either reading into the UTIP spec.
- v0.20 foundation is RED on its own track: 4 canonical v0.20 files were NOT FOUND in a workspace-wide search 2026-11-22; branch 98579c0 is local only and unmerged; v0.1 remains the authorized pilot and v0.2-Lite the live runner. UTIP Stage 1 therefore cannot just "inventory the repo" — it must first locate/re-supply those files (decision D-04) and confirm the pin. New tickets T-UTIP-07 (D-01) and T-UTIP-08 (D-04) below.

## Objective + acceptance criteria
Design UTIP v1.0 (Unified Tournament Intelligence Protocol) as an integration layer ONLY on top of TP/TP1 v0.20. Do NOT replace, rename, or rewrite TP, TP1, or Grand Prix. Must: preserve v0.20 intact; stay backward compatible; keep the three engines' judgment independent; trace every decision to evidence; cap all return loops; be shadow-testable; stay token/light; roll back cleanly. Must meet Sayed's five demonstrations (TP assigns/manages; TP1 verifies/qualifies independently; Grand Prix challenges/proposes better; evidence exchanged without corrupting records; win/loss/hold explainable and reproducible). Rollout in 7 stages with gates G1–G6 (G2/G5/G6 = Sayed).

## Scoring (coordinator-applied, same 8 criteria, 0–10 each)
Preserves v0.20 · Backward compat · Independent judgment · Evidence traceability · Loop safety · Shadow testability · Token/light cost · Rollback. Variant self-scores were taken as claims and adjusted by the coordinator where a weakness in the design contradicted a score.

## Group Stage — 5 variants
| Variant | Design | Scores (8 criteria, in order above) | Total |
|---|---|---|---|
| A — Thin interface-only | Adapters + contracts only; 3 separate ledgers; read-only reconciler; TP-as-arbiter | 10, 9, 8, 7, 8, 9, 9, 10 | 70 |
| B — Full shared ledger | Single append-only JSONL ledger, write scopes per engine, Chris evaluator, 2 retests | 9, 9, 8, 10, 8, 9, 9, 8 | 70 |
| C — Human evaluator, per-engine ledgers + reconciler | Each engine owns a hash-chained ledger; reconciler merges read-only, flags divergence; Chris evaluates, Sayed appeal, Jack recused on own claims | 10, 9, 9, 9, 8, 9, 8, 10 | 72 |
| D — Automated evaluator, separate repo | Own repo `utip-v1`, v0.20 pinned as dependency (98579c0); deterministic retest harness as evaluator, max 3 retests | 10, 9, 8, 9, 8, 9, 9, 10 | 72 |
| E — Shadow-first, TP-as-arbiter, thin + reconciler | Thin layer + reconciler; ≥3 clean shadow cycles before pilot; TP arbitrates except own matchups (owner); retest cap 1 | 10, 9, 9, 8, 9, 9, 9, 10 | 73 |

Group champion: E (73). Runner-up: C and D tied (72).
Eliminated: A. WHY: traceability 7 — fragmented ledgers plus a non-authoritative reconciler view fails demonstration 5 (explain/reproduce a win from one record). Dissent: A is the cheapest rollback and the safest against ledger corruption; its reconciler quarantine idea survives into the champion as a patch (see Challenger). B advances over A on the tie (70–70) by traceability 10 vs 7.
Note: self-scores were close; the real separation is qualitative — where each variant fails, and how bad that failure is.

## Semifinal — top 4
- **SF1: E vs B → E advances.** WHY: E fails safe (shadow-first, trivial rollback, loop cap 1); B fails stuck (single-ledger write contention, hash-break halts advancement, rollback 8). B's single source of truth is better for traceability, so B's ledger schema is carried into the champion as a component — but as a design B risks the tournament stalling on its own ledger. Dissent: B's replayability (one chain, one `explain`) is the cleanest demo-5 answer; the champion must match it, which the composite does via B's schema.
- **SF2: C vs D → C advances.** WHY: UTIP exists to preserve independent judgment; automating the judge (D) trades that away for speed. Scoring-rule bugs become law until a human notices, and deterministic retests can be gamed by evidence-count padding. D's deterministic retest harness survives as a first-pass filter inside the champion, not as the evaluator. Dissent: D is the fastest and cheapest at scale and the only variant with <5% overhead measured; if the evaluator queue ever grows, D's harness is the fallback — recorded as a ticket, not adopted now.

## Final — E vs C → C WINS
**Champion: Variant C — Human-Evaluator Disagreement Engine, Per-Engine Ledgers + Reconciler (composite).**
Runner-up: E.
WHY (2 lines): C makes disagreement visible by construction — no engine can overwrite another's record, and every dispute ends with a named human, a written WHY, a cap, and an appeal. E's TP-as-arbiter concentrates process power in the same engine that runs the matchups, and its self-arbitration ban is enforced by discipline only — its own designer flagged relabelling a matchup dispute as a "process" dispute as the failure mode.
Dissent: E is the safer rollout (3 clean shadow cycles, loop cap 1, rollback 10) and C's evaluator bottleneck is real — one person, one queue. The champion therefore adopts E's shadow discipline (≥3 clean cycles, divergence ≤5% blocks pilot) and D's automated retest as a pre-filter to keep the queue short. Final is a composite: C core + B ledger schema + D retest harness + E shadow discipline, per the house rule that champions are composites of per-item winners.

## Challenger round — hardest attacks on C, and whether it survives
1. **Scoring HOLD.** Attack: with S-01 HOLD, GP scores stay provisional/advisory, so GP challenges can be ignored and the engine is decorative. Survives, patched: GP challenges trigger retests on *evidence*, not on score — TP1 re-verifies from primary sources; provisional scores are labelled and never decisive. Patch P1: a GP challenge backed by verified evidence the TP1 verdict missed MUST produce a re-verdict, not a note.
2. **Infinite disagreement loop.** Attack: drip-fed "new evidence" restarts the 2-retest cap forever. Survives, patched: Patch P2 — retest requires *material* new evidence (evaluator judges materiality, may rule without retest); after cap, HOLD or Sayed, no third bite.
3. **Ledger corruption / reconciler lag.** Attack: reconciler stalls, shared view looks settled while ledgers diverge. Survives: per-engine ledgers are independent, so one bad ledger cannot poison the others; reconciler carries a freshness timestamp and a hard "view stale, do not promote" flag; hash mismatch is a blocker, not a note.
4. **TP matchup-rigging.** Attack: TP1 audit is flag-only; a biased bracket advances before appeal. Survives, patched: Patch P3 — rigging flags (repeat pairings, unexplained byes) are *blockers* for promotion past G5, not notes; GP may challenge pairings; evaluator reviews challenged pairings.
5. **Grand Prix gaming.** Attack: GP optimises for provisional scores / evidence-count padding. Survives: TP1 verifies from primary sources, never from GP summaries; challenges require cited evidence, not score claims; automated retest harness checks evidence hashes before counting anything.
6. **Shadow-mode divergence.** Attack: divergence waived as "noise" under schedule pressure. Survives: blocker-vs-note severity is in the reconciler spec; blockers halt promotion past G5 until resolved or waived by Sayed at G5/G6 — waiver is itself a ledger entry, never silent.
Challenger verdict: **no fatal flaw. Champion stands, with patches P1–P3.**

## Ratification vs status quo (v0.20 alone, no UTIP)
Status quo: v0.20 alone — no formal GP challenge channel, disagreements unrecorded, TP unaudited, Category Grand Prix evidence not reusable as UTIP evidence.
Champion's cost: branch + reconciler + evaluator digest per cycle (flagged items only, no full reruns); no new service, no new model calls by default.
**RATIFIED — conditionally.** UTIP earns its complexity only in shadow-first form with patches P1–P3. If shadow divergence is high or the evaluator queue grows past one cycle, UTIP pauses — it is never forced through. UTIP does not promote full v0.2 Grand Prix (still draft pending Jack + blind parity + Sayed's decision); it is an integration layer, not a promotion.

## Final champion design (composite)
- **Form:** branch `feature/utip-v1-integration` on tp-tp1-enterprise (NOT a separate repo — D's two-repo drift rejected; Sayed's stated branch). Additive `integrations/UTIP/` + `tests/UTIP/` only; zero edits to existing protocol files. Deleting the branch restores v0.20 exactly.
- **Modules:** `UTIP_MASTER_SPEC.md`, `ARCHITECTURE.md`, `ENGINE_ROLES.md`, `DATA_CONTRACTS/`, `SHARED_LEDGER/` (per-engine ledgers + reconciler), `DISAGREEMENT_ENGINE/`, `MATCHUP_ENGINE/`, `OWNER_APPROVAL_GATE/`, `VERSION_COMPATIBILITY/` (manifest pins TP/TP1 v0.20 @ 98579c0).
- **Interfaces:** IF-01 Tournament (TP publishes matchup/round/advancement); IF-02 Evidence Packet `{packet_id, source_engine, candidate_id, claim, evidence_refs[], sha256, as_of}`; IF-03 Qualification (TP1 PASS/HOLD/FAIL + reasons; HOLD blocks advancement); IF-04 Challenge (UTIP-GP challenger + cited evidence; scores PROPOSED only); IF-05 Compatibility Manifest (versions, contract versions, hash algorithm; mismatch = no connection).
- **Ledger schema (per engine, from B):** JSONL, hash-chained, append-only. Fields: `ledger_seq, event_id, timestamp_utc, engine, actor, candidate_id, stage/round, action, claim, verdict, evidence_ref, score_bars, supersedes_id, prev_hash, record_hash`. `candidate_id` permanent (`UTIP-CAND-0001…`). `score_bars` records Floor 70 / Line 93 only — no invented formula while S-01 is HOLD. Corrections are new records via `supersedes_id`; no UPDATE/DELETE. Batch SHA-256 manifests.
- **Write scopes:** TP creates candidates/assigns/advances — cannot edit verdicts. TP1 verifies/qualifies/QA — cannot change matchups. UTIP-GP proposes challengers — cannot overwrite TP1 verdicts. Evaluator files rulings to the TP1 ledger as rulings, never edits to disputed entries.
- **Disagreement engine:** named evaluator Chris; Sayed final appeal; Jack consulted as second opinion, recused on own claims. Procedure: reconciler flags divergence → automated retest harness first pass (deterministic, hash-checked) → Chris rules with written WHY → appeal to Sayed. Retest cap: max 2 per disputed claim, each requiring *material* new evidence (P2). Third dispute → HOLD or Sayed. TP disputes about its own matchups go to Sayed directly (E's self-arbitration ban, adopted). Ruling audit: periodic review of evaluator rulings for systematic bias.
- **Loop caps:** qualification-fail return max 2 retests; standards-fail retest max 2; disagreement retest max 2; then HOLD + owner escalation. No return loop without a cap.
- **Naming disambiguation:** inside UTIP the competitive engine is **UTIP-GP** (alias GP-Competitive). It is NOT the Category Grand Prix (Master Engine), NOT Format 6 Expansion Cup, NOT the JAX portable engine. Category Grand Prix remains one *instance* that can run under UTIP, not the engine itself. (Owner to confirm label — ticket T-UTIP-02.)
- **TP audit:** TP1 read-only samples matchup assignments for rigging patterns; GP may challenge pairings; rigging flags are G5 blockers (P3).
- **Rollout (7 stages) + gates:** 1 Preservation (inventory actual repo) → 2 Spec (this draft) → 3 Branch `feature/utip-v1-integration` → 4 Three-engine connection → 5 Shadow tournament (≥3 clean cycles, divergence ≤5%, zero unresolved hash mismatches) → 6 Controlled pilot (one limited category tournament, v0.20 fallback live) → 7 Release (PR, review, tag, gradual deploy, rollback = abandon branch). Gates G1 Chris reports, G2 Sayed, G3 Chris reports, G4 independent review, G5 Sayed, G6 Sayed. No automatic progression through owner gates.
- **TP1 role change (recorded, not silent):** TP1's standing role is the Q/A kernel (QA·001). UTIP extends it to verification/qualification/QA/execution — recorded as a dated change note with WHY in the spec and manifest (ticket T-UTIP-03, needs Sayed's acknowledgment at G2).

## Open tickets
- **T-UTIP-01 — Scoring formula HOLD (S-01).** GP competitive score + general TP1 qualification score have no canonical formula. UTIP v1.0 ships with bars only (Floor 70 / Line 93) and PROPOSED scores. Owner decision: authorise new versioned formula work, or accept advisory-only GP scores in v1.0.
- **T-UTIP-02 — Naming label.** Confirm "UTIP-GP" as the in-UTIP name for the competitive engine. Owner decision at G2.
- **T-UTIP-03 — TP1 role expansion.** Dated change note needs Sayed's acknowledgment at G2 (Q/A kernel → + verification/qualification/QA/execution).
- **T-UTIP-04 — Stage 3 branch creation. BLOCKED.** Needs Sayed's go on this champion. No branch, no PR, no production change until then.
- **T-UTIP-05 — Evaluator queue fallback.** If disputes queue past one cycle, D's automated harness escalates from pre-filter to interim evaluator only with Sayed's approval. Monitor in shadow mode.
- **T-UTIP-06 — Challenger patches P1–P3** to be written into the spec (evidence-triggered re-verdict; material-evidence bar; rigging flags as G5 blockers).
- **T-UTIP-07 — D-01 CPS divergence (from Batch 1).** Cycle 1 renormalization vs spec §3 literal raw-sum: 8 qualifiers vs 0. Owner decision owed before UTIP pins any CPS reading. Until called, UTIP carries both readings as PROPOSED and qualifies nothing on CPS alone.
- **T-UTIP-08 — D-04 v0.20 files not found.** 4 canonical v0.20 files missing (workspace search 2026-11-22); branch local only, unmerged. Stage 1 must locate/re-supply them before Stage 3. Owner decision owed.

## Evidence status
Variant designs: PROPOSED (5 crew designs, filed in this record, not independent verification). Scores: coordinator-applied, INFERRED from variant self-scores + design review — not a canonical formula (S-01 HOLD applies here too; totals are ranking aids, not certified scores). Repo facts: VERIFIED (remote, HEAD 98579c0, read-only inventory). Master Engine Cycle 1: VERIFIED (8/10 qualified, 0 matchups, champion NONE). No production system was touched; no test was run against live data — shadow mode is Stage 5, not yet reached.
Decision: **PASS (champion crowned, patched, ratified conditionally)** · Ticket status: 8 OPEN (T-UTIP-01..08), 0 CHEESED.

## Back Gate + next action
Stage 1 inventory + Stage 2 spec draft: DONE in this run (spec skeleton filed alongside this record). Next: Sayed decides on the champion + T-UTIP-01/02/03. Only then Stage 3 (branch creation). Deliverables: this file + `UTIP-MASTER-SPEC-DRAFT-2026-11-23.md` in the same folder.
