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

Ask the user (if not already clear):

```
To set up the AI Supervisor-Worker Framework, I need:

1. **Project Name**: What is the project called?
2. **Project Type**: What kind of project is this? (web app, API, library, etc.)
3. **Current Phase**: Is this a new project or ongoing? What's the current status?
4. **Documentation Location**: Where should I create the framework? (default: ./docs/SUPERVISOR/)
5. **Key Technologies**: What's the tech stack?
```

### Step 2: Create Directory Structure

Create the following structure:

```
{project_root}/
└── docs/
    └── SUPERVISOR/
        ├── SUPERVISOR-FRAMEWORK.md    # Copy from framework/
        ├── WORKER-FRAMEWORK.md        # Copy from framework/
        ├── CURRENT-STATUS.md          # Customize from templates/
        ├── DELEGATION-TRACKER.md      # Customize from templates/
        ├── THINKING-LOG.md            # Initialize empty
        ├── DECISIONS-LOG.md           # Initialize empty
        └── SESSION-SUMMARIES/         # Directory for session logs
```

### Step 3: Customize Templates

Replace these placeholders in all templates:

| Placeholder | Replace With |
|-------------|--------------|
| `{{PROJECT_NAME}}` | Actual project name |
| `{{PROJECT_TYPE}}` | Type of project |
| `{{TECH_STACK}}` | Technologies used |
| `{{CURRENT_DATE}}` | Today's date |
| `{{CURRENT_PHASE}}` | Current project phase |
| `{{PROJECT_DESCRIPTION}}` | Brief description |

### Step 4: Initialize Status Documents

**CURRENT-STATUS.md** should reflect:
- Current project health
- What's complete vs in progress
- Known issues or blockers
- Next priorities

**DELEGATION-TRACKER.md** should start with:
- "No active delegations" (for new projects)
- Or document existing work in progress

### Step 5: Confirm with User

After setup, confirm:

```markdown
## ✅ AI Supervisor-Worker Framework Initialized

I've created the framework structure in `docs/SUPERVISOR/`:

### Files Created
- ✅ SUPERVISOR-FRAMEWORK.md - Your guide for supervisor role
- ✅ WORKER-FRAMEWORK.md - Guide for delegated workers
- ✅ CURRENT-STATUS.md - Project health dashboard
- ✅ DELEGATION-TRACKER.md - Task tracking
- ✅ THINKING-LOG.md - Strategic decisions log
- ✅ DECISIONS-LOG.md - Technical decisions log

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
1. Review CURRENT-STATUS.md and update if needed
2. Add any existing decisions to DECISIONS-LOG.md
3. Start working!

Would you like me to initialize as SUPERVISOR now?
```

---

## 🔧 Customization Points

### For Different Project Types

**Web Application**:
- Add frontend/backend status sections
- Track API endpoints
- Monitor deployment status

**Library/Package**:
- Track API surface
- Version compatibility
- Documentation coverage

**Data/ML Project**:
- Track data pipelines
- Model versions
- Experiment results

**DevOps/Infrastructure**:
- Track environments
- Deployment configurations
- Security compliance

### For Different Team Sizes

**Solo Developer**:
- Simpler status tracking
- Focus on personal productivity
- Session continuity

**Small Team (2-5)**:
- Task assignment tracking
- Communication protocols
- Shared decision log

**Larger Team**:
- Multiple delegation streams
- Parallel work tracking
- Integration checkpoints

---

## 📝 Template Customization Examples

### CURRENT-STATUS.md Header Example

```markdown
# Current Status
## {{PROJECT_NAME}} - Real-time Project Health Dashboard

**Last Updated**: {{CURRENT_DATE}}  
**Project Phase**: {{CURRENT_PHASE}}  
**Overall Health**: 🟢 Good / 🟡 Issues / 🔴 Blocked

---

## 📊 PROJECT HEALTH DASHBOARD

| Component | Status | Notes |
|-----------|--------|-------|
| Core Feature 1 | ✅ Complete | |
| Core Feature 2 | 🚧 In Progress | 70% done |
| Core Feature 3 | ⏳ Planned | Next sprint |
```

### DELEGATION-TRACKER.md Example

```markdown
# Delegation Tracker

## 🟢 ACTIVE DELEGATIONS

### Feature: User Authentication
**Status**: 🔄 IN PROGRESS
**Delegated To**: Worker Chat #2
**Started**: {{CURRENT_DATE}}
**Expected**: 2 days

**Scope**:
- Login/logout functionality
- Password reset
- Session management

**Progress**:
- [x] Database schema
- [x] API endpoints
- [ ] Frontend forms
- [ ] Testing
```

---

## ⚠️ Common Mistakes to Avoid

1. **Don't skip customization** - Generic templates are less useful
2. **Don't forget SESSION-SUMMARIES/** - Important for continuity
3. **Don't make it too complex** - Start simple, evolve as needed
4. **Don't duplicate project docs** - Framework docs reference, not replace

---

## 🔄 Post-Installation

After installation, the AI should:

1. **Read existing project docs** (README, existing documentation)
2. **Update CURRENT-STATUS** with real project state
3. **Note any existing decisions** in DECISIONS-LOG
4. **Offer to initialize as SUPERVISOR** for immediate work

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

**Installation Guide Version**: 1.0.0  
**Last Updated**: December 2024

