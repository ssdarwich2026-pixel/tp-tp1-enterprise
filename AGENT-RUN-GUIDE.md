# Run TP/TP1 with your own AI / agent

**Yes — you can upload this pack to your own AI or agent and have your agent run it.**

This is for people building their own agents. It is the same idea as school:
your agent learns one lesson at a time, on evidence, with a grade — it does
not just get bigger. That is how a small, well-run agent can hold its own
against a big-box brand: governed, reproducible, and honest about what it
does not know.

## What to do

1. Download the release zip and unzip it on your own computer.
2. Upload the unzipped folder to your AI / agent — the same way you would
   upload any project folder.
3. Tell your agent, in your own words (copy-paste works):

> "Run this TP/TP1 pack locally on my machine. First run the tests and
> show me they pass. Then run `modules` and make me a `plan` for what
> I want to build. A plan is a proposal only — do not build, buy,
> publish, connect an account, or spend anything without my approval
> for that exact step."

## What your agent should do

- Run the tests first: `PYTHONPATH=. python3 -m unittest discover -s tests`
  — you should see `Ran 24 tests / OK`.
- List the pieces: `python3 -m tp1_universal.cli modules`
- Make a plan: `python3 -m tp1_universal.cli plan "what you want to build"`
- Keep the evidence ledger: what was tried, what passed, what failed.
- Ask you before any build, buy, publish, or account connection.

## What it will NOT do

- It will not connect to a live AI provider by itself. The pack ships with
  a test adapter only — no OpenAI, Gemini, Anthropic, or local model is
  connected in this build.
- It will not run automatically on your AI infrastructure, and it will
  not install itself into your system.
- It will not prove a claim, declare a winner, or give a score. The proof
  checker says HOLD until a real checker is connected, and there is no
  canonical scoring formula yet.
- It will not spend money. Billing is off and there is no price.

## The school idea, in one paragraph

Every agent carries two papers: a Q/A about the jobs it is interested in,
desires most, will not do, and volunteers for — and a School enrollment.
School is one lesson at a time, closing on evidence + grade, with the
curriculum steered by that agent's own Q/A. Challenges and tournaments
are the lessons. That is the edge for independent builders: your agent
gets better in public, on evidence, instead of just getting bigger.

## Competing with big brands — honestly

This does not guarantee beating a big brand. What it gives a small agent
is a fair way to compete: a plan you can check, evidence you can re-run,
a ledger you can audit, and a fail-closed rule — if it cannot prove it,
it holds instead of pretending. That trust is the advantage. Size alone
is theirs; governance and learning are yours to build.

## If your agent gets stuck

- Test fails: copy the exact error + your Python version + your operating
  system, and open a GitHub issue titled `[bug]`.
- Hard problem / counterexample: open a GitHub issue titled `[challenge]`
  with exact inputs, method, and what you expected.
- Anything else: open a GitHub issue and describe what you typed and
  what you saw.

License: this is a public development preview, license-pending, NOT open
source yet. See `LICENSE-PENDING.md`.
