# AI Defaults to Enthusiastic Implementation

The single most important lesson from using AI on substantive software
projects.

## The lesson

> AI defaults to enthusiastic implementation. It does not natively
> challenge "should we build this at all" before "how do we build this."

When you ask AI to help you build something, it will help you build that
thing. It will not natively ask whether you should be building it at all.
It will not natively stress-test your premise. It will not natively
identify the most likely ways your idea fails.

This is not a flaw to fix at the model level. It's a structural property
of how AI is used. AI is helpful; helpfulness defaults to "do what's asked."

## Why this matters

You can spend months building something AI helps you build, then discover
the thing didn't have edge or didn't have customers or didn't solve a real
pain. AI is not at fault for the wasted months. The lack of explicit
adversarial framing is at fault.

The cost of this trap is invisible until it's expensive: you don't see the
months you wasted until they're gone.

## The mechanism

When you prompt AI with "help me build X," several things happen by default:

1. AI accepts X as the goal
2. AI generates plausible-sounding implementation steps
3. AI produces working code that does X
4. Iterating with AI on X strengthens AI's commitment to X (each follow-up
   refines, doesn't reconsider)
5. After 100 iterations, AI is highly invested in X being correct
6. You're now invested in the months of code you have

At no point did anything explicitly ask: "is X the right thing?"

This isn't AI deceiving you. It's AI doing what you asked, optimally.

## The fix

You have to explicitly ask for adversarial framing. AI will not provide it
unprompted. The fix has three components:

1. **Adversarial agent**: a separate AI session whose job is to argue
   against the idea. See `templates/research-agent.md`.

2. **Explicit framing**: when prompting any AI, include direct asks like
   "argue against this idea" or "find the most likely ways this fails."
   Defaults are weak; explicit is strong.

3. **Discipline of the human director**: the human running the project
   has to enforce the standard. AI will drift back toward enthusiastic
   helpfulness without ongoing adversarial pressure. The human is the
   only persistent source of standards across sessions.

## When the fix breaks down

- When you're tired (the "yes that sounds great" response is easier than
  scrutinizing)
- When you're excited about an idea (you don't WANT adversarial pressure)
- When AI gives a particularly good-sounding answer (the more it sounds
  right, the less you check)
- When the work has been going well for weeks (sunk cost makes
  course-correction feel costly)

These are exactly the moments when discipline matters most. Notice them
and apply the discipline anyway.

## How to know you're in the trap

- You haven't run a kill-test on your current premise in over 4 weeks
- You're focused on "how to build X better" without recently asking
  "should we still be building X"
- AI keeps suggesting refinements rather than challenging direction
- You haven't talked to a customer in over 2 weeks
- You can't articulate, in one sentence, what specific evidence would make
  you kill the project

If 3+ of these apply, run a premise re-check (`playbooks/premise-recheck.md`).

## How to know you're holding the standard

- AI sometimes pushes back on you, not just helps you
- You've killed at least one feature or sub-project based on adversarial
  review
- Customer conversations regularly reveal things you didn't know
- The research-agent template lives in your workflow, not just in a doc
- You've experienced the discomfort of "the data says I'm wrong" and acted
  on it

## The asymmetry

Holding adversarial discipline costs you days of overhead per month.
Not holding it costs months of wasted work.

It's the cheapest insurance you'll ever buy.

## Worth re-reading periodically

This document is short on purpose. Read it before starting a new project.
Read it when premise re-check feels unnecessary. Read it when AI says
"great idea" too easily.

The more this lesson feels familiar, the more likely you are to slip back
into trusting AI's default mode. Re-read.
