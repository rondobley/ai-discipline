# Domain Knowledge Trap

Why expertise misleads. Specifically: why domain experts fail differently
than novices, and how to avoid the failure mode that comes from "I know
this space."

## The trap

When you have domain knowledge, you skip steps that novices wouldn't skip.
You assume things you would otherwise validate. You build for yourself
because you're confident you represent the customer.

Three failure modes:

### 1. You build for yourself, not the average customer

Your pain points are not the typical customer's pain points. Your usage
patterns are not the typical customer's usage patterns. Your tolerance for
complexity is not theirs.

Domain experts often build sophisticated tools that solve their own
sophisticated problems. The market wants simpler tools for simpler problems.

**The check**: would the typical customer in your target market use what
you've built without training? If not, you've built for the expert tier of
a market that's mostly non-expert.

### 2. Other experts have different priorities than you

Even within your domain, different experts have different priorities. Your
specific career path and pain points shaped your view. Another expert in
the same field has different views.

Domain knowledge doesn't average across the field. It's one perspective.

**The check**: have you talked to 5+ other domain experts (not just one or
two) about what they prioritize? Do their priorities match yours?

### 3. Domain experts overestimate willingness-to-pay

You know how valuable your time is. You'd pay for a tool that saves it.
Most domain practitioners haven't thought as carefully about their time
value, or have organizational constraints on what they can pay.

"This would save me 5 hours per week, so customers will pay $X" is a common
domain-expert reasoning. The customers themselves often won't.

**The check**: ask 5 prospects the willingness-to-pay question explicitly.
Don't average their answers; look at the lowest one. If 1 of 5 won't pay,
that's 20% of your potential market gone. Build for the median customer,
not the most enthusiastic one.

## The failure mode in code form

```
Day 1:   Domain expert: "I know this space. Customers have pain X."
Day 2:   AI: "Great! Let's build solution Y."
Day 30:  Domain expert: "I'm halfway through Y."
Day 60:  Demo to first prospect. Prospect: "Interesting, but my actual
         pain is Z, not X."
Day 60:  Domain expert: "Z is unsophisticated. Real customers care about X."
Day 90:  Demo to fifth prospect. Same pattern.
Day 120: Domain expert reads earlier customer feedback and realizes Z is
         what people are actually saying. X is what THEY care about.
```

The trap isn't the domain knowledge. It's letting domain knowledge
substitute for customer validation.

## What domain knowledge IS good for

- Recognizing what's possible in your space (saves you from building the
  impossible)
- Spotting solutions that have been tried before (saves you from
  recreating known failures)
- Identifying technical risk (saves you from underestimating complexity)
- Translating customer language to technical requirements (efficient
  communication)
- Knowing the regulatory / market / competitive landscape

These are real advantages. Don't dismiss them.

## What domain knowledge is NOT good for

- Predicting which specific customer pain is most common
- Estimating willingness-to-pay
- Designing UX for non-experts
- Anticipating customer adoption patterns
- Predicting how competitors will respond

These require evidence from the actual market, not expertise.

## How to use domain knowledge correctly

1. **Use it to identify the customer profile, not the customer pain.**
   "I know this market has senior practitioners who do X" is the right
   level. "I know they want feature Y" is overreach.

2. **Use it to ask better questions, not to assume answers.** Domain
   experts can run customer-validation conversations more efficiently
   because they understand the language and context. They don't replace
   the conversations.

3. **Use it adversarially against your own ideas.** Apply your domain
   expertise to argue why your idea won't work. The same expertise that
   suggests something will work can argue why it won't, if asked.

4. **Validate explicitly even when "obvious."** The cost of a 5-prospect
   call is small. The cost of building the wrong thing is large. The
   asymmetry favors validation even when you're confident.

## When domain experts succeed

Specifically: domain experts who succeed in starting businesses tend to
share patterns:
- They validated WITH other experts in their domain (not just believed
  their own intuition)
- They built for a specific customer profile they understood deeply, not
  "the market"
- They priced based on customer willingness-to-pay, not their own
  intuition about value
- They were comfortable killing initial ideas based on customer feedback,
  even when the feedback contradicted their expertise

The pattern is using domain knowledge as a starting point, not as a
substitute for validation.

## Honest acknowledgment

This document doesn't say domain knowledge is bad. It's an asset. The trap
is conflating "I know this space" with "I know what to build for this
space." The first is information; the second is a decision that requires
evidence beyond your own expertise.
