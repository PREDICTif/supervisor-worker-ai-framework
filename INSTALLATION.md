# AI Installation Guide

**For AI Assistants**: This document tells you exactly how to initialize the Supervisor-Worker Framework in a new project.

---

## 🎯 When You're Asked to Initialize

When a user says something like:
- "Initialize the supervisor-worker AI framework"
- "Set up the AI supervision framework from [source]"
- "Create the SUPERVISOR structure in my project"

Follow these steps:

---

## 📋 Step-by-Step Installation

### Step 1: Gather Project Information

**IMPORTANT**: Before creating any files, gather this information from the user or by examining the project:

```
To set up the AI Supervisor-Worker Framework, I need:

1. **Project Name**: What is the project called?
2. **Project Type**: What kind of project is this? (web app, API, library, etc.)
3. **Current Phase**: Is this a new project or ongoing? What's the current status?
4. **Documentation Location**: Where should I create the framework? (default: ./docs/SUPERVISOR/)
5. **Key Technologies**: What's the tech stack? (languages, frameworks, databases)
6. **Primary Language**: Main programming language used
7. **Key Commands**: How to run dev server, tests, build?
```

**How to gather this information:**
- Check `package.json`, `requirements.txt`, `Cargo.toml`, etc. for tech stack
- Read existing `README.md` for project description
- Look at directory structure to understand project type
- Ask user for anything not clear from the codebase

### Step 2: Create Directory Structure

Create the following structure:

```
{project_root}/
├── CLAUDE.md                       # AI assistant instructions (generated)
├── context.md                      # Project context for AI (generated)
├── .cursorrules                    # Cursor IDE rules (generated)
├── .windsurfrules                  # Windsurf IDE rules (generated)
├── .cursor/
│   ├── rules/
│   │   └── superpowers-methodology.md  # Methodology bridge rule
│   └── skills/                         # Project-level methodology skills
│       ├── init-supervisor/
│       ├── brainstorming/
│       ├── writing-plans/
│       ├── test-driven-development/
│       ├── systematic-debugging/
│       ├── requesting-code-review/
│       └── verification-before-completion/
└── docs/
    └── SUPERVISOR/
        ├── SUPERVISOR-FRAMEWORK.md # Copy from framework/
        ├── WORKER-FRAMEWORK.md     # Copy from framework/
        ├── BEST-PRACTICES.md       # Copy from framework/
        ├── CURRENT-STATUS.md       # Customize from templates/
        ├── DELEGATION-TRACKER.md   # Customize from templates/
        ├── THINKING-LOG.md         # Initialize
        ├── DECISIONS-LOG.md        # Initialize
        └── SESSION-SUMMARIES/      # Directory for session logs
```

### Step 3: Generate AI IDE Configuration Files

**This step is critical!** Based on the gathered project information, generate these files in the project root:

#### 3.1 Create `CLAUDE.md`

Use the template from `templates/ai-ide-configs/CLAUDE.md` and fill in:
- Project name, type, and description
- Technology stack details
- Directory structure
- Key commands
- Coding standards from existing codebase
- Important files and their purposes

#### 3.2 Create `context.md`

Use the template from `templates/ai-ide-configs/context.md` and fill in:
- Quick project summary
- Architecture overview
- Key concepts specific to the project
- Directory guide
- Current work focus (initially: "Framework just initialized")

#### 3.3 Create `.cursorrules` (for Cursor IDE)

Use the template from `templates/ai-ide-configs/.cursorrules` and fill in:
- Language-specific coding rules
- Project naming conventions
- Import organization preferences
- Preferred patterns from existing code

#### 3.4 Create `.windsurfrules` (for Windsurf IDE)

Use the template from `templates/ai-ide-configs/.windsurfrules` with similar customization.

### Step 3.5: Install Methodology Skills (Cursor IDE)

**This step installs Superpowers methodology skills as project-level Cursor skills.** These skills provide proven workflows for planning, TDD, debugging, code review, and more. They are available immediately in Cursor without any plugin installation or restart.

#### 3.5.1 Create `.cursor/skills/` directory

Create the `.cursor/skills/` directory in the target project root.

#### 3.5.2 Copy skills from vendored source

