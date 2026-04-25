# HALT Triggers

A reference of standard situations that should cause work to stop and
surface to the reviewer (or human director). Halt is not failure. Halt is
the system working correctly.

## Universal HALT triggers

These apply to all pair-coding rounds regardless of project context.

### Scope expansion
- Editing files outside the approved scope
- Adding tests, fixes, or cleanups not requested
- Bundling investigation findings with action

### Findings that change the picture
- A divergence so obvious that "fix this immediately" looks compelling —
  surface for review, do not fix inline
- Empirical result contradicts a pre-scope assumption
- Numerical computation diverges from documented formula
- Test coverage gap that suggests previous tests were inadequate

### Process violations
- Tests fail in unexpected places
- Freeze-check fails
- About to run a destructive operation (UPDATE on prod tables, DELETE,
  rm -rf, force push, etc.)
- About to modify a frozen surface (per STATUS.md)
- Missing instruction or ambiguous reviewer direction

### Tooling issues
- A required dependency is missing (library, tool, environment variable)
- A required service is unavailable (DB, API, MCP server)
- An unexpected version mismatch

## Project-specific HALT triggers

Define these per-project. Add to a project-specific overlay (or extend this
file in the project's repo) as the project surfaces them.

Example patterns to consider:
- Synthetic-data substitution detected in scoring/metric/loss path → STOP
- Calibration verdict shifts from PASS to FAIL → STOP
- Live-trading or production-deploy flag change attempted without explicit
  override → STOP
- Customer-facing API contract change → STOP

## What to do when triggered

1. Stop the current work immediately. Do not "just finish this small
   thing first."
2. Do not silently fix or work around. The trigger fired for a reason.
3. Surface to the reviewer with:
   - What the trigger was
   - What state you stopped at
   - What you would have done if you'd continued
   - Any partial work in progress
4. Wait for direction. The reviewer decides whether to proceed, fix, or
   change scope.

## What NOT to do when triggered

- Do not interpret the trigger as "minor" because the implementer thinks
  it's minor. Triggers exist BECAUSE in-the-moment judgment is unreliable.
- Do not fix and surface. The order matters: surface first, fix only after
  reviewer approval.
- Do not skip the surface step "to save time." The cost of a missed HALT
  is much higher than the cost of pausing.

## Common temptations to resist

| Temptation | Why to resist |
|---|---|
| "It's a one-line fix" | Bundling means the reviewer can't catch the issue |
| "I'll surface but keep going" | Defeats the purpose of HALT |
| "This trigger doesn't quite apply" | Triggers fire conservatively; respect them |
| "The reviewer would obviously approve this" | If obvious, the round-trip is fast |
| "We're behind schedule" | Schedule pressure is when discipline matters most |

## When triggers misfire

Sometimes a HALT trigger fires for something that isn't actually a problem.
That's fine. The cost of a false-positive HALT (one extra reviewer round
trip) is much smaller than the cost of a false-negative (a real issue
shipped silently).

If a specific trigger fires often without finding real issues, refine the
trigger. Don't ignore it.
