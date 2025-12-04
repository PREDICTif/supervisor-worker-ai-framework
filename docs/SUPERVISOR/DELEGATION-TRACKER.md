# Delegation Tracker
## Supervisor-Worker AI Framework - Task Delegation & Progress Tracking

**Last Updated**: December 4, 2025  
**Active Delegations**: 0  
**Completed This Week**: 0

---

## 🟢 ACTIVE DELEGATIONS

<!-- 
Template for active delegation:

### [Task Name]

**Status**: 🔄 IN PROGRESS | ⏳ PENDING START | 🔴 BLOCKED
**Delegated To**: [Worker identifier or "Unassigned"]
**Started**: [Date]
**Expected Completion**: [Date or duration]
**Plan Document**: [Link to delegation prompt if exists]

**Scope**:
- [Deliverable 1]
- [Deliverable 2]
- [Deliverable 3]

**Progress**:
| Deliverable | Status | Notes |
|-------------|--------|-------|
| [Item 1] | ✅ | |
| [Item 2] | 🔄 | In progress |
| [Item 3] | ⏳ | Not started |

**Blockers**: [None | Description of blocker]

**Last Update**: [Date] - [Brief note]

---
-->

**No active delegations** - Ready for new tasks.

---

## 🟡 PENDING REVIEW

<!--
Tasks completed by workers, awaiting supervisor validation.

### [Task Name]
**Completed By**: [Worker]
**Completion Date**: [Date]
**Completion Report**: [Link]
**Review Status**: ⏳ Pending | 🔄 In Review

---
-->

**No tasks pending review** - All caught up.

---

## ✅ RECENTLY COMPLETED

<!--
### [Task Name] ✅
**Worker**: [Who did it]
**Dates**: [Started] → [Completed]
**Duration**: [Time spent]
**Outcome**: [Success | Partial | Issues found]
**Notes**: [Any important observations]

---
-->

**No completed tasks yet** - History will appear here.

---

## ❌ CANCELLED / ON HOLD

<!--
### [Task Name] ❌
**Reason**: [Why cancelled or on hold]
**Date**: [When decision made]
**Resume Condition**: [What would need to happen to resume, if applicable]

---
-->

**No cancelled tasks**.

---

## 📋 DELEGATION QUEUE

Tasks planned for delegation but not yet started:

| Priority | Task | Est. Time | Dependencies |
|----------|------|-----------|--------------|
| - | [No tasks queued] | - | - |

---

## 📊 STATISTICS

### This Week
- Tasks Started: 0
- Tasks Completed: 0
- Tasks Blocked: 0
- Average Completion Time: N/A

### All Time
- Total Tasks Delegated: 0
- Total Tasks Completed: 0
- Success Rate: N/A
- Total Time Invested: 0 hours

---

## 📝 DELEGATION TEMPLATES

### Standard Task Delegation

```markdown
# DELEGATION TASK: [Task Name]

## Context
[Background information the worker needs]

## Your Task
1. [Deliverable 1]
2. [Deliverable 2]
3. [Deliverable 3]

## Technical Requirements
- [Requirement 1]
- [Requirement 2]

## Files to Reference
- `path/to/file` - [Why relevant]

## Success Criteria
- [ ] [Criterion 1]
- [ ] [Criterion 2]

## Estimated Time
[X-Y hours]

## When Done
Create completion report with:
1. Files created/modified
2. Testing performed
3. Any issues encountered
```

### Bug Fix Delegation

```markdown
# BUG FIX: [Bug Title]

## The Bug
[Description of the problem]

## Steps to Reproduce
1. [Step 1]
2. [Step 2]
3. [Expected vs Actual]

## Your Task
1. Investigate root cause
2. Implement fix
3. Verify fix works
4. Ensure no regression

## Files Likely Involved
- `path/to/file`

## Success Criteria
- [ ] Bug no longer reproducible
- [ ] No new bugs introduced
- [ ] Tests pass

## When Done
Report with: cause, fix description, testing performed
```

### Feature Phase Delegation

```markdown
# FEATURE PHASE: [Feature Name] - Phase [N]

## Feature Overview
[Brief description of the overall feature]

## This Phase
[What this specific phase accomplishes]

## Deliverables
1. [Deliverable 1]
2. [Deliverable 2]

## Previous Phase Summary
[What was done in previous phase, if applicable]

## Dependencies
- [Dependency 1]
- [Dependency 2]

## Success Criteria
- [ ] [Criterion 1]
- [ ] [Criterion 2]

## Integration Points
[How this phase connects to other work]

## When Done
Phase completion report enabling next phase to proceed
```

---

## 🔄 PROCESS NOTES

### How to Delegate

1. **Create delegation prompt** using templates above
2. **Add to Active Delegations** section with status "⏳ PENDING START"
3. **Assign to worker** (new chat session)
4. **Update status** as work progresses
5. **Move to Pending Review** when worker reports completion
6. **Validate** and move to Completed or send back for fixes

### How to Accept Completion

1. Review completion report
2. Verify success criteria met
3. Check for regressions
4. Update CURRENT-STATUS if needed
5. Update CHANGELOG if needed
6. Move to Recently Completed with notes

---

**Tracker Version**: 1.0  
**Last Updated**: December 4, 2025

