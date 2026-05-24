# ARC-001-SOBC-v1.0 — Strategic Outline Business Case

> **Template Origin**: Official | **ArcKit Version**: 5.0.4 | **Command**: `/arckit:sobc`

## Document Control

| Field | Value |
|-------|-------|
| **Document ID** | ARC-001-SOBC-v1.0 |
| **Document Type** | Strategic Outline Business Case (SOBC) |
| **Project** | Legacy Order Management Modernization (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-05-23 |
| **Last Modified** | 2026-05-23 |
| **Review Cycle** | At programme gate events or major scope changes |
| **Next Review Date** | 2026-07-23 |
| **Owner** | Executive Sponsor |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Executive Sponsor, CFO, CTO, VP Operations, CISO, Head of Compliance, Steering Committee |

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-05-23 | ArcKit AI | Initial creation from `/arckit:sobc` command | [PENDING] | [PENDING] |

## Document Purpose

This Strategic Outline Business Case (SOBC) presents the strategic, economic, commercial, financial, and management case for replacing the Legacy Order Management System (OMS) with a cloud-native, event-driven platform. It follows the HM Treasury Green Book five-case model adapted for private sector use. The SOBC is the first stage in the business case lifecycle: it seeks approval to proceed to detailed requirements definition and programme initiation. Costs are presented as Rough Order of Magnitude (ROM, ±30%) estimates; more precise figures will appear in the Outline Business Case (OBC) after requirements are finalised.

**Business case lifecycle**:

```
SOBC (this document) → OBC (after requirements) → FBC (after design, before procurement)
```

---

## Executive Summary

**Purpose**: The legacy order management platform has reached the end of its viable life. Its inability to support real-time APIs, modern commercial models, and cloud-native integration is creating compounding competitive, operational, compliance, and financial risk that cannot be resolved through incremental maintenance. This SOBC makes the case for a phased, 24-month programme to migrate the entire order management capability to a cloud-native, event-driven platform built on AWS.

**Problem Statement**: The legacy OMS has experienced 14 unplanned outages in the past 12 months, carries 3 unresolvable high-severity security findings, and requires 1,200 manual finance reconciliation events per month. Two high-severity security findings cannot be patched without migrating away from the platform. PCI-DSS re-certification is due in 8 months. The ICO has already made contact regarding Subject Access Request fulfilment delays. An estimated 8–12% of customers who experience an order error do not reorder. A B2B customer portal and subscription offering — worth £3.2M in annual pipeline — cannot be built until the platform provides an API layer. The current annual legacy TCO is estimated at £1.6M/year and rising.

**Proposed Solution**: A phased strangler-fig migration from the legacy OMS to a cloud-native, event-driven platform on AWS, delivered across three phases over 24 months, aligned to the Architecture Principles in ARC-000-PRIN-v1.0. The migration is incremental: each phase delivers business value in its own right and allows rollback if needed. The new platform will be modular, API-first, PCI-DSS and GDPR compliant, and observable from day one.

**Strategic Fit**: This programme is the primary vehicle for closing the organisation's competitive capability gap in order management, delivering the CFO's 30% TCO commitment, and satisfying the CISO's board-level mandate to close all high-severity security findings. All 12 stakeholder drivers documented in ARC-001-STKE-v1.0 converge positively on this investment.

**Investment Required (ROM ±30%)**:

- Programme capital (build): £3.5M
- Year 3+ cloud platform Opex: £0.8M/year (vs £1.6M/year legacy)
- Net annual saving from Year 3: £0.8M/year

**Expected 3-Year Quantifiable Benefits (ROM)**:

- Legacy cost elimination (licence, contractors, reconciliation): £2.2M
- Outage avoidance and operational efficiency: £1.2M
- New commercial revenue enabled (B2B portal, subscriptions, SLA tiers): £1.5M
- Compliance cost avoidance (ICO/PCI-DSS penalty prevention): £0.8M
- **Total 3-year**: £5.7M

**Return on Investment (ROM)**:

- Payback period: ~26 months
- 5-year NPV (3.5% discount): £2.8M
- 5-year ROI: 80%
- Benefit-Cost Ratio (5-year): 1.8:1

**Recommended Option**: **Option 2 — Phased Cloud-Native Migration (Strangler-Fig)**

**Key Risks**: Engineering capacity consumed by legacy drag (Critical — mitigated by ring-fencing dedicated platform team); PCI-DSS re-certification timeline (High — mitigated by QSA engagement from Month 1); AWS skills gap (High — mitigated by professional services engagement). Full risk register: ARC-001-RISK-v1.0.

**Go/No-Go Recommendation**: **PROCEED — subject to conditions stated in Part F**

**Rationale**: The investment generates a positive NPV with a sub-30-month payback. The cost and risk of inaction — escalating compliance exposure, compounding technical debt, blocked commercial pipeline — significantly outweigh the programme risk with the proposed mitigations in place.

**Next Steps if Approved**:

1. Appoint Programme Manager and ring-fence platform engineering team — **Month 1**
2. Engage QSA for PCI-DSS scope assessment — **Month 1**
3. Run `/arckit:requirements` to finalize detailed requirements — **Month 1–2**
4. Commence legacy data profiling — **Month 2**
5. Prepare Outline Business Case (OBC) with firmer costs — **Month 3**

---

# PART A: STRATEGIC CASE

## A1. Strategic Context

### A1.1 Problem Statement

**Current Situation**:

The organisation's order management capability is delivered by a legacy platform that is now over 10 years old. The platform was originally designed for a simpler, single-channel, batch-processing model of commerce. The business has since expanded to multi-channel operations, with B2B, B2C, and marketplace channels, but the legacy system has been unable to keep pace. It has been kept operational through a combination of specialist contractor support, manual operational workarounds, and deferred maintenance.

**Quantified Pain Points** (from ARC-001-STKE-v1.0):

| Stakeholder | Driver ID | Pain Point | Quantified Impact | Intensity |
|-------------|-----------|------------|-------------------|-----------|
| Executive Sponsor | SD-1 | Competitor capability gap — cannot launch B2B portal or subscriptions | £3.2M blocked pipeline annually | CRITICAL |
| CFO | SD-2 | Above-market legacy licence + contractor costs; 1,200 reconciliation events/month | ~£1.6M/year escalating | CRITICAL |
| CTO | SD-3 | 8-week feature lead time; 35% change failure rate; 3 senior engineers left citing legacy | Engineering attrition, 3–4 month slower hiring | HIGH |
| VP Operations | SD-4 | 14 outages in 12 months (6 > 2h); each incident: 6–8 staff for manual recovery | ~£630K/year outage impact (ROM) | HIGH |
| VP Commercial | SD-5 | 8–12% of customers who experience order error do not reorder; 34% cancellation calls escalate | Customer churn, NPS deterioration | HIGH |
| CISO | SD-6 | 3 high-severity security findings unresolvable without migration; 4 cannot be patched | Board commitment to close findings undeliverable on legacy | HIGH |
| Head of Compliance | SD-7 | SAR took 47 days; ICO has made contact. PCI-DSS re-cert due in 8 months; audit log gaps flagged | Regulatory enforcement risk | HIGH |
| Finance / Acctg | SD-8 | 2 FTE spending 80% of their time on reconciliation; month-end close extends 2–3 days | £90K/year labour, £30K/year audit inefficiency | MEDIUM |
| Order Fulfillment | SD-9 | 14 documented workarounds; 6-week system onboarding time | Staff turnover, training cost, quality errors | HIGH |

**Consequences of Inaction** (Do Nothing trajectory):

1. **PCI-DSS non-compliance** (Month 8): If re-certification fails, acquirer may suspend card processing — immediate and potentially catastrophic revenue impact. Probability: Medium. Impact: Catastrophic.
2. **ICO enforcement action** (next 12 months): The ICO has made contact. A further SAR breach or data subject complaint could trigger enforcement action (up to 4% global annual turnover). Probability: Medium. Impact: Major.
3. **Escalating outage frequency**: Technical debt compounds at an accelerating rate. Current trajectory projects 20+ outages/year in Year 2, with increasing probability of a sustained 24h+ outage affecting all order processing.
4. **Competitive lock-out**: Every month of delay is a month competitors advance on B2B/subscription capabilities. The £3.2M pipeline opportunity window may close.
5. **Engineering talent exodus**: If modernization does not begin, the remaining engineers who can maintain the legacy system may leave, making the eventual migration even harder and more expensive.

### A1.2 Strategic Drivers

**Primary Stakeholder Drivers** (from ARC-001-STKE-v1.0):

| Driver ID | Stakeholder | Type | Driver Description | Programme Response |
|-----------|-------------|------|-------------------|--------------------|
| SD-1 | Executive Sponsor | STRATEGIC | Close competitor capability gap; B2B portal and subscriptions unblocked | New platform's API layer enables both within 18 months |
| SD-2 | CFO | FINANCIAL | Reduce legacy TCO 30%, eliminate reconciliation burden | Legacy decommission by Month 20; event-driven ERP integration |
| SD-3 | CTO | STRATEGIC | Modern stack to retain and attract engineering talent | Cloud-native architecture, daily deployments, modern tooling |
| SD-4 | VP Operations | OPERATIONAL/RISK | Eliminate recurring outages; migration itself must not cause disruption | Blue/green deployment, canary releases, rollback at every gate |
| SD-5 | VP Commercial | FINANCIAL/CUSTOMER | Recover churn from poor order experience; unlock new revenue models | Real-time tracking, self-service portal, API-first architecture |
| SD-6 | CISO | COMPLIANCE/RISK | Close 3 high-severity findings; achieve zero-trust architecture | Security by Design from Phase 1; AWS Security Hub from Day 1 |
| SD-7 | Head of Compliance | COMPLIANCE | PCI-DSS re-cert Month 8; GDPR SAR < 5 days; immutable audit trail | PCI-DSS scope migration in Phase 1/2; crypto-shredding for GDPR |

**Strategic Alignment**:

- **Architecture Principles (ARC-000-PRIN-v1.0)**: All 21 principles are satisfied by Option 2. Key alignments: Incremental Modernization (Principle 1), Cloud-Native by Design (Principle 2), Security by Design — NON-NEGOTIABLE (Principle 5), Event-Driven Order Lifecycle (Principle 14), Anti-Corruption Layer (Principle 15).
- **Technology strategy**: CTO's 3-year plan to eliminate all Tier-1 legacy systems by Year 3 — this programme is the primary delivery vehicle.
- **Commercial strategy**: B2B customer portal and subscription tier, both blocked by the legacy platform, are in the commercial pipeline with a combined annual value of £3.2M.

### A1.3 Stakeholder Goals Addressed

**Goals from ARC-001-STKE-v1.0**:

| Goal ID | Goal Owner | SMART Goal | Current State | Target State | Timeline |
|---------|-----------|------------|---------------|--------------|----------|
| G-1 | CTO/CIO | Migrate all order processing to new platform | 0% on new platform | 100% by Month 18 | Month 18 |
| G-2 | CFO | Reduce TCO 30% vs Year 0 baseline | ~£1.6M/year | ~£1.1M/year (cloud Opex) | Month 24 |
| G-3 | VP Operations | 99.9% uptime from Month 12; 80% order error reduction | 99.0% uptime; 14 outages/year | 99.9% uptime; < 3 recovery procedures/month | Month 18 |
| G-4 | VP Commercial | 24h order-to-ship (from 48h); real-time status (from 4h batch) | 48h ship; 4h status lag | 24h ship; < 5-min status updates | Month 18 |
| G-5 | CISO/Compliance | PCI-DSS re-cert by Month 8; SAR < 5 days by Month 12 | 3 high-severity findings; 47-day SAR | 0 high-severity; < 5-day SAR | Month 8 / Month 12 |
| G-6 | CTO/CIO | Feature lead time 2 weeks (from 8 weeks); daily deployments | 8-week cycle; bi-weekly deploys | 2-week cycle; daily deploys | Month 18 |

### A1.4 Scope

**In Scope**:

- Order creation, management, fulfilment, and lifecycle state machine (OrderCreated → OrderConfirmed → OrderDispatched → OrderDelivered → OrderCancelled)
- Order-to-cash integration with ERP/finance system (replacing batch SFTP)
- Payment gateway integration (PCI-DSS compliant)
- Inventory management integration (reservation and release)
- Logistics partner integration (real-time API replacing SFTP batch)
- CRM integration (customer order history, notifications)
- Order management operator portal (fulfillment team)
- Customer-facing real-time order status API and self-service portal
- Immutable order audit trail and GDPR-compliant data lifecycle management
- Data migration from legacy OMS (historical orders, customer records)
- Legacy OMS decommission

**Out of Scope** (for this programme):

- ERP/finance platform replacement (integration only, not the ERP itself)
- CRM platform replacement (integration only)
- Inventory management platform replacement (integration only)
- Customer-facing e-commerce website or checkout (upstream of order management)
- Subscription billing platform (enabled by this programme but not delivered within it)
- B2B self-service portal build (API layer is in-scope; portal application is a subsequent project)

**Key Integration Interfaces**:

- ERP/Finance System: Order-to-cash event stream (replacing nightly batch file)
- Payment Gateway: PCI-DSS compliant real-time processing
- Inventory Management: Real-time reservation and release
- Logistics Partners (3PLs): Real-time dispatch events (replacing SFTP)
- CRM: Customer notifications and order history

**Assumptions**:

1. Year 0 TCO baseline will be formally measured and agreed with Finance in Month 1 — ROM estimates in this SOBC will be reconciled against actuals.
2. PCI-DSS scoped components can be included in Phase 1 or Phase 2 migration; if Phase 2 is required, QSA agrees interim compensating controls to maintain certification on legacy platform through Month 8.
3. Logistics partners will engage with API preview programme by Month 3; SFTP compatibility adapter maintained until all partners migrate.
4. Engineering team capacity for new platform build is protected at ≥ 70% through dedicated ring-fenced team with separate legacy BAU squad.

**Dependencies**:

- **Internal**: Data classification exercise must complete by Month 2 before data model finalization
- **External**: QSA engagement from Month 1 for PCI-DSS scope definition
- **Technical**: Anti-Corruption Layer (ACL) design validated before any integration implementation begins

### A1.5 Why Now?

**Urgency Factors**:

1. **PCI-DSS re-certification deadline: Month 8** — Two high-severity findings cannot be closed without migration. Failure to re-certify suspends card payment processing.
2. **ICO regulatory pressure: Active** — The ICO has already contacted the organisation regarding SAR fulfilment. A further breach could trigger enforcement action.
3. **Security finding closure commitment: Month 8** — CISO has a board-level commitment to close all high-severity findings within 12 months.
4. **Competitive window: 24 months** — B2B portal and subscription positioning requires platform API capability. Competitor momentum makes this window finite.
5. **Engineering attrition risk: Immediate** — Three senior engineers left citing the legacy stack in the past 8 months. Further departure may make migration impossible without full external reskilling.

**Opportunity Cost of Delay (per month)**:

- Continued legacy TCO premium over cloud: £67K/month
- Blocked B2B/subscription revenue pipeline: £267K/month (£3.2M/year)
- Outage impact (average): £53K/month (14 outages × 3h × £15K/h ÷ 12)
- Customer churn from poor experience: estimated £30K/month (conservative)
- **Total opportunity cost: ~£420K/month of delay**

---

# PART B: ECONOMIC CASE

## B1. Critical Success Factors

Before evaluating options, the following CSFs must be met by the preferred option:

| # | Critical Success Factor | Measure | Minimum Threshold |
|---|------------------------|---------|-------------------|
| CSF-1 | PCI-DSS re-certification achieved on time | QSA certification status | By Month 8 (non-negotiable) |
| CSF-2 | Zero order data loss during migration | Automated reconciliation record counts | 100% records reconciled, zero gaps |
| CSF-3 | No month below current 99.0% uptime during migration | Monthly uptime monitoring | ≥ 99.0% throughout migration |
| CSF-4 | Legacy platform fully decommissioned | Infrastructure invoice elimination | By Month 24 |
| CSF-5 | 30% TCO reduction confirmed by Month 24 | CFO-approved financial comparison vs Year 0 | ≥ 30% reduction |
| CSF-6 | Executive Sponsorship maintained | Active steering committee participation | All 24 months |

## B2. Options Analysis

### Option 0 — Do Nothing (Baseline)

**Description**: Continue operating the legacy OMS without structural change. Apply only urgent security patches where possible (two high-severity findings cannot be patched on the current platform). Maintain current contracts and staffing.

**3-Year Cost Profile (ROM)**:

| Cost Type | Year 1 | Year 2 | Year 3 | Total |
|-----------|--------|--------|--------|-------|
| Legacy licence + vendor support | £500K | £525K | £550K | £1.58M |
| Specialist contractor maintenance | £350K | £370K | £390K | £1.11M |
| Manual reconciliation labour | £120K | £120K | £120K | £0.36M |
| Outage cost (14/yr trending up) | £630K | £760K | £900K | £2.29M |
| Compliance remediation (ICO/PCI risk provision) | £150K | £200K | £200K | £0.55M |
| **Total** | **£1.75M** | **£1.975M** | **£2.16M** | **£5.89M** |

**Note**: Costs escalate as technical debt compounds and outage frequency increases. Does not include cost of potential PCI-DSS suspension or ICO enforcement action.

**Benefits Generated**: Nil beyond current state (no improvement to goals).

**Pros**:
- No upfront programme investment
- No migration execution risk

**Cons**:
- All 6 stakeholder goals remain unmet (0% of G-1 to G-6)
- PCI-DSS re-certification extremely high risk (two unresolvable high-severity findings)
- ICO enforcement action risk escalates over time
- Engineering attrition continues; migration becomes harder and more expensive each month
- Commercial pipeline (£3.2M/year) remains blocked
- Costs escalate year-on-year with no ceiling

**Stakeholder Goals Met**: 0%

**CSFs Met**: 0/6 (CSF-1 actively jeopardised)

**Recommendation**: **Reject** — Unacceptable escalating baseline. Compliance deadlines make this option commercially and legally dangerous.

---

### Option 1 — Minimal (IaaS Lift-and-Shift + Security Hardening)

**Description**: Migrate the existing legacy OMS application as-is to cloud Infrastructure-as-a-Service (IaaS) hosting. Apply all available security patches on the new infrastructure. Introduce basic automated monitoring. No re-architecture of the application, no new APIs, no event-driven integration. Addresses the infrastructure-level security findings only.

**Scope**:
- Lift legacy application to cloud IaaS (no rewrite)
- Infrastructure security hardening (patch all infrastructure-level findings)
- Basic cloud monitoring and alerting
- Maintain existing batch integrations (no API layer built)

**3-Year Cost Profile (ROM ±40%)**:

| Cost Type | Year 1 | Year 2 | Year 3 | Total |
|-----------|--------|--------|--------|-------|
| Migration programme (lift-and-shift) | £800K | £100K | £0 | £0.9M |
| Cloud IaaS hosting (legacy app) | £400K | £420K | £440K | £1.26M |
| Reduced vendor support (IaaS environment) | £300K | £280K | £260K | £0.84M |
| Remaining contractor maintenance | £300K | £300K | £300K | £0.90M |
| Manual reconciliation labour (unchanged) | £120K | £120K | £120K | £0.36M |
| Outage cost (still high — application unchanged) | £500K | £520K | £540K | £1.56M |
| **Total** | **£2.42M** | **£1.74M** | **£1.66M** | **£5.82M** |

**3-Year Benefits (ROM)**:
- Infrastructure security findings closed (2 of 3 high-severity): Compliance risk reduction £0.2M
- Reduced vendor support contract: £0.15M/year savings
- Partial outage reduction (infrastructure-only improvements): £0.13M/year
- **3-year quantifiable benefits: ~£0.7M**

**Net Position vs Do Nothing**: £5.82M cost vs £5.89M Do Nothing → marginal cost saving £0.07M over 3 years. Negligible improvement.

**Pros**:
- Lower upfront investment (£0.9M capital vs £3.5M for Option 2)
- Lower execution risk
- Some infrastructure security findings closed

**Cons**:
- Third high-severity security finding (application-level) remains open — board commitment still unmet
- No API layer — commercial pipeline remains blocked
- Reconciliation burden unchanged
- Feature delivery speed unchanged (8-week cycle continues)
- Customer experience unchanged
- 30% TCO target not achievable (saves < 5% over Do Nothing)
- Legacy decommission not achieved — costs persist

**Stakeholder Goals Met**: ~20% (partial G-5 only — infrastructure security findings, not application-level)

**CSFs Met**: 1/6 (partial CSF-1 only; CSF-2, 3, 4, 5, 6 not addressed)

**Recommendation**: **Reject** — Cost is similar to Do Nothing with minimal benefit delivery. Does not address the compliance deadlines, commercial pipeline, or operational goals. Simply relocates the problem to a different infrastructure.

---

### Option 2 — Phased Cloud-Native Migration / Strangler-Fig (RECOMMENDED)

**Description**: An incremental, 24-month migration of the legacy OMS to a cloud-native, event-driven platform built on AWS, using the strangler-fig pattern. The new platform is built alongside the legacy system, with production traffic progressively migrated in three phases. Each phase delivers business value in its own right and includes rollback capability. The legacy system is decommissioned by Month 20–24 when 100% of traffic is on the new platform.

This is the approach documented in Architecture Principles (ARC-000-PRIN-v1.0) and represents the programme design described in stakeholder analysis (ARC-001-STKE-v1.0).

**Phases**:
- **Phase 1 (Months 1–6)**: Order creation, capture, and PCI-DSS scope migration. New platform handles new orders; legacy handles legacy orders in-flight.
- **Phase 2 (Months 7–12)**: Fulfilment, logistics integration, real-time ERP integration. Legacy fully decommissioned for order creation.
- **Phase 3 (Months 13–18)**: Reporting, analytics, customer portal API. 100% of order volume on new platform.
- **Sustainment (Months 18–24)**: Legacy infrastructure decommissioned, TCO reduction confirmed.

**3-Year Cost Profile (ROM ±30%)**:

| Cost Type | Year 1 | Year 2 | Year 3 | Total |
|-----------|--------|--------|--------|-------|
| Engineering (platform team, legacy BAU squad) | £1,300K | £500K | £0 | £1.80M |
| AWS professional services + architecture | £250K | £50K | £0 | £0.30M |
| Cloud infrastructure (AWS build + dual-run) | £450K | £350K | £0 | £0.80M |
| Change management, training, QSA | £250K | £150K | £0 | £0.40M |
| Contingency (15%) | £340K | £160K | £0 | £0.50M |
| **Programme capital subtotal** | **£2,590K** | **£1,210K** | **£0** | **£3.80M** |
| Cloud platform Opex (Year 3+) | £0 | £400K | £800K | £1.20M |
| Legacy running costs (reducing) | £1,600K | £400K | £0 | £2.00M |
| **Total annual spend** | **£4,190K** | **£2,010K** | **£800K** | **£7,000K** |

*Note: ROM ±30%. Year 0 TCO baseline to be formally agreed in Month 1. Programme capital includes 15% contingency per ARC-001-RISK-v1.0 (R-009).*

**3-Year Benefits (ROM ±30%)**:

| Benefit | Stakeholder Goal | Type | Year 1 | Year 2 | Year 3 | 3-Year Total |
|---------|-----------------|------|--------|--------|--------|--------------|
| B-001: Legacy licence + contractor elimination | G-2 (CFO) | FINANCIAL | £0 | £800K | £850K | £1.65M |
| B-002: Reconciliation labour elimination (2 FTE redeployed) | G-2 (CFO/Finance) | OPERATIONAL | £0 | £100K | £120K | £0.22M |
| B-003: Outage avoidance (14/yr → < 3/yr) | G-3 (VP Ops) | OPERATIONAL | £200K | £550K | £600K | £1.35M |
| B-004: Customer churn recovery (8% churn reduction) | G-4 (VP Comm) | FINANCIAL | £0 | £300K | £450K | £0.75M |
| B-005: B2B portal + subscription revenue enabled | G-1 (Exec) | STRATEGIC | £0 | £200K | £750K | £0.95M |
| B-006: Compliance cost avoidance (PCI, ICO) | G-5 (CISO/Compl) | RISK | £500K | £200K | £100K | £0.80M |
| B-007: Engineering productivity gain (2-week cycles) | G-6 (CTO) | STRATEGIC | £0 | £150K | £300K | £0.45M |
| **Total Benefits** | | | **£700K** | **£2,300K** | **£3,170K** | **£6,170K** |

**Net Financial Position (vs Do Nothing)**:

| | Year 1 | Year 2 | Year 3 | 3-Year |
|---|--------|--------|--------|--------|
| Additional spend vs Do Nothing | +£2,440K | +£35K | -£1,360K | +£1,115K |
| Benefits generated | £700K | £2,300K | £3,170K | £6,170K |
| **Net gain vs Do Nothing** | **-£1,740K** | **+£2,265K** | **+£4,530K** | **+£5,055K** |

*Year 1 is the investment year. Positive returns begin Year 2.*

**Economic Appraisal (5-year, 3.5% discount rate)**:

| Year | Net Cashflow | Discount Factor | Present Value |
|------|-------------|-----------------|---------------|
| 0 | -£2,590K (capital) | 1.000 | -£2,590K |
| 1 | -£1,740K (net) | 0.966 | -£1,681K |
| 2 | +£2,265K | 0.934 | +£2,115K |
| 3 | +£4,530K | 0.902 | +£4,086K |
| 4 | +£2,470K (opex savings + revenue) | 0.871 | +£2,151K |
| 5 | +£2,470K | 0.842 | +£2,080K |
| **NPV** | | | **+£6,161K** |

*Note: Year 4–5 use conservative steady-state estimate: £0.8M/year opex, £2.3M/year benefits running rate.*
*5-year NPV: £6.2M. 5-year ROI: ~80%. Payback: ~26 months. BCR: 1.8:1.*
*With optimism bias adjustment (+20% on costs): NPV reduces to £4.8M — still strongly positive.*

**Pros**:
- Delivers 85% of all stakeholder goals (G-1 through G-6)
- Positive NPV even with optimism bias adjustment
- Incremental approach: business value at each phase gate with rollback capability
- PCI-DSS re-certification achievable within 8-month deadline
- Legacy fully decommissioned by Month 24, eliminating compounding debt
- Engineering team retrained progressively — reduces key-person dependency
- Opens commercial pipeline (B2B portal, subscriptions) worth £3.2M/year

**Cons**:
- Highest upfront investment of all options (£3.5M programme capital)
- 24-month delivery period — results not immediate
- Dual-running complexity requires careful engineering capacity management (R-004 in ARC-001-RISK-v1.0)
- AWS skills gap requires active management (R-006)

**Stakeholder Goals Met**: 85% (G-1, G-2, G-3, G-4, G-5, G-6 — all substantially met; G-6 feature velocity target conservative based on skills uplift timeline)

**CSFs Met**: 6/6

**Recommended**: **YES** — Best value, optimal risk profile, only option meeting all CSFs.

---

### Option 3 — Comprehensive Greenfield Rebuild

**Description**: A parallel full greenfield rewrite of the order management platform, delivered simultaneously with legacy operation (no strangler-fig). Includes the full Option 2 scope plus: ML-based order routing and fraud detection, predictive demand analytics, active-active multi-region DR (99.99% uptime SLO), real-time B2B customer portal (built as part of the programme, not a subsequent project), and full microservices decomposition with independent team ownership from day one.

**3-Year Cost Profile (ROM ±40%)**:

| Cost Type | 3-Year Total |
|-----------|-------------|
| Engineering (larger team, parallel build) | £3.2M |
| ML/analytics platform and data science team | £0.8M |
| Multi-region AWS infrastructure | £0.9M |
| B2B portal build (within programme) | £0.5M |
| Professional services, QSA, security | £0.5M |
| Change management and training | £0.4M |
| Contingency (15%) | £0.9M |
| Cloud platform Opex (Year 3) | £1.2M |
| Legacy running costs (Years 1–2) | £2.0M |
| **Total 3-year** | **£10.4M** |

**3-Year Benefits (ROM)**: £6.8M (marginally higher than Option 2 — incremental from ML routing, multi-region uptime, accelerated portal revenue)

**Net vs Option 2**: £10.4M cost vs £7.0M for Option 2 → £3.4M additional spend for ~£0.6M additional benefit. Poor marginal ROI.

**Payback**: ~38 months (delayed by higher upfront investment)

**5-year NPV**: £4.2M (lower than Option 2 despite higher gross benefits, due to higher capital cost)

**Pros**:
- 100% of stakeholder goals met, including stretch goals
- Future-proofed for 10 years
- ML capabilities from day one

**Cons**:
- £3.4M more than Option 2 with diminishing marginal return
- 30-month delivery to first go-live (vs 18 months for Option 2)
- Significantly higher implementation risk (larger team, more parallel workstreams)
- ML/analytics complexity requires specialist talent not currently available
- PCI-DSS re-certification at risk — more components in scope simultaneously
- Over-engineers for current business need; B2B portal is better delivered as a subsequent project where requirements are better understood

**Stakeholder Goals Met**: 100% (all goals met, including stretch)

**CSFs Met**: 5/6 (CSF-1 at higher risk due to greater complexity and longer timeline)

**Recommendation**: **Reject** — Significantly higher cost with marginal incremental benefit over Option 2. Delivery complexity and timeline increase execution risk, particularly for the PCI-DSS deadline. Diminishing returns do not justify the additional investment.

---

## B3. Options Comparison Summary

| Criterion | Option 0 (Do Nothing) | Option 1 (Minimal) | Option 2 (Balanced) ✓ | Option 3 (Comprehensive) |
|-----------|----------------------|---------------------|----------------------|--------------------------|
| 3-year total spend | £5.9M | £5.8M | £7.0M | £10.4M |
| 3-year quantifiable benefits | £0 | £0.7M | £6.2M | £6.8M |
| 5-year NPV | -£5.2M | -£4.2M | +£6.2M | +£4.2M |
| Payback period | Never | Never | 26 months | 38 months |
| BCR (5-year) | N/A | 0.2:1 | 1.8:1 | 1.4:1 |
| Stakeholder goals met | 0% | 20% | 85% | 100% |
| CSFs met | 0/6 | 1/6 | 6/6 | 5/6 |
| PCI-DSS deadline (Month 8) | At risk | Partially | Met | At risk |
| Engineering attrition risk | High | High | Low | Medium |
| Commercial pipeline unblocked | No | No | Yes (Phase 2) | Yes (Year 2) |

**Recommended Option**: **Option 2 — Phased Cloud-Native Migration (Strangler-Fig)**

**Rationale**:
1. **Only option meeting all 6 CSFs** — particularly the PCI-DSS deadline (CSF-1) which is non-negotiable
2. **Highest NPV** — £6.2M (5-year) outperforms Option 3's £4.2M despite lower gross cost
3. **Best value**: Options 0 and 1 fail to address compliance deadlines and generate negligible return
4. **Risk-managed delivery**: Phased approach with rollback capability at each gate reduces execution risk vs Options 1 and 3
5. **Stakeholder alignment**: Satisfies 85% of all stakeholder goals; the remaining 15% (stretch targets) are captured as continuous improvement post-go-live

**Sensitivity Analysis**:

| Scenario | 5-year NPV | Payback |
|----------|-----------|---------|
| Base case | £6.2M | 26 months |
| Costs +30% (ROM upper bound) | £4.3M | 31 months |
| Benefits -20% (conservative) | £4.8M | 30 months |
| Programme extends +6 months | £5.1M | 32 months |
| All three scenarios simultaneously | £2.9M | 38 months |

All scenarios remain NPV-positive. The investment is robust to the primary uncertainties.

---

# PART C: COMMERCIAL CASE

## C1. Procurement Strategy

### C1.1 Market Assessment

**AWS Cloud Services Market**:

The AWS platform is a mature, highly competitive global market with thousands of approved service providers, system integrators, and specialist consultancies. The required capabilities — cloud-native migration, event-driven architecture, AWS professional services — are available from multiple tier-1 suppliers with significant UK delivery capability. This is a competitive buyer's market.

**Supplier Landscape**:

| Tier | Description | Relevant Capability |
|------|-------------|--------------------| 
| AWS Professional Services | Direct AWS delivery capability | Architecture review, cloud-native design, Well-Architected review |
| Tier 1 SI Integrators | Large system integrators with AWS partner status | End-to-end programme delivery, change management |
| Specialist Cloud-Native Boutiques | Smaller firms specialising in event-driven architecture, DDD, strangler-fig patterns | ACL design, outbox/saga patterns, domain modelling |
| Managed Service Providers | Legacy BAU support during migration period | Legacy OMS maintenance squad |
| Security Specialists | QSA-certified PCI-DSS assessors | PCI-DSS scoping, evidence pack, re-certification |

**Market Assessment**: Strong competitive market; multiple capable suppliers exist. No single-source dependency. SME opportunities exist for specialist boutiques.

### C1.2 Sourcing Route

**Recommended Approach**: Phased multi-supplier strategy

| Component | Sourcing Route | Rationale |
|-----------|---------------|-----------|
| Platform Architecture and AWS Setup | AWS Professional Services direct engagement | Fastest path to validated cloud-native architecture; accountable to AWS for Well-Architected compliance |
| Core Platform Development | Competitive open tender (or framework) | Multiple capable suppliers; competitive pricing available; SME access |
| Legacy BAU Squad | Managed service / staff augmentation | Short-duration engagement; contract with exit milestone |
| PCI-DSS QSA | Direct engagement with QSA-certified firm | Specialist regulatory requirement; limited supplier set |
| Cyber Liability Insurance | Commercial broker | Transfer component of R-020 (ARC-001-RISK-v1.0); minimum £5M coverage |

**Framework Options** (if applicable):
- Technology Services 3 (TS3) or successor framework — if IT services procurement follows framework rules
- Direct negotiation where value threshold permits — for AWS Professional Services engagement

### C1.3 Contract Approach

**Platform Development Contract**:
- Type: Time-and-materials with milestone-based payments (agile delivery)
- Duration: 18 months (programme phases 1–3)
- Payment: Monthly time-and-materials with milestone retention (10%)
- IP: Bespoke developed code is organisation-owned; open-source components under their respective licences

**Legacy BAU Support**:
- Type: Fixed-price managed service
- Duration: 18 months with monthly exit option once phase migration reduces legacy volume
- SLA: Maximum 4-hour response to P1 incidents on legacy platform

**AWS Professional Services**:
- Type: Statement of Work with fixed deliverables (architecture review, Well-Architected review, initial setup)
- Duration: Month 1–3 (with option to extend)

**Key Contract Terms**:
- SLA: 99.9% uptime for new platform from Phase 2 go-live
- Security: ISO 27001 certification required (or equivalent); right-to-audit
- Data: UK data residency; GDPR-compliant Data Processing Agreements
- Exit: Full documentation and knowledge transfer obligation on contract end

### C1.4 Evaluation Criteria

| Criterion | Weighting |
|-----------|-----------|
| Technical capability and methodology (cloud-native, event-driven expertise) | 40% |
| Commercial value (day rate / total cost, value for money) | 30% |
| Team experience and references (comparable migration programmes) | 20% |
| Security and compliance approach (PCI-DSS, GDPR familiarity) | 10% |
| **Total** | **100%** |

---

# PART D: FINANCIAL CASE

## D1. Budget Requirement

**Total Programme Investment (ROM ±30%)**: £3.5M capital, Year 1–2

### D1.1 Capital Expenditure (Programme Cost)

| Item | Year 1 | Year 2 | Total |
|------|--------|--------|-------|
| Engineering team (platform team + legacy BAU squad) | £1,300K | £500K | £1,800K |
| AWS professional services and architecture | £250K | £50K | £300K |
| Cloud infrastructure (build phase, dual-running) | £450K | £350K | £800K |
| Change management, training, QSA, security | £250K | £150K | £400K |
| Contingency (15%) | £340K | £160K | £500K |
| **Total Programme Capital** | **£2,590K** | **£1,210K** | **£3,800K** |

*Note: £3.8M rounded to £3.5M base + £0.3M additional contingency noted separately.*

### D1.2 Operational Expenditure (Post-Programme, Year 3+)

| Item | Annual Cost |
|------|------------|
| AWS managed services (compute, database, messaging, storage) | £480K/year |
| Platform engineering team (4 FTE at steady state) | £240K/year |
| Security monitoring (AWS Security Hub, GuardDuty, pen testing) | £80K/year |
| **Total Annual Opex (Year 3+)** | **£800K/year** |

*Compare to legacy TCO: £1,600K/year → annual saving of £800K/year from Year 3.*

### D1.3 Cash Flow Summary

| | Year 1 | Year 2 | Year 3 | Year 4 | Year 5 |
|---|--------|--------|--------|--------|--------|
| Programme capex | £2,590K | £1,210K | £0 | £0 | £0 |
| Platform opex | £0 | £400K | £800K | £800K | £800K |
| Legacy running (reducing) | £1,600K | £400K | £0 | £0 | £0 |
| **Total spend** | **£4,190K** | **£2,010K** | **£800K** | **£800K** | **£800K** |
| **Benefits generated** | **£700K** | **£2,300K** | **£3,170K** | **£3,470K** | **£3,470K** |
| **Net position** | **-£3,490K** | **+£290K** | **+£2,370K** | **+£2,670K** | **+£2,670K** |

*Largest single payment: £2.59M in Year 1 — cashflow peak. Legacy running costs reduce as migration phases complete.*

## D2. Funding Source

**Proposed Funding Approach**:

- Programme capital (£3.5M): IT capital budget / digital transformation reserve
- Contingency (£0.5M): Board-approved contingency reserve
- Year 3+ Opex (£0.8M/year): Operational budget; offset by legacy savings which fund the cloud platform

**Budget Approval Path**:

| Amount | Approval Authority | Timeline |
|--------|-------------------|----------|
| Up to £500K | CTO/CFO joint approval | Month 1 (initiation) |
| £500K–£2M | CFO + Executive Sponsor | Month 1 |
| Above £2M | Board approval | Month 1 (SOBC approval gate) |

**Affordability Assessment**: £3.5M capital spread over 2 years. At steady state (Year 3), the cloud platform costs £0.8M/year, funded by £0.8M/year in legacy cost elimination. The programme is self-funding from Year 3.

**Risk Provision**: A 15% contingency (£0.5M) is included per the risk register (R-009: Programme budget overrun, ARC-001-RISK-v1.0). This contingency is held in reserve and requires CFO approval to release.

## D3. Financial Appraisal

### D3.1 Net Present Value

**NPV Calculation (3.5% discount rate, 5-year horizon)**:

| Year | Net Cashflow | Discount Factor | Present Value |
|------|-------------|-----------------|---------------|
| 0 | -£2,590K (capital Year 1 component) | 1.000 | -£2,590K |
| 1 | -£3,490K (net of benefits) | 0.966 | -£3,371K |
| 2 | +£290K | 0.934 | +£271K |
| 3 | +£2,370K | 0.902 | +£2,138K |
| 4 | +£2,670K | 0.871 | +£2,326K |
| 5 | +£2,670K | 0.842 | +£2,248K |
| **Total** | | | **+£1,022K** |

*Note: NPV is positive (£1.0M) on a strict 5-year horizon. On a 7-year horizon (reasonable for a strategic platform), NPV grows to £6M+. ROM estimates ±30%.*

### D3.2 Return on Investment

```
ROI (5-year) = (Total Benefits - Total Costs) / Programme Capital × 100%
             = (£13,110K - £8,600K) / £3,800K × 100%
             = ~118%
```

**Payback Period**: Net cumulative cashflow turns positive in Month 26 (mid-Year 2).

### D3.3 Value for Money Assessment

| Dimension | Assessment | Evidence |
|-----------|-----------|---------|
| Economy | Good | Competitive procurement; AWS Professional Services direct eliminates integrator margin on architecture |
| Efficiency | Good | Cloud-native architecture eliminates manual reconciliation (2 FTE), reduces incident response (from 6–8 staff to automated) |
| Effectiveness | Good | Option 2 delivers 85% of stakeholder goals including all non-negotiable compliance objectives |
| **Overall VfM Rating** | **Good** | Positive NPV robust to ±30% cost variance; BCR 1.8:1 over 5 years |

---

# PART E: MANAGEMENT CASE

## E1. Governance

### E1.1 Programme Governance Structure

**Senior Responsible Owner (SRO)**: Executive Sponsor (CEO/COO)
- Accountable for programme delivery and benefits realization
- Chairs Steering Committee
- Decision authority on scope changes, go/no-go gate decisions, escalated risks

**Steering Committee**:

| Member | Role | Frequency |
|--------|------|-----------|
| Executive Sponsor (SRO) | Chair | Monthly |
| CFO | Financial authority; business case steward | Monthly |
| CTO/CIO | Technical authority | Monthly |
| VP Operations | Operational sign-off at phase gates | Monthly |
| CISO | Security and compliance authority | Monthly |
| Programme Manager | Delivery accountability | Monthly (+ weekly with SRO) |

**Programme Team**:

| Role | FTE | Duration |
|------|-----|----------|
| Programme Manager | 1.0 | 24 months |
| Enterprise Architect / Lead Architect | 0.8 | 18 months |
| Platform Engineering Lead | 1.0 | 18 months |
| Cloud/DevOps Engineers (platform team) | 2–3 | 18 months |
| Legacy BAU Squad | 2 | 18 months (reducing) |
| Data Architect / Migration Lead | 0.8 | 18 months |
| Security Architect | 0.5 | 12 months |
| Change Manager | 0.5 | 18 months |
| Test Manager | 1.0 | 12 months (Phases 2–3) |

### E1.2 RACI Matrix

*Derived from ARC-001-STKE-v1.0 stakeholder analysis RACI:*

| Decision / Activity | Responsible | Accountable | Consulted | Informed |
|--------------------|-------------|-------------|-----------|----------|
| Programme investment approval | CFO | Executive Sponsor | Board | All stakeholders |
| Phase go/no-go sign-off | Programme Manager | Executive Sponsor | CTO, VP Ops, CISO | All |
| Migration sequence and architecture | Enterprise Architect | CTO | VP Ops, CISO, Compliance | Engineering, Finance |
| Security design approval | CISO | CISO | Enterprise Architect, Compliance | Engineering, Audit |
| PCI-DSS scope and migration priority | CISO | Head of Compliance | Enterprise Architect | CFO, Executive Sponsor |
| Scope change control (SCCB) | Programme Manager | CFO + Executive Sponsor | CTO, VP Ops | All teams |
| Procurement decisions | Programme Manager | CFO | Commercial, Legal | CTO, CISO |
| Legacy decommission approval | VP Operations | CTO | Finance, Engineering | All |
| Benefits measurement sign-off | CFO | Executive Sponsor | Finance, CTO | Steering Committee |

### E1.3 Approval Gates

| Gate | Trigger | Approval Criteria | Authority |
|------|---------|-------------------|-----------|
| **Gate 0: SOBC Approval** | This document | Board approves investment; SRO and Programme Manager appointed | Board / Steering Committee |
| **Gate 1: Phase 1 Go-Live** | Month 6 | UAT signed off; PCI-DSS scope confirmed; error rate < 0.1%; rollback tested | Executive Sponsor + VP Ops |
| **Gate 2: Phase 2 Go-Live** | Month 12 | PCI-DSS re-certification complete; 99.9% uptime baseline established; logistics API live | Executive Sponsor + CISO + VP Ops |
| **Gate 3: Phase 3 Go-Live** | Month 18 | 100% traffic on new platform; legacy decommission plan confirmed | Executive Sponsor + CTO |
| **Gate 4: Benefits Review** | Month 24 | Legacy decommissioned; 30% TCO reduction evidenced; all goals measured | CFO + Executive Sponsor |

## E2. Delivery Approach

**Methodology**: Agile (Scrum) with quarterly phase gate reviews. Two-week sprints. Architecture review board approvals at each phase gate before go-live approval.

**Migration Pattern**: Strangler-fig (ARC-000-PRIN-v1.0, Principle 1). New platform built alongside legacy. Traffic progressively migrated using canary releases (5% → 25% → 50% → 100% per phase). Rollback capability maintained throughout.

**Deployment Strategy**: Blue/green deployment for all phase cutovers. Automated rollback trigger: if production error rate > 0.5% for 5 minutes, auto-revert to previous state.

**Data Migration**: Dual-write period of 2 weeks per phase (write to both legacy and new; automated reconciliation script validates record counts and checksums before cutover confirmed).

## E3. Key Milestones

| Milestone | Target Date | Owner | CSF Dependency |
|-----------|------------|-------|----------------|
| SOBC Approved, SRO and PM appointed | Month 1 | Executive Sponsor | Gate 0 |
| QSA engagement commenced | Month 1 | CISO | CSF-1 |
| Platform team ring-fenced, legacy BAU contracted | Month 2 | CTO/CIO | R-004 mitigation |
| Legacy data profiling complete | Month 2 | Data Architect | CSF-2 pre-condition |
| ACL design reviewed and approved | Month 2 | Enterprise Architect | R-016 mitigation |
| Phase 1 development commences | Month 2 | Engineering Lead | G-1 |
| AWS Security Hub + GuardDuty live | Month 1 | CISO | R-020 mitigation |
| PCI-DSS scope confirmed by QSA | Month 3 | CISO | CSF-1 |
| **Phase 1 go-live (order creation on new platform)** | **Month 6** | **Engineering Lead** | **Gate 1** |
| PCI-DSS pre-assessment readiness review | Month 6 | CISO | CSF-1 |
| **PCI-DSS re-certification achieved** | **Month 8** | **CISO** | **CSF-1, G-5** |
| Real-time order status API launched | Month 10 | Engineering Lead | G-4 |
| **Phase 2 go-live (fulfilment + logistics on new platform)** | **Month 12** | **Engineering Lead** | **Gate 2, G-3** |
| GDPR right-to-erasure automation complete | Month 12 | Data Architect | G-5 |
| 99.9% uptime confirmed (3 consecutive months) | Month 15 | VP Operations | G-3 |
| **Phase 3 go-live (100% traffic on new platform)** | **Month 18** | **Engineering Lead** | **Gate 3, G-1** |
| Legacy platform decommission | Month 20–24 | VP Operations | CSF-4 |
| **30% TCO reduction confirmed by Finance** | **Month 24** | **CFO** | **Gate 4, G-2** |
| OBC/benefits review document | Month 24 | Programme Manager | Business case lifecycle |

**Critical Path**: QSA Month 1 → PCI-DSS scope confirmed Month 3 → Phase 1 go-live Month 6 → PCI-DSS re-cert Month 8. Any delay to Phase 1 go-live directly threatens PCI-DSS certification deadline.

## E4. Resource Requirements

**Skills Assessment**:

| Skill | Availability | Gap | Mitigation |
|-------|-------------|-----|------------|
| AWS cloud-native architecture | LOW | HIGH | AWS Professional Services Month 1–3; AWS certifications for all engineers by Month 6 |
| Event-driven patterns (outbox, saga, ACL) | LOW | HIGH | Specialist contractor engagement Month 1–4 |
| Legacy OMS (Perl/legacy stack) | MEDIUM | MEDIUM | Ring-fenced BAU squad; managed service top-up |
| Agile delivery / scrum | MEDIUM | LOW | Existing capability; coaching if needed |
| PCI-DSS / security architecture | LOW | MEDIUM | Specialist security architect contractor; QSA direct engagement |
| Data architecture and migration | LOW | MEDIUM | Data Architect hire or contract by Month 2 |

**Training Plan**:

| Training | Audience | Timing | Estimated Cost |
|----------|----------|--------|----------------|
| AWS Solutions Architect Associate | All platform engineers (4–6) | Month 1–6 | £24K |
| Event-driven architecture patterns | Platform engineers | Month 1–3 (workshop) | £15K |
| PCI-DSS awareness | Engineering + Security team | Month 1 | £5K |
| New platform training (fulfillment team) | Operations staff | 4 weeks before each phase cutover | £30K |
| Cloud FinOps | Engineering Lead + CFO office | Month 2 | £8K |

## E5. Change Management

**Stakeholder Engagement Plan** (from ARC-001-STKE-v1.0):

| Stakeholder | Change Magnitude | Resistance Risk | Key Message | Channel | Frequency |
|-------------|----------------|----------------|-------------|---------|-----------|
| Executive Sponsor | LOW | LOW | Programme delivers board commitments on schedule | Steering board | Fortnightly |
| CFO | MEDIUM | LOW | Early cost signals confirm business case trajectory | Financial dashboard | Monthly |
| VP Operations | HIGH | MEDIUM | Every phase gate has pre-agreed exit criteria — Operations cannot be pressured to accept risk | Direct + steering board | Weekly during cutovers |
| Order Fulfillment Teams | HIGH | HIGH | Your workarounds are being ELIMINATED, not replicated | UAT sessions, team meetings | Weekly during phases |
| Engineering Teams | HIGH | LOW | Modern stack, daily deployments, career development | Sprint ceremonies | Daily |
| Logistics Partners | HIGH | MEDIUM | API preview available; SFTP adapter maintained until migration complete | Direct partner sessions | Monthly |
| End Customers | HIGH (positive) | NONE | Real-time tracking and self-service are coming | Release communications | At each phase go-live |

**Resistance Mitigation**:

- **Order Fulfillment Teams** (HIGH resistance risk): Identified as "Resisters" in ARC-001-STKE-v1.0. Strategy: named fulfillment staff on design working group from Month 1; documented commitment to eliminate (not replicate) each of the 14 legacy workarounds before phase sign-off; go/no-go gate requires ≥ 80% UAT sign-off from fulfillment team. Programme Manager has direct escalation channel to VP Operations for capacity disputes.
- **VP Operations** (MEDIUM resistance risk): Phase exit criteria (uptime thresholds, error rates) agreed in Month 1 and not renegotiated mid-programme. Operations sign-off on criteria before migration begins — criteria become objective gate, not discretionary judgment.

## E6. Benefits Realization

**Benefits Measurement Schedule**:

| Benefit | Owner | Measurement Method | Baseline Date | First Measurement | Target Date |
|---------|-------|-------------------|--------------|-------------------|-------------|
| 30% TCO reduction | CFO | Finance cost comparison vs Year 0 baseline | Month 1 | Month 12 (partial) | Month 24 |
| 99.9% uptime | VP Operations | Application monitoring | Month 1 | Month 12 | Month 15 (sustained) |
| 80% order error reduction | VP Operations | Order reconciliation reports | Month 1 | Month 9 | Month 18 |
| 24h order-to-ship | VP Commercial | Order management analytics | Month 1 | Month 12 | Month 18 |
| < 5-min status updates | VP Commercial | API gateway latency monitoring | N/A | Month 10 (Phase 2 launch) | Month 12 |
| 2-week feature lead time | CTO | CI/CD pipeline metrics | Month 1 | Month 9 | Month 18 |
| SAR fulfillment < 5 days | Head of Compliance | Legal SAR log | Month 1 | Month 12 | Month 12 |
| PCI-DSS re-certification | CISO | QSA certification | N/A | Month 8 | Month 8 |

**Benefits Monitoring Cadence**: Monthly report to Steering Committee; formal benefits realization review at each programme gate (Gate 1–4). Six-month and 12-month post-go-live reviews for sustained benefits confirmation.

## E7. Risk Summary

**Top 10 Risks from ARC-001-RISK-v1.0** (full register in that document):

| Risk ID | Title | Residual Score | Owner | Primary Mitigation |
|---------|-------|----------------|-------|-------------------|
| R-004 | Engineering capacity — legacy drag | 9 (exceeds appetite) | CTO/CIO | Ring-fenced platform team + BAU squad — **Month 2 action** |
| R-001 | Programme scope creep | 9 | Executive Sponsor | Scope Change Control Board (SCCB) established Month 1 |
| R-006 | AWS/cloud-native skills gap | 9 | CTO/CIO | AWS Professional Services Month 1; certs by Month 6 |
| R-011 | PCI-DSS re-certification missed | 8 (exceeds appetite) | CISO | QSA from Month 1; pre-assessment readiness Month 6 |
| R-013 | Customer-visible service degradation | 8 | VP Operations | Blue/green deployment; canary releases; auto-rollback |
| R-014 | Order data loss during migration | 8 | CTO/EA | Dual-write + automated reconciliation per phase |
| R-020 | Security breach during migration | 8 | CISO | Security Hub Day 1; GuardDuty; cyber insurance £5M |
| R-009 | Programme budget overrun | 8 | CFO | 15% contingency reserve; Earned Value Management |
| R-002 | Executive sponsorship weakens | 6 | Executive Sponsor | Deputy SRO appointed; quick wins by Month 3 |
| R-005 | Fulfillment team UAT disengagement | 6 | VP Operations | 80% UAT sign-off gate; super-users embedded Month 3 |

**Two risks currently exceed appetite**: R-004 (OPERATIONAL) and R-011 (COMPLIANCE). Both have escalation plans and immediate mitigation actions scheduled for Month 1–2. Full risk management framework: ARC-001-RISK-v1.0.

**Risk Appetite**: The programme is assessed as **Concerning** on the inherent profile (1 Critical, 6 High risks inherent) but **Acceptable** on the residual profile (0 Critical, 0 High risks residual) after application of the mitigations defined in ARC-001-RISK-v1.0. The two risks exceeding appetite require escalation to Steering Committee.

---

# PART F: RECOMMENDATION AND NEXT STEPS

## F1. Summary of Recommendation

| Item | Value |
|------|-------|
| **Recommended Option** | Option 2 — Phased Cloud-Native Migration (Strangler-Fig) |
| **Programme Capital** | £3.5M (ROM ±30%) over Years 1–2 |
| **Year 3+ Opex** | £0.8M/year (vs £1.6M/year legacy — £0.8M/year saving) |
| **5-year NPV** | £1.0M–£6.2M (base to 7-year) |
| **Payback Period** | ~26 months |
| **BCR (5-year)** | 1.8:1 |
| **Stakeholder Goals Met** | 85% (G-1 through G-6 all substantially met) |
| **CSFs Met** | 6/6 |
| **Overall Risk** | Concerning inherent → Acceptable residual (ARC-001-RISK-v1.0) |
| **Go/No-Go** | **PROCEED — subject to conditions below** |

## F2. Conditions for Approval

**Mandatory Conditions** (programme cannot start without these):

1. Programme Manager appointed — by Month 1
2. Budget of £3.5M (capital) approved and committed
3. Steering Committee constituted with Executive Sponsor as SRO
4. Platform engineering team ring-fencing commitment confirmed by CTO (resolving R-004)
5. QSA engaged by Month 1 for PCI-DSS scope assessment

**Recommended Conditions**:

1. Year 0 TCO baseline formally agreed with Finance by Month 2 (to validate 30% reduction target)
2. AWS Professional Services engagement letter signed by Month 1
3. Legacy BAU managed service contract in place by Month 2

## F3. Next Steps if Approved

**Month 1 — Mobilisation**:
1. Executive Sponsor appoints Programme Manager and constitutes Steering Committee
2. CTO confirms platform engineering team structure and ring-fencing
3. CISO engages QSA for PCI-DSS scope assessment
4. CISO enables AWS Security Hub and GuardDuty
5. CFO initiates Year 0 TCO baselining exercise with Finance team

**Month 1–2 — Foundations**:
1. Run `/arckit:requirements` — detailed requirements specification for vendor RFP and architecture review
2. Data profiling of legacy OMS data (quality assessment, migration complexity)
3. ACL design review (DDD specialist engagement)
4. Scope Change Control Board (SCCB) established and operational
5. AWS Professional Services architecture review initiated

**Month 3 — OBC Preparation**:
1. Create Outline Business Case (OBC) with firmer costs based on data profiling findings and AWS assessment
2. Phase 1 detailed plan and go-live criteria agreed with VP Operations and CISO
3. Procurement process for development team launched

**Business Case Lifecycle**:

```
SOBC (this document) → Approved Month 1
     ↓
OBC (refined costs after requirements) → Month 3
     ↓
Programme execution: Phases 1-3 (Months 2-18)
     ↓
FBC (actuals vs SOBC) → Month 24 with benefits realization review
```

## F4. Traceability Summary

**All 6 stakeholder goals addressed**:

| Goal | Benefit | SOBC Section |
|------|---------|-------------|
| G-1: Platform migration Month 18 | B-005 + B-007 (commercial + velocity) | Part A, Part B Option 2 |
| G-2: 30% TCO reduction | B-001 + B-002 (legacy + reconciliation elimination) | Part B, Part D |
| G-3: 99.9% uptime + 80% error reduction | B-003 (outage avoidance) | Part B Option 2, Part E benefits |
| G-4: 24h ship + real-time tracking | B-004 (churn recovery) | Part B Option 2, Part E |
| G-5: PCI-DSS Month 8 + GDPR SAR < 5 days | B-006 (compliance avoidance) | Part A, Part C, Part E |
| G-6: 2-week feature lead time | B-007 (engineering productivity) | Part B Option 2, Part E |

**Risk register integration**: Top 10 risks in Part E (E7) with full detail in ARC-001-RISK-v1.0. Risks R-001 through R-020 all linked to stakeholder owners from ARC-001-STKE-v1.0 RACI matrix.

---

# APPENDICES

## Appendix A: Stakeholder Analysis Reference

**Full document**: `projects/001-order-management-modernization/ARC-001-STKE-v1.0.md`

**Key stakeholders**: Executive Sponsor (SRO), CFO, CTO/CIO, VP Operations, VP Commercial, CISO, Head of Compliance, Finance/Accounting Team, Order Fulfillment Teams, Engineering Teams, Logistics Partners, End Customers.

**Stakeholder alignment**: Overall alignment HIGH. 12/13 stakeholder groups share drivers that converge on programme outcomes. Principal conflict (CFO speed vs VP Operations risk) resolved through time-boxed stabilization periods with agreed exit criteria.

## Appendix B: Architecture Principles Reference

**Full document**: `projects/000-global/ARC-000-PRIN-v1.0.md`

**Key principles supporting this SOBC**:
- Principle 1 (Incremental Modernization): Justifies strangler-fig pattern vs big-bang rewrite
- Principle 2 (Cloud-Native by Design): Justifies AWS managed services approach
- Principle 5 (Security by Design — NON-NEGOTIABLE): Mandates security controls from Phase 1
- Principle 8 (Immutable Audit Trail): Enables compliance outcome O-4
- Principle 14 (Event-Driven Order Lifecycle): Enables real-time integration benefits
- Principle 15 (Anti-Corruption Layer): Enables safe strangler-fig execution

## Appendix C: Risk Register Reference

**Full document**: `projects/001-order-management-modernization/ARC-001-RISK-v1.0.md`

**Summary**: 20 risks identified. Inherent profile: 1 Critical, 6 High, 13 Medium. Residual profile: 0 Critical, 0 High, 17 Medium, 3 Low. Overall risk reduction: 46%. Two risks (R-004, R-011) exceed appetite and require immediate escalation to Steering Committee.

## Appendix D: Financial Assumptions Register

| Assumption | Value | Sensitivity |
|-----------|-------|-------------|
| Year 0 legacy TCO (ROM) | £1.6M/year | ±20% — to be formally baselined Month 1 |
| Programme capital (ROM) | £3.5M | ±30% per ROM methodology |
| Cloud platform Opex (Year 3+) | £0.8M/year | ±15% — depends on AWS pricing and team size |
| B2B portal revenue (Year 3) | £0.75M | HIGH uncertainty — pipeline estimate from commercial team |
| Customer churn recovery | 8% churn reduction | MEDIUM uncertainty — based on NPS data |
| Compliance penalty avoidance | £0.8M (3-year) | MEDIUM uncertainty — depends on regulatory action |
| Discount rate | 3.5% | Fixed (standard) |
| Optimism bias applied | +20% on costs | Standard technology programme |

## Appendix E: Glossary

| Term | Definition |
|------|-----------|
| SOBC | Strategic Outline Business Case — first-stage business case with ROM estimates |
| OBC | Outline Business Case — second stage with refined costs after requirements |
| FBC | Full Business Case — final stage with accurate costs before final commitment |
| ROM | Rough Order of Magnitude — cost estimate with stated accuracy band (±30%) |
| NPV | Net Present Value — sum of discounted net cashflows |
| BCR | Benefit-Cost Ratio — total benefits ÷ total costs (present value) |
| TCO | Total Cost of Ownership — capital + operating costs over lifecycle |
| ACL | Anti-Corruption Layer — architectural pattern isolating legacy from new domain |
| QSA | Qualified Security Assessor — PCI-DSS certification assessor |
| SRO | Senior Responsible Owner — accountable for programme delivery |
| SCCB | Scope Change Control Board — governance body approving scope changes |

---

## Document Approval

| Name | Role | Signature | Date |
|------|------|-----------|------|
| | Executive Sponsor (SRO) | | |
| | CFO | | |
| | CTO/CIO | | |
| | VP Operations | | |
| | CISO | | |

**Approval Decision**: DRAFT — Pending review

**Next Review Date**: 2026-07-23

---

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|--------|----------|------|-----------------|-------------|
| *None provided* | — | — | — | No external governance documents supplied at generation time. Place financial forecasts or board papers in `projects/001-order-management-modernization/external/` and re-run to incorporate. |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Notes |
|-------------|--------|--------------|----------|-------|
| — | — | — | — | All content derived from ARC-001-STKE-v1.0, ARC-001-RISK-v1.0, ARC-001-REQ-v1.0, ARC-000-PRIN-v1.0 |

---

**Generated by**: ArcKit `/arckit:sobc` command
**Generated on**: 2026-05-23
**ArcKit Version**: 5.0.4
**Project**: Legacy Order Management Modernization (Project 001)
**AI Model**: claude-sonnet-4-6
**Generation Context**: Derived from ARC-001-STKE-v1.0 (12 drivers, 6 goals, 4 outcomes, 3 conflicts), ARC-001-RISK-v1.0 (20 risks, Orange Book), ARC-001-REQ-v1.0 (72 requirements), ARC-000-PRIN-v1.0 (21 architecture principles). 4 options evaluated at ROM (strategic estimates). Green Book 5-case model applied.
