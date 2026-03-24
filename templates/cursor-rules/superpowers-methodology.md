# Superpowers Methodology Skills

This project uses the Supervisor-Worker AI Framework with methodology skills adapted from [Superpowers](https://github.com/obra/superpowers). These skills provide proven workflows for planning, implementation, debugging, and review.

## Available Skills

The following methodology skills are installed at `.cursor/skills/` and are automatically available to the AI assistant:

| Skill | When to Use |
|-------|-------------|
| `init-supervisor` | When asked to initialize, start, or resume as Supervisor |
| `brainstorming` | Before planning or designing — think before coding |
| `writing-plans` | When creating structured implementation plans |
| `test-driven-development` | When implementing any feature or bugfix — write tests first |
| `systematic-debugging` | When investigating bugs — trace root causes methodically |
| `requesting-code-review` | When reviewing code changes before merging |
| `verification-before-completion` | Before marking any task as done |

## Skill Priority

When multiple skills could apply, use this order:

1. **Bootstrap skill** — run first when starting a session:
   - `init-supervisor` (when initializing or resuming as Supervisor)

2. **Process skills** — these determine HOW to approach the task:
   - `brainstorming` (before any planning or design)
   - `systematic-debugging` (before any bug investigation)
   - `writing-plans` (before any implementation)

3. **Implementation skills** — these guide execution:
   - `test-driven-development` (during implementation)

4. **Completion skills last** — these ensure quality:
   - `requesting-code-review` (after implementation)
   - `verification-before-completion` (before marking done)

## Mapping Supervisor Activities to Skills

| Supervisor Activity | Use These Skills |
|---|---|
| Starting or resuming a session | `init-supervisor` |
| Planning new work | `brainstorming` → `writing-plans` |
| Implementing features | `test-driven-development` |
| Debugging issues | `systematic-debugging` |
| Reviewing completed work | `requesting-code-review` |
| Validating before completion | `verification-before-completion` |

## Integration with Supervisor Framework

These skills complement the Supervisor-Worker Framework documents in `docs/SUPERVISOR/`. The framework handles **what** to do (roles, delegation, tracking), while these skills handle **how** to do it (methodology, discipline, quality).

- **SUPERVISOR-FRAMEWORK.md** — defines roles and coordination
- **Methodology skills** — define execution workflows
- **BEST-PRACTICES.md** — provides patterns and anti-patterns

When initialized as SUPERVISOR or WORKER, read the framework docs first, then apply relevant methodology skills during execution.
