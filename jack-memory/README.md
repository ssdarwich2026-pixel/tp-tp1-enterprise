# jack_memory.py — Jack-82 conversation-memory patch (for the Pitch)

`jack_memory.py` is Jack's (82) conversation-memory tool for the Pitch: it
records checkpoints per BIN (a conversation thread's memory file), keeps a
`state.json` as the single canonical truth with `STATE.md` as its byte-checked
mirror, and refuses to overwrite anything it cannot verify — a bad state
stops safely instead of corrupting the record.

## Version line

- **v1.0** — the version installed on the Pitch. It works; its known limits
  are why the later versions exist.
- **v1.1** — Jack's first patch. **ON HOLD — do not install.** It has four
  fix-before findings (conflicting source of truth, BIN collision on gaps,
  interruption-unsafe checkpoint writes, stale v1.0 banner). It is preserved
  in the private handoff archive, not shipped here.
- **v1.2.1** — Chris's rebuild of v1.1: state.json is the single truth,
  gap-proof BIN allocation, interruption-safer writes, structural validation
  of state.json. 18/18 tests, verified by Chris. Not installed.
- **v1.2.2** — Jack's fix for one more hole Chris's review found: `repair`
  on a structurally invalid state crashed before validating. Independently
  reviewed by Chris (see `v1.2.2/CHRIS-INDEPENDENT-REVIEW-v1.2.2.md`) and
  approved for installation. 8/8 repair-path tests, re-run by Chris.
- **v1.2.3** — **the current candidate, installed on the Pitch and verified
  clean there.** Fixes a Windows line-ending bug found live on the Pitch
  during the v1.2.2 install: `_atomic_write` wrote CRLF on Windows while
  `verify` compared against LF-only renders, so `verify` could never pass
  and `repair` could not fix it. v1.2.3 writes LF-only and normalizes CRLF
  on comparison. 33/33 tests on the VM (7 CRLF + 18 full suite + 8 repair,
  Python 3.12.3, re-run by Chris); `verify` OK on the Pitch on JACK-BIN-001
  with v1.2.3. See `v1.2.3/CHANGELOG.md` and `v1.2.3/TEST-REPORT.md`.

Each version folder carries the patch, its changelog, its test report, its
test script(s), and its SHA256SUMS — verify the hashes before using anything.

## Honest status

- **The Pitch kill-tab commissioning test is STILL OUTSTANDING.** It needs
  Jack's own ChatGPT session (the kill-tab is the one test that cannot be
  run from this side). Nothing here claims it is done.
- **No install skips the gates.** Independent review + owner approval come
  first, every version, every time. The install and rollback notes that
  shipped with Jack's v1.2.2 package are the procedure; this README is not
  a shortcut around them.

## License

License pending — this tool is part of the TP/TP1 Enterprise release, which
is a public development preview, NOT open source yet. See `LICENSE-PENDING.md`.
