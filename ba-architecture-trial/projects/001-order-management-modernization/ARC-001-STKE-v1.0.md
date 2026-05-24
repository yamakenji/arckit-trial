# Stakeholder Drivers & Goals Analysis: Legacy Order Management Modernization

> **Template Origin**: Official | **ArcKit Version**: 5.0.4 | **Command**: `/arckit:stakeholders`

## Document Control

| Field | Value |
|---|---|
| **Document ID** | ARC-001-STKE-v1.0 |
| **Document Type** | Stakeholder Drivers & Goals Analysis (STKE) |
| **Project** | Legacy Order Management Modernization |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-05-23 |
| **Last Modified** | 2026-05-23 |
| **Review Cycle** | Quarterly |
| **Next Review Date** | 2026-08-23 |
| **Owner** | Enterprise Architect |
| **Reviewed By** | PENDING |
| **Approved By** | PENDING |
| **Distribution** | Executive Sponsor, Programme Manager, Architecture Review Board, Engineering Leads |

---

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-05-23 | ArcKit AI | Initial creation from `/arckit:stakeholders` command | PENDING | PENDING |

---

## Executive Summary

### Purpose

This document identifies all key stakeholders for the Legacy Order Management Modernization programme, their underlying drivers (motivations, pressures, and concerns), how those drivers translate into measurable goals, and the business outcomes that will confirm success. It provides complete Stakeholder → Driver → Goal → Outcome traceability and forms the foundation for requirements prioritization, architecture decisions, and communications planning.

### Key Findings

The programme has strong executive sponsorship with well-aligned financial, operational, and strategic drivers converging on a single shared goal: replacing a brittle, high-cost legacy platform with an event-driven, cloud-native order management capability. The primary tension is between the CFO's desire for rapid cost realization and the Operations team's risk aversion to service disruption during migration. A phased, strangler-fig approach with dual-running periods — aligned to the architecture principles in `ARC-000-PRIN-v1.0` — resolves this conflict by delivering early quick-win phases before touching the highest-risk order processing core.

### Critical Success Factors

- Executive Sponsor maintains active visible sponsorship and shields the programme from scope creep during dual-running phases
- Operations team actively participates in migration planning (not just sign-off); their domain knowledge of edge cases is irreplaceable
- Anti-corruption layer design is validated before any legacy integration work begins, preventing legacy data model contamination
- Customer-facing order status and fulfillment performance are maintained at or above current levels at every migration phase gate
- Engineering teams are retrained on the modern stack at least one phase ahead of implementation, not during it

### Stakeholder Alignment Score

**Overall Alignment**: HIGH

Twelve of thirteen stakeholder groups share drivers that converge on the same programme outcomes. The one meaningful conflict — delivery speed vs. migration risk — has a well-understood resolution strategy. No stakeholder group is fundamentally opposed to the programme objective.

---

## Stakeholder Identification

### Internal Stakeholders

| Stakeholder | Role / Department | Power | Interest | Quadrant | Engagement Strategy |
|-------------|------------------|-------|----------|----------|---------------------|
| Executive Sponsor (CEO/COO) | Executive Leadership | HIGH | HIGH | Manage Closely | Fortnightly steering, escalation authority |
| CFO / Finance Director | Finance | HIGH | HIGH | Manage Closely | Monthly financial reporting, ROI dashboard |
| CTO / CIO | Technology Leadership | HIGH | HIGH | Manage Closely | Architecture reviews, weekly programme sync |
| VP Operations | Operations | HIGH | HIGH | Manage Closely | Phase gate approvals, migration sign-off |
| VP Commercial / Sales | Commercial | HIGH | HIGH | Manage Closely | Customer impact briefings, release previews |
| CISO / Head of Security | Information Security | HIGH | MEDIUM | Keep Satisfied | Security design reviews, compliance milestones |
| Head of Compliance / Legal | Legal & Compliance | HIGH | MEDIUM | Keep Satisfied | GDPR, PCI-DSS gate reviews |
| Finance / Accounting Team | Finance Operations | MEDIUM | HIGH | Keep Informed | Reconciliation testing, UAT participation |
| Order Fulfillment Teams | Operations | MEDIUM | HIGH | Keep Informed | UAT, daily stand-ups during cutover phases |
| Customer Service / Support | Customer Operations | MEDIUM | HIGH | Keep Informed | Training schedule, runbook reviews |
| Engineering / Development | Technology | MEDIUM | HIGH | Keep Informed | Sprint ceremonies, architecture sessions |
| HR / Change Management | People | LOW | MEDIUM | Monitor | Change impact briefings, training coordination |
| Internal Audit | Risk & Assurance | HIGH | LOW | Keep Satisfied | Audit readiness reviews at phase gates |

### External Stakeholders

| Stakeholder | Organization | Relationship | Power | Interest | Engagement Strategy |
|-------------|--------------|--------------|-------|----------|---------------------|
| End Customers | General public / B2B buyers | Beneficiary | LOW | HIGH | Release communications, status page |
| Logistics / Fulfillment Partners | 3PL providers | Supplier / Integration | MEDIUM | HIGH | Integration design reviews, API preview |
| Payment Gateway Providers | Financial processors | Supplier / Integration | MEDIUM | HIGH | PCI-DSS compliance alignment, API versioning |
| ERP / CRM Vendors | Enterprise software | Supplier / Integration | MEDIUM | MEDIUM | Migration planning, data mapping workshops |
| Regulatory Bodies (ICO, PCI SSC) | Regulatory | Oversight | HIGH | LOW | Compliance evidence packs, breach notification plan |

### Stakeholder Power-Interest Grid

```text
                              INTEREST
                Low                          High
          ┌──────────────────────┬──────────────────────────┐
          │                      │                          │
          │   KEEP SATISFIED     │    MANAGE CLOSELY        │
     High │                      │                          │
          │  • CISO              │  • Executive Sponsor     │
          │  • Head of Compliance│  • CFO / Finance Dir.    │
          │  • Internal Audit    │  • CTO / CIO             │
 P        │  • Regulatory Bodies │  • VP Operations         │
 O        │                      │  • VP Commercial / Sales │
 W        ├──────────────────────┼──────────────────────────┤
 E        │                      │                          │
 R        │      MONITOR         │    KEEP INFORMED         │
          │                      │                          │
     Low  │  • HR / Change Mgmt  │  • Finance/Acctg Team    │
          │                      │  • Order Fulfillment     │
          │                      │  • Customer Service      │
          │                      │  • Engineering Teams     │
          │                      │  • End Customers         │
          │                      │  • Logistics Partners    │
          └──────────────────────┴──────────────────────────┘
```

**Quadrant Interpretation:**

- **Manage Closely** (High Power, High Interest): Key decision-makers requiring active engagement at every phase gate
- **Keep Satisfied** (High Power, Low Interest): Influential stakeholders requiring periodic assurance — neglecting them creates blockers
- **Keep Informed** (Low Power, High Interest): Engaged stakeholders who need regular updates to maintain trust and surface operational intelligence
- **Monitor** (Low Power, Low Interest): Light-touch engagement unless context changes

---

## Stakeholder Drivers Analysis

### SD-1: Executive Sponsor (CEO/COO) — Strategic Transformation

**Stakeholder**: Executive Sponsor (CEO or COO)

**Driver Category**: STRATEGIC

**Driver Statement**: Eliminate the competitive disadvantage created by a legacy order management platform that cannot support new business models (subscriptions, multi-channel, B2B portals) or integrate with modern partner ecosystems.

**Context & Background**: Competitors have migrated to modern order management platforms and are shipping new commercial models (buy-online-pick-up-in-store, subscription tiers, real-time partner APIs) that the legacy system structurally cannot support. Board-level pressure exists to close this capability gap within a 24-month window before a scheduled market repositioning.

**Driver Intensity**: CRITICAL

**Enablers**:
- Clear phased roadmap that delivers capability increments rather than a single end-state cutover
- Visible early wins (e.g., real-time order tracking, self-service portal) that demonstrate momentum to the Board

**Blockers**:
- Programme scope creep into adjacent systems (ERP, CRM) before order management core is stable
- Risk aversion from Operations team slowing migration phases beyond the 24-month window

