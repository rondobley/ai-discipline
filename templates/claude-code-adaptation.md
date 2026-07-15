# Claude Code Adaptation

Running ai-discipline when the reviewer **is** Claude Code — one session, subagents as implementers — instead of canonical claude.ai-reviewer + CLI-implementer + human bridge.

**Delta-only. For roles, cadence, HALT triggers, and governance, follow `templates/` and `governance/` unchanged.** Only the topology changes.

## What changes

The three roles collapse into one Claude Code session:

- **Reviewer** = the main session (directs, reviews, gates).
- **Implementer** = a subagent (Task tool) at the **same model as the main session** — inherited, never downgraded — run under `templates/implementer.md`.
- **Research agent** = a read-only subagent under `templates/research-agent.md`.
- **Bridge** = the reviewer dispatches subagents and relays results; no human copy-paste.
- **Decision-maker** = the human, unchanged; gates every commit.

## The rule the topology costs you

Canonical enforces "the reviewer never edits" *by the tool boundary* — a claude.ai reviewer physically cannot touch files. Here the reviewer **is** Claude Code and can. That guardrail is gone, so it is self-enforced:

> The reviewer does **zero** hands-on repo work — no edits, no `git add`/`commit`, no migrations, no DB writes. **Every** repo mutation goes through an implementer subagent. The reviewer only reads, verifies, dispatches, and relays the human's gate.

That single rule is why this file exists. Everything else is canonical.

## Governance file location

Another divergence from the base framework: the governance files (`STATUS.md`,
`TECHDEBT.md`, `TODO.md`) live in a **local, gitignored `ai-discipline/` dir at
each consuming repo root** and are `@import`ed into that repo's root `CLAUDE.md`
— not committed at the repo root as the base framework prescribes. Here they
steer the operator's own Claude Code sessions rather than encoding a shared team
contract, so they stay out of version control and load automatically via
`@import`.
