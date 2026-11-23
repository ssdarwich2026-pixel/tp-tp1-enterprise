# TP/TP1 Universal Intelligence Platform — Community Development Preview

> **Release 0.1.5 (2026-11-21) — the current public version.** Candidate code 0.1.1, unchanged. New in this release: the Red Agency doctrine draft, reconciled per Jack's review (still DRAFT, awaiting ratification) — see `red-agency/`; the tightened Commons call-out wording — see `commons/COMMONS-CALL-OUT-DRAFT.md`; and Jack's conversation-memory patch for the Pitch, versions v1.2.1–v1.2.3 with full test evidence — see `jack-memory/` (v1.2.3 is the current candidate, installed on the Pitch; the kill-tab commissioning test is still outstanding). **License decision pending — this is a public development preview, NOT open source yet.** See `LICENSE-PENDING.md` and `QUICKSTART.md` to start in five minutes.

**Tagline:** Install small. Think big. Build what you need.  
**Build ID:** `TP1-UNIVERSAL-INTELLIGENCE-001`  
**Candidate version:** `0.1.1`  
**Status:** Isolated local community-preview candidate; not yet promoted.  
**Active operating baseline:** approved v0.20 remains unchanged.

## What this is

TP/TP1 is a provider-neutral foundation for planning work, recording benchmark runs, preserving evidence and dependencies, and improving through reproducible challenges. It is a governed coordination framework, not one AI model.

This release is intentionally small. It demonstrates local planning, a model-adapter interface with deterministic test doubles, benchmark capture without scoring, an evidence ledger, proof-checker boundary, local persistence, awareness freshness, extension-manifest validation, and owner-gated local orchestration.

It is an experimental community development preview—not a finished universal AI system, hosted service, production multi-agent platform, or enterprise-ready product.

## Quick start

Requires Python 3.10+ and no third-party dependencies.

```bash
python -m unittest discover -s tests -v
python -m tp1_universal.cli modules
python -m tp1_universal.cli plan "Build an AI model benchmark with evidence and recovery"
```

Optional editable install:

```bash
python -m pip install -e .
tp1-universal modules
```

## Active component inventory

| Component | Code | Purpose |
|---|---|---|
| Policy kernel | `kernel.py` | Local fail-closed approval boundary; not production security |
| Intent planner | `planner.py` | Objective-to-module plan with dependency closure |
| Orchestrator | `orchestrator.py` | Plan-first coordination and explicit local build approval |
| Provider adapter contract | `providers.py` | Provider-neutral interface and deterministic test adapter |
| Benchmark harness | `benchmark.py` | Challenge capture, candidate IDs and response hashes; no score/ranking |
| Evidence ledger | `ledger.py` | Hash-chained local claims/evidence and dependency invalidation |
| Proof interface | `proofs.py` | Formal checker boundary; HOLD without real checker |
| Persistence | `persistence.py` | Local snapshot, integrity verification and restore |
| Awareness | `awareness.py` | Time-bounded observations and stale-state detection |
| Extensions | `extensions.py` | Manifest validation and least-privilege permission check |

## Deliberately deferred

The active 0.1.x runtime does not include billing, refunds, payment processing, support-desk intake, license enforcement, enterprise entitlements, public API gateway, marketplace, or paid-tier controls. Earlier reference implementations are preserved under `deferred_commercial/` for Chris's review only; they are not part of the active package and must not be wired back in without a separate owner-approved milestone.

Future individual or enterprise charges remain possible. No price or commitment is announced. See `COMMERCIAL_ROADMAP.md`.

## Why provider neutrality matters

The core uses normalized task, capability, evidence, permission, and result contracts rather than one model provider. Provider-specific differences must remain visible. OpenAI, Gemini, Anthropic, open-weight, and local models are not connected in this build. See `docs/UNIVERSAL_MODEL_PROTOCOL.md`.

TP/TP1 does not assume one model is best at everything. The benchmark harness does not declare a winner. Canonical Grand Prix and LAW·004 governance/scoring sources must be recovered before numerical scoring or champion claims. See `docs/GRAND_PRIX_BENCHMARK_PROTOCOL.md`.

## Test evidence

Run:

```bash
PYTHONPATH=. python -m unittest discover -s tests -v
```

The test count and result in `TEST_RESULTS.txt` are generated for this candidate and must be independently reproduced by Chris. Local functional tests are not formal proof, provider integration testing, security certification, or production acceptance.

## Critical limitations

- No live model-provider connector.
- No real multi-agent execution runtime.
- No formal theorem prover or proof-assistant connection.
- No canonical LAW·004 scoring formula or numeric Grand Prix score.
- No billing, refund, support desk, licensing, or entitlement enforcement in active runtime.
- No public API gateway or hosted service.
- No production security certification or deployment.
- Local snapshot manifest is not signed/encrypted and is not an off-site backup.
- No integration into the canonical v0.20 runtime has been performed.

## Governance and safety

- $0 default; no external spending.
- No external contact, publication, production deployment, account connection, credential handling, or destructive modification without separate approval.
- No uncontrolled self-modification. Plans are not execution authorization.
- v0.20 remains the approved operating baseline. Build 001 is not promoted.
- Original challenge and rationale materials are preserved in this handoff archive.

## Run it with your own AI / agent

Yes — upload this folder to your own AI or agent and have your agent run it
locally. See `AGENT-RUN-GUIDE.md` for the copy-paste prompt and the limits:
tests first, plan is a proposal only, no live provider connection, no
auto-run, no spending without your approval for that exact step. The school
idea is in there too: your agent learns one lesson at a time, on evidence
+ grade, so a small well-run agent can compete on governance and learning,
not just size.

## King of the Hill — v0.4-preview (2026-11-23)

An append-only weekly Live 200 chart engine: models, hybrids, and systems compete for chart positions. Two independent graders must evaluate every run; self-grading is rejected; every score needs a SHA-256 evidence reference. Empty chart positions are never fabricated.

Download the preview: [king-of-the-hill-v0.4-preview.zip](https://github.com/ssdarwich2026-pixel/tp-tp1-enterprise/releases/tag/koth-v0.4-preview) — 49 files, 53,854 bytes, SHA-256 e182cf0a2b203642ca0ad9392519e91d5cec76ecf6c237bd5c71fcfe7c8b247a.

Status: community development preview. License pending — NOT open source yet. 0 verified free providers; no live leaderboard; the 14-day collection clock has not started. Known defects in this preview: the /charts/rules route is defined twice (first body serves, second is dead); scripts/check_free_models.py crashes on the shipped manifest; the test suite passes 14/14 on a fresh database and 13/14 on a repeat run. See the release notes for the full list.

Run it: PYTHONPATH=. python -m pytest -q (14 passed on a fresh DB); DB_FILE=/tmp/koth.sqlite3 PYTHONPATH=. uvicorn app.api:app. Local only, $0.

## Contribution

Run the tests, report reproducible defects, submit challenge briefs and counterexamples, and contribute only data/materials you have rights to share. Preserve provenance, versions, assumptions, methods, limitations, and negative results. See `CONTRIBUTING.md` and `CHALLENGE_SUBMISSION_GUIDE.md`.