**Related Stakeholders**: CFO (cost alignment), CTO (delivery vehicle), VP Commercial (beneficiary of new capabilities)

---

### SD-2: CFO / Finance Director — Cost Reduction and ROI

**Stakeholder**: CFO / Finance Director

**Driver Category**: FINANCIAL

**Driver Statement**: Reduce the escalating total cost of ownership of the legacy order management platform — including licence fees, bespoke support contracts, manual reconciliation labour, and incident remediation — while generating a quantifiable return on the modernization investment within 24 months.

**Context & Background**: The legacy platform carries vendor support contracts at above-market rates (original vendor no longer mainstream), requires specialist contractors to maintain ageing codebase, and generates approximately 1,200 manual reconciliation events per month that consume finance team capacity. The CFO has committed to a 30% reduction in order management technology costs as part of a wider operational efficiency programme.

**Driver Intensity**: CRITICAL

**Enablers**:
- Cloud-native pricing model (pay-per-use) replacing fixed licence model
- Elimination of manual reconciliation through automated order-to-cash pipeline
- Early decommission of legacy infrastructure during phased migration (partial savings realized before full cutover)

**Blockers**:
- Dual-running period cost (new and legacy platforms simultaneously) may temporarily increase total spend before savings are realized
- Delay to migration phases extends the dual-running window and erodes the business case

**Related Stakeholders**: Executive Sponsor (ROI accountability), VP Operations (operational cost drivers), Engineering (delivery speed)

---

### SD-3: CTO / CIO — Technical Modernization and Talent

**Stakeholder**: CTO / CIO

**Driver Category**: STRATEGIC

**Driver Statement**: Replace a legacy monolithic order management system with a modular, cloud-native, event-driven architecture that attracts and retains engineering talent, reduces time-to-market for new features, and positions the organization as technically credible to enterprise customers and partners.

**Context & Background**: Engineering attrition has increased year-on-year with departing engineers citing the legacy stack as a primary reason. Recruitment for roles touching the order management system is 3–4 months slower than roles on modern parts of the estate. The CTO's 3-year technology strategy commits to eliminating all Tier-1 legacy systems by end of Year 3.

**Driver Intensity**: HIGH

**Enablers**:
- Modern, open-standard architecture that engineers can speak to in interviews and conferences
- Architecture Decision Records and principles (ARC-000-PRIN-v1.0) providing governance without slowing teams
- Investment in developer tooling, CI/CD pipelines, and automated testing as first-class deliverables

**Blockers**:
- Teams spending significant time maintaining legacy during migration, leaving insufficient capacity for modern build
- Architecture decisions made for short-term expediency that recreate the same coupling problems in a new technology stack

**Related Stakeholders**: Engineering Teams (direct beneficiary), VP Operations (delivery dependency), Executive Sponsor (strategic alignment)

---

### SD-4: VP Operations — Operational Reliability and Risk

**Stakeholder**: VP Operations

**Driver Category**: OPERATIONAL / RISK

**Driver Statement**: Eliminate the recurring operational disruption caused by legacy system outages, data integrity failures, and manual workarounds — while ensuring that the modernization programme itself does not introduce service disruption worse than the current state.

**Context & Background**: The legacy order management system has experienced 14 unplanned outages in the past 12 months, with 6 exceeding 2 hours and one 8-hour outage affecting approximately 4,200 customer orders. Each outage triggers a manual recovery process involving 6–8 staff across operations and finance. The VP Operations' personal KPIs include system uptime and order error rate — both of which have deteriorated year-on-year.

**Driver Intensity**: HIGH

**Enablers**:
- Incremental migration with explicit rollback plans tested before each phase goes live (aligned to Principle 1 in ARC-000-PRIN-v1.0)
- Dual-running period with clear exit criteria so Operations can observe new system stability before legacy is decommissioned
- Automated monitoring and alerting on the new platform, giving Operations real-time visibility

**Blockers**:
- Compressed migration timelines that skip stabilization periods between phases
- Insufficient Operations involvement in migration planning — Operations know where the edge cases are

**Related Stakeholders**: Order Fulfillment Teams (direct impact), Customer Service (customer-facing consequence), CFO (cost of outages)

---

### SD-5: VP Commercial / Sales — Revenue Growth and Customer Retention

**Stakeholder**: VP Commercial / Sales Director

**Driver Category**: FINANCIAL / CUSTOMER

**Driver Statement**: Recover lost revenue caused by order fulfillment failures and customer churn driven by poor order experience (inaccurate tracking, delayed shipping, inability to self-serve order changes), and unlock new revenue streams from commercial models the legacy platform cannot support.

**Context & Background**: Net Promoter Score surveys identify order management as the second-lowest-rated customer touchpoint. An estimated 8–12% of customers who experienced an order error in the past 12 months did not reorder within 90 days. The commercial team has been unable to launch a B2B customer portal or subscription offering because the legacy system has no API layer — two initiatives with a combined pipeline value of £3.2M annually.

**Driver Intensity**: HIGH

**Enablers**:
- Real-time order status API enabling self-service customer portal
- Webhook-based event notifications for logistics partners (replacing batch files)
- New commercial model enablement (subscriptions, tiered SLAs) via configurable order types on the modern platform

**Blockers**:
- Extended migration timeline keeps the commercial team blocked from launching new revenue initiatives
- Customer-visible degradation during cutover phases risks compounding existing NPS problems

**Related Stakeholders**: End Customers (beneficiary), VP Operations (fulfillment dependency), CTO (delivery)

---

### SD-6: CISO / Head of Security — Risk Reduction and Compliance

**Stakeholder**: CISO / Head of Information Security

**Driver Category**: COMPLIANCE / RISK

**Driver Statement**: Remediate the security debt in the legacy order management platform — including outdated authentication mechanisms, insufficient audit logging, and patch lag — and ensure the modernized platform is built to the zero-trust architecture principles defined in ARC-000-PRIN-v1.0.

**Context & Background**: The most recent penetration test against the legacy platform identified 3 high-severity and 11 medium-severity findings. The inability to apply vendor security patches (deprecated platform) means 4 of those findings cannot be remediated without migrating away from the legacy system. Two of the high-severity findings relate to insufficient audit logging for PCI-DSS scope. The CISO has a board-level commitment to close all high-severity findings within 12 months.

**Driver Intensity**: HIGH

**Enablers**:
- Security by Design review embedded into each migration phase gate (not retrofitted at end)
- Secrets management and zero-trust service authentication included in the architecture baseline from Phase 1
- Structured audit logging of all order state changes from day one of the new platform

**Blockers**:
- Migration phases designed for speed that de-prioritize security controls until a later phase
- Anti-corruption layer with the legacy system introducing new attack surface if not designed carefully

**Related Stakeholders**: Head of Compliance/Legal (regulatory consequence), Engineering Teams (implementation), Internal Audit (evidence consumption)

---

### SD-7: Head of Compliance / Legal — Regulatory Adherence

**Stakeholder**: Head of Compliance / Legal Counsel

**Driver Category**: COMPLIANCE

**Driver Statement**: Ensure the modernized platform is compliant with GDPR data subject rights (including right to erasure), PCI-DSS for payment data handling, and maintains an immutable, queryable audit trail sufficient for dispute resolution and regulatory enquiry response.

**Context & Background**: A GDPR Subject Access Request received 14 months ago took 47 days to fulfill because order history data was fragmented across 6 tables in the legacy system with no unified query path. The ICO has subsequently contacted the organization requesting evidence of improvement. PCI-DSS re-certification is due in 8 months and the auditors have flagged audit log gaps as a significant concern.

**Driver Intensity**: HIGH

**Enablers**:
- Immutable order audit trail designed into the data model from Phase 1 (Principle 8 in ARC-000-PRIN-v1.0)
- Automated data retention and deletion enforcement aligned to GDPR retention schedules
- Clear data classification applied to all order data fields (Principle 9 in ARC-000-PRIN-v1.0)

**Blockers**:
- PCI-DSS re-certification deadline in 8 months creates pressure on the migration timeline whether ready or not
- GDPR right-to-erasure becomes more complex if order data is replicated across multiple services without a clear system of record (Principle 10 in ARC-000-PRIN-v1.0)

