---
name: init-supervisor
description: Use when asked to initialize as SUPERVISOR, start a supervisor session, or resume supervision. Reads framework docs, assesses project state, and presents a situational briefing.
---

# Initialize as Supervisor

Bootstrap or resume a Supervisor session by loading the framework, reading project state, and presenting an actionable briefing.

## When to Use

- User says "initialize as supervisor", "start as supervisor", "resume supervision"
- Beginning of a new chat session on a project that has `docs/SUPERVISOR/`
- Returning to a project after a break

## The Process

### Step 1: Detect Project State

Check whether the Supervisor framework is already initialized:

```
Does docs/SUPERVISOR/SUPERVISOR-FRAMEWORK.md exist?
  YES → This is a re-initialization (go to Step 2)
  NO  → This is a fresh project (go to Step 3)
```

### Step 2: Re-initialize (Existing Framework)

Read these documents in order:

1. `docs/SUPERVISOR/SUPERVISOR-FRAMEWORK.md` — your role and protocols
2. `docs/SUPERVISOR/CURRENT-STATUS.md` — where the project stands
3. `docs/SUPERVISOR/DELEGATION-TRACKER.md` — what's in progress
4. `docs/SUPERVISOR/THINKING-LOG.md` (last 2-3 entries) — recent strategic decisions
5. `docs/SUPERVISOR/DECISIONS-LOG.md` (last 2-3 entries) — recent technical decisions
6. `CHANGELOG.md` — what changed recently

Then present the briefing (Step 4).

### Step 3: Fresh Initialization

The framework needs to be set up first. Read `INSTALLATION.md` from the framework source and follow its complete step-by-step process:

1. Gather project information (name, type, tech stack, commands)
2. Create `docs/SUPERVISOR/` with all framework documents
3. Generate AI IDE configuration files
4. Install methodology skills into `.cursor/skills/`
5. Create `.cursor/rules/superpowers-methodology.md`
6. Customize templates with project-specific information
7. Initialize status documents

After installation completes, proceed to Step 4.

### Step 4: Present Briefing

Respond with a situational briefing:

```
## Supervisor Initialized

**Project**: [name from CURRENT-STATUS or project root]
**Health**: [score from CURRENT-STATUS, or "Just initialized" for fresh projects]

### Current State
- [2-3 bullet summary of where things stand]
- [Active delegations count, or "No active delegations"]
- [Any blockers or urgent items]

### Recent Activity
- [Last 1-2 changes from CHANGELOG, or "Framework just initialized"]

### Available Methodology Skills
[List installed skills from .cursor/skills/, or note if not yet installed]

### Suggested Focus
[What seems most important to work on, based on status and user context]

Ready to supervise. What would you like to focus on?
```

## Key Rules

- **Always read CURRENT-STATUS.md** — never start supervising from memory or assumptions
- **Always read DELEGATION-TRACKER.md** — you need to know what's in flight
- **Don't skip the briefing** — the user needs to see your understanding to correct it
- **For fresh projects, follow INSTALLATION.md completely** — don't shortcut the setup
- **Mention methodology skills** — remind the user (and yourself) what workflows are available
