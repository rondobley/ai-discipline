# Greenfield SaaS Kickoff

Step-by-step from idea to "ready to build the actual product." Most projects
fail at steps 1-9; AI accelerates step 10. The discipline is doing 1-9 even
when AI makes 10 feel productive.

## Day 1-3: Premise validation

### Step 1: Write the product description
- One paragraph
- What it does, who pays for it, why
- If you can't fit it in a paragraph, you don't know it well enough yet

### Step 2: Identify 5 prospective customers
- Not friends, not investors, not "people who would be interested"
- Actual prospects with the pain you're solving and budget to spend
- If you can't name 5 specific people, kill or sharpen the idea

### Step 3: Customer kill-test
- See `playbooks/customer-validation.md`
- Outcome: 4+ of 5 say "yes I'd pay $X" → proceed
- Anything less → kill, sharpen, or pivot

### Step 4: Research-agent stress test
- Run `templates/research-agent.md` against the validated idea
- Read the report fully; do not skim
- If verdict is "kill" → kill
- If verdict is "run kill-test in section 7" → run it before any building
- If verdict is "proceed with risks to monitor" → log those risks

## Day 4-7: Foundation setup

### Step 5: Repo + governance
- Create the repo
- Add `STATUS.md` listing frozen surfaces (see `governance/frozen-surfaces.md`)
- Add `TECHDEBT.md` (see `governance/tech-debt-ledger.md`)
- Set up CI with at minimum: tests, freeze-check
- First commit is governance-only, not feature code

### Step 6: Find your human adversarial reviewer
- An advisor, co-founder, friend with SaaS experience, paid coach
- Their job: tell you "you're drifting" every 2-4 weeks
- Schedule the first 1:1 within 2 weeks of step 1
- Without this person, the rest of the discipline is harder to hold

### Step 7: Architecture decisions (each pre-scoped separately)
- Use `playbooks/architecture-decision.md` for each major choice:
  - Auth model
  - Database + multi-tenancy strategy
  - Framework
  - Deployment target
  - Background job system (or none)
  - Pricing model + billing integration
- Each gets pre-scope/Stage-2/Stage-3 treatment
- Each commits to STATUS.md frozen surfaces when decided

## Week 2-4: Smallest premise test

### Step 8: Build the smallest thing that tests the premise
- Not the smallest viable product
- The smallest thing that tells you if customers will actually use it
- Often a fake landing page, a manual-backed prototype, or a Figma mockup
- Aim: 1 week of work, not 1 month

### Step 9: Show that thing to the same 5 prospects from step 2
- Same customers, same conversation
- "Here's the thing I described. Would you pay for THIS specific implementation?"
- Iterate on validation, not features

### Stop here if step 9 doesn't land
- If 4+ out of 5 prospects don't want to pay for what you showed them
- Kill, pivot, or pivot harder
- Do NOT proceed to step 10 hoping it gets better

## Week 4+: Build the actual product

### Step 10: Implement using the pair-coding cadence
- `templates/reviewer.md` + `templates/implementer.md`
- Per-feature gate at `playbooks/feature-validation-gate.md`
- Premise re-check at `playbooks/premise-recheck.md` every 2-4 weeks

## Calibration questions for the human director

If you're tempted to skip step N, ask yourself why. Common excuses:
- "I already know my customers" → run step 3 anyway
- "Architecture is obvious" → run step 7 anyway
- "We need to ship fast" → ship step 8 fast, not step 10 fast
- "The research agent didn't tell me anything new" → that's the value;
  you've validated nothing has been missed

The temptation to skip is highest right after AI helps you build something.
That's exactly when discipline matters most.
