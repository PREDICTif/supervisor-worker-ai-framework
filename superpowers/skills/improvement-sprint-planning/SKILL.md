---
name: improvement-sprint-planning
description: Diagnose metric gaps in an existing ML or analytics project, design an ordered improvement strategy, write a TDD implementation plan, create self-contained worker prompts, and dispatch workers sequentially with spec and code quality review. Use when a project has a working baseline but needs accuracy or quality improvement, when the user asks to improve model performance, push metrics higher, or plan an improvement sprint.
---

# Improvement Sprint Planning

Turn a metric gap into a dispatched, reviewed, improvement sprint.

## When to Use

- Working baseline exists but accuracy / quality metric is low
- You understand the root causes well enough to prioritize fixes
- Improvements are additive (new files + new functions in shared files)
- You want to execute the improvements without the user driving each step

## The Process

```
Diagnose → Spec → Plan → Worker Prompts → Sequential Dispatch + Review → Verify
```

### 1. Diagnose root causes

Read the current metric artifact (e.g. `artifacts/model_comparison.csv`). Identify at least 3 distinct structural causes for the gap. Order them by expected impact.

Common causes for forecasting accuracy gaps:
- **Long-tail noise**: evaluating all items including rarely-ordered ones
- **Single global calibration**: one multiplier cannot capture day/item variation
- **No external signals**: model only sees order history (no weather, holidays)
- **Outlier contamination**: closures and spikes poison rolling averages
- **Wrong model family**: linear model on a non-linear target

### 2. Write the spec

Save to `docs/superpowers/specs/YYYY-MM-DD-<feature>-improvement.md`.

Required sections:
- **Current state table**: metrics for all existing models
- **Root cause analysis**: one paragraph per cause
- **Improvement strategy**: improvements ordered by expected impact, each with a "Benefits:" list
- **Constraints**: what must not break (tests, payload contract, UI)
- **Success criteria**: measurable targets (e.g. `global_accuracy_pct > 35%`)

### 3. Write the plan

Save to `docs/superpowers/plans/YYYY-MM-DD-<feature>-improvement.md`.

Follow `superpowers:writing-plans` format. Key addition for improvement sprints:

- Each chunk = one independent improvement
- Note shared files that multiple chunks touch (these force sequential execution)
- Add a **Worker Delegation Order** section at the end showing the dependency graph

**Shared-file rule**: If two chunks both modify the same file (e.g. `models_classical.py`), they **must run sequentially**, not in parallel.

### 4. Write worker prompts

Save to `docs/SUPERVISOR/prompts/YYYY-MM-DD-<feature>-worker-prompts.md`.

One prompt per chunk. Each prompt must include:
- **Current Status**: what exists, what the metrics are
- **What You Are Doing**: one sentence
- **Files to Create or Modify**: exact paths
- **Your Task**: numbered steps with code examples
- **Technical Requirements**: constraints (no future leakage, TDD, must not break existing tests)
- **Success Criteria**: checkboxes
- **Errors or Blockers to Watch**

### 5. Dispatch workers sequentially

Use `superpowers:subagent-driven-development`. Each worker gets:

```markdown
# CONTEXT
Project: [name] — [one sentence description]
Working directory: [absolute path]
Test command: [exact command]
Current test count: [N] passing
Current best metric: [value]

# EXISTING CODE RELEVANT TO THIS TASK
[paste key existing function signatures and imports, not full files]

# YOUR TASK
[full chunk text from the plan, including all code examples]

# CONSTRAINTS
- All existing tests must continue to pass
- Use TDD: write failing test first, then implement
- Do not modify files outside the scope of this task
- Report status as DONE, DONE_WITH_CONCERNS, NEEDS_CONTEXT, or BLOCKED
```

After each worker: dispatch spec compliance reviewer, then code quality reviewer. Fix before proceeding.

### 6. Verify

After all chunks complete, dispatch a final verification worker:

```markdown
Run:
1. [backtest command] to regenerate the comparison artifact
2. [test command] — confirm all tests pass
3. Check that the target metric improved

Report:
- New metric values for all models
- Whether success criteria were met
- Any regressions or unexpected results
```

## Dependency Graph Pattern

Most improvement sprints have this shape:

```
Improvement A ──┐
Improvement B ──┼── sequential (shared files) ──> Integration model ──> Verify
Improvement C ──┘
```

Even when improvements are conceptually independent, shared file writes force sequential execution. Run them one at a time in order of expected impact so early wins are locked in before later, riskier improvements.

## Key Principles

- **Additive only**: new files + new functions, never rewrite existing working code
- **TDD throughout**: every new function has a failing test first
- **Backward-compatible artifacts**: new columns in CSVs, new keys in payload dicts
- **Graceful degradation**: optional dependencies (e.g. API calls, new packages) must fail cleanly without crashing the existing stack
- **Document findings**: if an improvement does not help, note it explicitly — knowing what doesn't work is valuable

## Update Tracking Docs

After all workers complete, update:
- `CHANGELOG.md` — additive entry per improvement
- `docs/SUPERVISOR/CURRENT-STATUS.md` — new default model and metrics
- `docs/SUPERVISOR/DECISIONS-LOG.md` — new ADR for the winning approach
- `docs/SUPERVISOR/DELEGATION-TRACKER.md` — mark workers complete

## Additional Resources

- For writing the plan document: `superpowers:writing-plans`
- For dispatching workers: `superpowers:subagent-driven-development`
- For parallel-safe work: `superpowers:dispatching-parallel-agents` (only when no shared files)
- For TDD guidance: `superpowers:test-driven-development`