The framework includes a vendored copy of [Superpowers](https://github.com/obra/superpowers) skills in `superpowers/skills/`. Copy each of the following skills into `.cursor/skills/<skill-name>/`:

| Source (`superpowers/skills/...`) | Target (`.cursor/skills/...`) | Files to Copy |
|---|---|---|
| `init-supervisor/` | `init-supervisor/` | `SKILL.md` |
| `brainstorming/` | `brainstorming/` | `SKILL.md`, `spec-document-reviewer-prompt.md`, `visual-companion.md`, `scripts/*` |
| `writing-plans/` | `writing-plans/` | `SKILL.md`, `plan-document-reviewer-prompt.md` |
| `test-driven-development/` | `test-driven-development/` | `SKILL.md`, `testing-anti-patterns.md` |
| `systematic-debugging/` | `systematic-debugging/` | `SKILL.md`, `root-cause-tracing.md`, `defense-in-depth.md`, `condition-based-waiting.md`, `condition-based-waiting-example.ts`, `find-polluter.sh` |
| `requesting-code-review/` | `requesting-code-review/` | `SKILL.md`, `code-reviewer.md` |
| `verification-before-completion/` | `verification-before-completion/` | `SKILL.md` |

**Do NOT copy** these skills (platform-specific, meta, or redundant with the Supervisor framework):
- `using-superpowers/` (plugin bootstrap — replaced by the bridge rule below)
- `using-git-worktrees/` (orthogonal to the framework)
- `writing-skills/` (meta-skill for creating skills)
- `receiving-code-review/` (Claude Code specific)
- `executing-plans/` (redundant with WORKER-FRAMEWORK.md)
- `subagent-driven-development/` (platform-coupled orchestration; Supervisor delegation covers this)
- `finishing-a-development-branch/` (worktree-specific; basic git workflow)
- `dispatching-parallel-agents/` (narrow debugging tactic; Supervisor already covers parallel delegation)

For `systematic-debugging/`, skip test/example files (`test-academic.md`, `test-pressure-*.md`, `CREATION-LOG.md`) — only copy the core reference files listed above.

#### 3.5.3 Create `.cursor/rules/superpowers-methodology.md`

Create a Cursor rule file that bridges Supervisor workflows to the installed methodology skills. Use the template from `templates/cursor-rules/superpowers-methodology.md`.

This rule tells the AI:
- Methodology skills are available at `.cursor/skills/`
- Process skills (brainstorming, debugging) take priority over implementation skills
- How Supervisor activities map to specific skills

---

### Step 4: Customize Framework Templates

Replace these placeholders in all templates:

| Placeholder | Replace With |
|-------------|--------------|
| `{{PROJECT_NAME}}` | Actual project name |
| `{{PROJECT_TYPE}}` | Type of project |
| `{{PROJECT_DESCRIPTION}}` | Brief description |
| `{{TECH_STACK}}` | Technologies used |
| `{{PRIMARY_LANGUAGE}}` | Main programming language |
| `{{CURRENT_DATE}}` | Today's date |
| `{{CURRENT_PHASE}}` | Current project phase |
| `{{TEST_COMMAND}}` | Command to run tests |
| `{{DEV_COMMAND}}` | Command to start dev server |
| `{{BUILD_COMMAND}}` | Command to build project |

### Step 5: Initialize Status Documents

**CURRENT-STATUS.md** should reflect:
- Current project health (based on your assessment)
- What's complete vs in progress
- Known issues or blockers
- Next priorities

**DELEGATION-TRACKER.md** should start with:
- "No active delegations" (for new projects)
- Or document existing work in progress

### Step 6: Confirm with User

After setup, confirm:

```markdown
## ✅ AI Supervisor-Worker Framework Initialized

I've created the framework structure with AI IDE configurations:

### AI IDE Configuration Files (Project Root)
- ✅ CLAUDE.md - AI assistant instructions for this project
- ✅ context.md - Project context summary
- ✅ .cursorrules - Cursor IDE specific rules
- ✅ .windsurfrules - Windsurf IDE specific rules

### Framework Files (docs/SUPERVISOR/)
- ✅ SUPERVISOR-FRAMEWORK.md - Your guide for supervisor role
- ✅ WORKER-FRAMEWORK.md - Guide for delegated workers
- ✅ BEST-PRACTICES.md - Tips and patterns
- ✅ CURRENT-STATUS.md - Project health dashboard
- ✅ DELEGATION-TRACKER.md - Task tracking
- ✅ THINKING-LOG.md - Strategic decisions log
- ✅ DECISIONS-LOG.md - Technical decisions log

### Methodology Skills (.cursor/skills/)
- ✅ init-supervisor - Initialize or resume a Supervisor session with situational briefing
- ✅ brainstorming - Think before coding, explore approaches
- ✅ writing-plans - Structured implementation planning with bite-sized tasks
- ✅ test-driven-development - TDD discipline (red-green-refactor)
- ✅ systematic-debugging - Root-cause debugging methodology
- ✅ requesting-code-review - Code review workflow with templates
- ✅ verification-before-completion - Evidence-based completion verification

### Methodology Bridge Rule (.cursor/rules/)
- ✅ superpowers-methodology.md - Maps Supervisor workflows to skills

### Project Configuration Detected
- **Name**: [Project Name]
- **Type**: [Project Type]
- **Tech Stack**: [Technologies]
- **Primary Language**: [Language]

### How to Use

**As Supervisor** (planning, delegating, validating):
```
Initialize yourself as SUPERVISOR
```

**As Worker** (executing specific tasks):
```
Initialize yourself as WORKER
```

### Next Steps
1. Review AI IDE config files and adjust as needed
2. Review CURRENT-STATUS.md and update if needed
3. Add any existing decisions to DECISIONS-LOG.md
4. Start working!

Would you like me to initialize as SUPERVISOR now?
```

---

## 🔧 AI IDE Configuration Details

### Why These Files Matter

AI IDE configuration files help AI assistants:
- **Understand project context** without re-reading everything
- **Follow consistent patterns** across chat sessions
- **Know about the framework** and follow its protocols
- **Avoid common mistakes** with project-specific rules

### File Purpose Summary

| File | IDE Support | Purpose |
|------|-------------|---------|
| `CLAUDE.md` | Cursor, Claude.ai | Detailed instructions for Claude-based AI |
| `context.md` | All | Quick project context reference |
| `.cursorrules` | Cursor | Cursor-specific behavior rules |
| `.windsurfrules` | Windsurf | Windsurf/Cascade specific rules |
| `.cursor/skills/` | Cursor | Methodology skills (TDD, debugging, planning, etc.) |
| `.cursor/rules/superpowers-methodology.md` | Cursor | Bridge rule mapping Supervisor workflows to skills |

### Detecting Project Information

**For JavaScript/TypeScript projects**, check:
- `package.json` for dependencies and scripts
- `tsconfig.json` for TypeScript config
- `.eslintrc` or `eslint.config.js` for coding standards

**For Python projects**, check:
- `requirements.txt` or `pyproject.toml` for dependencies
- `setup.py` or `setup.cfg` for project info
- `.flake8` or `pyproject.toml` for coding standards

**For other languages**, check:
- Build files (`Cargo.toml`, `go.mod`, `pom.xml`, etc.)
- README for project description
- Existing configuration files

---

## 🔧 Customization Points

### For Different Project Types

**Web Application**:
- Include frontend/backend separation in context
- Add API routes documentation
- Track deployment environments

**Library/Package**:
- Emphasize API stability rules
- Include versioning guidelines
- Document public vs internal APIs

**Data/ML Project**:
- Track data pipelines in status
- Include model versioning rules
- Document experiment tracking

**DevOps/Infrastructure**:
- Track environments in status
- Include deployment safety rules
- Document infrastructure as code patterns

### For Different Team Sizes

**Solo Developer**:
- Simpler status tracking
- Focus on session continuity
- Personal productivity patterns

**Small Team (2-5)**:
- Task assignment tracking
- Communication protocols
- Shared decision log

**Larger Team**:
- Multiple delegation streams
- Parallel work tracking
- Integration checkpoints

---

## ⚠️ Common Mistakes to Avoid

1. **Don't skip project discovery** - Generic templates are less useful than customized ones
2. **Don't forget AI IDE configs** - These significantly improve AI assistant effectiveness
3. **Don't forget SESSION-SUMMARIES/** - Important for continuity
4. **Don't make it too complex** - Start simple, evolve as needed
5. **Don't duplicate project docs** - Framework docs reference, not replace

---

## 🔄 Post-Installation

After installation, the AI should:

1. **Read existing project docs** (README, existing documentation)
2. **Update AI IDE configs** with specific patterns found in codebase
3. **Update CURRENT-STATUS** with real project state
4. **Note any existing decisions** in DECISIONS-LOG
5. **Offer to initialize as SUPERVISOR** for immediate work

---

## 🎯 Initialization Commands

After setup is complete, these commands should work:

| Command | Action |
|---------|--------|
| "Initialize as SUPERVISOR" | Load SUPERVISOR-FRAMEWORK, start oversight mode |
| "Initialize as WORKER" | Load WORKER-FRAMEWORK, await task assignment |
| "What's the project status?" | Read CURRENT-STATUS, provide summary |
| "What's being worked on?" | Read DELEGATION-TRACKER, list active tasks |

---

**Installation Guide Version**: 1.3.1  
**Last Updated**: March 2026
