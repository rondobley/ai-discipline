# AI Discipline

Templates and playbooks for using AI on substantive software projects without
falling into the AI-defaults-to-yes trap.

## The core lesson

> AI defaults to enthusiastic implementation. It does not natively challenge
> "should we build this at all" before "how do we build this."

This repo encodes the discipline that prevents that trap.

## When to use what

**Starting a new project**
1. Read `lessons/ai-defaults-to-yes.md` — the assumption this all rests on
2. Run `templates/research-agent.md` against your idea
3. Read `playbooks/customer-validation.md` and run the 5-prospect test
4. If proceeding: `playbooks/greenfield-saas-kickoff.md` step-by-step

**During development**
- Per architecture decision: `playbooks/architecture-decision.md`
- Per feature: `playbooks/feature-validation-gate.md`
- Pair-coding: `templates/reviewer.md` + `templates/implementer.md`
- Standing governance: `governance/frozen-surfaces.md`, `governance/tech-debt-ledger.md`

**On schedule**
- Every 2-4 weeks: `playbooks/premise-recheck.md`

**After failure or success**
- `playbooks/post-mortem.md`

## The three roles

| Role | When | What it does |
|---|---|---|
| Research agent | Before building | Adversarially stress-tests the premise |
| Reviewer | During building | Directs implementation, holds standards |
| Implementer | During building | Executes approved scope cleanly |

These run in separate AI sessions. Don't mix roles in one chat.

## The cadence

All pair-coding work follows four explicit stages:

  Stage 1 — Pre-scope. Investigate. Answer questions about scope, constraints,
                       current state. No design, no code.
  Stage 2 — Design preview. Propose the approach. Function signatures, test
                            plans, commit split. No code.
  Stage 3 — Implementation. Write code, run tests, show diff. No commit.
  Stage 4 — Commit. Only after explicit reviewer approval of the diff.

The reviewer (`templates/reviewer.md`) directs the cadence; the implementer
(`templates/implementer.md`) executes within it. HALT triggers
(`governance/halt-triggers.md`) are explicit gates between stages.

Skipping stages is the most common failure mode. Don't.

## What this repo is not

- A guarantee of project success
- A substitute for domain knowledge
- A substitute for an outside human reviewer
- A set of magic prompts that make AI smart

These are habits encoded as documents. The discipline is in exercising them.
