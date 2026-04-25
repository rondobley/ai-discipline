# How to Use This Repo

Operational walkthrough for using ai-discipline with Claude.ai + Claude Code.
If you've never used this repo before, start here.

This is the practical companion to the strategic playbooks. The playbooks
tell you WHAT to do; this tells you exactly HOW to do it in your tools.

## Tool stack

The three roles map to different tools:

| Role | Tool | Why |
|---|---|---|
| Research agent | Claude.ai (Project) | Web UI; no filesystem needed; persistent context per project; easy to revisit |
| Reviewer | Claude.ai (Project) | Web UI; long conversations; the role you "live in" during a project |
| Implementer | Claude Code (CLI) | Filesystem access; runs tests; makes commits; operates in the project repo |

You are the human bridge between these. When the reviewer drafts a prompt
for the implementer, you paste it from one chat to another. Same for
implementer responses going back to the reviewer.

This is exactly the setup we used to build this repo: claude.ai as
reviewer, Claude Code as implementer, you as the bridge.

## One-time setup

Do this once. The Projects you create are reusable across all your
ai-discipline-managed projects.

### Step 1: Create the Research Agent Project in Claude.ai

1. Open claude.ai
2. Click "New Project" (left sidebar)
3. Name: `AI Discipline — Research Agent`
4. Description (optional): `Adversarial premise stress-test before any building. Use before starting a new project or evaluating a major pivot.`
5. Project instructions (the system prompt): paste the entire contents of `templates/research-agent.md`
6. Click "Create"

### Step 2: Create the Reviewer Project in Claude.ai

1. Click "New Project" again
2. Name: `AI Discipline — Reviewer`
3. Description: `Pair-coding reviewer; directs the implementer; holds standards`
4. Project instructions: paste the entire contents of `templates/reviewer.md`
5. Click "Create"

### Step 3: Set up Claude Code locally

1. Install Claude Code if you haven't (per claude-code installation docs)
2. Authenticate (`claude login` or per the setup flow)
3. No global setup needed — implementer template gets installed per-project

### Step 4 (per new project): install implementer instructions

When you start a new project repo, paste `templates/implementer.md` content
into a `CLAUDE.md` file at the repo root. Claude Code reads this on every
session start in that directory.

```bash
cd ~/projects/your-new-project
# create CLAUDE.md with templates/implementer.md content
```

That's it for setup. Now to use it.

## Sensitive data

Standard caveat that applies to any AI tool: don't paste secrets, credentials,
API keys, customer PII, payment data, medical records, legal documents, HR
records, or proprietary client data into AI sessions.

The multi-session workflow here doesn't change AI safety properties, but
moving content between sessions (research agent → reviewer → implementer)
creates more opportunities for accidental exposure than a single-prompt
interaction. Redact before you paste. If uncertain whether something should
be shared, don't share it.

## Day 1: starting a new project

Walkthrough of the first hour or two of a new project.

### 1. You have an idea

