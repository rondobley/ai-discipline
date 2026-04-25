# Post-Mortem

When and how to write a post-mortem. Whether the project succeeded, failed,
or was killed.

## When to write one

- Project killed
- Project pivoted significantly (premise changed)
- Project shipped to production (success retrospective)
- Major incident or outage (incident review)
- Team change or handoff (continuity record)

Don't skip it. The post-mortem is the highest-leverage hour you'll spend on
the project — the lessons you encode now save months later.

## What goes in it

Not a triumph story. Not a tragedy story. A factual record + honest
analysis + transferable lessons.

### Sections

1. **Summary** (1 paragraph)
   - What was built, what was attempted, what happened
   - Bottom-line outcome

2. **Timeline**
   - Key milestones with dates
   - Major decisions and pivots
   - When you knew (or should have known) what

3. **What we built**
   - The actual artifacts and components
   - Reference key commits, files, infrastructure

4. **What we attempted**
   - The strategic intent (what problem, for whom, with what edge)
   - The thesis (why it should have worked)

5. **Why it [worked / failed / pivoted]**
   - The diagnostic narrative
   - Specific evidence (numbers, customer signals, observed patterns)
   - The mechanism (why the outcome happened)

6. **Open items not addressed**
   - For shutdown projects: what's unfinished
   - For shipped projects: what's deferred to v2
   - Anyone returning to the work knows what's open

7. **What's reusable**
   - Code, methodology, lessons
   - Specific to your context vs generally applicable

8. **Lessons** (the highest-leverage section)
   - What you'd do differently
   - What you'd do the same
   - What you genuinely didn't see coming
   - Transferable to other projects

## How to write it honestly

- Don't soft-pedal failures. The point of a post-mortem is the lessons.
  Lessons require honest accounting of what went wrong.
- Don't blame externalities. "Market conditions" is rarely the full story.
- Don't blame yourself excessively. The system you built reflected the
  information you had at the time.
- Verify before claiming. "We learned X" should be backed by specific
  evidence, not generic insight.
- Confidence labels for substantive claims (Verified / Likely / Open /
  Speculation). Same discipline as the reviewer template.

## What to avoid

- "Lessons learned" (cliché phrasing; replaced by specific lessons)
- Generic insights that fit any project
- Self-deprecation as performance
- Triumphalism about what worked
- Skipping the failure modes because they're uncomfortable

## After the post-mortem

- Commit it to the repo (POSTMORTEM.md at root)
- Cross-link from the project's README
- If shutting down: also write a SHUTDOWN.md with the operational record
  (separate from the strategic post-mortem)
- Reference the post-mortem in any subsequent project that's related

## Special case: shutdown post-mortems

When killing a project (not pivoting, not pausing — actually killing):

1. Post-mortem first (strategic record)
2. SHUTDOWN.md second (operational record: what was stopped, what was
   archived, what's still running, reactivation procedure if any)
3. Cancel external subscriptions / dependencies
4. Archive data if needed
5. Final commit acknowledges the closure

The two-file split keeps strategic analysis separate from operational
record. Future readers want different things from each.

## Honest acknowledgment

Most post-mortems are read once when written and never again. That's fine.
The value isn't in re-reading; it's in writing. Writing forces clarity that
having-conclusions-in-your-head doesn't.

If you're tempted to skip writing the post-mortem because "we know what
happened," you don't. Write it.
