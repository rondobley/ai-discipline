# Premise Re-Check

Every 2-4 weeks during active development, formally re-check whether the
project's foundational premise still holds. Without this, drift is silent
and slow — by the time it feels obvious, you've already wasted weeks.

## Why this matters

In a multi-month build, you make hundreds of small decisions. Each one feels
local. Together they can drift the project away from its original intent.
You won't notice this in the day-to-day because each step is small.

The premise re-check forces a step-back at a regular cadence.

## Cadence

Schedule for every 2-4 weeks. Default: every other Friday afternoon.
Calendar block 60-90 minutes. Don't skip when busy; the busier you are, the
more likely you've drifted.

## The questions

Sit down with these and write actual answers (not in your head; on paper or
in a doc that gets dated and saved):

### 1. Restate the original premise.
- Pull up the project description from week 1
- In your own words today, what is this product? Who pays for it? Why?
- Compare to the original. Are you still building the same thing?
- If you've drifted, is that deliberate evolution or unconscious creep?

### 2. What evidence has accumulated for or against the premise?
- Customer conversations (good and bad)
- Usage data (if you have any users)
- What you've learned from building (feasibility, cost, time)
- What you've learned from the market (competitors, news, regulations)

Be specific. "Customers seem to like it" doesn't count. "3 of 4 demo
customers used the X feature within 24 hours" does.

### 3. What would now make us kill this project?
- Define your kill criterion based on current evidence
- Specific, measurable, time-bound
- "If by [date X] we don't have [Y signal], we kill"

### 4. Are we still on track, or have we drifted?
- What did we plan to build by now?
- What did we actually build?
- What's the gap, and is it justified by what we learned?
- What's in the codebase that shouldn't be there?

### 5. What should we delete?
- Code or features no customers use
- Tech debt that's grown beyond the budget (see TECHDEBT.md)
- Documentation that's stale
- AI artifacts (commit messages, comments, doc fragments) that don't fit
  the current direction

### 6. What's one specific thing to change in the next two weeks?
- Concrete, actionable
- Different from "ship faster" or "talk to more customers"
- Something a co-worker could verify happened or didn't

## Output

After the re-check, write a short note (a few paragraphs) capturing:
- Re-check date
- What changed since last re-check
- Decisions made (kill / pivot / continue / refocus)
- One concrete action for the next two weeks

Save these notes (e.g., `reviews/2026-XX-XX-premise-recheck.md`). Reading
back through them after 6 months is the most useful diagnostic for "what
went wrong" if the project fails.

## Anti-patterns this catches

- "We're so busy we can't step back" — exactly when you need to
- Sunk-cost momentum ("we've put 2 months in, can't pivot now")
- Drift via small "yes" decisions (each feels minor; cumulative effect is
  major)
- Forgetting why you chose specific architecture or features

## When to do it differently

- Major event (big customer signal, competitor launch, team change):
  re-check immediately, don't wait for the schedule
- Just shipped something significant: re-check after the dust settles
- Considering a major pivot: re-check first, decide second
