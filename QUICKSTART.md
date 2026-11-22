# TP/TP1 Enterprise — Quick Start

**For anyone, no experience needed. Five minutes, no account, no money, no internet required.**

This same file goes in the root of the public repo, so everyone who downloads it sees the same steps.

## What you need

- A computer with **Python 3.10 or newer**. (Check: open a terminal and type `python3 --version`. If it says 3.10 or higher, you're good. If Python isn't installed, get it from python.org first.)
- Nothing else. No sign-up, no API key, no payment, no extra downloads.

## Step 1 — Get the files

Download the release zip and unzip it. Open a terminal inside the unzipped folder.

- The main build is in the folder `01_CANDIDATE_BUILD_0.1.1` (version 0.1.1).
- The smaller starter kit is in `distribution-pack-0.1/foundation-0.1` (version 0.1.0).

## Step 2 — Prove it works (30 seconds)

From inside the `01_CANDIDATE_BUILD_0.1.1` folder, run:

```bash
PYTHONPATH=. python3 -m unittest discover -s tests
```

You should see:

```
Ran 24 tests
OK
```

If you see `OK`, it works on your machine. If a test fails, that's useful too — please report it (see below).

## Step 3 — See what it can do

List the pieces it knows about:

```bash
PYTHONPATH=. python3 -m tp1_universal.cli modules
```

Make your first plan — describe anything you want to build:

```bash
PYTHONPATH=. python3 -m tp1_universal.cli plan "Build an AI model benchmark with evidence and recovery"
```

You get back a plan: which modules it needs, what depends on what, the assumptions it made, and the risks. **A plan is a proposal, not permission to build.** Nothing gets built, bought, or published by running this.

## The smaller starter kit (optional)

From inside `distribution-pack-0.1/foundation-0.1`, run:

```bash
python3 -m tp1.cli status
python3 -m tp1.cli plan "Build a research and development workspace"
```

`status` shows the version, community tier, and that billing is off. `plan` builds a phased plan with an owner-approval gate on every phase.

## What this does NOT do

- No internet, no accounts, no live AI provider connections. Everything runs on your own computer.
- No money moves. Billing is off and there is no price.
- No proof engine yet — the proof checker says HOLD until a real checker is connected. It will not pretend a proof exists.
- No scores or champions yet — the scoring formula is still missing, so nothing here declares a winner.

## If something goes wrong

- `python3: command not found` — Python isn't installed or isn't on your path. Install Python 3.10+ from python.org and try again.
- `python` works but `python3` doesn't (or the reverse) — use whichever one prints a version 3.10 or higher.
- A test fails — copy the exact error message and open a GitHub issue titled `[bug]` with it, plus your Python version and operating system.
- Anything else — open a GitHub issue and describe what you typed and what you saw.

## How to give feedback

- **Found a bug:** GitHub issue, `[bug]`, exact steps + error.
- **Have a hard problem or counterexample:** GitHub issue, `[challenge]`, with exact inputs, method, and what you expected.
- **Want to help:** read `CONTRIBUTING.md` and `CHALLENGE_SUBMISSION_GUIDE.md` in the build folder.

## Verified on our side

Run live on 2026-11-21 by Chris: candidate 0.1.1 — 24/24 tests OK in 0.08s, `modules` and `plan` both return real output; Foundation 0.1 — status shows v0.1.0, community tier, billing off, and `plan` returns a phased plan. Python 3.12.3, Linux.