**Related Stakeholders**: CISO (technical implementation), Engineering (data model design), Finance (order-to-cash audit evidence)

---

### SD-8: Finance / Accounting Team — Elimination of Manual Reconciliation

**Stakeholder**: Finance / Accounting Operations Team

**Driver Category**: OPERATIONAL / FINANCIAL

**Driver Statement**: Eliminate the 1,200+ monthly manual reconciliation events caused by order data discrepancies between the legacy order management system and the finance/ERP system, freeing approximately 2 FTE currently dedicated to reconciliation remediation.

**Context & Background**: The legacy system exports order data to the ERP via nightly batch files. Batch failures, format inconsistencies, and duplicate records generate daily reconciliation work. Two finance staff spend an estimated 80% of their time each month on reconciliation exception handling. This also causes month-end close to extend 2–3 days beyond target.

**Driver Intensity**: MEDIUM

**Enablers**:
- Real-time event-driven integration with ERP replacing nightly batch (Principle 14 in ARC-000-PRIN-v1.0)
- Single source of truth for order financial data eliminating cross-system discrepancies (Principle 10)
- Automated reconciliation reporting with exception alerting

**Blockers**:
- ERP integration redesign is out of scope for initial migration phases — reconciliation benefits may be deferred to later phases
- Finance team availability for UAT and testing is constrained by month-end close cycles

**Related Stakeholders**: CFO (cost savings), Order Fulfillment Teams (upstream data quality), Engineering (integration design)

---

### SD-9: Order Fulfillment Teams — Usability and Workload Reduction

**Stakeholder**: Order Fulfillment Operations Staff

**Driver Category**: OPERATIONAL / PERSONAL

**Driver Statement**: Replace error-prone, manual-step-heavy legacy workflows with an intuitive, automated order management interface that reduces cognitive load, minimizes re-keying, and eliminates the need for system-specific workarounds that have accumulated over years of deferred maintenance.

**Context & Background**: The order fulfillment team currently relies on 14 documented workarounds for known legacy system defects — including a mandatory manual step to prevent a duplicate-order bug triggered by specific payment types. Staff onboarding time for the order management system is 6 weeks, primarily because of undocumented workarounds. High staff turnover in this team is partly attributed to system frustration.

**Driver Intensity**: HIGH

**Enablers**:
- Fulfillment team members included in the design and UAT process from Phase 1
- Existing workarounds documented and systematically eliminated (not replicated) in the modern platform
- Training delivered 4 weeks ahead of each phase cutover, not on the day

**Blockers**:
- New system that replaces legacy defects with different unfamiliar defects may increase rather than decrease frustration
- If the team is not involved early, the new system may not reflect operational realities

**Related Stakeholders**: VP Operations (accountability), Customer Service (downstream impact), Engineering (usability design)

---

### SD-10: Engineering / Development Teams — Developer Experience

**Stakeholder**: Software Engineering and Platform Engineering Teams

**Driver Category**: STRATEGIC / PERSONAL

**Driver Statement**: Work on a modern, well-documented, testable codebase with proper CI/CD pipelines, observability tooling, and clear architectural boundaries — enabling engineers to deliver features confidently and to build careers in relevant technologies rather than a deprecated legacy stack.

**Context & Background**: The legacy order management codebase has no automated tests, a 2-week manual release cycle, and is written in a framework version that has been end-of-life for 5 years. Engineers report high anxiety around deployments — one recent deployment took 11 hours to roll back due to the absence of an automated rollback path. Three senior engineers have left in the past 8 months citing the legacy stack as a primary reason.

**Driver Intensity**: MEDIUM

**Enablers**:
- CI/CD pipelines with automated testing and one-click rollback implemented before teams build on the new platform
- Architecture Decision Records (ADRs) giving engineers context for design decisions rather than arbitrary constraints
- Modern tooling and infrastructure as code from the start of Phase 1

**Blockers**:
- Engineers split between maintaining legacy and building modern — context switching erodes both quality and morale
- If the modern architecture recreates the same monolithic coupling in new technology, engineer motivation will collapse quickly

**Related Stakeholders**: CTO (strategic owner), VP Operations (delivery dependency), HR (retention impact)

---

### SD-11: End Customers — Service Quality and Transparency

**Stakeholder**: End Customers (B2C and B2B)

**Driver Category**: CUSTOMER

**Driver Statement**: Receive accurate, timely, and self-serviceable order management — real-time tracking, proactive notifications on delays, and the ability to modify or cancel orders without calling customer service.

**Context & Background**: Customer satisfaction surveys identify order tracking and communication as top pain points. Currently, order status is updated in batch every 4 hours, meaning customers call support for status information that the system already holds but has not surfaced. Self-service order cancellation is not available — customers must call, and 34% of those calls result in escalation due to the complexity of the manual cancellation process in the legacy system.

**Driver Intensity**: HIGH

**Enablers**:
- Real-time order status API powering a self-service customer portal
- Event-driven notifications (email/SMS/webhook) at each order lifecycle transition
- Self-service cancellation and modification for eligible orders

**Blockers**:
- Customer-facing features are dependent on the order processing core being migrated first — customer experience improvements are a Phase 2+ deliverable in most migration roadmaps

**Related Stakeholders**: VP Commercial (NPS impact), Customer Service (call volume reduction), VP Operations (fulfillment accuracy upstream)

---

### SD-12: Logistics / Fulfillment Partners — Integration Reliability

**Stakeholder**: Third-party logistics and fulfillment partners (3PLs)

**Driver Category**: OPERATIONAL

**Driver Statement**: Replace brittle, batch-based file integrations with reliable, real-time API integrations that reduce integration failures, enable faster order dispatch, and allow partners to onboard new capabilities without waiting for bespoke legacy integration work.

**Context & Background**: Current integration with logistics partners is via SFTP file exchange on a nightly batch schedule. Integration failures average 3 per month and require manual intervention from both parties. Adding a new logistics partner requires 3–4 months of bespoke integration work due to the absence of a standard API layer. One partner has threatened to charge penalty fees for SLA breaches caused by integration failures.

**Driver Intensity**: MEDIUM

**Enablers**:
- Versioned, documented REST or event-streaming API layer (Principle 13 in ARC-000-PRIN-v1.0)
- Standardized integration patterns enabling new partners to onboard via self-service documentation
- Real-time order dispatch events replacing batch files

**Blockers**:
- Partners must update their own integration code to consume the new API — this requires coordination and lead time
- API changes without adequate versioning and deprecation notice will break partner integrations

**Related Stakeholders**: VP Commercial (partner relationship), Engineering (API design), CISO (partner authentication and access controls)

---

## Driver-to-Goal Mapping

### Goal G-1: Migrate Core Order Processing to Cloud-Native Platform

**Derived From Drivers**: SD-1, SD-3, SD-4, SD-10

**Goal Owner**: CTO / CIO

**Goal Statement**: Complete the incremental migration of all core order creation, management, and fulfillment capabilities to the new cloud-native platform by Month 18, with zero loss of order data and no month exceeding the current 99.0% uptime baseline during migration.

**Why This Matters**: The new platform is the enabling condition for every other goal. Without it, cost savings, compliance improvements, and customer experience enhancements cannot be realized. The incremental approach (aligned to Principle 1 in ARC-000-PRIN-v1.0) satisfies both the CTO's modernization mandate and the VP Operations' risk constraint.

**Success Metrics**:
- **Primary Metric**: Percentage of order volume processed on the new platform (target: 100% by Month 18)
- **Secondary Metrics**:
  - Number of legacy components decommissioned per phase
  - Uptime of new platform per phase (target: >= 99.5% from Phase 2 onwards)
  - Zero order data loss events confirmed by reconciliation reports

**Baseline**: 0% of order volume on new platform; legacy system uptime 99.0% over trailing 12 months

**Target**: 100% of order volume on new platform by Month 18; new platform uptime >= 99.5%

**Measurement Method**: Order routing metrics from API gateway; automated reconciliation reports comparing legacy and new platform order counts per phase; uptime monitoring dashboard

**Dependencies**:
- Anti-corruption layer design approved before Phase 1 implementation begins
- Engineering team capacity protected from competing priorities during migration phases
- Operations team available for UAT and migration sign-off at each phase gate

