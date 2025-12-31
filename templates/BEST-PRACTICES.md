# Best Practices Guide

Patterns, tips, and anti-patterns for effective AI supervision and work execution.

---

## 🎯 Core Principles

### 1. Context is King

**Problem**: AI assistants have limited memory. Each new session starts fresh.

**Solution**: Keep context in documents, not in conversation:
- CURRENT-STATUS = "Where we are"
- THINKING-LOG = "Why we decided"
- DECISIONS-LOG = "What we chose"
- DELEGATION-TRACKER = "Who's doing what"

**Anti-pattern**: Expecting AI to "remember" from previous sessions without documentation.

---

### 2. Clear Boundaries

**Problem**: Scope creep and overlapping work between different AI sessions.

**Solution**: 
- Supervisors plan and validate, don't implement complex features
- Workers execute within scope, escalate if scope seems wrong
- Document task boundaries clearly

**Anti-pattern**: Worker decides to "also refactor this other thing while I'm here."

---

### 3. Verify Before Trust

**Problem**: AI can make mistakes or misunderstand requirements.

**Solution**:
- Always test before marking complete
- Supervisor validates worker output
- Check against success criteria, not just "seems done"

**Anti-pattern**: Accepting "I've completed the task" without verification.

---

### 4. Document Decisions, Not Just Actions

**Problem**: Later sessions don't know WHY something was done a certain way.

**Solution**:
- THINKING-LOG for strategic "why" decisions
- DECISIONS-LOG for technical "how" choices
- Include context and alternatives considered

**Anti-pattern**: Just updating code without documenting the reasoning.

---

## 📋 Delegation Patterns

### Pattern: Phased Delivery

For complex features, break into phases:

```
Feature: User Authentication

Phase 1: Database Schema (1-2 hours)
- Create user table
- Create session table
- Write migrations

Phase 2: API Endpoints (2-3 hours)
- Login endpoint
- Logout endpoint
- Session validation middleware

Phase 3: Frontend Forms (2-3 hours)
- Login form
- Logout button
- Session state management

Phase 4: Testing & Polish (1-2 hours)
- Unit tests
- Integration tests
- Error handling polish
```

**Benefits**:
- Each phase is independently testable
- Can validate before proceeding
- Easier to parallelize (Phase 2 & 3 can overlap)
- Clear progress tracking

---

### Pattern: Dependency Graph

Identify which tasks can run in parallel:

```
Phase 1 ──────┐
              ├──▶ Phase 4 (needs 1 & 2)
Phase 2 ──────┤
              │
Phase 3 ──────┴──▶ Phase 5 (needs 2 & 3)
```

**Use when**:
- Multiple workers available
- Tasks have clear interfaces
- Time is critical

---

### Pattern: Spike First

When requirements are unclear:

```
1. Spike: 1-2 hours exploring approaches
   - Don't build production code
   - Document findings
   - Identify blockers early

2. Decision: Review spike findings
   - Choose approach
   - Update plan if needed

3. Implementation: Build the real thing
   - Now with better understanding
   - Fewer surprises
```

**Use when**:
- New technology involved
- Complex integration
- Unclear performance requirements

---

## 🔄 Handover Patterns

### Pattern: Session Summary

End every significant session with:

```markdown
## Session Summary: [Date]

### What Was Done
- [Accomplishment 1]
- [Accomplishment 2]

### Key Decisions Made
- [Decision 1]: [Brief why]
- [Decision 2]: [Brief why]

### Current State
- [What's working]
- [What's in progress]

### Next Steps
1. [Priority 1]
2. [Priority 2]

### Blockers/Concerns
- [Any issues to watch]
```

**Benefits**:
- Next session starts informed
- No work duplication
- Decision history preserved

---

### Pattern: Warm Handover

When switching between workers on same task:

```markdown
1. Current Worker creates detailed handover:
   - What's done (with evidence)
   - What's in progress (exact state)
   - What's left (with estimates)
   - Gotchas discovered

2. New Worker reads handover
3. New Worker asks clarifying questions
4. Supervisor validates handover completeness
5. New Worker continues
```

---

## ⚠️ Anti-Patterns to Avoid

### Anti-Pattern: The Infinite Loop

**Symptom**: Same task keeps getting worked on, never completes.

**Cause**: Unclear success criteria or scope creep.

**Fix**: 
- Define explicit success criteria upfront
- Time-box tasks
- Supervisor validates "done" means done

