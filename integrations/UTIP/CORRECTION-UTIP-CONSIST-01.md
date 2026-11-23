# CORRECTION — UTIP-CONSIST-01 (append-only)

Date filed: 2026-11-23 (America/Chicago)
Run: TP/TP1 Run 019, 2026-11-23 — UTIP branch consistency review
Defect: UTIP-CONSIST-01 — FAIL
Author of this correction: Chris (Agent 81), at Sayed's go, 2026-11-23 ~09:00 CT
Scope: documentation / evidence-ledger correction only. No code. No production change. No merge to main. No release tag.

## What was wrong

Three documents in commit 70508ad disagreed about whether the UTIP branch was created, because they were written at different times in the same morning and read as if they were all written at once:

1. `TOURNAMENT_RECORD_T123_UTIP_001.md`, status line, written 2026-11-23 ~04:06–04:15 CT:
   > "Status: CHAMPION CROWNED (patched) — RATIFIED vs status quo, conditionally. No branch created. No GitHub write. No spend."
   And ticket T-UTIP-04 in the same file:
   > "T-UTIP-04 — Stage 3 branch creation. BLOCKED. Needs Sayed's go on this champion. No branch, no PR, no production change until then."

2. `UTIP_MASTER_SPEC.md`, header, drafted 2026-11-23 ~04:14 CT:
   > "Branch creation authorised by Sayed 2026-11-23 ~04:14 CT (ticket T-UTIP-04). No code written, no GitHub push yet, no production change."

3. `README.md`, in the same branch:
   > "Status: DRAFT branch only. Created 2026-11-23 at Sayed's go (tournament champion approval, ticket T-UTIP-04). No merge to main, no release tag, no production change, no shadow run yet."

Read together without as-of dates, (1) and (2) say no branch / no push, while (3) says the branch was created. That is the defect Run 019 caught. It is a documentation and evidence-ledger consistency defect, not a code defect.

## Verified ground truth (as of 2026-11-23 ~04:24 CT, re-checked 2026-11-23 ~08:57 CT)

The branch DOES exist on GitHub:

- Repository: https://github.com/ssdarwich2026-pixel/tp-tp1-enterprise
- Branch: `feature/utip-v1-integration`
- Commit: `70508ad395c21a865c2deb957a872dd35226c9d8`
- Commit message: "docs(utip): add UTIP v1.0 integration spec (branch only, no production change)"
- Parent: `6dd8094` (v0.1.5, the last published release)
- Change: 11 files, +594 lines, 0 deletions, main unchanged
- No pull request open, no merge to main, no release tag
- Author of the branch upload: Chris, via the browser as ssdarwich2026-pixel, after Sayed's "Yes, create the branch and upload it" (side chat 8ffc956e, 2026-11-23). Jack did NOT make this branch. Jack has no GitHub sign-in and was never given one.

## How the contradiction arose (the as-of reading)

- The tournament record's "No branch created" line was true when that run was written, before Sayed's go on T-UTIP-04.
- The master spec's "no GitHub push yet" line was true when that draft was written, ~04:14 CT, before the upload ran 04:15–04:24 CT.
- The README's "Created 2026-11-23 at Sayed's go" line was written for the upload, after the go, and is the one that matches the live branch.

None of the three lines is deleted or rewritten by this correction. They stand as historical as-of statements. This file supersedes them from 04:24 CT onward.

## Corrections (append-only, superseding, not rewriting)

- C-01: The branch `feature/utip-v1-integration` WAS created on 2026-11-23, at Sayed's go, and the GitHub push DID occur. The "No branch created / No GitHub write / no GitHub push yet" lines in the tournament record and master spec are superseded as of 2026-11-23 ~04:24 CT.
- C-02: Ticket T-UTIP-04 (Stage 3 branch creation) is CLOSED for branch creation only. The branch exists. Stages 4–7 remain gated (G2/G5/G6 are Sayed's), and no shadow run, pilot, merge, or release is authorised by this correction.
- C-03: The v0.20 reference is unchanged: this branch is based on v0.1.5 (commit 6dd8094), NOT on the local v0.20 prep work (commit 98579c0). The spec pins v0.20 @ 98579c0 only provisionally (flag F-02). v0.20 remains the governing standard; Runs 017 and 018 remain the governing release records.
- C-04: Acceptance tests remain NOT RUN (`tests/UTIP/acceptance/ACCEPTANCE_TESTS.md`). No executable integration code was in commit 70508ad, and none is added by this correction. Executable integration tests begin only after the actual code baseline is verified, per Run 019.
- C-05: UTIP remains a separate, unmerged development track. Deleting this branch restores v0.20 exactly.

## What this correction does not do

- It does not edit, delete, or rewrite any line in the tournament record, the master spec, or the README.
- It does not merge anything to main, create a pull request, or tag a release.
- It does not change v0.20, the Pitch, or any production installation.
- It does not claim Jack made the branch, or that the Pitch was freshly verified. The Pitch / Desktop Commander read-back in Run 019 remains owner-reported only; that device was offline at the time of Run 019.
