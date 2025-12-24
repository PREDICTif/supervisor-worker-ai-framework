# Bug Fix Documentation Template

> **Purpose**: Document bug fixes comprehensively for future reference, knowledge sharing, and prevention of similar issues.

---

## Bug Identification

### Bug ID/Name
**BUG-[FEATURE]-[DESCRIPTION]**  
Example: `BUG-CHAT-ORDERING`, `BUG-LEVEL-PROGRESS-CALCULATION`

### Severity Level
- 🔴 **CRITICAL**: System down, data loss, security breach
- 🟡 **HIGH**: Feature broken, major functionality impaired
- 🟢 **MEDIUM**: Feature partially working, workaround available
- 🔵 **LOW**: Minor issue, cosmetic, edge case

### Discovery Information
- **Discovered By**: User report | Testing | Code review | Production monitoring
- **Discovery Date**: YYYY-MM-DD
- **Environment**: Production | Staging | Development | Testing
- **Affected Versions**: vX.Y.Z to vA.B.C

---

## Bug Description

### Summary
[One-sentence description of the bug]

### Detailed Description
[Comprehensive description of what's wrong, what should happen vs. what actually happens]

### Impact
**Users Affected**: [All | Specific user group | Edge case]  
**Business Impact**: [How this affects business operations/user experience]  
**Frequency**: [How often does this occur? Always | Sometimes | Rare]

### Reproduction Steps
1. [Step 1 - be specific]
2. [Step 2 - be specific]
3. [Step 3 - be specific]
4. **Result**: [What happens]
5. **Expected**: [What should happen]

### Evidence
- **Screenshots**: [Attach if UI-related]
- **Error Messages**: 
  ```
  [Paste exact error message]
  ```
- **Logs**:
  ```
  [Paste relevant log entries]
  ```
- **Stack Trace**:
  ```
  [Paste stack trace if available]
  ```

---

## Root Cause Analysis

### Investigation Process
**Time Spent Investigating**: X hours

1. **Initial Hypothesis**: [What you first thought]
2. **Investigation Steps**:
   - [What you checked first]
   - [What you checked second]
   - [Key findings]
3. **Tools Used**: Debugger | Logs | Tests | Code inspection

### Root Cause
**Primary Cause**: [The fundamental reason this bug exists]

**Contributing Factors**:
1. [Factor 1 - e.g., Missing validation]
2. [Factor 2 - e.g., Incorrect assumption]
3. [Factor 3 - e.g., Missing test coverage]

### Why It Wasn't Caught Earlier
- [ ] Missing test coverage
- [ ] Test had incorrect assumption
- [ ] Edge case not considered
- [ ] Integration gap between components
- [ ] Documentation unclear
- [ ] Other: [Explanation]

---

## The Fix

### Solution Approach
**Strategy**: [High-level approach to fixing]

**Alternatives Considered**:
1. **Option A**: [Description] - ❌ Rejected because [reason]
2. **Option B**: [Description] - ✅ **Selected** because [reason]
3. **Option C**: [Description] - ❌ Rejected because [reason]

### Implementation Details

#### Files Modified
```
path/to/file1.ext
path/to/file2.ext
path/to/test_file.ext
```

#### Code Changes Summary
1. **File**: `path/to/file1.ext`
   - **Lines**: 45-67
   - **Change**: [What was changed]
   - **Reason**: [Why this change fixes it]

2. **File**: `path/to/file2.ext`
   - **Lines**: 123-145
   - **Change**: [What was changed]
   - **Reason**: [Why this change fixes it]

#### Key Code Snippets

**Before** (Buggy Code):
```language
[Paste problematic code]
```

**After** (Fixed Code):
```language
[Paste corrected code]
```

**Explanation**: [Why this fixes the issue]

---

## Testing & Verification

### Regression Test Added
**Test File**: `path/to/test_file.ext`  
**Test Name**: `test_[specific_bug_scenario]`

```language
[Paste test code or pseudocode]
```

**Test Coverage**:
- ✅ Reproduces original bug (fails on old code)
- ✅ Passes with fix
- ✅ Covers edge cases
- ✅ Tests related scenarios

### Manual Verification
**Verification Steps**:
1. [Step to verify fix works]
2. [Step to verify no regression]
3. [Step to verify edge cases]

**Verification Result**: ✅ PASS | ❌ FAIL (with details)

### Test Results
```
[Paste test output showing all tests pass]
```

---

## Prevention Strategy

### Immediate Actions
- [ ] Add regression test (Done above)
- [ ] Update related tests
- [ ] Fix similar issues in codebase
- [ ] Update error handling

### Long-Term Improvements
1. **Documentation**:
   - [ ] Update code comments
   - [ ] Update API documentation
   - [ ] Update user documentation
   - [ ] Add architecture notes

2. **Process Improvements**:
   - [ ] Add to code review checklist
   - [ ] Update testing guidelines
   - [ ] Add linter rule (if applicable)
   - [ ] Update validation rules

3. **Monitoring**:
   - [ ] Add logging/metrics
   - [ ] Add health checks
   - [ ] Add alerts (if critical)

### Knowledge Sharing
**Team Notification**: [How team was informed]  
**Documentation Updated**: [Which docs updated]  
**Lessons Learned**: [Key takeaways]

---

## Related Issues

### Similar Bugs
- [Link to similar bug 1] - [How it's related]
- [Link to similar bug 2] - [How it's related]

### Follow-Up Items
1. **[Task]** - [Description, priority]
2. **[Task]** - [Description, priority]

### Dependencies
**Blocked By**: [Other issues that must be fixed first]  
**Blocks**: [Other issues blocked by this bug]

---

## Timeline

| Date | Event |
|------|-------|
| YYYY-MM-DD | Bug discovered |
| YYYY-MM-DD | Investigation started |
| YYYY-MM-DD | Root cause identified |
| YYYY-MM-DD | Fix implemented |
| YYYY-MM-DD | Tests added |
| YYYY-MM-DD | Fix deployed to [env] |
| YYYY-MM-DD | Verified in production |

**Total Time**: X hours investigation + Y hours implementation = Z hours total

---

## Deployment Notes

### Deployment Risk Level
- 🟢 **LOW**: Minor fix, well-tested, no dependencies
- 🟡 **MEDIUM**: Moderate changes, some risk
- 🔴 **HIGH**: Major changes, high risk, requires careful deployment

### Deployment Checklist
- [ ] All tests passing
- [ ] Code reviewed
- [ ] Documentation updated
- [ ] Changelog updated
- [ ] Deployed to staging
- [ ] Verified in staging
- [ ] Deployed to production
- [ ] Verified in production
- [ ] Monitoring enabled
- [ ] Team notified

### Rollback Plan
**If issue occurs**: [Steps to rollback]  
**Recovery Time**: [Estimated time to rollback]

---

## Post-Fix Verification

### Success Criteria
- [ ] Original bug no longer reproduces
- [ ] All tests passing
- [ ] No new bugs introduced
- [ ] Performance not degraded
- [ ] No user complaints after X days

### Monitoring Period
**Duration**: [How long to monitor]  
**Metrics to Watch**: [Specific metrics]  
**Alert Conditions**: [When to escalate]

---

## References

### Documentation
- [Link to related documentation]
- [Link to API docs]
- [Link to architecture docs]

### External Resources
- [Stack Overflow question]
- [GitHub issue]
- [Blog post or article]

### Internal Discussion
- [Link to team discussion]
- [Link to code review]
- [Link to planning document]

---

## Metadata

**Author**: [Who fixed it]  
**Reviewers**: [Who reviewed the fix]  
**Date**: YYYY-MM-DD  
**Version Fixed**: vX.Y.Z  
**Framework Version**: 1.2.0  
**Template Version**: 1.0

**Tags**: `bug`, `[component]`, `[severity]`, `[category]`

---

## Appendix

### Additional Notes
[Any other relevant information]

### Lessons Learned
1. **What Went Well**: [Positive aspects]
2. **What Could Be Improved**: [Areas for improvement]
3. **Key Takeaways**: [Main lessons]

### Future Considerations
[Ideas for future improvements or refactoring related to this area]

---

**Last Updated**: YYYY-MM-DD  
**Status**: ✅ FIXED | 🚧 IN PROGRESS | ⏸️ DEFERRED | ❌ WONTFIX