---

### Anti-Pattern: The Orphan Task

**Symptom**: Task started, never finished, no handover.

**Cause**: Session ended without proper closure.

**Fix**:
- Always end sessions with status update
- Create handover if task incomplete
- Track in DELEGATION-TRACKER

---

### Anti-Pattern: The Hero Worker

**Symptom**: Worker takes on everything, makes all decisions.

**Cause**: Worker acting as supervisor.

**Fix**:
- Workers stay in scope
- Escalate architectural decisions
- Let supervisor coordinate

---

### Anti-Pattern: Documentation Debt

**Symptom**: Code works but nobody knows how or why.

**Cause**: Shipping without documenting.

**Fix**:
- CHANGELOG is mandatory
- Decision documentation is part of "done"
- Supervisor validates documentation exists

---

### Anti-Pattern: The Over-Planner

**Symptom**: Spending more time planning than doing.

**Cause**: Fear of mistakes, perfectionism.

**Fix**:
- Start with minimal viable plan
- Iterate based on learnings
- "Good enough" plan that evolves beats "perfect" plan that's never done

---

## 🧪 Testing Strategy

### Test Ownership

Clarify who owns testing for different types of work:

| Test Type | Owner | When |
|-----------|-------|------|
| Feature Unit Tests | WORKER implementing feature | Part of feature delegation |
| Integration Tests | WORKER or separate delegation | After multiple features complete |
| Bug Regression Tests | WORKER fixing bug | Required for every bug fix |
| E2E Tests | Scheduled milestone | After major feature sets |
| Performance Tests | Separate delegation | Before major releases |

### Test-Driven Delegation

When delegating features as SUPERVISOR:

```markdown
## Delegation: [Feature Name]

### Testing Requirements
- [ ] Minimum 80% code coverage for new code
- [ ] Unit tests for all public functions
- [ ] Integration test for happy path
- [ ] Edge case tests (empty input, max values, etc.)
- [ ] Error condition tests

### Success Criteria Includes Testing
- [ ] All tests passing (100% pass rate)
- [ ] Coverage target met
- [ ] Test report included in completion
```

### Test Failure Protocol

#### As WORKER

If tests fail during validation:
1. **Document failure** clearly in progress report
2. **Debug and fix** if within scope
3. **Escalate** if failure indicates larger issue
4. **Never report completion** with failing tests

#### As SUPERVISOR

If tests fail during validation of worker output:
1. **Document specific failures**
2. **Assess severity** (blocking vs. minor)
3. **Create new delegation** for fixes if needed
4. **Do NOT accept completion** until tests pass

### Testing Phases

#### Phase 1: During Development (WORKER)

```markdown
Development Testing Checklist:
- [ ] Unit test written for each function
- [ ] Manual verification as you code
- [ ] Edge cases identified and tested
- [ ] Error paths tested
- [ ] Integration points tested
```

#### Phase 2: Before Completion (WORKER)

```markdown
Pre-Completion Testing:
- [ ] All unit tests passing
- [ ] Integration tests passing
- [ ] Manual end-to-end test completed
- [ ] No regressions in existing features
- [ ] Test coverage report generated
```

#### Phase 3: Validation (SUPERVISOR)

```markdown
Validation Testing:
- [ ] Run full test suite
- [ ] Verify coverage meets minimum
- [ ] Manual verification of key functionality
- [ ] Check for integration issues
- [ ] Performance acceptable
```

### Testing Best Practices

#### DO ✅

- **Write tests first** or alongside code
- **Test edge cases** (empty, null, max, min)
- **Test error conditions** (bad input, failures)
- **Keep tests fast** (unit tests < 1s each)
- **Use descriptive test names** (`test_user_login_with_invalid_password_returns_401`)
- **Test one thing per test** (focused assertions)
- **Mock external dependencies** (APIs, databases)
- **Add regression tests** for every bug fixed

#### DON'T ❌

- Don't skip tests "to save time" (costs more later)
- Don't test implementation details (test behavior)
- Don't write flaky tests (inconsistent pass/fail)
- Don't commit failing tests (fix or skip them properly)
- Don't duplicate test logic (use helpers/fixtures)
- Don't test framework code (trust libraries)
- Don't ignore warnings about test quality

### Test Coverage Guidelines

#### Minimum Targets

| Code Type | Coverage Target |
|-----------|----------------|
| Business Logic | 90%+ |
| API Endpoints | 85%+ |
| Utilities | 80%+ |
| UI Components | 70%+ |
| Configuration | 60%+ |

