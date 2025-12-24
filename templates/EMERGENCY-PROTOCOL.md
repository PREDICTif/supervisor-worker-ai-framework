# Emergency Response Protocol

> **Purpose**: Define procedures for handling critical situations, blockers, and emergencies during AI-assisted development.

**Framework Version**: 1.2.0  
**Last Updated**: December 2025

---

## When to Use This Protocol

Use this protocol when encountering:
- 🔴 **Production outages** or critical bugs
- 🔴 **Security vulnerabilities** discovered
- 🟡 **Major blockers** preventing all progress
- 🟡 **Architecture pivots** requiring significant rework
- 🟡 **Data loss** or corruption issues
- 🟡 **Deadline-critical** situations

---

## Emergency Severity Levels

### 🔴 SEV1 - Critical Emergency
**Definition**: System down, data loss, security breach, or production outage  
**Response Time**: Immediate (within 15 minutes)  
**Escalation**: Required

**Examples**:
- Production API completely down
- Security breach or data leak
- Data corruption affecting users
- Critical feature completely broken in production

### 🟡 SEV2 - High Urgency
**Definition**: Major functionality impaired, significant user impact  
**Response Time**: Within 1 hour  
**Escalation**: If not resolved in 2 hours

**Examples**:
- Key feature broken for subset of users
- Performance degradation affecting UX
- Critical third-party service down
- Major blocker preventing deployment

### 🟢 SEV3 - Medium Urgency
**Definition**: Moderate impact, workaround available  
**Response Time**: Within 4 hours  
**Escalation**: If not resolved in 1 day

**Examples**:
- Non-critical feature broken
- Minor performance issues
- Development blocker with workaround
- Testing infrastructure issues

---

## 🔴 SEV1 - Critical Emergency Response

### Immediate Actions (First 15 Minutes)

1. **🛑 STOP All Other Work**
   - Halt all feature development
   - Cancel all scheduled meetings/demos
   - Focus 100% on emergency

2. **📢 Declare Emergency**
   - Update `CURRENT-STATUS.md` with 🚨 EMERGENCY banner
   - Create `EMERGENCY-[DATE]-[ISSUE].md` document
   - Notify all stakeholders immediately

3. **🔍 Quick Assessment**
   - What is broken?
   - Who is affected?
   - When did it start?
   - Is it getting worse?

4. **🛡️ Damage Control**
   - Can you rollback? (Do it immediately if safe)
   - Can you disable the feature?
   - Can you redirect traffic?
   - Can you isolate the problem?

### Investigation Phase (15-60 Minutes)

**EMERGENCY-[DATE]-[ISSUE].md Template:**

```markdown
# 🚨 EMERGENCY: [Issue Title]

## Status: 🔴 ACTIVE | 🟡 INVESTIGATING | 🟢 RESOLVED

**Started**: YYYY-MM-DD HH:MM UTC  
**Resolved**: [Pending]  
**Duration**: [X minutes/hours]

## Impact
- **Severity**: SEV1
- **Affected**: [All users | X% of users | Specific feature]
- **Business Impact**: [Revenue loss | User data | Reputation]

## Timeline
| Time | Event |
|------|-------|
| HH:MM | Issue first detected |
| HH:MM | Emergency declared |
| HH:MM | Investigation started |
| HH:MM | Root cause identified |
| HH:MM | Fix deployed |
| HH:MM | Verified resolved |

## Root Cause
[What caused this - fill in as discovered]

## Actions Taken
1. [Action 1 - timestamp]
2. [Action 2 - timestamp]
3. [Action 3 - timestamp]

## Current Status
[Real-time status updates]

## Next Steps
1. [Immediate next action]
2. [Following action]
```

### Resolution Phase

1. **🔧 Implement Fix**
   - Create hotfix branch: `hotfix/emergency-[issue]`
   - Make minimal changes to fix issue
   - Test thoroughly (but quickly)
   - Document every change

2. **✅ Verification**
   - Verify fix in staging
   - Test affected functionality
   - Check for side effects
   - Get second pair of eyes if possible

