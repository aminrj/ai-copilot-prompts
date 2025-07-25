# Debugging Prompts

Systematic approaches to problem-solving, troubleshooting, and code analysis.

---

## Systematic Analysis

**File: `prompts/02-debugging/systematic-analysis.md`**

### 🎯 Purpose

Debug any issue methodically using a structured investigative approach.

### 📋 Template

```markdown
Debug this issue systematically:

## Problem Statement

**Issue**: [Describe the problem clearly]
**Expected Behavior**: [What should happen]
**Actual Behavior**: [What actually happens]
**Environment**: [Development/Staging/Production]
**Frequency**: [Always/Sometimes/Rare - include percentage if known]
**Impact**: [User impact, business impact, system impact]

## Current State Investigation

### Immediate Symptoms

- **Error Messages**: [Exact error text, stack traces]
- **Log Entries**: [Relevant log entries with timestamps]
- **User Reports**: [What users are experiencing]
- **System Metrics**: [CPU, memory, network, database metrics]

### Reproduction Information

- **Steps to Reproduce**: [Exact steps that trigger the issue]
- **Required Conditions**: [Specific data, user states, system conditions]
- **Success Rate**: [How often reproduction succeeds]
- **Minimum Reproducible Example**: [Simplest case that shows the problem]

## Context Analysis

### Recent Changes

- **Code Deployments**: [Recent releases, commits, PRs merged]
- **Configuration Changes**: [Environment variables, feature flags, settings]
- **Infrastructure Changes**: [Server updates, scaling events, migrations]
- **Data Changes**: [Schema updates, large data operations, imports]
- **Dependencies**: [Library updates, external service changes]

### System Environment

- **Architecture**: [Components involved in the failure path]
- **Data Flow**: [How data moves through the system to the failure point]
- **Dependencies**: [External services, databases, queues involved]
- **Load Patterns**: [Current traffic, unusual spikes, timing patterns]

## Systematic Investigation

### 1. Isolate the Scope

- **Component Level**: Which specific service/module is failing?
- **Function Level**: Which specific function/method has the issue?
- **Data Level**: Does it affect all data or specific subsets?
- **User Level**: Does it affect all users or specific segments?
- **Time Level**: When did this start? Is there a pattern?

### 2. Hypothesis Generation

Based on symptoms and context, what are the most likely causes?

**Rank by probability:**

1. **[Most Likely]**: [Hypothesis with reasoning]
2. **[Likely]**: [Second hypothesis with reasoning]
3. **[Possible]**: [Third hypothesis with reasoning]
4. **[Edge Case]**: [Low probability but possible]

### 3. Evidence Collection Plan

For each hypothesis, what evidence would prove or disprove it?

**Hypothesis 1 Evidence**:

- [ ] Check [specific logs/metrics/database queries]
- [ ] Test [specific scenarios/inputs]
- [ ] Verify [specific system states/configurations]

**Hypothesis 2 Evidence**:

- [ ] [Investigation steps]

### 4. Systematic Testing

**Test Plan**:

1. **Validate Current State**: Confirm the problem still exists
2. **Test Hypotheses**: Run experiments to prove/disprove each theory
3. **Isolate Variables**: Change one thing at a time
4. **Document Results**: Record what works and what doesn't

## Root Cause Analysis

Once you identify the immediate cause:

### 1. Deep Cause Investigation

- **Why did this specific failure occur?**
- **Why wasn't this caught earlier?**
- **Why did our safeguards fail?**
- **Why wasn't this detected by monitoring?**
- **Why wasn't this prevented by our processes?**

### 2. Contributing Factors

- **Technical factors**: Code quality, architecture decisions, tooling
- **Process factors**: Testing, deployment, code review processes
- **Human factors**: Knowledge gaps, communication issues, time pressure
- **Organizational factors**: Resource constraints, priority conflicts

## Solution Strategy

### 1. Immediate Fix

- **Hotfix**: [Quick fix to restore service]
- **Rollback**: [Revert to previous working state if possible]
- **Workaround**: [Temporary solution while developing proper fix]

### 2. Proper Solution

- **Root Cause Fix**: [Address the fundamental issue]
- **Code Changes**: [Specific implementation fixes]
- **Configuration Updates**: [Setting changes needed]
- **Process Improvements**: [Changes to prevent recurrence]

### 3. Prevention Strategy

- **Testing Improvements**: [What tests would have caught this?]
- **Monitoring Enhancements**: [What monitoring would detect this faster?]
- **Code Quality**: [What practices would prevent this class of bug?]
- **Process Changes**: [What process changes would help?]

## Implementation Plan

### Phase 1: Immediate Response (< 1 hour)

- [ ] [Immediate actions to restore service]
- [ ] [User communication if needed]
- [ ] [Monitoring setup to track fix effectiveness]

### Phase 2: Proper Fix (< 24 hours)

- [ ] [Implement root cause fix]
- [ ] [Test thoroughly in staging]
- [ ] [Deploy with monitoring]
- [ ] [Verify fix in production]

### Phase 3: Prevention (< 1 week)

- [ ] [Add tests to prevent regression]
- [ ] [Improve monitoring/alerting]
- [ ] [Update documentation/runbooks]
- [ ] [Share lessons learned with team]

## Verification Plan

### Fix Validation

- **Functional Testing**: [Verify the fix works as expected]
- **Regression Testing**: [Ensure no new issues introduced]
- **Performance Testing**: [Verify performance impact]
- **User Acceptance**: [Confirm user-reported issues resolved]

### Monitoring Strategy

- **Key Metrics**: [What metrics indicate success?]
- **Alert Thresholds**: [What should trigger alerts?]
- **Dashboard Updates**: [What visualizations help track this?]

Provide the systematic analysis and solution for this specific issue.
```

