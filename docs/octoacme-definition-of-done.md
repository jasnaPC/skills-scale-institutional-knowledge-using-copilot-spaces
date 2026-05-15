# Definition of Done (DoD) Template

## Purpose
Define clear, measurable criteria that all work must meet before being considered "complete" and ready to move to the next phase or release.

## Use Cases
- Include in sprint planning and backlog refinement
- Validate during code review and QA sign-off
- Confirm during release readiness checks

---

## Feature Development Definition of Done

### Code Quality
- [ ] Code follows team coding standards and style guide
- [ ] All new code has unit test coverage (≥ 80% for new logic)
- [ ] Existing tests still pass (no regressions)
- [ ] Code review approved by at least one senior developer
- [ ] No known technical debt introduced

### Design & Architecture
- [ ] Design aligns with system architecture approved by Tech Lead
- [ ] Integration points documented (APIs, dependencies, data flows)
- [ ] Scalability implications assessed and acceptable
- [ ] No breaking changes to public interfaces (or documented migration path)

### Documentation
- [ ] Code comments on complex logic and edge cases
- [ ] API documentation updated (if applicable)
- [ ] Feature documented in user-facing docs or help center
- [ ] Runbook/operations guide created (if needed)

### Security & Compliance
- [ ] Security requirements reviewed and implemented
- [ ] No hardcoded secrets or sensitive data in code
- [ ] Input validation and error handling in place
- [ ] Security scan passed (automated or manual review)
- [ ] Privacy/GDPR considerations addressed (if applicable)

### Testing
- [ ] Unit tests written and passing
- [ ] Integration tests written and passing (if applicable)
- [ ] E2E smoke tests passing on staging
- [ ] QA acceptance testing completed
- [ ] Edge cases and error scenarios tested
- [ ] Accessibility testing completed (if user-facing)

### Performance & Operations
- [ ] Performance impact assessed and acceptable
- [ ] Monitoring and alerting configured
- [ ] Logging added for troubleshooting
- [ ] Database migrations (if any) tested and reversible
- [ ] Ops runbook created and validated

### Acceptance & Sign-Off
- [ ] All acceptance criteria from user story met
- [ ] Product Manager has reviewed and approved
- [ ] QA Lead has signed off on test completion
- [ ] Tech Lead has signed off on design and code quality
- [ ] No open blockers or technical debt items

---

## Bug Fix Definition of Done

### Investigation & Analysis
- [ ] Root cause identified and documented
- [ ] Reproduction steps documented
- [ ] Impact scope assessed (how many customers affected)
- [ ] Severity level assigned

### Fix Implementation
- [ ] Fix implemented and code reviewed
- [ ] Root cause fixed (not just symptom patching)
- [ ] Related code assessed for similar issues
- [ ] Test case added to prevent regression
- [ ] Performance impact verified

### Validation & Testing
- [ ] Fix verified in development environment
- [ ] Fix verified in staging environment
- [ ] Regression tests passing
- [ ] QA acceptance testing completed
- [ ] Customer reproduction case validated

### Release & Monitoring
- [ ] Release notes include bug fix details
- [ ] Monitoring configured to detect if issue recurs
- [ ] Support team briefed on fix
- [ ] Customer notification sent (if high-impact)

---

## Release Definition of Done

### Pre-Release Validation
- [ ] All features and fixes have DoD met
- [ ] All acceptance criteria passed
- [ ] Security scan passed with no critical issues
- [ ] Performance tests passed (latency, throughput)
- [ ] Backwards compatibility verified (no breaking changes)

### Documentation & Communication
- [ ] Release notes finalized and reviewed
- [ ] Migration guide created (if needed)
- [ ] Known issues and workarounds documented
- [ ] Support team briefed and trained
- [ ] Customer communication drafted

### Deployment Readiness
- [ ] Deployment runbook created and reviewed
- [ ] Rollback plan documented and tested
- [ ] Backup/snapshot created (if applicable)
- [ ] Monitoring and alerting configured
- [ ] Ops team trained and ready

### Post-Release Readiness
- [ ] Smoke test plan created and staged
- [ ] Support escalation paths verified
- [ ] Customer success team ready for go-live
- [ ] Incident response team on standby
- [ ] Status page ready for updates

### Go/No-Go Decision
- [ ] PM confirms go/no-go
- [ ] QA Lead confirms go/no-go
- [ ] Tech Lead confirms go/no-go
- [ ] Ops Lead confirms go/no-go
- [ ] Sponsor confirms go/no-go

---

## Sprint/Iteration Definition of Done

### Backlog Preparation
- [ ] Sprint backlog prioritized by PdM
- [ ] All items have acceptance criteria and estimation
- [ ] Team capacity planned
- [ ] High-risk or complex items have technical design docs

### Daily Progress
- [ ] Daily standups held
- [ ] Blockers identified and escalated same day
- [ ] Code commits reference issue/PR
- [ ] Pull requests opened for in-progress work

### Mid-Sprint (Optional)
- [ ] At-risk items re-estimated and escalated
- [ ] Scope change requests logged (not auto-committed)
- [ ] Technical risks assessed and mitigated

### Sprint Close
- [ ] All planned work completed (or explicitly deferred with reason)
- [ ] All PRs merged with required approvals
- [ ] Acceptance testing complete
- [ ] Retrospective held and action items assigned
- [ ] Metrics captured (velocity, quality, cycle time)
- [ ] Sprint notes and learnings documented

---

## How to Use This Template

1. **During Planning**: Review and customize DoD for your project's context
2. **During Sprint Planning**: Reference DoD when estimating and pulling items
3. **During Development**: Use as checklist for developer PRs
4. **During Review**: QA and Tech Lead reference DoD for sign-off
5. **During Release**: Confirm all release DoD criteria met before go-live
6. **During Retrospectives**: Discuss if DoD was realistic and achievable

## Customization Guidance

- Adapt criteria to your team's tech stack (e.g., specific test frameworks, deployment tools)
- Add org-specific requirements (e.g., specific security scanning tools, compliance frameworks)
- Adjust test coverage targets based on risk tolerance and domain (e.g., financial systems may need >90%)
- Include performance benchmarks for your application
- Reference your team's specific style guides and standards

