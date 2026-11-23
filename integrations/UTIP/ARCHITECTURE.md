# UTIP Architecture

Champion design from tournament T123+·UTIP·001: **Variant C composite** —
human-evaluator disagreement engine, per-engine ledgers + reconciler, with
Variant B's ledger schema, Variant D's automated retest harness as a first
pass, and Variant E's shadow-first discipline (≥3 clean shadow cycles,
divergence ≤5% per cycle).

```
Sayed (owner — gates G2/G5/G6, final appeal)
  │
  ▼
UTIP — integration layer (contracts, routing, ledger, disagreement, gates)
  ├── TP — Tournament Controller
  ├── TP1 — Intelligence Kernel
  └── UTIP-GP — Competitive Engine
```

## Trust boundaries

- Each engine owns **one** append-only, hash-chained ledger and writes only
  to it. No engine edits another engine's ledger.
- The **reconciler** merges the three ledgers into a read-only shared view.
  It never edits a ledger and is never the source of truth. A stale view is
  flagged "do not promote".
- **UTIP-GP** inside UTIP is the competitive engine. It is NOT the Category
  Grand Prix (Master Engine), NOT Format 6 Expansion Cup, NOT the JAX
  portable engine. The Category Grand Prix is one instance that may run
  under UTIP.
- Corrections are new records (`supersedes_id`); there is no UPDATE/DELETE.
- A compatibility mismatch (wrong engine version, wrong contract version)
  means **no connection** — fail closed into HOLD.

## What UTIP does not do

Replace TP, TP1 or Grand Prix; invent a scoring formula; publish content;
authorise spending; bypass rights or originality review; manufacture missing
metrics; guarantee performance or watch hours; promote itself to production.
