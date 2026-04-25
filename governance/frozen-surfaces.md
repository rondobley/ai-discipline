# Frozen Surfaces

What this is: the list of things in your codebase or product that should
NEVER change without explicit approval. Created on day one of the project,
maintained throughout.

Without this, your codebase silently rewrites itself across months. With it,
you have a contract with future-you.

## Template for STATUS.md

The consuming project creates a STATUS.md at its repo root. Here's the
shape:

  # Status — Frozen Surfaces

  This document lists code, configuration, and product surfaces that may
  not be changed without explicit PLAN-OVERRIDE approval. Changes to these
  surfaces require:

  1. Explicit reasoning in a commit message body
  2. The token PLAN-OVERRIDE in the commit message
  3. Update to this document with the new value + change date + change
     reason

  ## Public API

  - Endpoint URLs (versioned; never break v1 once shipped)
  - Request/response schemas (v1 frozen)
  - Authentication method
  - Rate-limit behavior

  ## Database schema

  - User-facing entities (users, accounts, subscriptions)
  - Multi-tenancy boundary
  - Audit log shape

  ## Auth and permissions

  - User roles
  - Permission scopes
  - Session model

  ## Pricing and billing

  - Pricing tiers and feature gates
  - Billing integration choice
  - Refund policy

  ## Privacy boundaries

  - What goes in logs (no PII)
  - What goes in telemetry (aggregated only)
  - What goes in analytics (consent-gated)
  - Data retention rules

  ## Project-specific

  [Add as you go]

## How to use

1. Day 1: create STATUS.md with all sections, populated with whatever
   defaults you've chosen
2. Add a CI check (`tools/check_frozen_surfaces.sh` or equivalent) that:
   - Parses STATUS.md
   - Checks declared surfaces match code
   - Fails if mismatch and no PLAN-OVERRIDE token in the commit
3. Update STATUS.md whenever you intentionally change a frozen surface
4. Review STATUS.md at every premise re-check

## What frozen surfaces are not

- A bureaucracy
- A way to prevent change
- A list of everything in the code

They are the things that are EXPENSIVE to change, where silent change
breaks customers or breaks future-you. Be selective. 10-20 surfaces is
about right; 100+ surfaces means you're frozen for the wrong things.

## When to add a frozen surface

- After a customer integration depends on it
- After a security review pins it
- After a "we should have caught that" bug from a silent change
- After any decision you don't want to revisit casually

## When to remove one

- After enough time has passed that change is genuinely safe
- After a deliberate review concludes the surface no longer matters
- Never silently
