# Version Compatibility

- **UTIP:** `1.0.0`, status `PROPOSED_NOT_DEPLOYED`.
- **Branch base:** `origin/main` @ `6dd8094` — release v0.1.5, the last
  published release. This branch adds UTIP files only; it does not modify
  any existing protocol file.
- **TP/TP1 v0.20 pin (provisional):** commit `98579c0`, local-only branch
  `dev/v020-governance-integration`, unmerged. Four canonical v0.20 files
  were not found in a workspace-wide search 2026-11-22 (D-04 / F-02). The
  pin is a reference, not a base: this branch deliberately does **not**
  carry the v0.20 prep commits, so uploading it does not silently publish
  unreviewed v0.20 work. Stage 1 must locate/re-supply those files before
  the pin can be confirmed.
- **Grand Prix:** Master Engine rulebook v1.0 (Category Grand Prix).
  Founding slate: 100 topics across 10 categories, all prospect-only.
- **Schemas:** `utip.candidate.v1`, `utip.evidence.v1`, `utip.result.v1`,
  `utip.event.v1`. Hash algorithm: SHA-256.
- **Feature flags:** `utip_enabled: false`, `shadow_mode: true`,
  `pilot_mode: false`, `production_mode: false`.
- If the actual version or schema differs from this manifest, UTIP fails
  closed into compatibility HOLD. Do not infer compatibility from similar
  version labels.
