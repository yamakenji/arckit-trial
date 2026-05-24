# ARC-001-RISK-v1.0 — Risk Register

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-RISK-v1.0 |
| **Document Type** | Risk Register |
| **Project** | Legacy Order Management Modernization (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-05-23 |
| **Last Modified** | 2026-05-23 |
| **Review Date** | 2026-06-23 |
| **Owner** | [PENDING] |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Project Team, Architecture Team, Steering Committee |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-05-23 | ArcKit AI | Initial creation from `/arckit:risk` command | [PENDING] | [PENDING] |

## Orange Book Compliance

This risk register follows HM Treasury's **Orange Book (2023)** risk management framework:

- **5 Risk Management Principles**: Governance, Integration, Collaboration, Risk Processes, Continual Improvement
- **4Ts Response Framework**: Tolerate, Treat, Transfer, Terminate
- **Risk Scoring**: Likelihood × Impact (1–25 scale) for Inherent and Residual risk
- **Risk Categories**: Strategic, Operational, Financial, Compliance, Reputational, Technology

---

## A. Executive Summary

### Risk Profile

| Metric | Value |
|--------|-------|
| **Total Risks Identified** | 20 |
| **Total Inherent Score** | 252 |
| **Total Residual Score** | 135 |
| **Score Reduction from Controls** | 46% |
| **Overall Risk Profile** | Concerning — requires active management |

### Distribution

| Rating | Inherent | Residual |
|--------|----------|----------|
| Critical (20–25) | 1 | 0 |
| High (13–19) | 6 | 0 |
| Medium (6–12) | 13 | 17 |
| Low (1–5) | 0 | 3 |

### Risks by Category

| Category | Count | Key Risks |
|----------|-------|-----------|
| STRATEGIC | 3 | Programme scope creep, executive sponsorship |
| OPERATIONAL | 4 | Legacy drag on engineering, partner adoption |
| FINANCIAL | 3 | Dual-run costs, budget overrun, TCO target |
| COMPLIANCE | 2 | PCI-DSS, GDPR right-to-erasure |
| REPUTATIONAL | 2 | Service degradation, data loss |
| TECHNOLOGY | 6 | Skills gap, ACL design, data quality, security breach |

### Risks Exceeding Appetite

| Risk | Category | Residual Score | Threshold | Action |
|------|----------|----------------|-----------|--------|
| R-004 | OPERATIONAL | 9 | 8 | Escalate to Steering Committee |
| R-011 | COMPLIANCE | 8 | 6 | Escalate to CISO + Compliance Board |

### Top Risks Requiring Immediate Attention

1. **R-004** (OPERATIONAL, Inherent Critical 20): Engineering capacity — legacy drag — *Owner: CTO/CIO*
2. **R-001** (STRATEGIC, Inherent High 16): Programme scope creep — *Owner: Executive Sponsor*
3. **R-006** (TECHNOLOGY, Inherent High 16): AWS/cloud-native skills gap — *Owner: CTO/CIO*
4. **R-011** (COMPLIANCE, Inherent High 15): PCI-DSS re-certification missed — *Owner: CISO/Compliance*
5. **R-020** (TECHNOLOGY, Inherent High 15): Security breach during migration — *Owner: CISO*

---

## B. Risk Matrix Visualization

### Inherent Risk Matrix (Before Controls)

```
                                  IMPACT
              1-Minimal   2-Minor    3-Moderate   4-Major    5-Severe
           ┌───────────┬───────────┬───────────┬───────────┬───────────┐
5-Almost   │           │           │           │  R-004    │           │
Certain    │    5      │    10     │    15     │    20     │    25     │
           ├───────────┼───────────┼───────────┼───────────┼───────────┤
4-Likely   │           │           │  R-005    │  R-001    │           │
           │    4      │    8      │    12     │    16     │    20     │
L          │           │           │  R-007    │  R-006    │           │
I          │           │           │  R-008    │  R-013    │           │
K          │           │           │  R-015    │           │           │
E          │           │           │  R-017    │           │           │
L          ├───────────┼───────────┼───────────┼───────────┼───────────┤
I 3-Possible│          │           │  R-010    │  R-009    │  R-011    │
H          │    3      │    6      │    9      │    12     │    15     │
O          │           │           │           │  R-012    │  R-014    │
O          │           │           │           │  R-016    │  R-020    │
D          │           │           │           │  R-018    │           │
           ├───────────┼───────────┼───────────┼───────────┼───────────┤
2-Unlikely │           │           │  R-003    │  R-002    │           │
           │    2      │    4      │    6      │    10     │    10     │
           │           │           │  R-019    │           │           │
           ├───────────┼───────────┼───────────┼───────────┼───────────┤
1-Rare     │           │           │           │           │           │
           │    1      │    2      │    3      │    4      │    5      │
           └───────────┴───────────┴───────────┴───────────┴───────────┘

Legend: ■ Critical (20-25)  ▲ High (13-19)  ● Medium (6-12)  ○ Low (1-5)
```

### Residual Risk Matrix (After Controls)

```
                                  IMPACT
              1-Minimal   2-Minor    3-Moderate   4-Major    5-Severe
           ┌───────────┬───────────┬───────────┬───────────┼───────────┐
5-Almost   │           │           │           │           │           │
Certain    │    5      │    10     │    15     │    20     │    25     │
           ├───────────┼───────────┼───────────┼───────────┼───────────┤
4-Likely   │           │           │           │           │           │
           │    4      │    8      │    12     │    16     │    20     │
L          ├───────────┼───────────┼───────────┼───────────┼───────────┤
I 3-Possible│          │  R-005    │  R-001    │           │           │
K          │    3      │    6      │    9      │    12     │    15     │
E          │           │  R-007    │  R-004    │           │           │
L          │           │  R-008    │  R-006    │           │           │
I          │           │  R-015    │           │           │           │
H          │           │  R-017    │           │           │           │
O          ├───────────┼───────────┼───────────┼───────────┼───────────┤
O 2-Unlikely│  R-003   │  R-010    │  R-002    │  R-009    │  R-011    │
D          │    2      │    4      │    6      │    8      │    8      │
           │  R-018    │           │  R-012    │  R-013    │  R-014    │
           │  R-019    │           │  R-016    │           │  R-020    │
           ├───────────┼───────────┼───────────┼───────────┼───────────┤
1-Rare     │           │           │           │           │           │
           │    1      │    2      │    3      │    4      │    5      │
           └───────────┴───────────┴───────────┴───────────┴───────────┘

Legend: ■ Critical (20-25)  ▲ High (13-19)  ● Medium (6-12)  ○ Low (1-5)
```

**Movement summary (Inherent → Residual):**
- R-004: Critical (20) → Medium (9) — 55% reduction
- R-001: High (16) → Medium (9) — 44% reduction
- R-006: High (16) → Medium (9) — 44% reduction
- R-011: High (15) → Medium (8) — 47% reduction
- R-013: High (16) → Medium (8) — 50% reduction
- R-020: High (15) → Medium (8) — 47% reduction

---

## C. Top 10 Risks (by Residual Score)

| Rank | ID | Title | Category | Inh. Score | Res. Score | Owner | Response |
|------|----|-------|----------|------------|------------|-------|----------|
| 1 | R-004 | Engineering capacity — legacy drag | OPERATIONAL | 20 | 9 | CTO/CIO | TREAT |
| 2 | R-001 | Programme scope creep | STRATEGIC | 16 | 9 | Executive Sponsor | TREAT |
| 3 | R-006 | AWS/cloud-native skills gap | TECHNOLOGY | 16 | 9 | CTO/CIO | TREAT |
| 4 | R-009 | Programme budget overrun | FINANCIAL | 12 | 8 | CFO | TREAT |
| 5 | R-011 | PCI-DSS re-certification missed | COMPLIANCE | 15 | 8 | CISO/Compliance | TREAT |
| 6 | R-013 | Customer-visible service degradation | REPUTATIONAL | 16 | 8 | VP Operations | TREAT |
| 7 | R-014 | Order data loss during migration | REPUTATIONAL | 15 | 8 | CTO/EA | TREAT |
| 8 | R-020 | Security breach during migration | TECHNOLOGY | 15 | 8 | CISO | TREAT+TRANSFER |
| 9 | R-002 | Executive sponsorship weakens | STRATEGIC | 10 | 6 | Executive Sponsor | TREAT |
| 10 | R-005 | Fulfillment team UAT disengagement | OPERATIONAL | 12 | 6 | VP Operations | TREAT |

---

## D. Risk Register — Detailed Profiles

### R-001 — Programme Scope Creep

| Field | Value |
|-------|-------|
| **Risk ID** | R-001 |
| **Category** | STRATEGIC |
| **Title** | Programme scope creep and uncontrolled feature additions |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | Executive Sponsor |
| **Action Owner** | Programme Manager |
| **Escalation Path** | Steering Committee |

**Description**: Stakeholders and product teams continuously add requirements to the modernisation scope, extending the programme timeline and consuming budget allocated for core migration work. The 24-month roadmap assumes a disciplined scope boundary.

**Root Cause**: Absence of a locked MVP definition and a formal scope change governance board. Stakeholder enthusiasm post-programme launch historically drives feature creep in large-scale transformation programmes.

**Trigger Events**: Business stakeholders request "while we're at it" features; legacy decommission dates are extended; sprint velocity falls behind roadmap; new regulatory requirements emerge mid-programme.

**Consequences if Realized**: Programme extends beyond Month 24; dual-running costs accumulate; team morale declines; TCO savings delayed; CFO confidence in programme erodes.

**Affected Stakeholders**: CFO (ARC-001-STKE-v1.0 — budget impact), VP Operations (delivery timelines), Product Owner (scope definition).

**Related Objectives**: G-1 (Platform migration by Month 18), G-6 (2-week feature lead time after go-live).

**Inherent Risk Assessment**:
- Likelihood: **4 — Likely** (50–75% probability — common in large transformation programmes)
- Impact: **4 — Major** (threatens programme timeline and budget by 20–40%)
- Inherent Score: **16 (High)**

**Existing Controls**:
- Architecture Principles document (ARC-000-PRIN-v1.0) providing guardrails
- MoSCoW prioritisation captured in ARC-001-REQ-v1.0
- Control Effectiveness: Adequate

**Residual Risk Assessment**:
- Residual Likelihood: **3 — Possible**
- Residual Impact: **3 — Moderate**
- Residual Score: **9 (Medium)**

**Additional Mitigations**:
1. Establish a Scope Change Control Board (SCCB) with CFO and Executive Sponsor as approvers
2. Baseline and freeze MVP scope by Month 2; all additions require SCCB approval
3. Publish monthly scope health dashboard to Steering Committee
4. Implement story-point velocity tracking with burn-up chart visible to sponsors

**Target Residual Score**: 6 (Medium) | **Target Date**: Month 2

**Success Criteria**: Zero uncontrolled scope additions in any sprint; all changes processed through SCCB within 5 business days.

---

### R-002 — Executive Sponsorship Weakens

| Field | Value |
|-------|-------|
| **Risk ID** | R-002 |
| **Category** | STRATEGIC |
| **Title** | Executive sponsorship weakens or changes mid-programme |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | Executive Sponsor |
| **Action Owner** | Programme Manager |
| **Escalation Path** | CEO / Board |

**Description**: The Executive Sponsor reduces active involvement or is replaced, leaving the programme without senior advocacy required to resolve cross-functional blockers, secure budget, and maintain organisational priority.

**Root Cause**: Executive churn in the organisation and competing strategic priorities competing for C-suite attention over a 24-month horizon.

**Trigger Events**: Executive Sponsor announces departure or role change; programme fails to demonstrate early value; organisational restructure changes reporting lines.

**Consequences if Realized**: Cross-functional blockers remain unresolved; budget bids fail; programme loses priority against other initiatives; team loses confidence.

**Affected Stakeholders**: All stakeholders — loss of programme authority affects every workstream.

**Inherent Risk Assessment**:
- Likelihood: **2 — Unlikely** (5–25% probability)
- Impact: **5 — Catastrophic** (could terminate programme)
- Inherent Score: **10 (Medium)**

**Existing Controls**:
- Executive Sponsor named and committed in stakeholder analysis (ARC-001-STKE-v1.0)
- Control Effectiveness: Adequate

**Residual Risk Assessment**:
- Residual Likelihood: **2 — Unlikely**
- Residual Impact: **3 — Moderate**
- Residual Score: **6 (Medium)**

**Additional Mitigations**:
1. Name a Deputy Executive Sponsor to provide continuity
2. Monthly Steering Committee reporting to embed programme in governance cadence
3. Quick-win delivery by Month 3 to build positive track record
4. Succession plan documented for Executive Sponsor role

**Target Residual Score**: 4 | **Target Date**: Month 1

---

### R-003 — Competitive Urgency Reduces

| Field | Value |
|-------|-------|
| **Risk ID** | R-003 |
| **Category** | STRATEGIC |
| **Title** | Competitive urgency for modernisation reduces |
| **Status** | Open |
| **4Ts Response** | TOLERATE |
| **Risk Owner** | Executive Sponsor |
| **Action Owner** | Executive Sponsor |
| **Escalation Path** | CEO |

**Description**: Market conditions or competitor actions change such that the business case urgency for legacy modernisation is perceived to have reduced, causing programme prioritisation to slip.

**Root Cause**: Uncertainty in market conditions over a 24-month programme horizon.

**Trigger Events**: Key competitor experiences major technology failure, reducing competitive pressure; economic downturn causes board to freeze discretionary spend.

**Consequences if Realized**: Programme de-prioritised; budget redirected; technical debt continues to accumulate on legacy system.

**Inherent Risk Assessment**:
- Likelihood: **2 — Unlikely**
- Impact: **3 — Moderate**
- Inherent Score: **6 (Medium)**

**Residual Risk Assessment**:
- Residual Likelihood: **2 — Unlikely**
- Residual Impact: **2 — Minor**
- Residual Score: **4 (Low)**

**Rationale for Tolerate**: Inherent and residual scores are low. The risk of NOT modernising (compounding technical debt, compliance exposure, reliability degradation) outweighs pause risk. Within appetite.

---

### R-004 — Engineering Capacity — Legacy Drag

| Field | Value |
|-------|-------|
| **Risk ID** | R-004 |
| **Category** | OPERATIONAL |
| **Title** | Engineering team split across legacy support and new platform build |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | CTO/CIO |
| **Action Owner** | Engineering Manager |
| **Escalation Path** | Executive Sponsor → Steering Committee |
| **Appetite Assessment** | Exceeds Appetite (Residual 9 > threshold 8) — escalation required |

**Description**: The same engineering team is required to maintain the live legacy order management system while simultaneously building the new cloud-native platform. Context-switching and unplanned legacy incidents will materially reduce new platform velocity.

**Root Cause**: Absence of a dedicated platform team ring-fenced from BAU legacy operations. The strangler-fig migration pattern requires parallel system operation, inherently creating this tension.

**Trigger Events**: Legacy system incident demands all-hands response; sprint allocation below 60% new platform; key engineer leaves; critical legacy bug discovered requiring emergency patch.

**Consequences if Realized**: Platform build falls behind milestone schedule; Month 18 migration date extends; dual-running cost period extends; business stakeholder confidence erodes.

**Affected Stakeholders**: CTO/CIO (delivery accountability), CFO (budget impact of delay), VP Operations (go-live date dependency), Product Owner (feature delivery).

**Related Objectives**: G-1 (Platform migration by Month 18), G-6 (2-week feature lead time).

**Inherent Risk Assessment**:
- Likelihood: **5 — Almost Certain** (> 75% probability — structural certainty in parallel operation)
- Impact: **4 — Major** (threatens milestone schedule by 20–40%)
- Inherent Score: **20 (Critical)**

**Existing Controls**:
- Strangler-fig pattern (ARC-000-PRIN-v1.0, Principle 1) enables incremental migration reducing legacy load over time
- Anti-Corruption Layer pattern isolates legacy touchpoints
- Control Effectiveness: Adequate

**Residual Risk Assessment**:
- Residual Likelihood: **3 — Possible**
- Residual Impact: **3 — Moderate**
- Residual Score: **9 (Medium — exceeds OPERATIONAL appetite of 8)**

**Additional Mitigations**:
1. Hire dedicated platform team (2–3 engineers) ring-fenced from legacy BAU by Month 2
2. Engage a managed service partner for legacy BAU support during migration period
3. Define SLA for legacy incident response so platform engineers are not always on-call
4. Track engineering allocation weekly (target: ≥ 70% new platform, ≤ 30% legacy BAU)
5. Establish on-call rotation with clear escalation so incidents do not absorb entire team

**Target Residual Score**: 6 | **Target Date**: Month 3

**Success Criteria**: Weekly engineering allocation report shows ≥ 70% time on new platform for 8+ consecutive weeks; no sprint missed due to legacy incident response.

---

### R-005 — Fulfillment Team UAT Disengagement

| Field | Value |
|-------|-------|
| **Risk ID** | R-005 |
| **Category** | OPERATIONAL |
| **Title** | Fulfillment operations team disengages from UAT and change adoption |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | VP Operations |
| **Action Owner** | Change Manager |
| **Escalation Path** | Executive Sponsor |

**Description**: Warehouse and fulfillment staff who depend on the order management system daily disengage from user acceptance testing, training, and change adoption activities, leading to a poorly tested go-live and/or low adoption of the new system.

**Root Cause**: Operational teams prioritise daily fulfillment targets over programme participation. Change identified as MEDIUM risk in ARC-001-STKE-v1.0 conflict analysis (C-1: speed vs operations risk appetite).

**Trigger Events**: Testing participation falls below 60%; training attendance below 70%; team raises multiple "too busy" deferrals; VP Operations deprioritises programme involvement.

**Consequences if Realized**: Critical operational workflows untested before go-live; post-cutover operational disruption; order processing errors; customer impact.

**Inherent Risk Assessment**:
- Likelihood: **4 — Likely**
- Impact: **3 — Moderate**
- Inherent Score: **12 (Medium)**

**Residual Risk Assessment**:
- Residual Likelihood: **3 — Possible**
- Residual Impact: **2 — Minor**
- Residual Score: **6 (Medium)**

**Additional Mitigations**:
1. Embed 2 fulfillment super-users in the programme team full-time from Month 3
2. VP Operations formally committed in programme governance with measurable participation KPIs
3. Run UAT sessions during shift handovers to minimise operational disruption
4. Go/no-go gate: Minimum 80% UAT sign-off from fulfillment team before cutover approval

**Target Residual Score**: 4 | **Target Date**: Month 6 (ahead of UAT phase)

---

### R-006 — AWS/Cloud-Native Skills Gap

| Field | Value |
|-------|-------|
| **Risk ID** | R-006 |
| **Category** | TECHNOLOGY |
| **Title** | Engineering team lacks sufficient AWS and cloud-native expertise |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | CTO/CIO |
| **Action Owner** | Engineering Manager |
| **Escalation Path** | Steering Committee |

**Description**: The existing engineering team has deep expertise in the legacy monolith but limited hands-on experience with AWS managed services, event-driven architecture patterns (outbox, saga, ACL), and cloud-native observability tooling required to build and operate the new platform.

**Root Cause**: Historical investment concentrated in on-premise legacy technology. Cloud-native architecture (ARC-000-PRIN-v1.0) requires a step-change in team capability.

**Trigger Events**: Pull request reviews reveal AWS anti-patterns; cloud cost anomalies due to misconfiguration; security misconfiguration incident; team unable to debug event-driven failures.

**Consequences if Realized**: Poor architectural decisions baked into new platform; technical debt in new system from day one; security misconfigurations; extended delivery timelines; increased AWS costs.

**Inherent Risk Assessment**:
- Likelihood: **4 — Likely**
- Impact: **4 — Major**
- Inherent Score: **16 (High)**

**Existing Controls**:
- Architecture Principles (ARC-000-PRIN-v1.0) provide guardrails
- Control Effectiveness: Weak (guardrails without capability = compliance risk)

**Residual Risk Assessment**:
- Residual Likelihood: **3 — Possible**
- Residual Impact: **3 — Moderate**
- Residual Score: **9 (Medium)**

**Additional Mitigations**:
1. AWS professional services engagement for architecture review and initial setup (Month 1–3)
2. AWS certification programme for all engineers — Solutions Architect Associate minimum by Month 6
3. Appoint a Cloud Centre of Excellence lead (internal or hired) by Month 2
4. Architecture review board gates at each phase to validate cloud-native patterns
5. Engage specialist contractor for event-driven architecture (outbox, saga, ACL) design in Month 1–4

**Target Residual Score**: 6 | **Target Date**: Month 6

---

### R-007 — Legacy System Further Deterioration

| Field | Value |
|-------|-------|
| **Risk ID** | R-007 |
| **Category** | OPERATIONAL |
| **Title** | Legacy OMS deteriorates further during the migration period |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | VP Operations |
| **Action Owner** | Engineering Manager (Legacy) |
| **Escalation Path** | CTO/CIO → Executive Sponsor |

**Description**: The legacy order management system, already carrying technical debt, experiences increasing failure rates and performance degradation during the 18-month migration period, disrupting live order processing.

**Root Cause**: Reduced engineering investment in legacy maintenance as team shifts focus to new platform build. Technical debt compounds.

**Trigger Events**: Legacy system P1 incident frequency exceeds 2 per month; database performance degrades; third-party dependencies reach EOL; infrastructure patch falls behind.

**Consequences if Realized**: Live order processing disruption; customer-visible service degradation (triggers R-013); emergency diversion of engineering from new platform.

**Inherent Risk Assessment**:
- Likelihood: **4 — Likely**
- Impact: **3 — Moderate**
- Inherent Score: **12 (Medium)**

**Residual Risk Assessment**:
- Residual Likelihood: **3 — Possible**
- Residual Impact: **2 — Minor**
- Residual Score: **6 (Medium)**

**Additional Mitigations**:
1. Legacy system health baseline (performance, error rate, incident frequency) established at programme start
2. Dedicated legacy BAU support role (managed service or contractor) to hold current state
3. Accelerate migration of highest-risk legacy components to new platform first
4. Monthly legacy system health review with engineering and VP Operations

**Target Residual Score**: 4 | **Target Date**: Month 2

---

### R-008 — Dual-Running Cloud Costs Exceed Forecast

| Field | Value |
|-------|-------|
| **Risk ID** | R-008 |
| **Category** | FINANCIAL |
| **Title** | Dual-running period cloud costs materially exceed budget forecast |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | CFO |
| **Action Owner** | Cloud FinOps Lead |
| **Escalation Path** | CFO → Executive Sponsor |

**Description**: During the strangler-fig migration, the organisation runs both the legacy system and new AWS platform simultaneously. Cloud costs (compute, storage, data transfer, managed services) exceed the forecast, eroding the business case TCO savings.

**Root Cause**: AWS cost estimation is complex; usage patterns differ from legacy; development and test environments incur unexpected spend; data egress charges underestimated.

**Trigger Events**: Monthly AWS bill exceeds forecast by > 15%; FinOps review identifies untagged or idle resources; migration extends beyond planned timeline increasing dual-run period.

**Consequences if Realized**: CFO confidence in business case erodes; TCO savings target (G-2: 30% reduction) delayed or missed; additional budget approval required.

**Inherent Risk Assessment**:
- Likelihood: **4 — Likely**
- Impact: **3 — Moderate**
- Inherent Score: **12 (Medium)**

**Residual Risk Assessment**:
- Residual Likelihood: **3 — Possible**
- Residual Impact: **2 — Minor**
- Residual Score: **6 (Medium)**

**Additional Mitigations**:
1. Implement AWS Cost Explorer with resource tagging from Day 1; monthly FinOps review
2. AWS Budgets alerts at 80% and 100% of monthly allocation
3. Reserved Instance / Savings Plans analysis at Month 3 once usage patterns established
4. Automated shutdown of dev/test environments outside business hours
5. Cloud cost transparency dashboard shared with CFO monthly

**Target Residual Score**: 4 | **Target Date**: Month 2

---

### R-009 — Programme Budget Overrun

| Field | Value |
|-------|-------|
| **Risk ID** | R-009 |
| **Category** | FINANCIAL |
| **Title** | Total programme budget overruns approved envelope |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | CFO |
| **Action Owner** | Programme Manager |
| **Escalation Path** | CFO → Board |

**Description**: The total programme cost (staff, contractors, AWS, licences, change management) exceeds the approved budget envelope, requiring additional funding approval or scope reduction.

**Root Cause**: Complex multi-system integration, unknown legacy data quality issues, and potential timeline extensions create budget uncertainty.

**Trigger Events**: Scope additions approved without budget adjustment; engineering timeline extends; contractor rates increase; discovered integration complexity adds effort.

**Consequences if Realized**: Programme paused pending board funding approval; scope reduction compromising functionality; reputational impact on programme team.

**Inherent Risk Assessment**:
- Likelihood: **3 — Possible**
- Impact: **4 — Major**
- Inherent Score: **12 (Medium)**

**Residual Risk Assessment**:
- Residual Likelihood: **2 — Unlikely**
- Residual Impact: **4 — Major**
- Residual Score: **8 (Medium)**

**Additional Mitigations**:
1. Maintain 15% contingency reserve within approved budget envelope
2. Monthly budget burn-rate reporting to CFO with forecast-to-complete
3. Scope Change Control Board (SCCB) — all additions require CFO budget impact sign-off
4. Earned Value Management (EVM) tracking from Month 1

**Target Residual Score**: 6 | **Target Date**: Month 1

---

### R-010 — TCO Reduction Target Not Achieved

| Field | Value |
|-------|-------|
| **Risk ID** | R-010 |
| **Category** | FINANCIAL |
| **Title** | 30% TCO reduction target (G-2) not achieved by Year 3 |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | CFO |
| **Action Owner** | Cloud FinOps Lead |
| **Escalation Path** | CFO → Executive Sponsor |

**Description**: The business case projects a 30% Total Cost of Ownership reduction by Year 3. If cloud costs, licencing, or extended dual-running erode savings, this headline outcome is not delivered.

**Root Cause**: TCO projections are estimates with multiple assumptions; actual savings depend on migration speed, cloud cost discipline, and legacy decommission timeline.

**Trigger Events**: Year 1 cloud spend tracking above forecast; legacy decommission delayed beyond Month 20; TCO model assumptions challenged by actuals.

**Consequences if Realized**: Business case ROI not delivered; CFO confidence damaged; further investment in platform questioned.

**Inherent Risk Assessment**:
- Likelihood: **3 — Possible**
- Impact: **3 — Moderate**
- Inherent Score: **9 (Medium)**

**Residual Risk Assessment**:
- Residual Likelihood: **2 — Unlikely**
- Residual Impact: **3 — Moderate**
- Residual Score: **6 (Medium)**

**Additional Mitigations**:
1. TCO dashboard tracking actuals vs model monthly from Month 1
2. Legacy infrastructure decommission milestone locked in programme plan (Month 20)
3. FinOps review at Month 12 to validate Year 3 trajectory

**Target Residual Score**: 4 | **Target Date**: Month 6

---

### R-011 — PCI-DSS Re-Certification Missed

| Field | Value |
|-------|-------|
| **Risk ID** | R-011 |
| **Category** | COMPLIANCE |
| **Title** | PCI-DSS re-certification missed during platform transition |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | CISO / Head of Compliance |
| **Action Owner** | Security Architect |
| **Escalation Path** | CISO → CFO → Board |
| **Appetite Assessment** | Exceeds Appetite (Residual 8 > COMPLIANCE threshold 6) — escalation required |

**Description**: The migration introduces new AWS components into the PCI-DSS cardholder data environment (CDE). If AWS services are not correctly scoped, documented, and independently assessed before the re-certification deadline (BR-004: Month 8), the organisation risks losing payment card processing capability.

**Root Cause**: PCI-DSS assessment requires complete evidence of controls across all in-scope systems. New AWS services (API Gateway, Lambda, RDS, KMS, WAF) must be included in scope and demonstrate compliance.

**Trigger Events**: QSA identifies undocumented AWS services in CDE scope; penetration test reveals gaps; evidence packs incomplete at assessment deadline; WAF or encryption configuration non-compliant.

**Consequences if Realized**: Payment card processing suspended by acquirer; immediate revenue loss; regulatory investigation; reputational damage; potential significant financial penalties.

**Affected Stakeholders**: CFO (revenue impact), CISO (regulatory accountability), VP Operations (order processing capability), CEO (existential business impact).

**Inherent Risk Assessment**:
- Likelihood: **3 — Possible**
- Impact: **5 — Catastrophic**
- Inherent Score: **15 (High)**

**Existing Controls**:
- NFR-SEC-001 (authentication), NFR-SEC-003 (encryption), NFR-C-001 (PCI-DSS) in ARC-001-REQ-v1.0
- Control Effectiveness: Weak (requirements defined but not yet implemented)

**Residual Risk Assessment**:
- Residual Likelihood: **2 — Unlikely**
- Residual Impact: **4 — Major**
- Residual Score: **8 (Medium — exceeds COMPLIANCE appetite of 6)**

**Additional Mitigations**:
1. Engage QSA from Month 1 to advise on AWS CDE scoping — do not wait for assessment
2. PCI-DSS control mapping document for all AWS services by Month 3
3. Internal pre-assessment readiness review at Month 6 (2 months before deadline)
4. AWS Security Hub PCI-DSS standard enabled and monitored from Day 1
5. Dedicated Security Architect (or specialist contractor) assigned to compliance workstream
6. Network segmentation diagram reviewed and approved by QSA before deployment

**Target Residual Score**: 6 | **Target Date**: Month 4

**Escalation Required**: Yes — exceeds COMPLIANCE risk appetite; notify CISO and Compliance Board immediately.

---

### R-012 — GDPR Right-to-Erasure Non-Compliance

| Field | Value |
|-------|-------|
| **Risk ID** | R-012 |
| **Category** | COMPLIANCE |
| **Title** | GDPR right-to-erasure obligations cannot be met in new platform |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | Head of Compliance |
| **Action Owner** | Data Architect |
| **Escalation Path** | Head of Compliance → CISO → DPO |

**Description**: The immutable order audit trail (ARC-000-PRIN-v1.0, Principle 8) and event sourcing architecture must be reconciled with GDPR Article 17 right-to-erasure requirements. PII within historical order events and audit logs must be erasable without destroying audit integrity.

**Root Cause**: Tension between immutability (regulatory audit requirement) and erasure (GDPR) — a known conflict in event-sourced systems handling personal data.

**Trigger Events**: ICO audit identifies PII in immutable event streams; data subject erasure request cannot be fulfilled; DPO identifies non-compliant data architecture.

**Consequences if Realized**: ICO enforcement action; financial penalty up to 4% global annual turnover; mandatory public notification; reputational damage.

**Inherent Risk Assessment**:
- Likelihood: **3 — Possible**
- Impact: **4 — Major**
- Inherent Score: **12 (Medium)**

**Residual Risk Assessment**:
- Residual Likelihood: **2 — Unlikely**
- Residual Impact: **3 — Moderate**
- Residual Score: **6 (Medium)**

**Additional Mitigations**:
1. Implement crypto-shredding pattern — encrypt PII with customer-specific key; erasure = key deletion
2. PII tokenisation in event payloads — store reference tokens, not raw PII, in event streams
3. Data Protection Impact Assessment (DPIA) for event-sourcing architecture by Month 3
4. DPO review and sign-off on data architecture before production deployment
5. Automated erasure workflow tested in pre-production before go-live

**Target Residual Score**: 4 | **Target Date**: Month 5

---

### R-013 — Customer-Visible Service Degradation

| Field | Value |
|-------|-------|
| **Risk ID** | R-013 |
| **Category** | REPUTATIONAL |
| **Title** | Migration causes customer-visible order processing degradation |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | VP Operations |
| **Action Owner** | Engineering Manager / SRE Lead |
| **Escalation Path** | VP Operations → CEO → Executive Sponsor |

**Description**: A failure during the strangler-fig migration (routing misconfiguration, event processing backlog, ACL error) causes customers to experience order confirmation delays, incorrect order status, or failed transactions during the cutover period.

**Root Cause**: Parallel system operation during migration creates complex routing, synchronisation, and consistency challenges. Any failure in the ACL or event bus impacts live customer journeys.

**Trigger Events**: Customer complaint volume spikes > 200% above baseline; order confirmation latency exceeds 30 seconds; error rate on order submission API > 0.5%; social media complaints appear.

**Consequences if Realized**: Customer trust erosion; order abandonment; media coverage; competitor opportunity; customer churn.

**Inherent Risk Assessment**:
- Likelihood: **4 — Likely**
- Impact: **4 — Major**
- Inherent Score: **16 (High)**

**Residual Risk Assessment**:
- Residual Likelihood: **2 — Unlikely**
- Residual Impact: **4 — Major**
- Residual Score: **8 (Medium)**

**Additional Mitigations**:
1. Blue/green deployment pattern for all cutover events — instant rollback capability
2. Customer-facing SLO dashboard with real-time alerting (p95 < 3s, error rate < 0.1%)
3. Canary releases — 5% → 25% → 50% → 100% traffic migration per phase
4. Automated rollback triggers: if error rate > 0.5% for 5 minutes, auto-revert
5. Customer communications plan for planned cutover windows with status page updates
6. War room (virtual) for all major cutover events with VP Operations, CTO, SRE

**Target Residual Score**: 6 | **Target Date**: Before Phase 2 cutover (Month 9)

---

### R-014 — Order Data Loss During Migration

| Field | Value |
|-------|-------|
| **Risk ID** | R-014 |
| **Category** | REPUTATIONAL |
| **Title** | Historical or in-flight order data lost during migration |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | CTO / Enterprise Architect |
| **Action Owner** | Data Architect / Migration Lead |
| **Escalation Path** | CTO → CEO → Executive Sponsor |

**Description**: Data migration from the legacy OMS to the new platform results in loss of historical orders, customer records, or in-flight orders (orders in processing at cutover time). This creates customer disputes, operational failures, and financial reconciliation issues.

**Root Cause**: Legacy data quality issues (R-015), complex data model transformation, and in-flight transaction state during cutover create data integrity risk.

**Trigger Events**: Post-migration data validation fails; customers report missing orders; financial reconciliation discrepancy detected; audit trail gaps identified.

**Consequences if Realized**: Customer disputes unresolvable; financial losses from unprocessed orders; regulatory non-compliance (audit trail gaps); catastrophic reputational damage; potential litigation.

**Inherent Risk Assessment**:
- Likelihood: **3 — Possible**
- Impact: **5 — Catastrophic**
- Inherent Score: **15 (High)**

**Residual Risk Assessment**:
- Residual Likelihood: **2 — Unlikely**
- Residual Impact: **4 — Major**
- Residual Score: **8 (Medium)**

**Additional Mitigations**:
1. Full legacy data backup immediately before every migration phase
2. Dual-write period: write to both legacy and new system; compare outputs for 2 weeks per phase
3. Automated data reconciliation script comparing record counts, checksums, and spot samples
4. In-flight order freeze window: no new orders processed for 30-minute cutover window (off-peak)
5. Rollback plan: documented procedure to revert to legacy within 2 hours of any cutover
6. Independent data quality audit before each phase migration sign-off

**Target Residual Score**: 6 | **Target Date**: Before first data migration (Month 7)

---

### R-015 — Legacy Data Quality Worse Than Expected

| Field | Value |
|-------|-------|
| **Risk ID** | R-015 |
| **Category** | TECHNOLOGY |
| **Title** | Legacy OMS data quality significantly worse than anticipated |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | CTO |
| **Action Owner** | Data Architect |
| **Escalation Path** | CTO → Programme Manager |

**Description**: A comprehensive audit of legacy OMS data reveals data quality issues (duplicates, nulls, format inconsistencies, referential integrity violations, orphaned records) that significantly increase migration effort and timeline beyond estimates.

**Root Cause**: Legacy system has accumulated 10+ years of data with variable quality standards, multiple ETL processes, and minimal data governance.

**Trigger Events**: Initial data profiling reveals > 10% records with quality issues; duplicate customer records detected; referential integrity failures in legacy schema.

**Consequences if Realized**: Migration timeline extended; significant data cleansing effort required (unplanned resource); risk of carrying poor quality data into new system.

**Inherent Risk Assessment**:
- Likelihood: **4 — Likely**
- Impact: **3 — Moderate**
- Inherent Score: **12 (Medium)**

**Residual Risk Assessment**:
- Residual Likelihood: **3 — Possible**
- Residual Impact: **2 — Minor**
- Residual Score: **6 (Medium)**

**Additional Mitigations**:
1. Legacy data profiling and quality assessment completed by Month 2 (before migration planning finalised)
2. Data Quality Requirements (DR-005 in ARC-001-REQ-v1.0) enforced in migration pipeline
3. Automated data quality pipeline: profile, cleanse, validate, reject/quarantine
4. Contingency added to migration timeline estimate based on profiling findings

**Target Residual Score**: 4 | **Target Date**: Month 3

---

### R-016 — ACL Inadequately Designed

| Field | Value |
|-------|-------|
| **Risk ID** | R-016 |
| **Category** | TECHNOLOGY |
| **Title** | Anti-Corruption Layer (ACL) fails to adequately isolate legacy domain model |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | CTO / Enterprise Architect |
| **Action Owner** | Lead Architect |
| **Escalation Path** | CTO → Steering Committee |

**Description**: The Anti-Corruption Layer (ARC-000-PRIN-v1.0, Principle 15) between the new cloud-native platform and the legacy OMS is incorrectly designed, allowing legacy data model concepts and constraints to "leak" into the new domain, creating coupling that undermines the strangler-fig migration strategy.

**Root Cause**: ACL design is complex; requires deep understanding of both legacy and new domain models simultaneously; difficult to get right first time.

**Trigger Events**: New platform logic contains direct references to legacy field names/codes; legacy system changes break new platform; integration tests reveal tight coupling.

**Consequences if Realized**: New platform inherits legacy complexity; migration becomes harder as coupling increases; strangler-fig strategy fails; architectural rework required.

**Inherent Risk Assessment**:
- Likelihood: **3 — Possible**
- Impact: **4 — Major**
- Inherent Score: **12 (Medium)**

**Residual Risk Assessment**:
- Residual Likelihood: **2 — Unlikely**
- Residual Impact: **3 — Moderate**
- Residual Score: **6 (Medium)**

**Additional Mitigations**:
1. ACL design review by specialist architect (DDD expertise) before implementation begins
2. Contract tests between ACL and both legacy and new platform domains
3. Zero-tolerance code review policy: any legacy field name appearing in new domain = build failure
4. Architecture decision record (ADR) documenting ACL design rationale and boundaries

**Target Residual Score**: 4 | **Target Date**: Month 2 (before implementation)

---

### R-017 — Logistics Partner API Adoption Delayed

| Field | Value |
|-------|-------|
| **Risk ID** | R-017 |
| **Category** | OPERATIONAL |
| **Title** | Logistics partner API integration delayed by partner capacity constraints |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | VP Operations |
| **Action Owner** | Integration Lead |
| **Escalation Path** | VP Operations → Executive Sponsor |

**Description**: Third-party logistics partners (INT-004 in ARC-001-REQ-v1.0) are slow to provide API specifications, complete integration testing, or certify their connection to the new platform, delaying the order dispatch capability go-live.

**Root Cause**: Logistics partners have their own change management timelines and competing priorities; they are not under the programme's direct control.

**Trigger Events**: Partner fails to provide API spec by agreed date; partner integration test window cancelled; partner requests 3+ month delay.

**Consequences if Realized**: Order dispatch capability delayed; fulfillment must use legacy system workarounds longer; dual-running complexity increases.

**Inherent Risk Assessment**:
- Likelihood: **4 — Likely**
- Impact: **3 — Moderate**
- Inherent Score: **12 (Medium)**

**Residual Risk Assessment**:
- Residual Likelihood: **3 — Possible**
- Residual Impact: **2 — Minor**
- Residual Score: **6 (Medium)**

**Additional Mitigations**:
1. Partner integration agreements signed with SLA commitments by Month 2
2. Logistics partner mock service for development/testing so programme not blocked on live partner
3. Fallback: legacy dispatch workflow maintained until partner certification complete
4. Monthly partner integration status review with VP Operations

**Target Residual Score**: 4 | **Target Date**: Month 2

---

### R-018 — IMS Throughput Insufficient

| Field | Value |
|-------|-------|
| **Risk ID** | R-018 |
| **Category** | TECHNOLOGY |
| **Title** | Internal Messaging System (event bus) throughput insufficient at peak load |
| **Status** | Open |
| **4Ts Response** | TREAT |
| **Risk Owner** | CTO |
| **Action Owner** | Platform Architect |
| **Escalation Path** | CTO/CIO |

**Description**: The event-driven architecture (ARC-000-PRIN-v1.0, Principle 14) requires the internal messaging system to handle peak order volumes without backlog. If throughput is insufficient, order state events queue up, creating processing delays and inconsistent order status.

**Root Cause**: Event volume at peak (600 orders/min with multiple events per order = 3,000–6,000 events/min) requires careful capacity planning for event bus, consumers, and downstream processors.

**Trigger Events**: Event consumer lag > 60 seconds during load test; order status latency exceeds SLA during peak; DLQ (dead letter queue) accumulates messages.

**Consequences if Realized**: Order status updates delayed; customer-facing APIs return stale data; outbox processor falls behind; compensating transactions triggered incorrectly.

**Inherent Risk Assessment**:
- Likelihood: **3 — Possible**
- Impact: **4 — Major**
- Inherent Score: **12 (Medium)**

**Residual Risk Assessment**:
- Residual Likelihood: **2 — Unlikely**
- Residual Impact: **2 — Minor**
- Residual Score: **4 (Low)**

**Additional Mitigations**:
1. Load testing at 2× peak (1,200 orders/min) before production go-live
2. Consumer auto-scaling configured with appropriate target throughput metrics
3. Dead letter queue monitoring with alerting and runbook for reprocessing
4. Capacity model reviewed quarterly as order volumes grow

**Target Residual Score**: 4 (already at target) | **Target Date**: Before Phase 2 (Month 9)

---

### R-019 — AWS Vendor Lock-In

| Field | Value |
|-------|-------|
| **Risk ID** | R-019 |
| **Category** | TECHNOLOGY |
| **Title** | Deep AWS dependency creates long-term vendor lock-in |
| **Status** | Open |
| **4Ts Response** | TOLERATE |
| **Risk Owner** | CTO |
| **Action Owner** | CTO |
| **Escalation Path** | CTO → Executive Sponsor |

**Description**: The new platform's use of AWS managed services (RDS, SQS/SNS/EventBridge, Lambda, API Gateway, CloudWatch) creates dependency on AWS APIs and services that would be expensive to migrate to another cloud provider.

**Root Cause**: Cloud-native architecture (ARC-000-PRIN-v1.0, Principle 2) optimises for managed service benefits, which inherently involves provider-specific APIs.

**Inherent Risk Assessment**:
- Likelihood: **2 — Unlikely** (cloud provider change is rare and costly for any architecture)
- Impact: **3 — Moderate**
- Inherent Score: **6 (Medium)**

**Residual Risk Assessment**:
- Residual Likelihood: **2 — Unlikely**
- Residual Impact: **2 — Minor**
- Residual Score: **4 (Low)**

**Rationale for Tolerate**: The business value of AWS managed services (reduced operational overhead, reliability, security, scalability) materially outweighs lock-in risk. Architecture Principle 4 (Resilience) and Principle 2 (Cloud-Native) accept this trade-off. Risk is within appetite. Mitigated by use of open standards (OpenTelemetry, CloudEvents) where possible.

---

### R-020 — Security Breach During Migration

| Field | Value |
|-------|-------|
| **Risk ID** | R-020 |
| **Category** | TECHNOLOGY |
| **Title** | Security breach or data exfiltration during the migration period |
| **Status** | Open |
| **4Ts Response** | TREAT + TRANSFER |
| **Risk Owner** | CISO |
| **Action Owner** | Security Architect |
| **Escalation Path** | CISO → CEO → Board |

**Description**: The migration period creates an expanded attack surface: new AWS infrastructure being stood up, credentials being provisioned, legacy and new systems connected via ACL, and large-scale data movements creating exfiltration risk. A security breach could expose customer PII, payment card data, or order history.

**Root Cause**: Migrating systems always create temporary complexity and potential gaps in security controls. Developers provisioning AWS resources may create misconfigured buckets, open security groups, or over-privileged IAM roles.

**Trigger Events**: AWS Security Hub critical finding; unauthorised API access detected; S3 bucket misconfiguration alert; penetration test identifies exploit; abnormal data egress pattern detected by CloudWatch.

**Consequences if Realized**: Customer PII breach — ICO notification required within 72 hours; PCI-DSS breach — card scheme penalties and potential suspension; regulatory investigation; severe reputational damage; litigation.

**Affected Stakeholders**: CISO (accountability), CFO (financial penalties and insurance), CEO (regulatory and reputational impact), Customers (PII exposure).

**Inherent Risk Assessment**:
- Likelihood: **3 — Possible**
- Impact: **5 — Catastrophic**
- Inherent Score: **15 (High)**

**Existing Controls**:
- NFR-SEC-001–005 in ARC-001-REQ-v1.0 (authentication, RBAC, encryption, secrets management, vulnerability management)
- Architecture Principles: Security by Design (NON-NEGOTIABLE, Principle 5)
- Control Effectiveness: Weak (requirements defined but not yet implemented)

**Residual Risk Assessment**:
- Residual Likelihood: **2 — Unlikely**
- Residual Impact: **4 — Major**
- Residual Score: **8 (Medium)**

**Additional Mitigations** (TREAT):
1. AWS Security Hub enabled with all standards (CIS, PCI-DSS, Foundational) from Day 1
2. GuardDuty enabled across all accounts from Day 1
3. IAM: least-privilege policy; no wildcard permissions in production; service control policies
4. S3 Block Public Access enabled at organisation level
5. All secrets via AWS Secrets Manager — zero hard-coded credentials policy enforced in CI/CD
6. Independent penetration test before each phase go-live
7. Security incident response playbook and 24/7 alerting from Month 1

**Transfer**:
8. Obtain cyber liability insurance covering data breach notification, regulatory defence, and customer liability (minimum £5M coverage) by Month 2

**Target Residual Score**: 6 | **Target Date**: Month 2

---

## E. Risk by Category Analysis

| Category | Count | Avg Inherent | Avg Residual | Control Effectiveness | Key Themes |
|----------|-------|-------------|-------------|----------------------|------------|
| STRATEGIC | 3 | 10.7 | 6.3 | 41% reduction | Scope governance, sponsor continuity |
| OPERATIONAL | 4 | 14.0 | 6.8 | 51% reduction | Engineering capacity is dominant concern |
| FINANCIAL | 3 | 11.0 | 6.7 | 39% reduction | Dual-run cost discipline critical |
| COMPLIANCE | 2 | 13.5 | 7.0 | 48% reduction | PCI-DSS timeline is highest compliance risk |
| REPUTATIONAL | 2 | 15.5 | 8.0 | 48% reduction | Customer impact requires strong rollback |
| TECHNOLOGY | 6 | 11.7 | 6.7 | 43% reduction | Skills gap and security are top concerns |

---

## F. Risk Ownership Matrix

| Risk Owner | Owned Risks | Critical/High (Inherent) | Residual Scores | Notes |
|------------|-------------|--------------------------|-----------------|-------|
| Executive Sponsor | R-001, R-002, R-003 | 1 High | 9, 6, 4 | Scope governance is primary action |
| CTO/CIO | R-004, R-006 | 1 Critical, 1 High | 9, 9 | Heaviest risk concentration — escalation required for R-004 |
| CTO | R-015, R-016, R-018, R-019 | 0 Critical | 6, 6, 4, 4 | Data quality and architecture quality |
| CTO/EA | R-014 | 1 High | 8 | Data migration — shared with CTO |
| CFO | R-008, R-009, R-010 | 0 Critical | 6, 8, 6 | Financial oversight requires FinOps investment |
| VP Operations | R-005, R-007, R-013, R-017 | 1 High | 6, 6, 8, 6 | Customer experience and partner management |
| CISO/Compliance | R-011 | 1 High | 8 | Exceeds compliance appetite — escalation required |
| CISO | R-020 | 1 High | 8 | Cyber insurance and security posture |
| Head of Compliance | R-012 | 0 Critical | 6 | GDPR architecture decision needed urgently |

---

## G. 4Ts Response Summary

| Response | Count | % | Key Risks |
|----------|-------|---|-----------|
| TREAT | 17 | 85% | R-001, R-002, R-004, R-005, R-006, R-007, R-008, R-009, R-010, R-011, R-012, R-013, R-014, R-015, R-016, R-017, R-018 |
| TOLERATE | 2 | 10% | R-003 (competitive urgency), R-019 (vendor lock-in) |
| TRANSFER | 0 | 0% | — (transfer element in R-020 is supplementary to TREAT) |
| TERMINATE | 0 | 0% | — |
| TREAT + TRANSFER | 1 | 5% | R-020 (security breach — treat + cyber insurance) |

---

## H. Risk Appetite Compliance

| Category | Appetite Threshold | Risks Within Appetite | Risks Exceeding | Action Required |
|----------|-------------------|----------------------|-----------------|-----------------|
| STRATEGIC | Medium (9) | R-002(6), R-003(4) | R-001(9) — at boundary | Monitor monthly |
| OPERATIONAL | Medium (8) | R-005(6), R-007(6), R-017(6) | **R-004(9) — exceeds** | Escalate to Steering Committee |
| FINANCIAL | Medium (9) | R-008(6), R-010(6) | R-009(8) — at boundary | Monitor quarterly |
| COMPLIANCE | Low (6) | R-012(6) — at boundary | **R-011(8) — exceeds** | Escalate to CISO + Compliance Board |
| REPUTATIONAL | Medium (9) | — | R-013(8), R-014(8) — near boundary | Active monitoring |
| TECHNOLOGY | Medium (8) | R-015(6), R-016(6), R-018(4), R-019(4) | R-020(8) — at boundary | Security posture review |

---

## I. Prioritised Action Plan

| Priority | Action | Risk(s) Addressed | Owner | Due Date | Status |
|----------|--------|-------------------|-------|----------|--------|
| 1 | Hire/contract dedicated platform team (ring-fence from BAU) | R-004 (Critical → exceeds appetite) | CTO/CIO | Month 2 | Not Started |
| 2 | Engage QSA from Month 1 for PCI-DSS scoping | R-011 (exceeds compliance appetite) | CISO | Month 1 | Not Started |
| 3 | Enable AWS Security Hub + GuardDuty from Day 1 | R-020 (High security breach) | CISO | Month 1 | Not Started |
| 4 | AWS professional services engagement for cloud-native architecture | R-006 (High skills gap) | CTO/CIO | Month 1 | Not Started |
| 5 | Establish Scope Change Control Board (SCCB) | R-001 (High scope creep) | Executive Sponsor | Month 2 | Not Started |
| 6 | Obtain cyber liability insurance (minimum £5M) | R-020 (transfer component) | CISO/CFO | Month 2 | Not Started |
| 7 | Legacy data profiling and quality assessment | R-015 (data quality) | CTO/Data Architect | Month 2 | Not Started |
| 8 | Implement AWS Cost Explorer + Budgets alerts | R-008, R-010 (financial) | CFO/FinOps | Month 1 | Not Started |
| 9 | Data Protection Impact Assessment for event-sourcing + crypto-shredding design | R-012 (GDPR) | Head of Compliance | Month 3 | Not Started |
| 10 | ACL design review by DDD specialist before implementation | R-016 (ACL design) | CTO/EA | Month 2 | Not Started |
| 11 | Managed service / contractor for legacy BAU support | R-004, R-007 | Engineering Manager | Month 3 | Not Started |
| 12 | Partner integration agreements with SLA commitments | R-017 (logistics) | VP Operations | Month 2 | Not Started |
| 13 | Load test event bus at 2× peak before Phase 2 go-live | R-018 (throughput) | Platform Architect | Month 8 | Not Started |
| 14 | Blue/green deployment and canary rollout strategy defined | R-013 (customer degradation) | SRE Lead | Month 4 | Not Started |
| 15 | Dual-write reconciliation framework for data migration | R-014 (data loss) | Data Architect | Month 6 | Not Started |

---

## J. Monitoring and Review Framework

### Review Cadence

| Risk Level | Review Frequency | Forum | Escalation |
|------------|-----------------|-------|------------|
| Critical (20–25) | Weekly | Programme Manager + Risk Owner | Steering Committee same week |
| High (13–19) | Fortnightly | Programme Team Risk Review | CTO/CFO/CISO as appropriate |
| Medium (6–12) | Monthly | Programme Risk Register Review | Risk Owner |
| Low (1–5) | Quarterly | Risk Register Refresh | No escalation required |

### Escalation Criteria

- Any risk score increasing by 5+ points in one review period → immediate escalation to Steering Committee
- Any new risk assessed as Critical (20–25) → immediate escalation to Executive Sponsor
- Any risk exceeding risk appetite → escalate to Risk Owner + approval authority within 3 business days
- Compliance risk (R-011, R-012) score increase → immediate DPO/CISO notification

### Reporting Requirements

| Report | Audience | Frequency | Owner |
|--------|----------|-----------|-------|
| Critical/High Risk Summary | Steering Committee | Monthly | Programme Manager |
| Full Risk Register | Project Board | Monthly | Programme Manager |
| Compliance Risk Update | CISO + Compliance Board | Monthly | Head of Compliance |
| Risk Appetite Compliance | Audit Committee | Quarterly | CISO |
| Financial Risk Dashboard | CFO | Monthly | FinOps Lead |

### Next Review Date

2026-06-23 (monthly cycle)

### Risk Register Owner

Programme Manager (with Risk Owner accountability per individual risk)

---

## K. Integration with SOBC

This risk register integrates with the programme business case as follows:

| SOBC Section | Integration |
|-------------|-------------|
| **Strategic Case** | R-001 (scope creep), R-002 (sponsorship), R-003 (urgency) — inform "Why Act Now" urgency argument |
| **Economic Case** | R-008, R-009, R-010 (financial risks) — feed optimism bias adjustment in cost models; residual risk scores inform sensitivity analysis |
| **Commercial Case** | R-017 (partner delays) — inform contract SLAs and liquidated damages clauses |
| **Financial Case** | R-008, R-009 — inform contingency reserve sizing (15% recommended) |
| **Management Case Part E** | Full risk register — this document is the direct input to Management Case Part E |
| **Option Appraisal** | High risks (R-004, R-006, R-011, R-020) may influence option selection; higher-risk options should carry larger optimism bias adjustments |

**Recommendation**: R-004 (Critical inherent, exceeds appetite) should be surfaced in the Strategic Case as a key programme risk that the chosen option must address. R-011 (PCI-DSS) should appear in the Financial Case sensitivity analysis.

---

## L. Orange Book Compliance Checklist

| Orange Book Requirement | Status | Evidence |
|------------------------|--------|---------|
| Risk governance established | Planned | Steering Committee reporting cadence defined (Section J) |
| Risk appetite defined and applied | Partial | Appetite thresholds applied; formal appetite statement pending |
| Risk assessment uses Likelihood × Impact | Complete | All 20 risks scored L×I inherent and residual |
| Inherent and residual risk both assessed | Complete | All risks have both assessments |
| 4Ts response applied to all risks | Complete | All 20 risks assigned Tolerate/Treat/Transfer/Terminate |
| All risks have named owners | Complete | Owners from STKE RACI matrix (ARC-001-STKE-v1.0) |
| Risk mitigations have action owners and dates | Complete | Action plan (Section I) with owners and target dates |
| Risks exceeding appetite identified | Complete | R-004 and R-011 flagged; escalation required |
| Monitoring and review framework defined | Complete | Section J with cadences, escalation criteria |
| Risk register integrated with business case | Complete | Section K maps to all five SOBC cases |
| Traceability to stakeholder analysis | Complete | All risks linked to STKE owners and conflicts |
| Traceability to requirements | Partial | Key risks reference REQ IDs; full matrix TBD |

---

## M. Stakeholder Traceability

```
CFO (ARC-001-STKE-v1.0)
  → Driver SD-3: Achieve 30% TCO reduction
    → Conflict C-1: Speed (CFO) vs Risk (VP Operations)
      → Risk R-008: Dual-running cloud costs (FINANCIAL, Residual 6)
      → Risk R-009: Programme budget overrun (FINANCIAL, Residual 8)
      → Risk R-010: TCO target not achieved (FINANCIAL, Residual 6)
        → Owner: CFO
          → Action: FinOps controls, monthly cost reviews, 15% contingency

CTO/CIO (ARC-001-STKE-v1.0)
  → Driver SD-5: Cloud-native architecture and engineering excellence
    → Risk R-004: Engineering capacity — legacy drag (OPERATIONAL, Critical inherent → Residual 9)
    → Risk R-006: AWS/cloud-native skills gap (TECHNOLOGY, Residual 9)
      → Owner: CTO/CIO
        → Action: Ring-fence platform team, AWS professional services, certifications
        → Escalation: Steering Committee (R-004 exceeds appetite)

CISO/Head of Compliance (ARC-001-STKE-v1.0)
  → Driver SD-9: PCI-DSS and GDPR compliance
    → Conflict C-2: PCI-DSS deadline vs engineering readiness
      → Risk R-011: PCI-DSS re-certification (COMPLIANCE, Residual 8 — exceeds appetite)
      → Risk R-012: GDPR right-to-erasure (COMPLIANCE, Residual 6)
      → Risk R-020: Security breach during migration (TECHNOLOGY, Residual 8)
        → Owner: CISO
          → Action: QSA engagement Month 1, Security Hub Day 1, cyber insurance Month 2
          → Escalation: CISO + Compliance Board (R-011 exceeds appetite)

VP Operations (ARC-001-STKE-v1.0)
  → Driver SD-6: 99.9% platform availability
    → Risk R-013: Customer-visible service degradation (REPUTATIONAL, Residual 8)
    → Risk R-005: Fulfillment team UAT disengagement (OPERATIONAL, Residual 6)
    → Risk R-017: Logistics partner API adoption delayed (OPERATIONAL, Residual 6)
      → Owner: VP Operations
        → Action: Blue/green deployment, canary releases, partner SLAs, super-user embedding
```

---

*Generated by*: ArcKit `/arckit:risk` command
*Generated on*: 2026-05-23
*ArcKit Version*: 5.0.4
*Project*: Legacy Order Management Modernization (Project 001)
*AI Model*: claude-sonnet-4-6
*Generation Context*: Derived from ARC-001-STKE-v1.0 (stakeholders/RACI), ARC-001-REQ-v1.0 (requirements/NFRs), ARC-000-PRIN-v1.0 (architecture principles). 20 risks identified across 6 Orange Book categories.
