# Dependency & Integration Tracking Guide

## Purpose
Proactively identify, track, and manage cross-team dependencies and integration points to prevent surprises, delays, and integration failures.

## Dependency Types

### 1. **External Dependencies**
Dependencies on outside teams, services, or vendors
- Examples: API from partner team, data from external system, third-party SaaS, compliance approval
- Risk: Outside team delays impact your timeline; lack of visibility

### 2. **Internal Dependencies**
Dependencies between internal teams or components
- Examples: Backend API must be ready for frontend, shared library version, infra resource provisioning
- Risk: Misaligned timelines; miscommunication between teams

### 3. **Technical Dependencies**
Technical constraints or library/framework decisions
- Examples: Database schema migration, library upgrade, API version compatibility
- Risk: Technical blocker discovered late; rework required

### 4. **Compliance / Security Dependencies**
Approvals or requirements from compliance, security, or legal
- Examples: Data classification approval, security scan clearance, GDPR review
- Risk: Gate discovered late in timeline; project delayed for review

---

## Dependency Discovery & Mapping

### During Planning Phase

**Discovery Activities:**
1. **Kickoff meeting**: Ask explicitly: "What external teams/systems do we depend on?"
2. **Technical design review**: Tech Lead identifies technical and integration points
3. **Security/Ops reviews**: Security and Ops identify compliance and operational dependencies
4. **Cross-team sync**: Share initial roadmap with dependent teams

**Dependency Register Template:**
- ID (DEP-001, DEP-002, etc.)
- Name / Description
- Type (External, Internal, Technical, Compliance)
- Dependent Team / Component
- Critical Path? (Yes/No — blocks release)
- Planned Handoff Date
- Owner
- Risk Level (High/Med/Low)

### Example Dependency Register

| ID | Description | Type | Team | Critical | Handoff | Owner | Risk |
|-----|-----------|------|------|----------|---------|-------|------|
| DEP-001 | Auth API v2 ready | Internal | Auth Team | Yes | May 20 | Sarah (Auth PM) | High |
| DEP-002 | Database migration script | Technical | DevOps | Yes | May 18 | Alex (Tech Lead) | Med |
| DEP-003 | Security pen test clearance | Compliance | Security | Yes | May 27 | Jamie (Security) | High |
| DEP-004 | Payment provider API docs | External | Stripe | No | May 15 | Kim (Dev) | Low |

---

## Collaboration Timeline by Phase

### **Planning Phase (Weeks 1-2)**

**Initiate Dependencies:**
- [ ] Create dependency register with all identified items
- [ ] Assign owner to each dependency
- [ ] Reach out to dependent teams: "We'll need X by date Y"
- [ ] Set up recurring syncs with teams owning critical dependencies
- [ ] Document fallback/mitigation plans for high-risk items

**Deliverable**: Signed-off dependency register shared with all teams

---

### **Execution Phase (Weeks 3-8)**

**Weekly Dependency Monitoring (PM Checklist):**
- [ ] Review each open dependency in Monday standup with owner
- [ ] Ask: "Still on track? Any blockers?" 
- [ ] If at risk (80% of planned date): escalate and activate mitigation plan
- [ ] Update status in dependency register (Green / Yellow / Red)
- [ ] Add any newly discovered dependencies immediately

**Monthly Dependency Review (PM + Product Lead):**
- [ ] Assess cumulative impact of delayed dependencies
- [ ] Discuss timeline risk: Is release date at risk? 
- [ ] Escalate critical delays to Sponsor
- [ ] Adjust project plan if needed

---

### **Release Phase (Weeks 8-10)**

**Pre-Release Dependency Validation:**
- [ ] All critical dependencies marked "Complete" or "Mitigated"
- [ ] Integration testing passed for all external/internal handoffs
- [ ] Compliance approvals received (no outstanding reviews)
- [ ] Rollback plans account for dependency failures

**Go/No-Go Gate:**
- [ ] PM: "Are all dependencies met or mitigated?" ✓
- [ ] Tech Lead: "Are all technical dependencies resolved?" ✓
- [ ] Security: "Are compliance dependencies complete?" ✓

---

## Integration Testing & Handoff Checklist

For each critical dependency, validate the integration before release:

### **API Integration (Internal or External)**
- [ ] API documentation reviewed and understood
- [ ] Dev environment setup and API accessible
- [ ] Test cases written for normal and error paths
- [ ] Happy path tested and passing
- [ ] Error handling and edge cases tested
- [ ] Performance benchmarks met (latency, throughput)
- [ ] Monitoring/alerting configured for API calls
- [ ] Runbook updated with troubleshooting steps