3. **🚀 Deploy**
   - Deploy to production immediately
   - Monitor closely for 30 minutes
   - Keep rollback plan ready
   - Document deployment

4. **📊 Confirm Resolution**
   - Verify issue is resolved
   - Check metrics/logs
   - Get user confirmation if possible
   - Monitor for 1-2 hours

### Post-Emergency (After Resolution)

1. **📝 Post-Mortem Required**
   - Create detailed incident report
   - Schedule post-mortem meeting (within 24 hours)
   - Document lessons learned
   - Update prevention strategies

2. **🔄 Follow-Up Actions**
   - Add regression tests
   - Fix related issues
   - Update monitoring/alerts
   - Improve documentation

---

## 🟡 SEV2 - High Urgency Response

### Immediate Actions (First Hour)

1. **⏸️ Pause Non-Critical Work**
   - Continue only P0 tasks
   - Defer all P2/P3 work
   - Focus on blocker resolution

2. **📊 Document Blocker**
   - Update `DELEGATION-TRACKER.md` with ⚠️ BLOCKED status
   - Update `CURRENT-STATUS.md` with blocker details
   - Create clear issue description

3. **🎯 Assess Options**
   - Can you work around it?
   - Can you pivot to different approach?
   - What's needed to unblock?
   - Who can help?

### Resolution Strategy

**BLOCKER Template in DELEGATION-TRACKER.md:**

```markdown
## ⚠️ BLOCKED TASK: [Task Name]

**Status**: 🟡 SEV2 - HIGH URGENCY  
**Blocked Since**: YYYY-MM-DD HH:MM  
**Impact**: [What can't proceed]

**Blocker Description**:
[Clear description of what's blocking progress]

**Tried**:
- [x] [Attempted solution 1] - Failed because [reason]
- [x] [Attempted solution 2] - Failed because [reason]
- [ ] [Potential solution 3] - To try next

**Escalation**:
- **To**: [User | Team Lead | Vendor]
- **Requested**: [What you need]
- **ETA**: [Expected resolution time]

**Workaround**:
[Temporary solution if available, or "None available"]

**Impact if Not Resolved**:
[What happens if this stays blocked]
```

### Escalation Triggers

Escalate to user/stakeholder if:
- Can't resolve within 2 hours
- Need external resources (API keys, credentials, etc.)
- Requires architectural decision
- Blocks critical path items
- Technical solution unclear

---

## 🟢 SEV3 - Medium Urgency Response

### Standard Blocker Handling

1. **📝 Document**
   - Update task status to ⚠️ BLOCKED
   - Document blocker clearly
   - Note attempted solutions

2. **🔄 Pivot**
   - Switch to unblocked tasks
   - Make progress elsewhere
   - Return when unblocked

3. **⏰ Set Follow-Up**
   - Schedule check-in (4-24 hours)
   - Set reminder to revisit
   - Track in DELEGATION-TRACKER

---

## Major Pivot Protocol

### When Architecture/Approach Must Change

**Triggers for Major Pivot**:
- Chosen technology doesn't work as expected
- Requirements changed significantly  
- Discovered better approach mid-implementation
- External dependency unavailable

### Pivot Procedure

1. **🛑 STOP Current Work**
   - Commit current state to branch
   - Document progress to date
   - Create detailed handover

2. **📚 Document Current State**
   Create `PIVOT-[DATE]-[REASON].md`:
   
   ```markdown
   # Major Pivot: [Reason]
   
   ## Original Plan
   [What was originally planned]
   
   ## Why Pivot Required
   [Detailed reasoning]
   
   ## Current Progress
   - [X] Completed: [List]
   - [ ] Incomplete: [List]
   - Files: [List of modified files]
   
   ## New Approach
   [What will be done instead]
   
   ## Work to Salvage
   [What can be reused]
   
   ## Work to Discard
   [What must be discarded]
   
   ## Estimated Impact
   - Time: +/- X hours/days
   - Scope: [Changes]
   - Risk: [Assessment]
   ```