#### What to Prioritize

1. **Critical paths** (user login, payment, data save)
2. **Complex logic** (algorithms, calculations)
3. **Error handling** (exception paths)
4. **Edge cases** (boundary conditions)
5. **Integration points** (external APIs, databases)

### Test Report Template

Include in completion reports:

```markdown
## Test Results

### Unit Tests
- **Total**: 47 tests
- **Passed**: 47 (100%)
- **Failed**: 0
- **Coverage**: 87%

### Integration Tests
- **Total**: 12 tests
- **Passed**: 12 (100%)
- **Coverage**: 73%

### Manual Testing
- [x] Happy path: User can log in successfully
- [x] Error case: Invalid credentials show error message
- [x] Edge case: Empty fields show validation error

### Performance
- Response time: 45ms (target: < 100ms)
- Memory usage: 12MB (acceptable)
```

### When Tests Are Blocked

If testing is blocked (missing test infrastructure, etc.):

```markdown
## Testing Status: ⚠️ BLOCKED

**Blocker**: [Description]
**Impact**: Cannot write [type] tests
**Workaround**: Manual testing performed
**Next Steps**: Need test infrastructure setup

### Manual Verification
Since automated tests blocked, performed:
- [x] Manual test 1
- [x] Manual test 2
- [x] Manual test 3

### Follow-Up Required
- [ ] Set up test infrastructure
- [ ] Convert manual tests to automated
```

---

## 💡 Efficiency Tips

### For Supervisors

1. **Batch similar decisions** - Group related choices together
2. **Parallelize when possible** - Multiple workers on independent tasks
3. **Front-load clarity** - Better requirements = fewer iterations
4. **Trust but verify** - Don't micromanage, do validate
5. **Keep status current** - 5 minutes updating docs saves 30 minutes of confusion

### For Workers

1. **Read fully before starting** - Understand the whole task
2. **Ask early, not late** - Questions at start save time at end
3. **Test incrementally** - Don't wait until "done" to test
4. **Document as you go** - Easier than remembering later
5. **Stay in scope** - It's not your job to fix everything

### For Both

1. **Use checklists** - They prevent forgetting things
2. **Be explicit** - Assume the other party doesn't share your context
3. **Update status often** - Stale information is worse than no information
4. **Name things clearly** - "Feature X Phase 2" beats "the next part"

---

## 📊 Metrics That Matter

### Healthy Signs

- Tasks complete on first attempt (clear requirements)
- Few escalations (right scope)
- Documentation stays current (discipline)
- Handovers are smooth (good protocols)
- Decisions are traceable (good logging)

### Warning Signs

- Same task appears multiple times (unclear completion)
- Many "blockers" (poor planning or communication)
- Outdated CURRENT-STATUS (neglected documentation)
- Workers making architecture decisions (role confusion)
- No CHANGELOG entries (documentation debt)

---

## 🔗 Integration with Tools

### With Version Control

- CHANGELOG syncs with commit messages
- Tag releases with version from status
- Branch names match task names

### With Issue Trackers

- DELEGATION-TRACKER can mirror issues
- Use issue IDs in task references
- Link completion reports to issues

### With CI/CD

- Success criteria can include CI checks
- Deployment is part of "done"
- Status reflects deployment state

---

## 📚 Further Reading

### Related Concepts

- **Agile/Scrum**: Sprint planning, user stories
- **GTD (Getting Things Done)**: Task management
- **RACI Matrix**: Role clarity
- **Decision Journals**: Recording decisions

### This Framework Was Inspired By

- Real-world experience with AI-assisted development
- Software engineering best practices
- Project management methodologies
- Human-AI collaboration patterns

---

**Best Practices Version**: 1.2.0  
**Last Updated**: December 2025

---

## 🆕 What's New in v1.2.0

### New Sections
- **Testing Strategy**: Comprehensive testing guidance including:
  - Test ownership clarification
  - Test-driven delegation approach
  - Test failure protocols
  - Coverage guidelines and targets
  - Test report templates

### Key Additions
- Clear testing phases (development, completion, validation)
- Testing best practices (DOs and DON'Ts)
- Test coverage targets by code type
- Handling blocked testing scenarios
- Test report template for completion docs

### Impact
- Better test quality across projects
- Clear expectations for testing
- Fewer bugs reaching production
- More consistent test coverage