**Risks to Achievement**:
- Legacy system instability during dual-running period increases migration urgency and reduces available stabilization time
- Underestimated complexity in legacy data model delays Phase 1 and compresses subsequent phases

---

### Goal G-2: Reduce Total Cost of Ownership by 30%

**Derived From Drivers**: SD-2, SD-8, SD-9

**Goal Owner**: CFO / Finance Director

**Goal Statement**: Reduce the total annual cost of ownership (TCO) of the order management platform by 30% within 24 months of programme start, measured against the Year 0 TCO baseline including licence fees, support contracts, contractor costs, and manual reconciliation labour.

**Why This Matters**: The CFO has a board commitment to operational efficiency targets. Demonstrating TCO reduction validates the investment case and secures continued programme funding through annual budget cycles.

**Success Metrics**:
- **Primary Metric**: Annual TCO (Year 2 vs. Year 0 baseline) — target: 30% reduction
- **Secondary Metrics**:
  - Legacy licence and support contract costs eliminated (target: 100% eliminated by Month 18)
  - Manual reconciliation events per month (current: 1,200; target: < 100 by Month 24)
  - Finance FTE hours spent on reconciliation (current: ~2 FTE; target: < 0.25 FTE)

**Baseline**: Year 0 TCO to be formally captured and agreed with Finance at programme initiation (estimated: legacy licence + support + contractors + reconciliation labour = to be confirmed)

**Target**: 30% TCO reduction vs. Year 0 baseline, confirmed by Month 24 Finance review

**Measurement Method**: Programme finance tracking against TCO baseline model; payroll data for reconciliation labour; cloud cost management tooling for new platform spend

**Dependencies**:
- Legacy decommission milestones achieved on schedule (costs persist while legacy runs in parallel)
- Finance team engagement in TCO baselining exercise at programme initiation

**Risks to Achievement**:
- Extended dual-running period increases cloud spend before legacy costs are eliminated
- Scope expansion into adjacent systems (ERP, CRM) increases programme cost without proportional TCO benefit in the order management domain

---

### Goal G-3: Achieve 99.9% Order Processing Uptime and 80% Error Rate Reduction

**Derived From Drivers**: SD-4, SD-5, SD-11

**Goal Owner**: VP Operations

**Goal Statement**: Achieve 99.9% uptime for order processing on the new platform by Month 12 (first full stable phase in production) and reduce order error rate (incorrect status, duplicate orders, lost orders) by 80% compared to the trailing 12-month baseline by Month 18.

**Why This Matters**: Operational reliability is the VP Operations' primary KPI and the prerequisite for VP Commercial's customer satisfaction targets. Failure to meet this goal undermines the entire business case for modernization from Operations' perspective.

**Success Metrics**:
- **Primary Metric**: New platform monthly uptime percentage (target: >= 99.9% from Month 12)
- **Secondary Metrics**:
  - Mean time to recover (MTTR) from incidents (current: ~3 hours; target: < 30 minutes)
  - Order error events per 10,000 orders (current baseline to be measured in Month 1; target: 80% reduction)
  - Number of manual recovery procedures triggered per month (current: 14; target: < 3)

**Baseline**: Legacy system 12-month uptime: 99.0%; order error rate and MTTR to be formally measured in Month 1

**Target**: 99.9% uptime, 80% error rate reduction, MTTR < 30 minutes — all by Month 18

**Measurement Method**: Application performance monitoring; automated alerting and incident tracking; order reconciliation reports

**Dependencies**:
- Automated health checks and alerting fully instrumented from Phase 1 (Principle 6 in ARC-000-PRIN-v1.0)
- Chaos / fault injection testing completed before each phase goes fully live
- On-call runbooks created and rehearsed before production traffic is routed to new platform

**Risks to Achievement**:
- Insufficient observability instrumentation in early phases means incidents are detected late, inflating MTTR
- Legacy system deteriorates further during migration window, displacing Operations team attention from new platform stabilization

---

### Goal G-4: Improve Order-to-Ship Time and Enable Real-Time Customer Tracking

**Derived From Drivers**: SD-5, SD-11, SD-12

**Goal Owner**: VP Commercial / Sales

**Goal Statement**: Reduce average order-to-ship time for standard orders from 48 hours to 24 hours by Month 18, and provide real-time order status to customers (updated within 5 minutes of status change, replacing current 4-hour batch cycle) by Month 12.

**Why This Matters**: Real-time tracking directly addresses the top customer complaint and will improve NPS; reduced order-to-ship time is the enabler for new commercial SLA tiers that the commercial team have in their pipeline.

**Success Metrics**:
- **Primary Metric**: Average order-to-ship time (target: 24 hours for standard orders)
- **Secondary Metrics**:
  - Order status update latency (current: up to 4 hours; target: < 5 minutes)
  - Customer service call volume for order status enquiries (current baseline to be measured; target: 30% reduction)
  - Customer NPS for order experience (current NPS to be baselined; target: +15 points over 18 months)

**Baseline**: Average order-to-ship: 48 hours; status update latency: up to 4 hours; NPS to be baselined

**Target**: 24-hour order-to-ship; < 5-minute status updates; NPS +15 by Month 18

**Measurement Method**: Order management analytics; customer satisfaction surveys (quarterly); call centre reporting for order status call volume

**Dependencies**:
- Event-driven order lifecycle architecture implemented (Principle 14 in ARC-000-PRIN-v1.0)
- Logistics partner API integration completed (replaces batch SFTP)
- Customer-facing portal or notification service built on order events

**Risks to Achievement**:
- Logistics partner adoption of the new API is slower than planned, keeping real-time dispatch blocked
- Customer portal development is descoped or delayed, meaning status data is available internally but not surfaced to customers

---

### Goal G-5: Achieve and Maintain Security and Compliance Posture

**Derived From Drivers**: SD-6, SD-7

**Goal Owner**: CISO / Head of Compliance

**Goal Statement**: Remediate all 3 high-severity and 11 medium-severity legacy platform findings within the 12-month programme window; achieve PCI-DSS re-certification for the new platform within 8 months; implement GDPR-compliant data lifecycle management (including automated right-to-erasure) by Month 12.

**Why This Matters**: Two of the high-severity findings cannot be remediated without migrating away from the legacy platform — migration and security remediation are the same action. PCI-DSS re-certification has a fixed external deadline that cannot be moved.

**Success Metrics**:
- **Primary Metric**: Open high-severity security findings (current: 3; target: 0 by Month 8)
- **Secondary Metrics**:
  - PCI-DSS re-certification achieved by Month 8 (pass/fail)
  - Time to fulfill a GDPR Subject Access Request (current: 47 days; target: < 5 days by Month 12)
  - GDPR right-to-erasure automation coverage (target: 100% of personal data fields automated by Month 12)

**Baseline**: 3 high-severity findings, 11 medium-severity findings; PCI-DSS re-cert due in 8 months; SAR fulfillment time: 47 days

**Target**: Zero high-severity findings by Month 8; PCI-DSS re-certified; SAR fulfillment < 5 days

**Measurement Method**: Security findings tracker (updated after each penetration test); PCI-DSS QSA report; SAR response time log; automated data lifecycle audit reports

**Dependencies**:
- Phase 1 of migration must include the components in PCI-DSS scope to enable re-certification on the new platform
- Data classification exercise (Principle 9 in ARC-000-PRIN-v1.0) completed in Month 1 before data model design is finalized

**Risks to Achievement**:
- PCI-DSS scope components are in a later migration phase — certification cannot be achieved on the new platform until those components are migrated
- Right-to-erasure automation is harder than estimated due to undiscovered PII fields in the legacy data model

---

### Goal G-6: Reduce Feature Delivery Lead Time by 75%

**Derived From Drivers**: SD-1, SD-3, SD-10

**Goal Owner**: CTO / CIO

**Goal Statement**: Reduce mean time from feature request to production deployment for order management features from 8 weeks to 2 weeks by Month 18, and reduce production incidents caused by deployments by 60% compared to the legacy baseline.

**Why This Matters**: Delivery velocity is the CTO's primary measure of architectural health and is directly tied to the commercial team's ability to respond to market opportunities. The current 8-week cycle means the commercial team has stopped requesting order management changes, routing requests instead to expensive workarounds.

