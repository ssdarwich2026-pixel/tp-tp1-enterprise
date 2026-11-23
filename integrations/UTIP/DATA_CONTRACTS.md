# Data Contracts (IF-01..IF-05, frozen at v1.0)

- **IF-01 Tournament:** TP publishes matchup, entrants, round, advancement,
  status.
- **IF-02 Evidence Packet:** `{packet_id, source_engine, candidate_id, claim,
  evidence_refs[], sha256, as_of}`.
- **IF-03 Qualification:** TP1 returns PASS / HOLD / FAIL + reasons +
  evidence refs.
- **IF-04 Challenge:** UTIP-GP returns challenger, claim, cited evidence,
  proposed score (PROPOSED only while S-01 is HOLD).
- **IF-05 Compatibility Manifest:** engine versions, contract versions,
  ledger IDs, hash algorithm. Mismatch = no connection.

Every command/event has a unique event ID and idempotency key. Replaying the
same event must not duplicate candidates, scores, matchups, or state
transitions. Conflicting updates require reconciliation, not last-write-wins.

## Compatibility (this branch)

- `utip_version`: `1.0.0` — status `PROPOSED_NOT_DEPLOYED`
- `tp` / `tp1`: v0.20 pinned provisionally @ `98579c0` — **not yet on GitHub**
  (see F-02). Branch base is v0.1.5 (`6dd8094`, last published release).
- `grand_prix`: Master Engine rulebook v1.0 (Category Grand Prix).
- Schemas: `utip.candidate.v1`, `utip.evidence.v1`, `utip.result.v1`,
  `utip.event.v1`
- Feature flags: `utip_enabled: false`, `shadow_mode: true`,
  `pilot_mode: false`, `production_mode: false`
- Owner approval required for: production deployment, publishing, spending,
  external commitments, destructive changes, automation schedule changes.
