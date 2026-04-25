# Feature Validation Gate

Before any feature ships, answer these five questions. If you can't answer
all five, don't build it.

## The five questions

### 1. What customer pain does this solve?
- Specific pain, specific customer, specific cost they're paying today
- "Customers want better X" doesn't count — what's the actual pain?

### 2. Have you confirmed at least 3 customers actually have that pain?
- Named customers, with quotes or notes
- "Many customers might have this" doesn't count
- If you only have your own pain, you're building for yourself

### 3. Is this the simplest solution to that pain?
- What are the 3 simplest alternatives?
- Why is yours better than each?
- Default toward the simpler option unless you have specific evidence

### 4. What's the cheapest version that tests whether customers care?
- The MVP of the feature, not the production version
- 1 day of work, not 1 week
- What can be faked, manual, or stubbed?

### 5. What's the kill criterion?
- If after X weeks, fewer than Y customers use this feature, you remove it
- Specific X and Y, not "if it's not working"
- The default kill criterion if you can't think of one: "If 0% of customers
  use this within 4 weeks of shipping, remove it"

## What to do when stuck on a question

| Stuck on | What it means |
|---|---|
| #1 | You're building speculatively. Talk to customers. |
| #2 | Your "domain knowledge" is your own pain. Validate. |
| #3 | You haven't thought hard enough. Slow down. |
| #4 | You're building too much. Cut scope. |
| #5 | You'll never remove it once shipped. Pre-commit. |

## Anti-patterns this gate catches

- "Customers might want it" → fails Q2
- "It's a small feature" → fails Q5 (small features compound into bloat)
- "Easy to build with AI" → ease of building is irrelevant; ease of
  maintaining is the cost
- "Customer A asked for it" → check Q2 (one customer ≠ pattern)
- "We need this for [milestone/launch/fundraise]" → that's not a customer
  pain

## When to use this gate

- Before adding any feature to the build queue
- When tempted to "just add" something while in the codebase
- During premise re-check, against features already shipped (delete unused
  ones)