Write it down in a paragraph. Be specific. Include:
- What it does
- Who pays for it
- Why they'd choose this over alternatives
- What edge you have (don't skip this — see `lessons/domain-knowledge-trap.md`)

### 2. Open the Research Agent

In claude.ai:
1. Click the `AI Discipline — Research Agent` project
2. Click "New chat" within the project
3. Paste your idea paragraph
4. Send

Wait for the report. Read it carefully. Don't skim.

### 3. Decide based on the report's verdict

Three possible outcomes:

- **"Kill this idea now"**: stop. Don't proceed. Save the chat for reference.
- **"Run the kill-test in section 7 first"**: do that experiment before any building. Often involves customer conversations (see `playbooks/customer-validation.md`).
- **"Idea passes initial stress-test; risks to monitor"**: log the risks, proceed.

Do NOT default to "proceed" because the report sounds reasonable. Most
ideas should land at kill or run-kill-test.

### 4. If proceeding: open the Reviewer Project

In claude.ai:
1. Click the `AI Discipline — Reviewer` project
2. Click "New chat" within the project
3. Brief the reviewer with this template:

   > **Project**: [name]
   >
   > **Description**: [one paragraph]
   >
   > **Research agent findings**: [paste the verdict + 3-5 key risks]
   >
   > **My specific edge / unique advantage**: [your edge claim]
   >
   > **Customer validation status**: [done with N=X / not yet started / planned for next week]
   >
   > **What I want to do today**: [first concrete goal — usually "set up the repo" or "scope the first feature"]

The reviewer responds with a Stage 1 pre-scope prompt for the implementer.

### 5. Open Claude Code locally

In your terminal:

```bash
cd ~/projects
mkdir my-new-project
cd my-new-project
# Create CLAUDE.md with templates/implementer.md content
claude
```

In the Claude Code session, paste the reviewer's Stage 1 prompt. The
implementer responds with pre-scope answers.

### 6. Bridge back to the reviewer

Copy the implementer's response. Paste it into the Reviewer chat.

The reviewer reviews, then drafts the Stage 2 prompt (design preview).

### 7. Iterate per cadence

Continue: Stage 2 design preview → Stage 3 implementation → Stage 4 commit.
For each stage, copy from one chat to the other.

This is exactly the rhythm we used to build this repo.

## Mid-project mechanics

After Day 1, the cadence stabilizes:

- **Reviewer chat**: one chat per major stretch of work. Use the same chat
  for several rounds of pair-coding so context accumulates. Start a new
  chat when context gets long (>40-50 turns) or when shifting to a new
  feature.

- **Implementer chat**: one chat per Stage 3 implementation cycle. New
  task, new chat. This keeps context clean and makes it easier to recover
  if something goes wrong.

- **Research agent**: revisit when:
  - Major architecture decision (pre-scope it adversarially)
  - Premise re-check (every 2-4 weeks; see `playbooks/premise-recheck.md`)
  - Considering a pivot
  - A feature feels unsure

## The cadence in practice

What each stage actually looks like in your tools:

### Stage 1 — Pre-scope
- Reviewer drafts a prompt with explicit questions
- You paste to Claude Code (implementer)
- Implementer answers with confidence labels (Verified/Likely/Open/Speculation)
- You paste back to Reviewer

### Stage 2 — Design preview
- Reviewer approves or revises pre-scope answers
- Reviewer drafts a Stage 2 prompt (design proposal request)
- You paste to implementer
- Implementer proposes function signatures, test plan, commit split
- You paste back to Reviewer

### Stage 3 — Implementation
- Reviewer approves the design
- Reviewer drafts a Stage 3 prompt (implementation instructions)
- You paste to implementer
- Implementer writes code, runs tests, shows diff
- **Implementer does not commit yet**
- You paste the diff back to Reviewer

### Stage 4 — Commit
- Reviewer reviews the diff
- If clean: drafts approval (e.g., "Commit using the drafted message")
- You paste to implementer
- Implementer commits and reports SHA
- You paste back to Reviewer for confirmation

### After commit
- Reviewer confirms and queues the next task
- Back to Stage 1 of the next round

## When to spawn a new agent vs continue existing one

| Scenario | What to do |
|---|---|
| New project, same Claude.ai account | New chats inside existing Research Agent + Reviewer projects |
| New feature within current project | New chat in Reviewer project; brief with context; new Claude Code chat |
| Premise re-check during current project | New chat in Research Agent project; brief with current state |
| Recovering from a long context window | Start fresh chat; brief with summary; lose nothing critical |
| Switching projects entirely | Close current Reviewer chat; new chat with new project's brief |

You don't need to "log out and back in." Each chat is a fresh session
within a project. The Project's instructions stay the same.

## Common pitfalls

### Mixing roles
**Symptom**: asking the research agent to also help implement, or the
reviewer to also do the customer research.
**Fix**: each role has one job. If you need a different mode, switch
projects.

### Skipping research because "obvious"
**Symptom**: "I know this idea is good; I'll skip step 2."
**Fix**: run it anyway. The discipline is the discipline. Cost is 30
minutes; value is catching what you missed.

### Reviewer drifting to yes-man
**Symptom**: the reviewer agrees with everything you propose. No pushback.
**Fix**: prompt explicitly. "Push back on this. What's the strongest case
against?" If still soft, start a new chat with more aggressive briefing.

### Implementer scope creep
**Symptom**: implementer adds files you didn't approve, fixes things you
didn't ask.
**Fix**: catch in diff review. The reviewer's job is to spot this. Push
back: "I see you also touched X; that wasn't in scope. Revert that part."

### Templates as theater
**Symptom**: you fill out the customer-validation playbook with imaginary
customers, or run the research agent and accept whatever it says.
**Fix**: the templates only work when exercised honestly. The discipline
is yours; the templates encode it but don't enforce it.

### Long context degrades quality
**Symptom**: after 100+ turns in one chat, the reviewer starts drifting,
forgetting earlier decisions.
**Fix**: start a new chat. Brief with a summary of where you are. The
Project instructions persist; the conversation context resets.

## How to know it's working

Signs you're holding the discipline:

- The research agent has killed at least one idea you were excited about
- The reviewer regularly pushes back on you (not just the implementer)
- You've run a premise re-check and changed direction at least once
- Customer validation has revealed something you didn't already know
- You've experienced "the data says I'm wrong" and acted on it
- Pair-coding rounds occasionally HALT and the issue is real

Signs the discipline has become theater:

- The research agent always says proceed
- The reviewer agrees with everything
- The implementer never halts
- You haven't had a customer conversation in over 4 weeks
- You can't remember the last time a template caught a real issue

If theater: pause. Re-read `lessons/ai-defaults-to-yes.md`. Run a premise
re-check. Reset the discipline.

## When to update the templates

Refine the templates in this repo when:

- A specific HALT trigger keeps misfiring or missing real issues
- A playbook's "When to use" criteria didn't match a real situation
- A new failure mode emerges that no template covers
- After closing a project and writing the post-mortem

Update via the same pair-coding cadence. Templates aren't sacred; they're
living documents.
