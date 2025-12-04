# CLAUDE.md Template
# AI Assistant Instructions for {{PROJECT_NAME}}

> **Note**: This file provides instructions to AI coding assistants (Claude, GPT, etc.) about this project. It's automatically read by compatible AI IDEs.

## Project Overview

**Project Name**: {{PROJECT_NAME}}  
**Type**: {{PROJECT_TYPE}}  
**Description**: {{PROJECT_DESCRIPTION}}

## Technology Stack

{{TECH_STACK_LIST}}

## Project Structure

```
{{PROJECT_STRUCTURE}}
```

## AI Framework Integration

This project uses the **Supervisor-Worker AI Framework** for structured AI-assisted development.

### Framework Location
- Framework docs: `docs/SUPERVISOR/`
- Current status: `docs/SUPERVISOR/CURRENT-STATUS.md`
- Task tracker: `docs/SUPERVISOR/DELEGATION-TRACKER.md`

### Role Initialization

**To work as SUPERVISOR** (planning, delegating, validating):
```
Read docs/SUPERVISOR/SUPERVISOR-FRAMEWORK.md and initialize as SUPERVISOR
```

**To work as WORKER** (executing specific tasks):
```
Read docs/SUPERVISOR/WORKER-FRAMEWORK.md and initialize as WORKER
```

## Coding Standards

### General Rules
- Follow existing code patterns and conventions
- Keep functions small and focused
- Write self-documenting code with clear naming
- Add comments only where logic is complex

### File Organization
{{FILE_ORGANIZATION_RULES}}

### Naming Conventions
{{NAMING_CONVENTIONS}}

## Important Files

| File | Purpose |
|------|---------|
| {{IMPORTANT_FILE_1}} | {{DESCRIPTION_1}} |
| {{IMPORTANT_FILE_2}} | {{DESCRIPTION_2}} |

## Commands

```bash
# Development
{{DEV_COMMAND}}

# Testing
{{TEST_COMMAND}}

# Build
{{BUILD_COMMAND}}
```

## What NOT to Do

- Don't modify {{PROTECTED_FILES}}
- Don't introduce new dependencies without discussion
- Don't change architecture without updating DECISIONS-LOG
- Don't skip updating CHANGELOG after changes

## Session Workflow

1. **Start**: Read `docs/SUPERVISOR/CURRENT-STATUS.md` for context
2. **During**: Follow framework protocols for your role
3. **End**: Update relevant docs, create handover if needed

---

**Last Updated**: {{CURRENT_DATE}}  
**Framework Version**: 1.1.0

