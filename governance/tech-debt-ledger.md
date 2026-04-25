# Tech Debt Ledger

What this is: the explicit list of "we'll fix it later" decisions you've
made. Created day one, maintained throughout.

Without this, your tech debt is invisible until it's overwhelming. With it,
you have a continuous signal of how much you've borrowed against future-you.

## Template for TECHDEBT.md

The consuming project creates a TECHDEBT.md at its repo root. Here's the
shape:

  # Tech Debt Ledger

  Each entry: what was hacked, why, when to revisit, cost estimates.

  ## Format

  ### [DATE] Title

  **What**: One-line description of the hack.
  **Why**: What we shipped first that made this acceptable.
  **When**: Specific date or trigger to revisit.
  **Cost-of-leaving**: Estimate (cents per request? engineer-hours per
    incident? customer churn? security risk?).
  **Cost-of-fixing**: Estimate (engineer-days).
  **Fixed**: [date] in commit [SHA] — when resolved.

  ---

  ### [2026-XX-XX] Hardcoded user ID in audit log

  **What**: AuditLog.user_id is hardcoded to "system" instead of being
    threaded through.
  **Why**: Shipping admin dashboard for first customer; threading was
    2-day work.
  **When**: Before second customer onboards (estimated 4 weeks out).
  **Cost-of-leaving**: Audit logs unreliable for multi-user customers;
    potential compliance issue.
  **Cost-of-fixing**: 2 engineer-days.
  **Fixed**: (open)

## How to use

1. Day 1: create TECHDEBT.md with empty Format section
2. Every "we'll fix it later" gets a new entry IMMEDIATELY when shipped
3. Review at every premise re-check
4. If the file gets longer than 30 items, that's a signal something's wrong
5. If you've ignored it for 3 months, that's a signal to schedule a debt
   sprint

## What goes in here

- Hacks shipped to meet deadlines
- "Good enough for now" decisions
- Workarounds for upstream issues
- Test coverage gaps you noticed but didn't fill
- Documentation that's stale but still "mostly right"
- Performance problems below the threshold-of-pain

## What does NOT go in here

- Bugs (those go in your issue tracker)
- Feature ideas (those go in your roadmap)
- Architectural decisions (those go in STATUS.md or ADRs)
- Things you've fully thought through and decided are correct

## Discipline pattern

The mistake: "we'll fix it later" without writing it down. Without writing
it down, you forget. Then you ship more on top of it, compounding the
forgotten debt.

The fix: writing it down takes 90 seconds. Do it as part of the same
commit that introduces the debt. The commit message should reference the
TECHDEBT.md entry.