### 💡 Usage Example

```markdown
Debug this issue systematically:

## Problem Statement

**Issue**: User registration API returns 500 errors intermittently
**Expected Behavior**: All valid registration attempts should return 201 with user data
**Actual Behavior**: ~15% of registration attempts return 500 "Internal Server Error"
**Environment**: Production
**Frequency**: 15% of attempts, no clear pattern
**Impact**: Users can't create accounts, estimated $5k/day revenue loss

## Current State Investigation

### Immediate Symptoms

- **Error Messages**: "Error: duplicate key value violates unique constraint 'users_email_unique'"
- **Log Entries**: 2025-01-15 14:32:15 ERROR Database connection timeout after 5s
- **User Reports**: "Registration form shows 'Something went wrong' message"
- **System Metrics**: Database CPU at 85%, connection pool 90% utilized

### Reproduction Information

- **Steps to Reproduce**:
  1. Fill registration form with valid email
  2. Submit form
  3. 15% chance of failure, no pattern based on email/timing
- **Required Conditions**: Production load, doesn't happen in staging
- **Success Rate**: 85% success, 15% failure
- **Minimum Reproducible Example**: Single registration API call with valid data

## Context Analysis

### Recent Changes

- **Code Deployments**: User service v2.3.1 deployed 3 days ago
- **Configuration Changes**: Database connection pool increased from 20 to 50 connections yesterday
- **Infrastructure Changes**: None in past week
- **Data Changes**: User table has grown 40% in past month (now 2.5M records)
- **Dependencies**: No external service changes

### System Environment

- **Architecture**: Load balancer → 3 API servers → PostgreSQL primary + read replica
- **Data Flow**: API validates input → checks email uniqueness → inserts user → returns response
- **Dependencies**: PostgreSQL, Redis cache, email service (SendGrid)
- **Load Patterns**: Peak registration during lunch hours (12-2pm), matches error timing

## Systematic Investigation

### 1. Isolate the Scope

- **Component Level**: User registration service specifically
- **Function Level**: Email uniqueness check + user insertion
- **Data Level**: All email domains affected equally
- **User Level**: All user types affected equally
- **Time Level**: Started 3 days ago with v2.3.1 deployment

### 2. Hypothesis Generation
```
