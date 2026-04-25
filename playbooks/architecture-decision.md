# Architecture Decision

Architecture decisions in week 1 of a project compound forever. Auth model,
multi-tenancy strategy, framework choice, billing integration — each one
constrains every later decision. AI is happy to make these enthusiastically.
You should slow down on each.

This playbook applies the pair-coding cadence to architectural choices.

## When to use

Trigger this playbook if any of the following apply:

- Will be expensive to reverse (estimated >2 weeks of work)
- Affects multiple subsystems
- Touches a frozen surface (see `governance/frozen-surfaces.md`)
- Has 3+ viable alternatives

Examples:
- Auth model (custom vs Auth0 vs Clerk vs Supabase)
- Database choice (Postgres vs MySQL vs DynamoDB)
- Multi-tenancy strategy (separate DBs vs shared DB with tenant_id vs schema-per-tenant)
- Framework (Rails vs Django vs Next.js vs Phoenix)
- Background jobs (Sidekiq vs Celery vs Hatchet vs none)
- Pricing model (per-seat vs per-usage vs flat)
- Billing integration timing (now vs after $X MRR)

## Cadence

### Stage 1: Pre-scope (the AI as adversary, not implementer)

Pose the question to AI WITHOUT framing it as "help me decide." Frame as:

> "For [problem X], list 3-5 viable architectural approaches. For each:
> - Pros (specific, not generic)
> - Cons (specific, not generic)
> - Reversibility cost in engineer-weeks
> - What it commits us to permanently
> - Real-world examples of teams that chose this and what happened
>
> Do not recommend one yet. Just enumerate."

Use the research-agent template if needed for adversarial framing.

### Stage 2: Design preview

Pick one option WITH explicit reasoning:
- Why this option over the next-best alternative
- What evidence would force a reversal
- What's now off-limits without explicit re-decision
- What gets added to STATUS.md as a frozen surface

A future-you in 6 months should be able to read the reasoning and understand
why.

### Stage 3: Implementation

- Build the smallest thing that exercises the decision
- Add tests that lock in the decision (make accidental changes break)
- Update STATUS.md with the new frozen surface
- Commit message body explains the decision

### Stage 4: Review

Per `templates/reviewer.md`:
- Decision-grade review: what's verified, what's likely, what's open
- HALT if implementation diverges from the documented decision

## Anti-patterns

- "AI suggested this so it must be reasonable" — AI suggests whatever fits
  your prompt; it doesn't know your specific constraints
- "We can change this later" — sometimes true, often not, and you almost
  never actually do
- "This is what [popular framework] does so we should too" — popular
  doesn't mean right for your context
- "We need to ship fast so let's just pick" — speed costs less than
  rebuilding; pre-scope adds days, rebuilding costs months

## Honest limit

Architecture-decision pre-scope catches obvious mistakes. It does not catch
subtle ones — choices that look right with the information you have but turn
out wrong as the product evolves. Some architectural mistakes are only
visible in retrospect. The discipline reduces avoidable mistakes; it doesn't
make every decision correct.