### **Data Handoff (Database, File, API)**
- [ ] Data format and schema documented
- [ ] Sample data provided and validated
- [ ] Data migration tested in non-prod environment
- [ ] Data validation rules implemented
- [ ] Backwards compatibility verified (if existing data)
- [ ] Rollback procedure tested

### **Shared Library or Component**
- [ ] Version compatibility verified
- [ ] Breaking changes understood and handled
- [ ] Test coverage for integration points
- [ ] Documentation updated
- [ ] Build/deployment process includes new dependency

### **Team Handoff (e.g., Ops, QA, Support)**
- [ ] Runbook/operations guide completed and validated
- [ ] Training session held with receiving team
- [ ] Q&A on design decisions and troubleshooting
- [ ] Support playbook finalized
- [ ] Escalation paths and on-call procedures defined

---

## Escalation Playbook: Common Dependency Scenarios

### **Scenario 1: Dependency Delayed (Red Flag)**

**Situation**: Dependent team says they'll miss handoff date by 1+ weeks

**Immediate Action (24 hours):**
1. PM: Schedule call with dependent team + Product Leads (both sides)
2. Understand root cause: Is it fixable? Temporary or permanent?
3. Assess impact: Can your team work around it? Parallel path?

**Options:**
- **Option A: Negotiate earlier interim delivery** (e.g., API with limited features)
- **Option B: Parallel work** (e.g., mock the dependency, continue development)
- **Option C: Scope out dependency** (ship without it or defer to next release)
- **Option D: Extend timeline** (only if customer/sponsor approves)

**Decision & Communication:**
- PM: Make decision with PdM + Tech Lead
- PM: Communicate decision to Sponsor if timeline impacts
- All teams: Update roadmaps and dependencies register

---

### **Scenario 2: Silent Dependency (Surprise)**

**Situation**: Dependency discovered late (week 7 of 10-week project)

**Immediate Action (24 hours):**
1. Tech Lead / PM: Assess criticality — is it a blocker?
2. If blocker: Escalate to Level 2 (Product Lead + dependent teams)
3. If non-critical: Add to backlog for next phase

**Mitigation Options:**
- Work around it or mock it for this release
- Expedite the dependent team's work (add resources)
- Push feature to next release

**Prevention:**
- Retrospective: Why was this missed? (Planning process improvement)
- Add checklist item: "Identify all dependencies in planning phase"

---

### **Scenario 3: Integration Failure in Testing (Red Flag)**

**Situation**: Integration test fails in staging; root cause is dependent team's API bug

**Immediate Action (24 hours):**
1. QA Lead: Confirm the issue; document exact failure
2. PM: Contact dependent team with issue details
3. Dependent team: Acknowledge and provide timeline to fix
4. Your Tech Lead: Assess impact — can you proceed without this integration or with workaround?

**Options:**
- Dependent team fixes in time for release
- Use workaround / mock for release; patch after go-live
- Scope out feature from this release

---

### **Scenario 4: Compliance Approval Not Received (Red Flag)**

**Situation**: Security team hasn't completed pen test 2 weeks before release

**Immediate Action (48 hours):**
1. PM: Escalate to Sponsor + Product Lead + Security Leader
2. Understand blocker: Is it resourcing? Technical issue?
3. Assess criticality: Can you release with mitigation plan?

**Options:**
- Security expedites review (priority bump)
- Release to limited audience with enhanced monitoring
- Delay release until security approval obtained
- Implement mitigation controls and monitor closely

---

## Dependency Communication Template

**To**: Dependent team (via email or Slack)
**Subject**: Dependency Status & Timeline Alignment — [Project Name]

---

Hi [Team Name],

We need to sync up on the timeline for [dependency name]. Here's what we're planning:

**Our Timeline:**
- Milestone: [Feature/Release Name]
- Target Go-Live: [Date]
- We need [dependency] by [date] to meet this

**What we need from you:**
- [Specific deliverable description]
- [Format/interface specification]
- [Acceptance criteria]

**Key questions for you:**
- Is your team on track to deliver by [date]?
- What are your dependencies that could impact this?
- Any risks or concerns we should know about?

**Next steps:**
- Let's sync on [date] to align on details
- I'll track this in our dependency register and follow up weekly

Thanks for partnering with us on this!

[Your name]

---

## Dependency Retrospective & Lessons Learned

**Post-Release, discuss:**

1. **What dependencies did we identify upfront?** Which did we miss?
2. **Which dependencies caused the most risk or delay?**
3. **How effective was our escalation protocol?**
4. **What process improvements would help next time?**
   - Better discovery questions?
   - Earlier engagement with external teams?
   - Better contingency planning?
   - Clearer contracts / SLAs with dependent teams?

5. **Action items for next project:**
   - Add dependency discovery checklist to planning
   - Create dependency communication template
   - Build in 1-week buffer for critical paths
   - Schedule kickoff syncs with dependent teams earlier

