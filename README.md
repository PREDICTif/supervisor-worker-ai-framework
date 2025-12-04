# AI Supervisor-Worker Framework

A universal framework for AI-assisted software development using a **Supervisor-Worker** pattern. This framework enables structured collaboration between AI assistants, with clear role definitions, task delegation protocols, and quality assurance processes.

## 🎯 Purpose

When working on complex software projects with AI assistants, having a structured approach dramatically improves:

- **Consistency** - Same patterns across all tasks
- **Quality** - Clear success criteria and validation
- **Traceability** - Complete history of decisions and progress
- **Handovers** - Seamless transitions between sessions/assistants
- **Scalability** - Delegate tasks to multiple workers efficiently

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                      SUPERVISOR                              │
│  • Strategic planning & oversight                           │
│  • Task delegation & coordination                           │
│  • Quality assurance & validation                           │
│  • Documentation maintenance                                │
└────────────────────┬────────────────────────────────────────┘
                     │
        ┌────────────┼────────────┐
        ▼            ▼            ▼
┌──────────────┐ ┌──────────────┐ ┌──────────────┐
│   WORKER 1   │ │   WORKER 2   │ │   WORKER N   │
│  • Execute   │ │  • Execute   │ │  • Execute   │
│  • Report    │ │  • Report    │ │  • Report    │
│  • Deliver   │ │  • Deliver   │ │  • Deliver   │
└──────────────┘ └──────────────┘ └──────────────┘
```

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
└── templates/
    ├── CURRENT-STATUS.md          # Project health dashboard
    ├── DELEGATION-TRACKER.md      # Task tracking
    ├── THINKING-LOG.md            # Strategic decisions
    ├── DECISIONS-LOG.md           # Technical decisions
    └── SESSION-SUMMARY.md         # Session handover template
```

## 🚀 Quick Start

### For Humans

Ask your AI assistant:

```
Initialize the supervisor-worker AI framework from:
https://github.com/YOUR_USERNAME/supervisor-worker-ai-framework

Create the framework in ./docs/SUPERVISOR/ folder.
```

### For AI Assistants

When asked to initialize this framework:

1. Read `INSTALLATION.md` for complete setup instructions
2. Create `docs/SUPERVISOR/` directory in target project
3. Copy and customize templates for the specific project
4. Initialize as either SUPERVISOR or WORKER based on user request

## 🎭 Roles

### Supervisor
- **When to use**: Starting new projects, planning features, coordinating multiple tasks
- **Initialize**: "Initialize yourself as SUPERVISOR"
- **Responsibilities**: Plan, delegate, validate, document

### Worker
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
1. User: "Initialize as SUPERVISOR"
   ↓
2. Supervisor reads CURRENT-STATUS, plans work
   ↓
3. Supervisor creates delegation prompts
   ↓
4. User: Opens new chat, "Initialize as WORKER"
   ↓
5. Worker executes task, reports progress
   ↓
6. Worker delivers completion report
   ↓
7. Supervisor validates and updates status
```

## ✅ Success Criteria

A well-implemented framework should enable:

- [ ] Any AI assistant can pick up work from any point
- [ ] Clear history of what was done and why
- [ ] No duplicate or conflicting work
- [ ] Consistent code quality across all contributions
- [ ] Efficient task parallelization when possible

## 📚 Documentation

- [Quick Start Guide](QUICK-START.md) - Get running in 5 minutes
- [Installation Guide](INSTALLATION.md) - Complete setup instructions
- [Supervisor Framework](framework/SUPERVISOR-FRAMEWORK.md) - Full supervisor guide
- [Worker Framework](framework/WORKER-FRAMEWORK.md) - Full worker guide
- [Best Practices](framework/BEST-PRACTICES.md) - Tips and patterns

## 🤝 Contributing

This framework is designed to evolve. If you find patterns that work well:

1. Document them in your project's THINKING-LOG
2. Consider contributing back to the main framework
3. Share what works (and what doesn't) with the community

## 📜 License

MIT License - Use freely in any project.

---

**Version**: 1.0.0  
**Created**: December 2024  
**Inspiration**: Developed through practical experience on TSL Portal V3 project