3. **🔄 Update Planning Docs**
   - Update `THINKING-LOG.md` with rationale
   - Update `CURRENT-STATUS.md` with new direction
   - Update `DELEGATION-TRACKER.md` with new tasks
   - Archive old plans

4. **📢 Notify Stakeholders**
   - Explain why pivot is needed
   - Show new approach
   - Get buy-in
   - Adjust expectations

5. **🎯 Create New Plan**
   - Break down new approach
   - Create new delegations
   - Update timelines
   - Document thoroughly

---

## Communication Templates

### Emergency Notification

```markdown
🚨 EMERGENCY: [Issue Title]

Severity: SEV1 | SEV2 | SEV3
Impact: [Brief description]
Status: [Current status]

Actions Taken:
1. [Action]
2. [Action]

Next Steps:
1. [Next step]

ETA: [Expected resolution time]

Updates: [How/where you'll provide updates]
```

### Blocker Escalation

```markdown
⚠️ BLOCKED: Need Help

Task: [What you're trying to do]
Blocker: [What's blocking you]

Tried:
- [Solution attempt 1]
- [Solution attempt 2]

Need:
[Specifically what you need to unblock]

Impact:
[What can't proceed without this]

Urgency: [Why this matters now]
```

### Pivot Notification

```markdown
🔄 MAJOR PIVOT: [Reason]

Original: [Original plan]
New: [New approach]

Reason: [Why pivot is necessary]

Impact:
- Time: +/- X
- Scope: [Changes]
- Risk: [Assessment]

Approval Needed: [Yes/No]
```

---

## Recovery Checklist

After any emergency, complete this checklist:

### Immediate (Within 24 Hours)
- [ ] Issue fully resolved
- [ ] Monitoring confirms stability
- [ ] Emergency documentation complete
- [ ] Stakeholders notified of resolution
- [ ] Hot fix properly documented
- [ ] CHANGELOG updated

### Short-Term (Within 1 Week)
- [ ] Post-mortem completed
- [ ] Root cause analysis documented
- [ ] Regression tests added
- [ ] Related issues identified and fixed
- [ ] Monitoring/alerting improved
- [ ] Documentation updated

### Long-Term (Within 1 Month)
- [ ] Prevention strategies implemented
- [ ] Process improvements made
- [ ] Team trained on lessons learned
- [ ] Similar code patterns reviewed
- [ ] Architecture improvements considered

---

## Prevention Strategies

### Proactive Measures

1. **Testing**
   - Comprehensive test coverage
   - Integration tests for critical paths
   - Load/stress testing before deployment
   - Regression tests for all bugs

2. **Monitoring**
   - Health checks on critical services
   - Error rate monitoring
   - Performance monitoring
   - User impact metrics

3. **Process**
   - Code review for all changes
   - Staging environment testing
   - Gradual rollouts
   - Rollback procedures ready

4. **Documentation**
   - Clear architecture docs
   - Runbooks for common issues
   - Deployment procedures
   - Emergency contacts

---

## Rollback Procedures

### Quick Rollback (Under 5 Minutes)

```bash
# 1. Identify last good version
git log --oneline

# 2. Revert to last good commit
git revert [commit-hash]

# 3. Deploy immediately
./deploy.sh production

# 4. Verify
curl https://api.example.com/health
```

### Full Rollback (5-15 Minutes)

1. Identify last stable version
2. Checkout that version
3. Run full test suite
4. Deploy to production
5. Verify all functionality
6. Monitor for 30 minutes

---

## Contact Information

### Escalation Chain

1. **Level 1**: Continue working, document blocker
2. **Level 2**: Notify project lead/user
3. **Level 3**: Escalate to technical lead
4. **Level 4**: Escalate to stakeholders

### Emergency Contacts

- **User/Project Owner**: [Contact]
- **Technical Lead**: [Contact]
- **DevOps/Infrastructure**: [Contact]
- **Security Team**: [Contact]

---

**Remember**: 
- Stay calm
- Document everything
- Communicate clearly
- Fix first, analyze later
- Learn and improve

---

**Template Version**: 1.0  
**Framework Version**: 1.2.0  
**Last Updated**: December 2025

