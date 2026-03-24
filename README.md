# AI Supervisor-Worker Framework

> **⚠️ What This Is**: A **methodology and workflow framework** for managing multiple AI coding assistants in AI-powered IDEs like **Cursor**, **Windsurf**, **Cline**, etc. This is **NOT** a library or SDK for building AI agents into your applications.

A structured approach for AI-assisted software development using a **Supervisor-Worker** pattern. This framework enables organized collaboration between AI assistants across multiple chat sessions, with clear role definitions, task delegation protocols, and quality assurance processes.

## 🎯 Purpose

When working on complex software projects with AI coding assistants in modern AI IDEs, having a structured methodology dramatically improves:

- **Consistency** - Same patterns across all tasks and chat sessions
- **Quality** - Clear success criteria and validation
- **Traceability** - Complete history of decisions and progress
- **Handovers** - Seamless transitions between sessions/assistants
- **Scalability** - Delegate tasks to multiple AI workers efficiently
- **Context Preservation** - AI assistants can pick up work without losing context

## 💡 Who Is This For?

This framework is designed for:

- **Developers** using AI-powered IDEs (Cursor, Windsurf, Cline, etc.)
- **Teams** coordinating multiple AI chat sessions on the same project
- **Solo developers** who want structured AI-assisted workflows
- **Anyone** who finds their AI coding sessions becoming chaotic or losing context

This framework is **NOT** for:

- Building AI agents into your application
- Creating autonomous AI systems
- LLM API integration or AI/ML development

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    SUPERVISOR (AI Chat #1)                  │
│  • Strategic planning & oversight                           │
│  • Task delegation & coordination                           │
│  • Quality assurance & validation                           │
│  • Documentation maintenance                                │
└────────────────────┬────────────────────────────────────────┘
                     │
        ┌────────────┼────────────┐
        ▼            ▼            ▼
┌──────────────┐ ┌──────────────┐ ┌──────────────┐
│ WORKER #1    │ │ WORKER #2    │ │ WORKER #N    │
│ (AI Chat #2) │ │ (AI Chat #3) │ │ (AI Chat #N) │
│  • Execute   │ │  • Execute   │ │  • Execute   │
│  • Report    │ │  • Report    │ │  • Report    │
│  • Deliver   │ │  • Deliver   │ │  • Deliver   │
└──────────────┘ └──────────────┘ └──────────────┘
```

## 🤖 Supported AI IDEs

This framework works with any AI-powered IDE that supports chat-based coding assistance:

| IDE | Status | Notes |
|-----|--------|-------|
| **Cursor** | ✅ Tested | Primary development environment |
| **Windsurf** | ✅ Compatible | Works with Cascade |
| **Cline** | ✅ Compatible | VS Code extension |
| **Continue** | ✅ Compatible | VS Code/JetBrains |
| **GitHub Copilot Chat** | ✅ Compatible | Limited multi-chat |
| **Other AI IDEs** | 🔄 Should work | Any chat-based AI assistant |

## 📦 Framework Contents

```
supervisor-worker-ai-framework/
├── README.md                      # This file
├── QUICK-START.md                 # 5-minute setup guide
├── INSTALLATION.md                # Full installation guide for AI
├── framework/
│   ├── SUPERVISOR-FRAMEWORK.md    # Complete supervisor guide
│   ├── WORKER-FRAMEWORK.md        # Complete worker guide
│   └── BEST-PRACTICES.md          # Tips, patterns, anti-patterns
├── superpowers/                   # Vendored Superpowers skills (source)
│   └── skills/                    # Methodology skills library
│       ├── init-supervisor/       # Bootstrap or resume Supervisor session
│       ├── brainstorming/         # Think before coding
│       ├── writing-plans/         # Structured planning
│       ├── test-driven-development/  # TDD discipline
│       ├── systematic-debugging/  # Root-cause debugging
│       ├── requesting-code-review/  # Code review workflow
│       └── verification-before-completion/  # Evidence-based completion
└── templates/
    ├── CURRENT-STATUS.md          # Project health dashboard
    ├── DELEGATION-TRACKER.md      # Task tracking
    ├── THINKING-LOG.md            # Strategic decisions
    ├── DECISIONS-LOG.md           # Technical decisions
    ├── SESSION-SUMMARY.md         # Session handover template
    ├── cursor-rules/              # Cursor rule templates
    │   └── superpowers-methodology.md  # Methodology bridge rule
    └── ai-ide-configs/            # AI IDE configuration templates
        ├── CLAUDE.md              # Claude/Anthropic instructions
        ├── context.md             # Project context for AI
        └── .cursorrules           # Cursor-specific rules
```

## 🚀 Quick Start

### For Humans

Open your AI IDE (Cursor, Windsurf, etc.) and ask your AI assistant:

```
Initialize the supervisor-worker AI framework from:
https://github.com/PREDICTif/supervisor-worker-ai-framework

Create the framework in ./docs/SUPERVISOR/ folder.
```

If the framework already exists in a project, asking to initialize it again should be treated as an upgrade/repair pass that refreshes framework files and re-syncs missing project-level skills.

### For AI Assistants

When asked to initialize this framework:

1. Read `INSTALLATION.md` for complete setup instructions
2. Gather project information (name, type, tech stack)
3. Create `docs/SUPERVISOR/` directory in target project
4. Generate AI IDE configuration files (CLAUDE.md, .cursorrules, etc.)
5. Install or sync methodology skills into `.cursor/skills/` (Cursor IDE)
6. Copy and customize templates for the specific project
7. Initialize as either SUPERVISOR or WORKER based on user request

## 🎭 Roles

### Supervisor (Typically: Main AI Chat Session)
- **When to use**: Starting new projects, planning features, coordinating multiple tasks
- **Initialize**: "Initialize yourself as SUPERVISOR"
- **Responsibilities**: Plan, delegate, validate, document

### Worker (Typically: Separate AI Chat Sessions)
- **When to use**: Executing specific, well-defined tasks
- **Initialize**: "Initialize yourself as WORKER"
- **Responsibilities**: Execute, report, deliver, handover

## 📋 Key Documents

| Document | Purpose | When to Update |
|----------|---------|----------------|
| `CURRENT-STATUS.md` | Project health dashboard | Every session |
| `DELEGATION-TRACKER.md` | Track delegated tasks | When tasks change |
| `THINKING-LOG.md` | Strategic decisions | Major decisions |
| `DECISIONS-LOG.md` | Technical decisions | Architecture changes |

## 🔄 Typical Workflow

```
1. User opens AI IDE, starts new chat
   ↓
2. User: "Initialize as SUPERVISOR"
   ↓
3. Supervisor reads CURRENT-STATUS, plans work
   ↓
4. Supervisor creates delegation prompts for tasks
   ↓
5. User: Opens NEW chat session, "Initialize as WORKER"
   ↓
6. Worker executes task, reports progress
   ↓
7. Worker delivers completion report
   ↓
8. User returns to Supervisor chat
   ↓
9. Supervisor validates and updates status
```

## ✅ Success Criteria

A well-implemented framework should enable:

- [ ] Any AI chat session can pick up work from any point
- [ ] Clear history of what was done and why
- [ ] No duplicate or conflicting work across chat sessions
- [ ] Consistent code quality across all contributions
- [ ] Efficient task parallelization when possible

## 📚 Documentation

- [Quick Start Guide](QUICK-START.md) - Get running in 5 minutes
- [Installation Guide](INSTALLATION.md) - Complete setup instructions
- [Supervisor Framework](framework/SUPERVISOR-FRAMEWORK.md) - Full supervisor guide
- [Worker Framework](framework/WORKER-FRAMEWORK.md) - Full worker guide
- [Best Practices](framework/BEST-PRACTICES.md) - Tips and patterns

## 🛠️ Methodology Skills (Powered by Superpowers)

This framework includes methodology skills adapted from [Superpowers](https://github.com/obra/superpowers) (MIT License, by Jesse Vincent). During initialization, these are installed as project-level Cursor skills (`.cursor/skills/`), making them immediately available without any plugin installation or IDE restart. Re-running framework initialization in an existing project should also re-sync missing or newly added skills.

| Skill | Purpose |
|-------|---------|
| `init-supervisor` | Bootstrap or resume a Supervisor session — reads framework, assesses state, presents briefing |
| `brainstorming` | Think before coding — explore approaches, get approval before implementing |
| `writing-plans` | Create structured implementation plans with bite-sized TDD tasks |
| `test-driven-development` | TDD discipline — red, green, refactor. No code without a failing test. |
| `systematic-debugging` | Root-cause debugging — four-phase methodology, never guess-and-fix |
| `requesting-code-review` | Structured code review workflow with severity-categorized feedback |
| `verification-before-completion` | Evidence-based completion — run the command, read the output, then claim done |

The framework defines **what** to do (roles, delegation, tracking). The skills define **how** to do it (methodology, discipline, quality).

## 🤝 Contributing

This framework is designed to evolve. If you find patterns that work well:

1. Document them in your project's THINKING-LOG
2. Consider contributing back to the main framework
3. Share what works (and what doesn't) with the community

## 📜 License

MIT License - Use freely in any project.

---

**Version**: 1.3.2  
**Created**: December 2024  
**Last Updated**: March 2026  
**Inspiration**: Developed through practical experience coordinating AI assistants in Cursor IDE  
**Methodology Skills**: Adapted from [Superpowers](https://github.com/obra/superpowers) by Jesse Vincent (MIT License)