**Success Metrics**:
- **Primary Metric**: Mean lead time for order management feature delivery (current: 8 weeks; target: 2 weeks)
- **Secondary Metrics**:
  - Deployment frequency (current: bi-weekly; target: daily or on-demand)
  - Change failure rate (production incidents caused by deployments; current: ~35%; target: < 10%)
  - Mean time to restore after deployment-caused incident (current: 3 hours; target: < 30 minutes)

**Baseline**: 8-week feature lead time; bi-weekly deployments; 35% change failure rate

**Target**: 2-week lead time; daily deployments; < 10% change failure rate — by Month 18

**Measurement Method**: CI/CD pipeline metrics (deployment frequency, lead time); incident tracking system (deployment correlation); team velocity tracking

**Dependencies**:
- CI/CD pipelines with automated testing and rollback operational from Phase 1
- Engineers fully trained on new stack before being asked to deliver features on it
- Architecture boundaries defined so teams can deploy independently without coordination overhead

**Risks to Achievement**:
- Engineering team split across legacy maintenance and new development reduces velocity on both
- Automated test coverage insufficient to give engineers confidence in continuous deployment

---

## Goal-to-Outcome Mapping

### Outcome O-1: Platform Modernization Delivered

**Supported Goals**: G-1, G-6

**Outcome Statement**: 100% of order volume processed on the new cloud-native platform by Month 18 with full legacy decommission by Month 24, and engineering teams delivering order management features in 2-week cycles with daily deployments.

**Measurement Details**:

- **KPI**: Order volume on new platform (%)
- **Current Value**: 0%
- **Target Value**: 100% by Month 18
- **Measurement Frequency**: Monthly (per phase gate)
- **Data Source**: API gateway routing telemetry; platform analytics
- **Report Owner**: CTO / Programme Manager

**Business Value**:

- **Financial Impact**: Enables legacy decommission, eliminating licence and contractor costs
- **Strategic Impact**: Closes capability gap with competitors; enables new commercial models
- **Operational Impact**: 2-week feature cycle vs. 8-week; daily deployments vs. bi-weekly
- **Customer Impact**: New features (real-time tracking, self-service) enabled by modern platform

**Timeline**:

- **Phase 1 (Months 1–6)**: Order creation and capture on new platform; legacy handles fulfillment
- **Phase 2 (Months 7–12)**: Fulfillment and logistics integration migrated; dual-running ends for creation
- **Phase 3 (Months 13–18)**: Reporting, analytics, and ERP integration migrated; 100% on new platform
- **Sustainment (Year 2+)**: Legacy fully decommissioned; TCO savings fully realized

**Stakeholder Benefits**:

- **CTO**: Modern architecture, talent retention, speed of delivery
- **Executive Sponsor**: Board commitment delivered, competitive parity restored
- **Engineering Teams**: Modern tooling, meaningful work, career development

**Leading Indicators**:
- Phase 1 go-live achieved on schedule
- No rollbacks required beyond the planned stabilization window
- Deployment frequency increasing month-on-month

**Lagging Indicators**:
- Legacy system fully decommissioned
- All high-severity security findings closed
- Feature delivery lead time confirmed at 2 weeks over 3 consecutive months

---

### Outcome O-2: 30% Total Cost of Ownership Reduction

**Supported Goals**: G-2

**Outcome Statement**: Annual order management TCO reduced by 30% vs. Year 0 baseline by Month 24, with legacy licence and support costs fully eliminated and reconciliation labour reduced to < 0.25 FTE.

**Measurement Details**:

- **KPI**: Annual TCO vs. Year 0 baseline (%)
- **Current Value**: Year 0 TCO baseline (to be confirmed in Month 1)
- **Target Value**: 30% reduction by Month 24
- **Measurement Frequency**: Quarterly financial review
- **Data Source**: Finance cost tracking; cloud billing; payroll for reconciliation labour
- **Report Owner**: CFO / Finance Director

**Business Value**:

- **Financial Impact**: 30% TCO reduction; 2 FTE reconciliation labour redirected to value-adding finance work
- **Strategic Impact**: Validates the modernization business case for future programme phases
- **Operational Impact**: Month-end close cycle shortened by 2–3 days (elimination of reconciliation backlog)
- **Customer Impact**: Indirect — cost savings reinvested in product capability

**Timeline**:

- **Phase 1 (Months 1–6)**: Dual-running cost peak; partial savings from reduced contractor spend
- **Phase 2 (Months 7–12)**: First legacy components decommissioned; licence cost reduction begins
- **Phase 3 (Months 13–24)**: Legacy fully decommissioned; 30% TCO reduction confirmed
- **Sustainment (Year 2+)**: Cloud cost optimization drives further incremental savings

**Stakeholder Benefits**:

- **CFO**: Board target achieved; business case validated
- **Finance / Accounting Team**: Reconciliation burden eliminated; 2 FTE redirected
- **Executive Sponsor**: Efficiency commitment honoured

**Leading Indicators**:
- Dual-running period cost tracked against forecast
- First legacy component decommissioned on schedule
- Reconciliation event count reducing in tandem with migration phases

**Lagging Indicators**:
- Month 24 Finance sign-off on 30% TCO reduction vs. baseline
- Legacy infrastructure fully decommissioned and invoicing ceased

---

### Outcome O-3: 99.9% Order Processing Uptime and Improved Customer Experience

**Supported Goals**: G-3, G-4

**Outcome Statement**: New platform achieves 99.9% monthly uptime from Month 12 onwards; order-to-ship time reduced to 24 hours; customer NPS for order experience improves by +15 points by Month 18.

**Measurement Details**:

- **KPI 1**: Monthly uptime (%) — target >= 99.9%
- **KPI 2**: Average order-to-ship time — target 24 hours
- **KPI 3**: Order experience NPS — target baseline + 15 points
- **Current Value**: Uptime 99.0%; order-to-ship 48 hours; NPS to be baselined Month 1
- **Target Value**: 99.9% uptime; 24-hour ship; NPS +15
- **Measurement Frequency**: Uptime: monthly; Order-to-ship: weekly; NPS: quarterly
- **Data Source**: Application monitoring; order management analytics; customer surveys
- **Report Owner**: VP Operations (uptime); VP Commercial (NPS, order-to-ship)

**Business Value**:

- **Financial Impact**: 8–12% customer churn recovery from order experience improvement; new SLA tiers enabled
- **Strategic Impact**: Competitive parity on order experience; B2B portal and subscription model unblocked
- **Operational Impact**: 30% reduction in customer service call volume for order status enquiries
- **Customer Impact**: Real-time tracking, self-service cancellation, fewer order errors

**Timeline**:

- **Phase 1 (Months 1–6)**: Reliability baseline established; MTTR improvement first visible
- **Phase 2 (Months 7–12)**: 99.9% uptime target first achieved; real-time status launched
- **Phase 3 (Months 13–18)**: NPS +15 confirmed; 24-hour order-to-ship confirmed
- **Sustainment (Year 2+)**: 99.95% uptime target set; further NPS improvement through self-service features

**Stakeholder Benefits**:

- **VP Operations**: Personal KPI achieved; manual recovery burden eliminated
- **VP Commercial / Sales**: NPS improvement; new revenue streams unblocked
- **End Customers**: Fewer errors, real-time visibility, self-service
- **Customer Service**: 30% reduction in order-status call volume

**Leading Indicators**:
- Incident MTTR reducing month-on-month from Phase 1
- Order status update latency confirmed < 5 minutes from Phase 2
- Customer service call deflection rate increasing after real-time tracking launch

**Lagging Indicators**:
- 99.9% uptime confirmed over 3 consecutive months
- NPS survey confirms +15 improvement vs. baseline

---

### Outcome O-4: Security and Compliance Posture Achieved

**Supported Goals**: G-5

**Outcome Statement**: All 3 high-severity security findings closed by Month 8; PCI-DSS re-certification achieved by Month 8; GDPR Subject Access Request fulfillment time reduced from 47 days to < 5 days by Month 12.

**Measurement Details**:

