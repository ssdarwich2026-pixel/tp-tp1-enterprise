# UTIP Acceptance Tests — NOT RUN

Status: **NOT RUN.** These are the acceptance criteria for Stages 4–6.
No test in this file has been executed against the branch.

## Five demonstrations (must all pass, repeatedly)

1. TP assigns and manages a tournament end to end.
2. TP1 independently verifies and qualifies the same candidate from primary
   sources.
3. UTIP-GP proposes a challenger or better-scoring alternative with cited
   evidence.
4. All three exchange hash-cited packets with zero cross-writes; the
   reconciler rebuilds the shared view from the ledgers alone.
5. Any win / loss / hold is reproduced from the ruling + both ledgers,
   including dissent.

## Mandatory scenarios

- Same event replayed twice produces one logical state change.
- Missing evidence produces HOLD, not PASS.
- Rights status UNKNOWN cannot qualify.
- TP cannot override a TP1 hard gate.
- Grand Prix cannot alter a frozen rulebook during a round.
- TP1 cannot rewrite a Grand Prix score; it can flag evidence or scoring
  defects.
- A disagreement freezes affected advancement until resolved.
- Every score can be reconstructed from its component values and evidence.
- Every result identifies the exact protocol and rulebook versions.
- An incompatible schema/version fails closed.
- An unauthorized production / publishing / spending request is blocked.
- Rollback restores prior behavior and preserves the audit trail.
- Historical losses, rejected candidates, and superseded decisions remain
  retrievable.

## Test layers

Unit (state transitions, scoring math, validation, idempotency) · contract
(each adapter accepts/emits the agreed schema) · regression (existing TP/TP1
and Grand Prix behavior unchanged) · adversarial (malformed evidence,
conflicting scores, duplicate events, rulebook mismatch, unauthorized
action) · integration (all three engines exchange records, provenance
preserved) · shadow (identical frozen cases, comparable explainable outcomes,
no production change) · recovery (rollback and replay verified).

## Release gates

No critical test failures · no unexplained state divergence · no lost or
corrupted ledger events · all mandatory test evidence attached ·
compatibility matrix complete · rollback demonstrated · owner explicitly
approves pilot and production stages.

For every test: ID, version/commit, input fixture hash, expected result,
actual result, pass/fail, logs, reviewer, reproduction steps.
