# Shared Evidence and Decision Ledger

Per-engine ledgers + reconciler (tournament Variant C, ledger schema from
Variant B). Each engine owns one append-only, hash-chained JSONL ledger.

## Record schema (per engine)

`ledger_seq, event_id, timestamp_utc, engine, actor, candidate_id,
stage/round, action, claim, verdict, evidence_ref, score_bars, supersedes_id,
prev_hash, record_hash`

- `candidate_id` is permanent (`UTIP-CAND-0001…`).
- `evidence_ref` = SHA-256 + path/URL.
- `score_bars` = Floor 70 / Line 93 only — no invented formula while S-01
  is HOLD.
- Corrections are new records via `supersedes_id`; no UPDATE/DELETE.
- Batch SHA-256 manifests.

## Write scopes

- TP creates candidates / assigns / advances — cannot edit verdicts.
- TP1 verifies / qualifies / QA — cannot change matchups.
- UTIP-GP proposes challengers — cannot overwrite TP1 verdicts.
- Evaluator files rulings to the TP1 ledger as rulings, never as edits to
  disputed entries.

## Reconciler

Merges the three ledgers into a read-only shared view; never edits a ledger.
Divergence = same claim/candidate with different verdict, score band or
status; a verdict citing evidence absent from its home ledger; duplicate
claim IDs or contradictory ordering. Auto-merge only for exact duplicates.
All else goes to a `UTIP-DIVERGENCE` log (blocker vs note, both excerpts,
hashes). Blockers halt promotion past G5 until resolved or waived by Sayed
(a waiver is itself a ledger entry). A hash proves integrity of the recorded
bytes, not truth of the underlying claim — provenance and independent
verification remain required.
