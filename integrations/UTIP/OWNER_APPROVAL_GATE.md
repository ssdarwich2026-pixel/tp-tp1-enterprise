# Owner Approval Gate (G1–G6)

| Gate | Requirement | Who authorizes |
|---|---|---|
| G1 | Existing protocol inventoried | Chris reports |
| G2 | UTIP specification complete | Sayed |
| G3 | Integration tests pass | Chris reports |
| G4 | Shadow tournament passes | Independent review |
| G5 | Pilot passes | Sayed |
| G6 | Production release | Sayed |

No automatic progression through the owner gates. Spend, credentials,
publishing, deletions, and destructive changes always need Sayed's explicit
approval (Lite card §7).

## Rollout — 7 stages

1. Preservation — inventory actual repo + locate/re-supply missing v0.20
   files (F-02).
2. Specification — the draft in this branch → G2.
3. **Branch — this branch.**
4. Three-engine connection.
5. Shadow tournament — ≥3 clean cycles, divergence ≤5% of cases per cycle,
   zero unresolved hash mismatches, evaluator queue clear at cycle end.
6. Controlled pilot — one limited category tournament, v0.20 fallback live.
7. Release — pull request, review, tag, gradual deploy, rollback = abandon
   branch (history kept as audit).

## Rollback triggers

Evidence ledger corruption or loss · duplicate or conflicting state
transitions · unauthorized publishing, spending, or production action ·
mandatory qualification bypass · incompatible protocol version or schema ·
critical rights, provenance, or security failure · unreproducible
tournament result.

## Rollback sequence

1. Disable UTIP feature flag / stop integration workers.
2. Preserve logs and current ledger snapshot.
3. Restore previous known-good configuration and code.
4. Verify original TP/TP1 and Grand Prix operation.
5. Record rollback as an append-only event.
6. Notify Sayed with evidence and next steps.
