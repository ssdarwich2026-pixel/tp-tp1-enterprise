# Disagreement Engine

Make conflicts visible, testable, and resolvable — without averaging
incompatible opinions or letting a component grade itself.

## Open a disagreement when

- TP1 and Grand Prix reach materially different conclusions.
- A score cannot be reproduced from its evidence.
- A rulebook interpretation differs between engines.
- Evidence sources conflict or have changed.
- A candidate's status differs across components.
- A result depends on an unknown or unsupported input.

## Required record

`disagreement_id, subject_id / candidate_id, opened_at, component_claims
(claim, actor, version, timestamp), evidence_refs and hashes,
applicable_rulebook_version, impact / severity, independent_test_plan,
resolution and rationale, reviewer, resolved_at, supersedes / related event IDs`

## Procedure

1. Freeze the disputed decision; set the affected candidate/matchup to HOLD
   if advancement could be affected.
2. Capture both positions exactly, including scores and evidence.
3. Check both used the same frozen inputs and rulebook version.
4. Identify whether the conflict is factual, procedural, scoring-related,
   or interpretive.
5. Run an independent check or controlled retest.
6. Apply the authoritative rulebook and responsibility matrix.
7. Record resolution and dissent; never delete the losing argument.
8. Recompute affected results only through a new, traceable event.

**Evaluator: Chris** (named). **Final appeal: Sayed.** Jack may be consulted
as a second opinion, recused on claims he authored. Automated deterministic
retest harness runs first (hash-checked, no new model calls by default);
Chris then rules with a written WHY.

**Caps:** max **2 retests per disputed claim**, each requiring *material*
new evidence (evaluator judges materiality, may rule without retest). Third
dispute → HOLD or Sayed. A UTIP-GP challenge backed by verified evidence the
TP1 verdict missed **must** produce a re-verdict, not a note (Patch P1).
TP disputes about its own matchups go directly to Sayed (self-arbitration
ban); the case freezes until he rules. Evaluator rulings get a periodic
audit for systematic bias.

## Prohibited

Blind score averaging · silent rule changes · deleting failed tests or losing
arguments · letting Grand Prix waive mandatory gates · letting TP1
unilaterally declare a competitive winner.