- **KPI 1**: Open high-severity findings — target: 0 by Month 8
- **KPI 2**: PCI-DSS certification status — target: re-certified by Month 8
- **KPI 3**: SAR fulfillment time — target: < 5 days by Month 12
- **Current Value**: 3 high-severity findings; PCI-DSS re-cert due in 8 months; SAR time: 47 days
- **Measurement Frequency**: Monthly security findings review; PCI-DSS: milestone-based; SAR: per occurrence
- **Data Source**: Security findings tracker; QSA report; legal team SAR log
- **Report Owner**: CISO (findings, PCI-DSS); Head of Compliance (SAR, GDPR)

**Business Value**:

- **Financial Impact**: Avoidance of ICO enforcement action (potential fines); avoidance of PCI-DSS non-compliance penalties
- **Strategic Impact**: Trustworthy data handling as a competitive differentiator with enterprise B2B customers
- **Operational Impact**: SAR fulfillment < 5 days removes compliance team bottleneck
- **Customer Impact**: Improved data rights experience; confidence in data handling

**Timeline**:

- **Phase 1 (Months 1–6)**: Data classification completed; immutable audit trail live on new platform; PCI-DSS scoped components identified for migration
- **Phase 2 (Months 7–8)**: PCI-DSS scoped components migrated; re-certification audit submitted
- **Phase 3 (Months 9–12)**: GDPR right-to-erasure automation complete; SAR fulfillment SLA confirmed
- **Sustainment (Year 2+)**: Annual penetration testing; continuous compliance monitoring

**Stakeholder Benefits**:

- **CISO**: Board commitment to close high-severity findings honoured
- **Head of Compliance**: ICO response evidence pack complete; PCI-DSS clean bill
- **Internal Audit**: Compliance evidence available and queryable
- **End Customers**: Data rights respected and fulfillable within statutory timeframes

**Leading Indicators**:
- High-severity findings count reducing per month
- PCI-DSS scoped components confirmed in migration Phase 1 or 2 scope
- Data classification exercise completed by Month 2

**Lagging Indicators**:
- QSA sign-off on PCI-DSS re-certification
- ICO acknowledgment of SAR fulfillment improvement
- Zero data breach events attributable to legacy platform findings

---

## Complete Traceability Matrix

### Stakeholder → Driver → Goal → Outcome

| Stakeholder | Driver ID | Driver Summary | Goal ID | Goal Summary | Outcome ID | Outcome Summary |
|-------------|-----------|----------------|---------|--------------|------------|-----------------|
| Executive Sponsor | SD-1 | Strategic transformation, close capability gap | G-1 | Migrate core platform by Month 18 | O-1 | Platform modernized, legacy decommissioned |
| Executive Sponsor | SD-1 | Strategic transformation | G-6 | 75% reduction in feature lead time | O-1 | Platform modernized, velocity improved |
| CFO | SD-2 | 30% TCO reduction | G-2 | Reduce TCO by 30% by Month 24 | O-2 | 30% TCO reduction confirmed |
| CFO | SD-2 | Eliminate reconciliation costs | G-2 | Reduce reconciliation FTE cost | O-2 | Reconciliation < 0.25 FTE |
| CTO / CIO | SD-3 | Technical modernization, talent | G-1 | Migrate core platform | O-1 | Modern platform live |
| CTO / CIO | SD-3 | Reduce talent attrition | G-6 | Feature lead time 2 weeks | O-1 | Developer velocity confirmed |
| VP Operations | SD-4 | Operational reliability | G-3 | 99.9% uptime, 80% error reduction | O-3 | Uptime and reliability targets met |
| VP Commercial | SD-5 | Revenue recovery, new models | G-4 | 24-hour ship, real-time tracking | O-3 | NPS +15, order experience improved |
| VP Commercial | SD-5 | New revenue streams | G-1 | Platform enabling new models | O-1 | B2B portal and subscription unblocked |
| CISO | SD-6 | Security finding remediation | G-5 | Close all high-severity findings | O-4 | Security compliance achieved |
| Head of Compliance | SD-7 | PCI-DSS, GDPR compliance | G-5 | PCI-DSS re-cert, SAR < 5 days | O-4 | Compliance posture confirmed |
| Finance / Acctg | SD-8 | Eliminate manual reconciliation | G-2 | < 100 reconciliation events/month | O-2 | TCO and labour savings realized |
| Order Fulfillment | SD-9 | Usability, workload reduction | G-3 | Error rate -80%, fewer workarounds | O-3 | Operational reliability and usability |
| Engineering Teams | SD-10 | Developer experience | G-6 | Lead time 2 weeks, daily deploys | O-1 | Modern tooling and delivery velocity |
| End Customers | SD-11 | Real-time tracking, self-service | G-4 | Real-time status, 24-hour ship | O-3 | NPS +15, customer experience |
| Logistics Partners | SD-12 | Real-time API integration | G-4 | Real-time dispatch, API-first | O-3 | Reliable partner integration |

---

### Conflict Analysis

**Conflict C-1: CFO's cost urgency vs. VP Operations' migration risk aversion**

The CFO wants to move quickly through migration phases to realize cost savings as early as possible (dual-running period is a cost drag). The VP Operations wants each phase to have an extended stabilization period before the next phase begins, to verify new platform reliability before increasing its load.

- **Resolution Strategy**: Define time-boxed stabilization periods per phase (e.g., 4 weeks of parallel running with < 5% error rate as the exit criterion) rather than open-ended stabilization. This gives Operations a clear safety net while giving Finance a predictable migration schedule. Phase gate criteria are agreed in Month 1 and not renegotiated mid-programme.

**Conflict C-2: Engineering team split between legacy maintenance and new build**

The CTO wants maximum engineering capacity on the new platform. VP Operations needs the legacy system kept stable during migration (requiring ongoing engineering support). These compete for the same finite engineering resource.

- **Resolution Strategy**: Dedicated legacy maintenance squad (minimum viable team) defined before programme start and ring-fenced. Modern platform team is separately resourced and does not rotate into legacy maintenance during migration phases.

**Conflict C-3: PCI-DSS re-certification deadline vs. migration phasing**

The compliance deadline (8 months) may force PCI-DSS scoped components into Phase 1 of the migration regardless of technical readiness, potentially compressing the anti-corruption layer design and testing time for those components.

- **Resolution Strategy**: PCI-DSS scope components are identified in Month 1 as part of the data classification exercise (Principle 9 in ARC-000-PRIN-v1.0). If those components cannot safely be migrated in Phase 1, an interim compensating control is negotiated with the QSA to maintain certification on the legacy platform while migration proceeds — this is escalated to CISO and Head of Compliance within the first month.

---

### Synergies

**Synergy S-1: SD-4 (Operations reliability) and SD-11 (Customer experience)** — Both are satisfied by the same goal (G-3: 99.9% uptime, 80% error reduction). Investing in reliability benefits both the internal Operations team and end customers simultaneously, giving this goal the broadest stakeholder backing in the programme.

**Synergy S-2: SD-6 (Security remediation) and SD-7 (GDPR compliance)** — Security and compliance goals (G-5) are jointly owned and share the same evidence base (audit logs, data classification). A single immutable audit trail and data classification exercise satisfies both stakeholders, reducing duplicated effort.

**Synergy S-3: SD-2 (Cost reduction) and SD-8 (Reconciliation elimination)** — Finance team reconciliation pain (SD-8) is both an operational and a financial cost. Eliminating it satisfies the Finance team's operational driver while directly contributing to the CFO's 30% TCO goal (G-2). The same event-driven integration that fixes SD-12 (logistics partner batching) also fixes the ERP reconciliation problem, making the integration modernization investment serve three stakeholder groups simultaneously.

**Synergy S-4: SD-3 (Engineering modernization) and SD-10 (Developer experience)** — CTO and Engineering have perfectly aligned drivers. Investment in CI/CD pipelines, automated testing, and modern tooling (Principles 19–21 in ARC-000-PRIN-v1.0) simultaneously satisfies both, with no trade-off.

---

## Communication & Engagement Plan

### Executive Sponsor (CEO/COO)

**Primary Message**: The programme is on track to close the competitive capability gap within 24 months through a risk-managed, incremental approach that delivers business value at each phase gate.

