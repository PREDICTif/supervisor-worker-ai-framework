# Superpowers Methodology Skills

This project uses the Supervisor-Worker AI Framework with methodology skills adapted from [Superpowers](https://github.com/obra/superpowers). These skills provide proven workflows for planning, implementation, debugging, and review.

## Available Skills

The following methodology skills are installed at `.cursor/skills/` and are automatically available to the AI assistant:

| Skill | When to Use |
|-------|-------------|
| `brainstorming` | Before planning or designing — think before coding |
| `writing-plans` | When creating structured implementation plans |
| `executing-plans` | When executing plans across multiple sessions |
| `subagent-driven-development` | When executing plans with subagents in the current session |
| `test-driven-development` | When implementing any feature or bugfix — write tests first |
| `systematic-debugging` | When investigating bugs — trace root causes methodically |
| `requesting-code-review` | When reviewing code changes before merging |
| `verification-before-completion` | Before marking any task as done |
| `finishing-a-development-branch` | When completing work on a development branch |
| `dispatching-parallel-agents` | When coordinating multiple parallel work streams |

## Skill Priority

When multiple skills could apply, use this order:

1. **Process skills first** — these determine HOW to approach the task:
   - `brainstorming` (before any planning)
   - `systematic-debugging` (before any bug investigation)
   - `writing-plans` (before any implementation)

2. **Implementation skills second** — these guide execution:
   - `test-driven-development` (during implementation)
   - `subagent-driven-development` or `executing-plans` (during plan execution)
   - `dispatching-parallel-agents` (when parallelizing)

3. **Completion skills last** — these ensure quality:
   - `requesting-code-review` (after implementation)
   - `verification-before-completion` (before marking done)
   - `finishing-a-development-branch` (when wrapping up a branch)

## Mapping Supervisor Activities to Skills

| Supervisor Activity | Use These Skills |
|---|---|
| Planning new work | `brainstorming` → `writing-plans` |
| Executing a plan | `subagent-driven-development` or `executing-plans` |
| Implementing features | `test-driven-development` |
| Debugging issues | `systematic-debugging` |
| Reviewing completed work | `requesting-code-review` |
| Validating before completion | `verification-before-completion` |
| Finishing a branch | `finishing-a-development-branch` |
| Parallelizing tasks | `dispatching-parallel-agents` |

## Integration with Supervisor Framework

These skills complement the Supervisor-Worker Framework documents in `docs/SUPERVISOR/`. The framework handles **what** to do (roles, delegation, tracking), while these skills handle **how** to do it (methodology, discipline, quality).

- **SUPERVISOR-FRAMEWORK.md** — defines roles and coordination
- **Methodology skills** — define execution workflows
- **BEST-PRACTICES.md** — provides patterns and anti-patterns

When initialized as SUPERVISOR or WORKER, read the framework docs first, then apply relevant methodology skills during execution.
