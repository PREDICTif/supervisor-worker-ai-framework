# Prompt Execution Tracker

> **Purpose**: Track execution status of all prompts/task definitions to ensure no work is missed or duplicated across multiple AI sessions.

**Last Updated**: [Date]  
**Project**: [Project Name]  
**Total Prompts**: [X]  
**Completed**: [Y]  
**Pending**: [Z]

---

## Quick Stats

| Status | Count | Percentage |
|--------|-------|------------|
| ✅ DONE | 0 | 0% |
| 🚧 IN PROGRESS | 0 | 0% |
| ⏳ PENDING | 0 | 0% |
| ❌ BLOCKED | 0 | 0% |
| 🔄 ADAPTED | 0 | 0% |
| 🚫 SKIPPED | 0 | 0% |

---

## Prompt Status Legend

| Icon | Status | Description |
|------|--------|-------------|
| ✅ | DONE | Completed successfully, delivered, tested |
| 🚧 | IN PROGRESS | Currently being worked on |
| ⏳ | PENDING | Not started yet, ready to begin |
| ❌ | BLOCKED | Cannot proceed, dependencies or issues |
| 🔄 | ADAPTED | Modified approach, different implementation |
| 🚫 | SKIPPED | Intentionally not executed, documented reason |
| ⏸️ | DEFERRED | Postponed to later phase/sprint |

---

## Execution Priority

### P0 - Critical (Must Complete First)
[Prompts that are foundational or blocking other work]

### P1 - High Priority (Complete Soon)
[Important prompts that should be done early]

### P2 - Medium Priority (Standard Timeline)
[Regular prompts, no urgency]

### P3 - Low Priority (Nice to Have)
[Can be deferred if needed]

---

## Prompt Tracking Table

| ID | Prompt Name | Status | Priority | Assigned To | Date Started | Date Completed | Output Document | Notes |
|----|-------------|--------|----------|-------------|--------------|----------------|-----------------|-------|
| 01 | [Prompt Title] | ✅ DONE | P0 | SUPERVISOR | 2025-12-20 | 2025-12-20 | [FEATURE-COMPLETE.md] | All tests pass |
| 02 | [Prompt Title] | 🚧 IN PROGRESS | P1 | WORKER-A | 2025-12-21 | - | - | 60% complete |
| 03 | [Prompt Title] | ⏳ PENDING | P1 | - | - | - | - | Waiting for 01 |
| 04 | [Prompt Title] | ❌ BLOCKED | P0 | WORKER-B | 2025-12-21 | - | - | Missing API key |
| 05 | [Prompt Title] | 🔄 ADAPTED | P2 | SUPERVISOR | 2025-12-22 | 2025-12-22 | [ADAPTED-SOLUTION.md] | Used different approach |
| 06 | [Prompt Title] | 🚫 SKIPPED | P3 | - | - | - | - | Feature not needed |
| 07 | [Prompt Title] | ⏸️ DEFERRED | P2 | - | - | - | - | Phase 2 feature |

---

## Detailed Prompt Information

### Prompt 01: [Prompt Title]
**File**: `docs/prompts/01-feature-name.md`  
**Status**: ✅ DONE  
**Priority**: P0  
**Assigned**: SUPERVISOR  
**Started**: 2025-12-20  
**Completed**: 2025-12-20

**Objective**: [What this prompt aimed to accomplish]

**Deliverables**:
- ✅ [Deliverable 1]
- ✅ [Deliverable 2]
- ✅ [Deliverable 3]

**Output**: `FEATURE-COMPLETE.md`  
**Tests Added**: 15 (100% pass rate)  
**Files Modified**: 8

**Notes**: [Any relevant notes about execution]

---

### Prompt 02: [Prompt Title]
**File**: `docs/prompts/02-feature-name.md`  
**Status**: 🚧 IN PROGRESS  
**Priority**: P1  
**Assigned**: WORKER-A  
**Started**: 2025-12-21  
**Estimated Completion**: 2025-12-22

**Objective**: [What this prompt aims to accomplish]

**Deliverables**:
- ✅ [Deliverable 1] - Done
- 🚧 [Deliverable 2] - In progress (60%)
- ⏳ [Deliverable 3] - Pending

**Current Status**: [Brief status update]

**Next Steps**:
1. [Next action]
2. [Following action]

**Blockers**: [None | Description]

---

### Prompt 03: [Prompt Title]
**File**: `docs/prompts/03-feature-name.md`  
**Status**: ⏳ PENDING  
**Priority**: P1  
**Dependencies**: Prompt 01 must complete first

**Objective**: [What this prompt will accomplish]

**Estimated Effort**: [X hours/days]

**Prerequisites**:
- ✅ [Prerequisite 1] - Met
- ⏳ [Prerequisite 2] - Waiting
- ⏳ [Prerequisite 3] - Waiting

**Assignment Plan**: [Who should take this, when]

---

### Prompt 04: [Prompt Title]
**File**: `docs/prompts/04-feature-name.md`  
**Status**: ❌ BLOCKED  
**Priority**: P0  
**Assigned**: WORKER-B  
**Blocked Since**: 2025-12-21

