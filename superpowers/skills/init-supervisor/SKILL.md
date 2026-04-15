---
name: init-supervisor
description: Use when asked to initialize as SUPERVISOR, start a supervisor session, or resume supervision. Reads framework docs, assesses project state, and presents a situational briefing.
---

# Initialize as Supervisor

Bootstrap, resume, or repair a Supervisor session by reconciling the framework install, reading project state, and presenting an actionable briefing.

## When to Use

- User says "initialize as supervisor", "start as supervisor", "resume supervision"
- User asks to re-initialize or refresh the Supervisor framework in an existing project
- Beginning of a new chat session on a project that has `docs/SUPERVISOR/`
- Returning to a project after a break

## The Process

### Step 1: Detect Project State

Check whether the Supervisor framework is already initialized:

```text
Does docs/SUPERVISOR/SUPERVISOR-FRAMEWORK.md exist?
  YES → This is a re-initialization (go to Step 2)
  NO  → This is a fresh project (go to Step 3)
```

### Step 2: Re-initialize or Upgrade (Existing Framework)

Before reading project state, reconcile the installed framework assets:

1. Ensure `.cursor/skills/` exists
2. Ensure these project-level skills exist and are up to date:
   - `init-supervisor`
   - `brainstorming`
   - `writing-plans`
   - `test-driven-development`
   - `systematic-debugging`
   - `requesting-code-review`
   - `verification-before-completion`
3. If any of those skills are missing or outdated, copy/update them from the framework source using the file list in `INSTALLATION.md`
4. Ensure `.cursor/rules/superpowers-methodology.md` exists and refresh it from the framework template if it is missing or outdated

Then read these documents in order:

1. `docs/SUPERVISOR/SUPERVISOR-FRAMEWORK.md` — your role and protocols
2. `docs/SUPERVISOR/CURRENT-STATUS.md` — where the project stands
3. `docs/SUPERVISOR/DELEGATION-TRACKER.md` — what's in progress
4. `docs/SUPERVISOR/THINKING-LOG.md` (last 2-3 entries) — recent strategic decisions
5. `docs/SUPERVISOR/DECISIONS-LOG.md` (last 2-3 entries) — recent technical decisions
6. `CHANGELOG.md` — what changed recently

Then present the briefing (Step 4).

### Step 3: Fresh Initialization

The framework needs to be set up first. Read `INSTALLATION.md` from the framework source and follow its complete step-by-step process.

**Empty folder?** `INSTALLATION.md` Step 0.5 will detect if the project folder is empty (no source files, `package.json`, `README.md`, etc.). If it is, the user is asked to choose a project type — study project, development project, or content writing project — and the matching scaffolding template from `templates/project-types/` is used to create real project files before the framework setup continues. This means the framework is never initialized over a truly blank slate.

Full installation steps:

1. Detect empty project and scaffold if needed (Step 0.5)
2. Gather project information (name, type, tech stack, commands)
3. Create `docs/SUPERVISOR/` with all framework documents
4. Generate AI IDE configuration files
5. Install methodology skills into `.cursor/skills/`
6. Create `.cursor/rules/superpowers-methodology.md`
7. Customize templates with project-specific information
8. Initialize status documents

After installation completes, proceed to Step 4.

### Step 4: Present Briefing

Respond with a situational briefing:

```markdown
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

- **Always reconcile skills and bridge rule on re-init** — don't assume an older install already has the latest skill set
- **Always read CURRENT-STATUS.md** — never start supervising from memory or assumptions
- **Always read DELEGATION-TRACKER.md** — you need to know what's in flight
- **Don't skip the briefing** — the user needs to see your understanding to correct it
- **For fresh projects, follow INSTALLATION.md completely** — don't shortcut the setup
- **Mention methodology skills** — remind the user (and yourself) what workflows are available