**Key Talking Points**:
- Phase-by-phase milestones with clear go/no-go criteria protect business continuity
- Early phases unlock real-time tracking and API capabilities that unblock commercial pipeline
- Architecture principles established in ARC-000-PRIN-v1.0 govern all decisions without creating bureaucratic delay

**Communication Frequency**: Fortnightly steering board; escalation as needed

**Preferred Channel**: Steering board meeting; executive dashboard (uptime, migration %, cost trend)

**Success Story**: At 6 months — first phase live, real-time order tracking launched, zero unplanned outages during migration.

---

### CFO / Finance Director

**Primary Message**: The investment is on schedule to return 30% TCO savings by Month 24, with early cost indicators (contractor reduction, partial legacy decommission) visible by Month 9.

**Key Talking Points**:
- Dual-running period cost modelled and tracked against forecast
- Reconciliation event count reducing in line with migration phases
- Business case ROI confirmed quarterly against agreed baseline

**Communication Frequency**: Monthly financial review; quarterly business case update

**Preferred Channel**: Financial dashboard; written monthly report

**Success Story**: At 12 months — first legacy components decommissioned, licence invoice line eliminated, reconciliation events down 40%.

---

### CTO / CIO

**Primary Message**: The architecture is being built to the principles in ARC-000-PRIN-v1.0 — modular, event-driven, cloud-native — with engineering teams gaining modern skills that will accelerate delivery beyond this programme.

**Key Talking Points**:
- ADRs document every significant decision so the architecture rationale is preserved
- CI/CD pipelines and testing automation built in Phase 1, before features are delivered
- Engineering attrition risk tracked as a leading indicator alongside technical metrics

**Communication Frequency**: Weekly programme sync; architecture reviews at phase gates

**Preferred Channel**: Architecture review sessions; programme Slack / collaboration tool

**Success Story**: At 9 months — engineering team deploying to production daily with < 10% change failure rate; first senior engineer hire citing modern stack as reason for joining.

---

### VP Operations

**Primary Message**: Every migration phase has an explicit rollback plan tested before go-live, a stabilization window with defined exit criteria, and full Operations involvement in sign-off.

**Key Talking Points**:
- Operations team members are named participants in phase planning, not just approvers
- New platform observability gives Operations better real-time visibility than the legacy system ever provided
- Dual-running exit criteria are agreed in advance — Operations cannot be pushed to cut over early

**Communication Frequency**: Weekly operational sync; daily during phase cutover windows

**Preferred Channel**: Operational runbook reviews; monitoring dashboards; direct channel to Programme Manager

**Success Story**: At 12 months — three months at 99.9% uptime confirmed; MTTR reduced from 3 hours to 25 minutes.

---

### VP Commercial / Sales

**Primary Message**: Real-time order tracking and the API layer that enables a B2B customer portal are deliverables within Phase 2 — the commercial pipeline is being unblocked on a defined schedule.

**Key Talking Points**:
- Phase 2 milestone (Month 12) delivers the API foundation for the self-service portal
- Order-to-ship reduction and NPS improvement are measured and reported quarterly
- New commercial models (subscriptions, SLA tiers) are architecturally enabled from Phase 3

**Communication Frequency**: Monthly commercial impact briefing; release previews before each phase

**Preferred Channel**: Commercial dashboard; pre-release briefing sessions

**Success Story**: At 12 months — real-time tracking live, customer service order-status call volume down 25%, B2B portal in development.

---

### CISO / Compliance

**Primary Message**: Security controls are embedded at Phase 1 — not retrofitted. PCI-DSS scope components are prioritized within the migration sequence to hit the re-certification deadline.

**Key Talking Points**:
- Immutable audit trail and secrets management are Phase 1 deliverables, not deferred items
- PCI-DSS scoped components identified in Month 1 and migration sequence adjusted if needed
- Security architecture reviewed at each phase gate before go-live approval

**Communication Frequency**: Monthly security review; phase gate sign-off

**Preferred Channel**: Security design review sessions; findings tracker; compliance evidence pack

**Success Story**: At 8 months — PCI-DSS re-certification achieved on new platform; zero high-severity findings open.

---

### Order Fulfillment Teams

**Primary Message**: Your operational knowledge of existing workarounds will be built into the new system design — this migration will eliminate workarounds, not just replicate them in new technology.

**Key Talking Points**:
- Fulfillment team members are involved in UAT for every phase that affects their workflows
- Training is delivered 4 weeks before cutover, not the day before
- A feedback channel is open during the first 30 days post-cutover for each phase

**Communication Frequency**: Sprint reviews; weekly during UAT phases; daily during cutover windows

**Preferred Channel**: Direct team sessions; UAT feedback forms; team chat channel

**Success Story**: At 6 months — first phase live, 3 of the 14 documented workarounds eliminated, staff onboarding time reduced.

---

## Change Impact Assessment

### Impact on Stakeholders

| Stakeholder | Current State | Future State | Change Magnitude | Resistance Risk | Mitigation Strategy |
|-------------|---------------|--------------|------------------|-----------------|---------------------|
| Executive Sponsor | Monitoring escalating costs and competitive gap | Delivery milestones and strategic capability gains | LOW | LOW | Maintain fortnightly steering with visible progress metrics |
| CFO | Approving escalating legacy costs with no end in sight | ROI-positive TCO trajectory with quarterly confirmation | MEDIUM | LOW | Quarterly business case updates; early cost reduction signals |
| CTO | Managing legacy technical debt and attrition risk | Leading a modern, capable engineering organization | LOW | LOW | Architecture ownership; talent story emphasized |
| VP Operations | Firefighting legacy outages with manual recovery | Proactive monitoring, automated recovery, stable platform | HIGH | MEDIUM | Co-designed migration plan; Operations sign-off at every gate |
| VP Commercial | Blocked from new revenue initiatives | API-enabled commercial model launch | MEDIUM | LOW | Release previews; commercial pipeline unblocked milestone |
| CISO | Unresolvable findings due to legacy constraints | Clean security posture, zero-trust architecture | MEDIUM | LOW | Phase 1 security controls; findings closure tracked publicly |
| Order Fulfillment | 14 manual workarounds, high cognitive load | Streamlined workflows, automated steps | HIGH | HIGH | Early involvement, 4-week training lead time, feedback channel |
| Engineering Teams | Legacy codebase, 8-week deployments, anxiety | Modern stack, daily deploys, confidence | HIGH | LOW | Phase 1 tooling investment; dedicated capacity protection |
| Finance / Acctg | 2 FTE on manual reconciliation | Automated reconciliation, value-adding work | MEDIUM | LOW | SAR fulfillment and reconciliation as tangible personal wins |
| Customer Service | High call volume for order status | Reduced call volume; better tooling for escalations | MEDIUM | LOW | Training on new status visibility tools pre-launch |
| End Customers | Batch tracking, no self-service | Real-time tracking, self-service portal | HIGH (positive) | NONE | Proactive launch communications; gradual rollout |
| Logistics Partners | SFTP batch files, manual error resolution | Real-time API, automated error handling | HIGH | MEDIUM | API preview programme; migration support documentation |

### Change Readiness

**Champions** (Enthusiastic supporters):
- **CTO / CIO** — Personal mandate to modernize; will actively advocate across engineering organization
- **VP Commercial / Sales** — Commercial pipeline unblocked; highly motivated champion in executive conversations
- **Engineering Teams** — Genuine appetite to leave the legacy stack; need to be empowered, not just informed

**Fence-sitters** (Need convincing):
- **VP Operations** — Risk-averse due to past incident history; will become a champion once Phase 1 delivers demonstrable stability
- **Finance / Accounting Team** — Currently skeptical based on past ERP integration failures; the reconciliation elimination benefit is their specific "win" to activate support
- **Logistics Partners** — Will support once they see the API documentation and understand their migration lead time

**Resisters** (Skeptical or opposed):
- **Order Fulfillment Teams** — History of being promised improvements that replicated legacy problems in new wrapping; trust must be earned by involving them in design, not presenting finished decisions for sign-off. Strategy: named team members on design working group from Month 1, with documented commitment to eliminate (not replicate) each workaround before sign-off.

---

## Risk Register (Stakeholder-Related)

### R-1: Operations Resistance Delays Migration Phases

**Related Stakeholders**: VP Operations, Order Fulfillment Teams