**Objective**: [What this prompt aims to accomplish]

**Blocker Details**:
- **Issue**: [Description of blocker]
- **Impact**: [What's affected]
- **Resolution Required**: [What needs to happen]
- **ETA**: [When can this be unblocked]
- **Workaround**: [Temporary solution if any]

**Action Items**:
- [ ] [Action to unblock]
- [ ] [Action to unblock]

---

### Prompt 05: [Prompt Title]
**File**: `docs/prompts/05-feature-name.md`  
**Status**: 🔄 ADAPTED  
**Priority**: P2  
**Assigned**: SUPERVISOR  
**Completed**: 2025-12-22

**Original Objective**: [What the prompt originally specified]

**Adaptation Reason**: [Why approach was changed]

**Actual Implementation**: [What was done instead]

**Deliverables Modified**:
- ✅ [Deliverable 1] - Done as specified
- 🔄 [Deliverable 2] - Adapted (see notes)
- ❌ [Deliverable 3] - Not needed

**Output**: `ADAPTED-SOLUTION.md`

**Rationale for Changes**: [Detailed explanation]

---

### Prompt 06: [Prompt Title]
**File**: `docs/prompts/06-feature-name.md`  
**Status**: 🚫 SKIPPED  
**Priority**: P3  
**Decision Date**: 2025-12-22  
**Decided By**: SUPERVISOR

**Original Objective**: [What the prompt specified]

**Skip Reason**: [Why this was not executed]
- [ ] Feature not needed
- [ ] Duplicate of another prompt
- [ ] Out of scope
- [ ] Superseded by different approach
- [ ] Technical constraints
- [ ] Other: [Explanation]

**Impact Analysis**: [What impact does skipping this have]

**Documented In**: [Where decision is recorded]

---

### Prompt 07: [Prompt Title]
**File**: `docs/prompts/07-feature-name.md`  
**Status**: ⏸️ DEFERRED  
**Priority**: P2  
**Deferred Date**: 2025-12-22

**Original Objective**: [What the prompt specifies]

**Deferral Reason**: [Why postponed]
- [ ] Phase 2 feature
- [ ] Lower priority
- [ ] Dependency not ready
- [ ] Resource constraints
- [ ] Other: [Explanation]

**Target Timeline**: [When to revisit]

**Prerequisites for Resumption**: [What needs to happen first]

---

## Dependencies Map

```
Prompt 01 (DONE)
├── Prompt 03 (PENDING) - Waiting for 01
└── Prompt 08 (PENDING) - Waiting for 01

Prompt 02 (IN PROGRESS)
└── Prompt 09 (PENDING) - Waiting for 02

Prompt 04 (BLOCKED)
└── Prompt 10 (PENDING) - Cannot start until 04 unblocked
```

---

## Timeline View

### Week 1 (Dec 20-26, 2025)
- ✅ Prompt 01 - DONE
- ✅ Prompt 05 - DONE (Adapted)
- 🚧 Prompt 02 - IN PROGRESS
- ⏳ Prompt 03 - Scheduled

### Week 2 (Dec 27 - Jan 2, 2026)
- ⏳ Prompt 08 - Scheduled
- ⏳ Prompt 09 - Scheduled

### Backlog (Unscheduled)
- ⏳ Prompt 10
- ⏳ Prompt 11
- ⏸️ Prompt 07 - Deferred to Phase 2

---

## Completion Metrics

### Velocity Tracking
- **Week 1**: 2 prompts completed
- **Week 2**: X prompts completed
- **Average**: X prompts/week

### Quality Metrics
- **Test Coverage**: Average X% across completed prompts
- **Bug Rate**: X bugs found per prompt
- **Adaptation Rate**: X% of prompts required changes

### Time Tracking
- **Estimated Total**: X hours
- **Actual Total**: Y hours
- **Variance**: +/- Z%

---

## Review & Updates

### Update Schedule
- **Daily**: Update status for in-progress prompts
- **Weekly**: Review overall progress, adjust priorities
- **Monthly**: Archive completed prompts, plan next phase

### Last Review
**Date**: [Date]  
**Reviewed By**: [SUPERVISOR]  
**Key Findings**: [Summary]  
**Action Items**: [Any changes needed]

---

## Notes & Observations

### Patterns Observed
1. [Pattern 1 - e.g., "Prompts estimating X hours actually take Y hours"]
2. [Pattern 2 - e.g., "Testing prompts find issues in prior work"]
3. [Pattern 3 - e.g., "Some prompts assume features not yet implemented"]

### Lessons Learned
1. [Lesson 1]
2. [Lesson 2]
3. [Lesson 3]

### Process Improvements
1. [Improvement idea 1]
2. [Improvement idea 2]
3. [Improvement idea 3]

---

## Archive

### Completed Prompts (Last 30 Days)
Moved to: `docs/archive/completed-prompts/YYYY-MM.md`

### Skipped Prompts (Historical)
Moved to: `docs/archive/skipped-prompts/YYYY-MM.md`

---

**Template Version**: 1.0  
**Framework Version**: 1.2.0  
**Last Updated**: [Date]  
**Maintained By**: [SUPERVISOR]