**Risk Description**: VP Operations withholds phase sign-off due to insufficient stabilization time or unresolved operational concerns, extending the dual-running period beyond forecast and increasing programme cost.

**Impact on Goals**: G-1 (migration timeline), G-2 (TCO reduction delayed), O-1, O-2

**Probability**: MEDIUM

**Impact**: HIGH

**Mitigation Strategy**: Agree phase exit criteria (uptime thresholds, error rate targets) in Month 1 before any migration begins. Operations review these criteria and sign off on them — the criteria become the objective gate, not a discretionary judgment call. Include Operations in migration design from the start.

**Contingency Plan**: Steering board arbitration with Executive Sponsor; time-boxed escalation process (maximum 5 business days) to resolve gate disputes.

---

### R-2: PCI-DSS Deadline Compresses Security-Critical Migration Phase

**Related Stakeholders**: CISO, Head of Compliance, Head of Compliance

**Risk Description**: PCI-DSS scoped components are not ready for migration by Month 8, forcing either a partial certification on the legacy platform or a compressed migration that bypasses security design reviews.

**Impact on Goals**: G-5 (compliance), O-4

**Probability**: MEDIUM

**Impact**: HIGH

**Mitigation Strategy**: Identify PCI-DSS scoped components in Month 1. If migration cannot be safely completed by Month 7 (allowing 1 month for certification), engage QSA immediately to agree an interim plan — either a compensating control extension on the legacy platform or accelerated in-scope component migration as a parallel workstream.

**Contingency Plan**: QSA-agreed interim certification with documented migration commitment letter; CISO escalation to Executive Sponsor if compensating controls are insufficient.

---

### R-3: Logistics Partner Adoption Delays Real-Time Integration

**Related Stakeholders**: Logistics / Fulfillment Partners, VP Commercial

**Risk Description**: One or more key logistics partners are slow to migrate their integration from SFTP batch to the new API, keeping real-time order dispatch and the NPS improvement delayed beyond Month 12.

**Impact on Goals**: G-4 (order-to-ship, real-time tracking), O-3

**Probability**: MEDIUM

**Impact**: MEDIUM

**Mitigation Strategy**: Engage logistics partners in Month 2 with API preview documentation and migration timeline. Include integration migration as a contractual milestone where possible. Build a compatibility adapter that accepts partner SFTP files and converts them to internal events during the transition period — removing the partner dependency from the critical path.

**Contingency Plan**: Maintain SFTP adapter in production until all partners have migrated; set internal deadline (Month 18) after which SFTP support is removed with written notice to partners.

---

### R-4: Engineering Capacity Consumed by Legacy Maintenance

**Related Stakeholders**: Engineering Teams, CTO, VP Operations

**Risk Description**: Ongoing legacy system incidents and maintenance requests consume engineering capacity needed for new platform development, causing migration phase delays.

**Impact on Goals**: G-1 (migration timeline), G-6 (delivery velocity)

**Probability**: HIGH

**Impact**: HIGH

**Mitigation Strategy**: Define and fund a dedicated legacy maintenance squad (minimum 2 engineers) before programme start. Ring-fence them from modern platform work. Establish a formal request process for legacy changes with a high bar — only security and critical production fixes accepted during migration.

**Contingency Plan**: If legacy incidents escalate beyond the maintenance squad's capacity, Executive Sponsor authorizes temporary contractor support rather than pulling from modern platform team.

---

### R-5: Order Fulfillment Team Disengagement from UAT

**Related Stakeholders**: Order Fulfillment Teams, VP Operations

**Risk Description**: Order fulfillment staff are too busy with day-to-day operations to meaningfully engage in UAT, resulting in undiscovered usability issues going live and damaging trust.

**Impact on Goals**: G-3 (error rate reduction), O-3

**Probability**: MEDIUM

**Impact**: MEDIUM

**Mitigation Strategy**: UAT periods are agreed with VP Operations in advance; backfill or reduced workload is arranged for UAT participants. UAT is a named deliverable with a start and end date, not an open-ended review. Team leads are empowered to raise blockers directly to the Programme Manager.

**Contingency Plan**: If UAT capacity is insufficient, phase go-live date is extended rather than UAT scope reduced. Quality is not negotiated away.

---

## Governance & Decision Rights

### Decision Authority Matrix (RACI)

| Decision Type | Responsible | Accountable | Consulted | Informed |
|---------------|-------------|-------------|-----------|----------|
| Programme budget approval | Programme Manager | CFO / Executive Sponsor | Finance | All stakeholders |
| Migration phase sequencing | Enterprise Architect | CTO | VP Operations, CISO | Executive Sponsor, Finance |
| Phase go/no-go sign-off | VP Operations + CTO | Executive Sponsor | Engineering, CISO, Compliance | All stakeholders |
| Architecture decisions (significant) | Engineering Lead | Enterprise Architect | Security, Operations | VP Commercial, CFO |
| Security design approval | CISO | CISO | Enterprise Architect, Head of Compliance | Engineering, Audit |
| PCI-DSS scope and migration priority | CISO | Head of Compliance | Enterprise Architect | CFO, Executive Sponsor |
| Logistics partner API migration timeline | VP Commercial | VP Operations | Engineering | Logistics Partners |
| Legacy maintenance prioritization | Legacy Maintenance Lead | CTO | VP Operations | Programme Manager |
| Exception to architecture principles | Enterprise Architect | CTO | CISO, Head of Compliance | All teams |
| Customer communications (migration periods) | VP Commercial | Executive Sponsor | Customer Service, Legal | All |

### Escalation Path

1. **Level 1** — Programme Manager (day-to-day decisions, scope within approved plan, resource conflicts within budget)
2. **Level 2** — Steering Committee: Executive Sponsor, CFO, CTO, VP Operations (scope changes, budget variances > 10%, phase gate disputes, timeline changes > 2 weeks)
3. **Level 3** — Board (budget increases > 25% of approved programme, strategic direction changes, regulatory escalations)

---

## Validation & Sign-off

### Stakeholder Review

| Stakeholder | Review Date | Comments | Status |
|-------------|-------------|----------|--------|
| Executive Sponsor | PENDING | — | PENDING |
| CFO / Finance Director | PENDING | — | PENDING |
| CTO / CIO | PENDING | — | PENDING |
| VP Operations | PENDING | — | PENDING |
| VP Commercial | PENDING | — | PENDING |
| CISO | PENDING | — | PENDING |
| Head of Compliance | PENDING | — | PENDING |

### Document Approval

| Role | Name | Signature | Date |
|------|------|-----------|------|
| Executive Sponsor | | | |
| Enterprise Architect | | | |
| Programme Manager | | | |

---

## Appendices

### Appendix A: Stakeholder Interview Summaries

No formal interviews have been conducted at the time of document generation. The following represents assumed driver intelligence based on the project context and should be validated through stakeholder engagement sessions in Month 1.

#### Recommended Interview Agenda (Month 1)

- **Executive Sponsor**: Confirm strategic timeline, board commitments, and programme constraints
- **CFO**: Confirm TCO baseline figures, cost reduction targets, and business case approval process
- **VP Operations**: Document all known legacy edge cases, existing workarounds, and outage history
- **Order Fulfillment Team Leads**: Capture all 14+ documented workarounds with business impact assessment
- **CISO**: Confirm penetration test findings detail, PCI-DSS scope components, and QSA contact

---

### Appendix B: References

- ARC-000-PRIN-v1.0 — Enterprise Architecture Principles, Legacy Order Management Modernization
- Project 001 README — `projects/001-order-management-modernization/README.md`

---

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| *None provided* | — | — | — | No external governance documents supplied at generation time. Place org charts or strategy documents in `projects/001-order-management-modernization/external/` and re-run. |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|-------------|--------|--------------|----------|----------------|
| — | — | — | — | — |

### Unreferenced Documents

| Filename | Source Location | Reason |
|----------|-----------------|--------|
| — | — | — |

---

**Generated by**: ArcKit `/arckit:stakeholders` command
**Generated on**: 2026-05-23
**ArcKit Version**: 5.0.4
**Project**: Legacy Order Management Modernization (Project 001)
**AI Model**: Claude Sonnet 4.6
