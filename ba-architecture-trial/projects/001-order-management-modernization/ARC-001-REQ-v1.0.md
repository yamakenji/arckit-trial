# Project Requirements: Legacy Order Management Modernization

> **Template Origin**: Official | **ArcKit Version**: 5.0.4 | **Command**: `/arckit:requirements`

## Document Control

| Field | Value |
|---|---|
| **Document ID** | ARC-001-REQ-v1.0 |
| **Document Type** | Business and Technical Requirements (REQ) |
| **Project** | Legacy Order Management Modernization (Project 001) |
| **Classification** | OFFICIAL |
| **Status** | DRAFT |
| **Version** | 1.0 |
| **Created Date** | 2026-05-23 |
| **Last Modified** | 2026-05-23 |
| **Review Date** | 2026-06-22 |
| **Owner** | Enterprise Architect |
| **Reviewed By** | [PENDING] |
| **Approved By** | [PENDING] |
| **Distribution** | Project Team, Architecture Team, Engineering Leads, Product Owners |

---

## Revision History

| Version | Date | Author | Changes | Approved By | Approval Date |
|---------|------|--------|---------|-------------|---------------|
| 1.0 | 2026-05-23 | ArcKit AI | Initial creation from `/arckit:requirements` command | [PENDING] | [PENDING] |

## Document Purpose

This document defines the complete set of business, functional, non-functional, integration, and data requirements for the Legacy Order Management Modernization programme. It is the authoritative requirements baseline for vendor RFPs, architecture design reviews, UAT planning, and programme governance. All requirements are traced to stakeholder goals in `ARC-001-STKE-v1.0` and architecture principles in `ARC-000-PRIN-v1.0`.

---

## Executive Summary

### Business Context

The organization's current order management system is a legacy monolith with documented reliability, security, and scalability deficits. Over the past 12 months it has experienced 14 unplanned outages (6 exceeding 2 hours), accumulates approximately 1,200 manual reconciliation events per month, and carries 3 unresolvable high-severity security findings that require platform migration to close. Engineering attrition is increasing, with departing staff citing the legacy stack as a primary factor. Competitors have already migrated to modern, API-capable order management platforms that support commercial models — subscriptions, B2B portals, real-time partner integrations — that the legacy system structurally cannot deliver.

The modernization programme replaces the legacy platform incrementally using a strangler-fig migration pattern, preserving business continuity at every phase. It targets completion of all core order processing migration within 18 months and full legacy decommission by Month 24.

### Objectives

- Migrate 100% of order processing volume to a cloud-native, event-driven platform by Month 18
- Reduce total cost of ownership of the order management function by 30% by Month 24
- Achieve 99.9% order processing uptime on the new platform from Month 12 onwards
- Remediate all 3 high-severity security findings and achieve PCI-DSS re-certification by Month 8
- Reduce feature delivery lead time from 8 weeks to 2 weeks by Month 18

### Expected Outcomes

- **O-1**: Platform modernized — 100% order volume on new platform, legacy decommissioned by Month 24 (supports G-1, G-6; satisfies SD-1, SD-3, SD-10)
- **O-2**: 30% TCO reduction vs. Year 0 baseline confirmed by Month 24; manual reconciliation labour below 0.25 FTE (supports G-2; satisfies SD-2, SD-8)
- **O-3**: 99.9% order processing uptime from Month 12; order-to-ship 24 hours; customer NPS +15 by Month 18 (supports G-3, G-4; satisfies SD-4, SD-5, SD-11)
- **O-4**: All high-severity security findings closed; PCI-DSS re-certified by Month 8; GDPR SAR fulfillment < 5 days by Month 12 (supports G-5; satisfies SD-6, SD-7)

### Project Scope

**In Scope**:

- Order creation, capture, management, and status lifecycle (all channels)
- Order fulfillment, dispatch, and delivery tracking
- Returns and refund initiation workflows
- Customer-facing order status and self-service portal (Phase 2)
- Integrations with payment gateway, ERP/finance, logistics partners, and CRM
- Data migration from legacy order management system including full order history
- Decommission of legacy order management platform

**Out of Scope**:

- ERP system replacement or re-architecture
- CRM system replacement
- Product catalogue management system (separate initiative)
- Customer identity and authentication platform (pre-existing, integrated via API)
- Warehouse management system internals (integrate via API only)
- New commercial model development (subscriptions, B2B portal) beyond enabling API infrastructure

---

## Stakeholders

| Stakeholder | Role | Organization | Involvement Level |
|-------------|------|--------------|-------------------|
| Executive Sponsor (CEO/COO) | Programme authority | Executive | Decision maker, phase gate approver |
| CFO / Finance Director | Financial accountability | Finance | Business case owner, ROI sign-off |
| CTO / CIO | Technical authority | Technology | Architecture approver |
| VP Operations | Operational owner | Operations | Phase migration sign-off |
| VP Commercial / Sales | Commercial outcomes | Commercial | Requirements input, UAT lead |
| CISO | Security authority | Information Security | Security gate sign-off |
| Head of Compliance | Regulatory authority | Legal & Compliance | PCI-DSS, GDPR gate sign-off |
| Enterprise Architect | Architecture design | Technology | Requirements owner |
| Engineering Lead | Delivery | Engineering | Implementation |
| Order Fulfillment Team Leads | Domain experts | Operations | UAT, domain requirements |
| Finance / Accounting Team | Finance operations | Finance | Reconciliation UAT |

*Full stakeholder analysis: see `ARC-001-STKE-v1.0`*

---

## Business Requirements

### BR-001: Incremental Platform Migration with Business Continuity

**Description**: The modernization programme MUST deliver the new platform incrementally across defined phases. At no point during migration shall customer-facing order processing be unavailable due to programme activity. Each phase must leave the system in a fully production-deployable state.

**Rationale**: Big-bang migration carries unacceptable business continuity risk for a revenue-critical system. Incremental delivery allows early value realization and risk management per phase. Aligned to Principle 1 in `ARC-000-PRIN-v1.0`.

**Success Criteria**:

- Zero unplanned order processing outages attributable to migration activity across all phases
- Each phase has documented entry/exit criteria signed off before migration begins
- Rollback plan tested for each phase before any production traffic is routed to new components
- At least one phase delivering customer-visible value within 6 months of programme start

**Priority**: MUST_HAVE

**Stakeholder**: Executive Sponsor, VP Operations (SD-1, SD-4; G-1)

---

### BR-002: 30% Total Cost of Ownership Reduction by Month 24

**Description**: The programme MUST deliver a quantified 30% reduction in annual order management TCO by Month 24, measured against the Year 0 baseline agreed in Month 1. TCO includes legacy licence fees, support contracts, specialist contractor costs, and manual reconciliation labour.

**Rationale**: The CFO has a board-level commitment to operational efficiency targets. TCO reduction validates the modernization business case and funds future phases. Aligned to stakeholder goal G-2 in `ARC-001-STKE-v1.0`.

**Success Criteria**:

- Year 0 TCO baseline formally agreed with Finance by Month 1
- Legacy licence and specialist support contracts fully terminated by Month 18
- Manual reconciliation events below 100 per month by Month 24 (from current 1,200)
- Finance/accounting reconciliation labour below 0.25 FTE by Month 24 (from current ~2.0 FTE)
- Month 24 Finance review confirms 30% TCO reduction vs. baseline

**Priority**: MUST_HAVE

**Stakeholder**: CFO / Finance Director (SD-2; G-2; O-2)

---

### BR-003: Achieve 99.9% Order Processing Uptime from Month 12

**Description**: The new platform MUST achieve and sustain 99.9% monthly uptime for order processing from Month 12 onwards. This represents a material improvement over the legacy system's trailing 12-month uptime of 99.0%.

**Rationale**: Operations team KPIs and customer SLAs depend on order processing reliability. Unplanned outages cost an estimated 6–8 staff hours of manual recovery per event plus direct revenue and customer satisfaction impact. Aligned to stakeholder goal G-3 and outcome O-3 in `ARC-001-STKE-v1.0`.

**Success Criteria**:

- New platform achieves >= 99.9% uptime in each calendar month from Month 12
- MTTR for order processing incidents below 30 minutes from Month 12 (from current ~3 hours)
- Order error rate (duplicates, lost orders, incorrect status) reduced by 80% vs. legacy baseline
- Three consecutive months at 99.9% uptime confirmed before Operations approves full legacy decommission

**Priority**: MUST_HAVE

**Stakeholder**: VP Operations (SD-4; G-3; O-3)

---

### BR-004: Remediate Security Findings and Achieve PCI-DSS Re-Certification by Month 8

**Description**: All 3 high-severity and 11 medium-severity security findings from the most recent penetration test MUST be remediated, and PCI-DSS re-certification MUST be achieved on the new platform by Month 8. This is a fixed compliance deadline that cannot be extended.

**Rationale**: Two of the high-severity findings are unresolvable on the legacy platform and require migration. PCI-DSS re-certification has an external auditor deadline at Month 8. Failure carries financial and reputational consequence. Aligned to stakeholder goal G-5 and outcome O-4 in `ARC-001-STKE-v1.0`.

**Success Criteria**:

- PCI-DSS scoped components identified and documented by Month 1
- PCI-DSS scoped components migrated to new platform by Month 7
- QSA audit submitted by Month 7; re-certification letter received by Month 8
- All 3 high-severity findings confirmed closed by Month 8 penetration test
- All 11 medium-severity findings resolved or have accepted compensating controls by Month 10

**Priority**: MUST_HAVE

**Stakeholder**: CISO, Head of Compliance (SD-6, SD-7; G-5; O-4)

---

### BR-005: GDPR-Compliant Data Lifecycle Management

**Description**: The new platform MUST implement automated data lifecycle management for all customer and order data, including right-to-erasure (subject to legal hold), Subject Access Request fulfillment in under 5 days, and automated retention/deletion enforcement.

**Rationale**: A recent GDPR Subject Access Request took 47 days to fulfill due to fragmented legacy data. The ICO has requested evidence of improvement. Manual SAR fulfillment is both a compliance risk and an operational overhead. Aligned to SD-7 and G-5 in `ARC-001-STKE-v1.0`.

**Success Criteria**:

- Data classification performed for all data entities before platform design is finalized (Month 2)
- Automated right-to-erasure implemented for all personal data fields (with legal hold exception) by Month 12
- SAR fulfillment time below 5 days (calendar) from Month 12 onwards, confirmed by legal team review of 3 consecutive SARs
- Automated data retention deletion enforcement operational for all data classes by Month 12

**Priority**: MUST_HAVE

**Stakeholder**: Head of Compliance (SD-7; G-5; O-4)

---

### BR-006: Reduce Feature Delivery Lead Time to 2 Weeks

**Description**: The new platform architecture and engineering delivery practice MUST reduce the mean lead time for order management feature delivery from the current 8 weeks to 2 weeks by Month 18, with daily production deployments enabled.

**Rationale**: The current 8-week deployment cycle has caused the commercial team to stop requesting order management changes, routing around the system with workarounds. Developer experience improvement is also critical for engineering retention. Aligned to SD-3, SD-10, G-6 in `ARC-001-STKE-v1.0`.

**Success Criteria**:

- CI/CD pipelines with automated testing and rollback operational before any features are delivered on the new platform
- Mean feature lead time (request to production) below 2 weeks, confirmed over 3 consecutive months by Month 18
- Deployment frequency at minimum daily from Month 12
- Change failure rate (production incidents from deployments) below 10% from Month 12 (from current ~35%)

**Priority**: MUST_HAVE

**Stakeholder**: CTO / CIO, Engineering Teams (SD-3, SD-10; G-6; O-1)

---

### BR-007: Enable Real-Time Order Visibility for Customers

**Description**: The new platform MUST provide real-time order status visibility updated within 5 minutes of each lifecycle transition, and deliver a foundation for a customer self-service portal that supports order tracking and cancellation for eligible orders.

**Rationale**: Order tracking is the second-lowest-rated customer touchpoint. Batch status updates (currently 4-hour cycle) drive avoidable call centre volume. Real-time status also unblocks the B2B portal commercial initiative. Aligned to SD-5, SD-11, G-4 in `ARC-001-STKE-v1.0`.

**Success Criteria**:

- Order status updated and visible via API within 5 minutes of each lifecycle event from Phase 2 (Month 12)
- Customer service call volume for order status enquiries reduced by 30% by Month 18
- Customer order experience NPS improved by +15 points vs. baseline by Month 18
- Self-service order cancellation available for eligible orders (standard orders not in dispatch) from Phase 2

**Priority**: MUST_HAVE

**Stakeholder**: VP Commercial, End Customers (SD-5, SD-11; G-4; O-3)

---

### BR-008: Reduce Order-to-Ship Time to 24 Hours for Standard Orders

**Description**: End-to-end processing time from order placement to dispatch confirmation for standard in-stock orders MUST be reduced from the current 48-hour average to 24 hours, enabled by real-time logistics partner integrations replacing the current nightly batch exchange.

**Rationale**: Order-to-ship time is a key commercial differentiator and a prerequisite for the commercial team's planned premium SLA tier. Reduction requires replacing SFTP batch logistics integration with real-time event-driven dispatch. Aligned to SD-5, SD-12, G-4 in `ARC-001-STKE-v1.0`.

**Success Criteria**:

- Average order-to-ship for standard in-stock orders below 24 hours by Month 18
- Logistics partner SFTP batch integration replaced with real-time API integration for all primary partners by Month 15
- Logistics integration failure rate below 0.5% of order dispatches by Month 18 (from current ~3 failures/month manual resolution)

**Priority**: MUST_HAVE

**Stakeholder**: VP Commercial, Logistics Partners (SD-5, SD-12; G-4; O-3)

---

## Functional Requirements

### User Personas

#### Persona 1: Order Fulfillment Operator

- **Role**: Operations staff responsible for managing order processing queues, resolving exceptions, and coordinating with logistics
- **Goals**: Process orders accurately and efficiently with minimal manual intervention; resolve exceptions quickly with clear system guidance
- **Pain Points**: 14 documented manual workarounds in legacy system; 6-week onboarding due to undocumented edge cases; high error correction overhead
- **Technical Proficiency**: Medium — comfortable with web-based tools; not technical developers

#### Persona 2: Customer Service Agent

- **Role**: Front-line support staff handling customer enquiries about order status, modifications, and returns
- **Goals**: Answer customer order questions quickly using real-time data; initiate returns and refunds without escalation
- **Pain Points**: Order status data stale by up to 4 hours; escalation required for most cancellation requests; no unified order view
- **Technical Proficiency**: Medium — power user of internal tools

#### Persona 3: Finance / Reconciliation Analyst

- **Role**: Finance operations staff responsible for order-to-cash reconciliation and financial reporting
- **Goals**: Automated reconciliation with exceptions surfaced proactively; clean month-end close without manual correction
- **Pain Points**: 1,200 manual reconciliation events per month; month-end close extends 2–3 days; legacy ERP batch failures
- **Technical Proficiency**: Medium — Excel proficient; uses ERP and reporting tools

#### Persona 4: Logistics / Fulfillment Partner (External)

- **Role**: Third-party logistics provider receiving dispatch instructions and returning delivery status updates
- **Goals**: Receive dispatch instructions in real time; return delivery events reliably; onboard new capabilities without bespoke development
- **Pain Points**: SFTP batch integration unreliable; integration failures require manual resolution from both parties; 3–4 months to onboard new capabilities
- **Technical Proficiency**: High — technical integration team

#### Persona 5: Enterprise Customer (B2B Buyer)

- **Role**: Business customer placing and managing orders via portal or API
- **Goals**: Self-service order placement, status tracking, and modification; webhook notifications for order events
- **Pain Points**: No self-service portal; phone/email required for all order management; no programmatic API access
- **Technical Proficiency**: High — may have technical integration team

---

### Use Cases

#### UC-1: Place and Confirm an Order

**Actor**: Order Fulfillment Operator / Customer (via channel)

**Preconditions**:
- Customer identity verified and authorised
- Product availability confirmed
- Payment method valid and authorised

**Main Flow**:
1. Order submitted via channel (web, API, or internal tool)
2. System validates order data (customer, products, quantities, delivery address)
3. System reserves inventory atomically with order creation
4. System initiates payment authorisation
5. On payment authorisation success, system transitions order to CONFIRMED state
6. System publishes OrderConfirmed event to event bus
7. System sends confirmation notification to customer
8. Logistics dispatch event queued for fulfillment

**Postconditions**:
- Order record created with immutable audit entry
- Inventory reservation recorded
- Payment authorisation token stored
- OrderConfirmed event published and durable

**Alternative Flows**:
- **Alt 4a**: Payment authorisation fails — order transitions to PAYMENT_FAILED; inventory reservation released; customer notified
- **Alt 2a**: Validation failure — order rejected with specific error codes; no inventory reserved; no payment attempted

**Exception Flows**:
- **Ex 1**: Inventory system unavailable — order held in PENDING state with durable message; customer notified of delay; retry with backoff
- **Ex 2**: Duplicate submission (idempotency key match) — return existing order confirmation; do not create duplicate

**Business Rules**:
- Order creation and inventory reservation MUST be atomic (Principle 7, `ARC-000-PRIN-v1.0`)
- Idempotency key required on all order creation requests to prevent duplicates
- Payment authorisation MUST precede order confirmation; no order confirmed without successful authorisation

**Priority**: CRITICAL

---

#### UC-2: Process Order Fulfillment and Dispatch

**Actor**: Order Fulfillment Operator, Logistics Partner

**Preconditions**:
- Order in CONFIRMED state
- Inventory physically allocated in warehouse

**Main Flow**:
1. Fulfillment operator views CONFIRMED orders queue
2. Operator marks order as PROCESSING (or system auto-assigns based on rules)
3. System sends real-time dispatch instruction to logistics partner API
4. Logistics partner acknowledges receipt
5. System transitions order to DISPATCHED; publishes OrderDispatched event
6. Customer receives dispatch notification with tracking reference
7. Logistics partner sends delivery status events (IN_TRANSIT, DELIVERED)
8. System processes delivery event; transitions order to DELIVERED
9. Immutable audit entries created at each transition

**Postconditions**:
- Order in DELIVERED state with full lifecycle audit trail
- All events published and recorded
- Customer notified at each status transition

**Alternative Flows**:
- **Alt 3a**: Logistics partner API unavailable — dispatch instruction held in durable queue; retry with backoff; operator alerted after 3 failed retries
- **Alt 7a**: Delivery failed / returned — system transitions to DELIVERY_FAILED; returns process initiated

**Priority**: CRITICAL

---

#### UC-3: Self-Service Order Cancellation

**Actor**: Customer (via self-service portal or API)

**Preconditions**:
- Order in CONFIRMED or PROCESSING state (not yet DISPATCHED)
- Customer authenticated and authorised as order owner

**Main Flow**:
1. Customer requests cancellation via portal or API
2. System validates order is eligible for self-service cancellation (state check)
3. System initiates cancellation saga: release inventory reservation → void payment authorisation → transition order to CANCELLED
4. System publishes OrderCancelled event
5. Customer receives cancellation confirmation

**Exception Flows**:
- **Ex 1**: Order already DISPATCHED — system rejects self-service cancellation; presents returns initiation option instead
- **Ex 2**: Payment void fails — order flagged for manual finance review; inventory released; customer notified of refund timeline

**Business Rules**:
- Cancellation saga MUST have compensating transactions for each step (Principle 7, `ARC-000-PRIN-v1.0`)
- Self-service cancellation only available for orders not yet in DISPATCHED state

**Priority**: HIGH

---

#### UC-4: Initiate and Process Return / Refund

**Actor**: Customer Service Agent, Customer (self-service)

**Preconditions**:
- Order in DELIVERED state
- Return window not expired (configurable per order type)

**Main Flow**:
1. Return request submitted with reason code and items to return
2. System creates return record linked to original order
3. Return Merchandise Authorisation (RMA) issued
4. Customer returns item(s)
5. Warehouse confirms receipt and condition assessment
6. Refund amount calculated per return policy
7. Refund initiated to original payment method
8. System transitions return to COMPLETED; publishes ReturnCompleted event
9. Audit trail recorded for all steps

**Priority**: HIGH

---

### Functional Requirements Detail

#### FR-001: Order Lifecycle State Machine

**Description**: The system MUST implement a well-defined, enforced order state machine. Orders transition between states only via defined, authorised events. Invalid state transitions MUST be rejected.

**Relates To**: BR-001, BR-003, UC-1, UC-2

**States**: PENDING → CONFIRMED → PROCESSING → DISPATCHED → DELIVERED (terminal); CANCELLED (terminal from PENDING/CONFIRMED/PROCESSING); DELIVERY_FAILED; RETURN_REQUESTED → RETURN_IN_PROGRESS → RETURN_COMPLETED; PAYMENT_FAILED (terminal from PENDING)

**Acceptance Criteria**:

- [ ] Given an order in DISPATCHED state, when a cancellation request is received, then the system rejects it with error code ORDER_NOT_CANCELLABLE
- [ ] Given any state transition event, when the transition is processed, then an immutable audit record is created with actor identity, timestamp, previous state, and new state
- [ ] Given a duplicate state transition event (idempotency key match), when processed, then the system returns success without creating a duplicate transition

**Priority**: MUST_HAVE

**Complexity**: HIGH

**Dependencies**: FR-002 (idempotency), FR-009 (audit trail)

---

#### FR-002: Idempotent Order Operations

**Description**: All order creation and mutation operations MUST accept an idempotency key. Re-submission of the same request MUST return the original response without creating duplicates or re-processing.

**Relates To**: BR-001, BR-003, UC-1

**Acceptance Criteria**:

- [ ] Given an order creation request with idempotency key K, when the same request is submitted a second time with key K within the idempotency window (24 hours), then the original order record is returned and no new order is created
- [ ] Given an idempotency key K submitted after the 24-hour window, when received, then the request is treated as a new order
- [ ] Given a request with no idempotency key, when received on a mutating endpoint, then the system rejects it with HTTP 400

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-003: Order Creation via Multiple Channels

**Description**: The system MUST support order creation via REST API (for B2B and partner integrations), internal operator interface (web-based), and MUST provide a channel-agnostic order processing core that applies identical business rules regardless of submission channel.

**Relates To**: BR-001, BR-007, UC-1

**Acceptance Criteria**:

- [ ] Given an order submitted via REST API, when processed, then it follows the identical state machine and business rules as an order placed via the operator interface
- [ ] Given a channel identifier in the order payload, when stored, then it is recorded on the order record and preserved in audit events
- [ ] Given an API order submission, when successfully created, then the response includes the order ID, confirmation reference, and current state within 3 seconds (p95)

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-004: Real-Time Order Status API

**Description**: The system MUST expose a versioned, authenticated REST API allowing authorised consumers to query current order state and retrieve the full state transition history for any order.

**Relates To**: BR-007, UC-2

**Acceptance Criteria**:

- [ ] Given an authenticated API request for order O, when processed, then the response includes current state, last updated timestamp, and full lifecycle event history
- [ ] Given an order status change event, when processed, then the API reflects the new state within 5 minutes
- [ ] Given an unauthenticated API request, when received, then the system returns HTTP 401

**Data Requirements**:

- **Outputs**: Order ID, state, last transition timestamp, lifecycle event history array, estimated delivery date
- **Validations**: Order ID format; consumer authorisation scope checked against order ownership or admin role

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-005: Customer Self-Service Order Portal

**Description**: The system MUST provide a web-based self-service portal enabling authenticated customers to view their order history, track active orders in real time, initiate cancellations for eligible orders, and initiate returns for delivered orders.

**Relates To**: BR-007, BR-008, UC-3, UC-4

**Acceptance Criteria**:

- [ ] Given an authenticated customer, when viewing the portal, then all their orders are displayed with current status updated within 5 minutes of last change
- [ ] Given an eligible order (state CONFIRMED or PROCESSING), when the customer selects cancel, then the cancellation flow is presented with confirmation step
- [ ] Given an order in DISPATCHED or DELIVERED state, when the customer views it, then a tracking link sourced from the logistics partner is displayed
- [ ] Given a delivered order within the return window, when the customer selects return, then the return initiation flow is presented

**Priority**: MUST_HAVE (Phase 2, Month 12)

**Complexity**: HIGH

**Dependencies**: FR-004 (status API), FR-011 (logistics tracking events), FR-014 (returns)

---

#### FR-006: Order Event Publication

**Description**: The system MUST publish a domain event to the event bus at each order lifecycle state transition. Events MUST be published durably alongside the database write using an outbox or equivalent pattern — never fire-and-forget.

**Relates To**: BR-001, BR-003, Principle 14 (`ARC-000-PRIN-v1.0`)

**Events**: OrderCreated, OrderConfirmed, OrderProcessing, OrderDispatched, OrderDelivered, OrderCancelled, OrderPaymentFailed, ReturnRequested, ReturnCompleted

**Acceptance Criteria**:

- [ ] Given a successful order state transition, when committed to the database, then the corresponding domain event is published to the event bus as part of the same logical operation (outbox pattern)
- [ ] Given an event bus outage during order processing, when the bus recovers, then all unpublished events are delivered in order (at-least-once delivery)
- [ ] Given a domain event, when consumed by a downstream service, then re-processing the same event (duplicate) produces the same result (consumer idempotency)

**Priority**: MUST_HAVE

**Complexity**: HIGH

---

#### FR-007: Order Search and Queue Management

**Description**: The system MUST provide an operator interface for searching orders by multiple criteria (order ID, customer, date range, state, channel) and managing order processing queues with configurable filters and sort orders.

**Relates To**: BR-001, UC-2

**Acceptance Criteria**:

- [ ] Given a search query with any combination of supported criteria, when submitted, then results are returned within 2 seconds (p95) for queries spanning up to 90 days of data
- [ ] Given an operator viewing the CONFIRMED orders queue, when new orders arrive, then they appear in the queue without requiring a page refresh (real-time or polling at 30-second interval)
- [ ] Given a search result, when an operator selects an order, then the full order detail and lifecycle history are displayed

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-008: Exception Queue and Manual Intervention Workflow

**Description**: The system MUST maintain an exception queue for orders that cannot be automatically processed (payment retries exhausted, inventory discrepancies, integration failures). Operators MUST be able to review, action, and resolve exceptions with a full audit trail of actions taken.

**Relates To**: BR-001, BR-003, UC-2

**Acceptance Criteria**:

- [ ] Given an order that cannot be auto-processed after defined retry attempts, when it enters the exception queue, then an alert is sent to the configured on-call channel within 5 minutes
- [ ] Given an operator resolving an exception, when they record their action and resolution, then the action is recorded as an immutable audit event with operator identity and timestamp
- [ ] Given an exception queue, when viewed, then orders are sorted by age (oldest first) and flagged if beyond SLA threshold

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-009: Immutable Order Audit Trail

**Description**: The system MUST record every order state change, manual action, and API call affecting an order as an immutable, append-only audit record. Records MUST NOT be modifiable or deletable through any application interface.

**Relates To**: BR-004, BR-005, Principle 8 (`ARC-000-PRIN-v1.0`)

**Acceptance Criteria**:

- [ ] Given any order state transition, when it occurs, then an audit record is created containing: actor identity (user ID or service name), timestamp (UTC millisecond precision), action, previous state, new state, and correlation ID
- [ ] Given an audit record, when any application interface attempts to update or delete it, then the operation is rejected
- [ ] Given a query for the complete history of order O, when executed, then every state transition from creation to current state is returned in chronological order

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-010: Inventory Reservation Integration

**Description**: The system MUST integrate with the inventory management system to reserve stock atomically with order creation and release reservations on cancellation or payment failure. Reservations MUST expire automatically after a configurable timeout.

**Relates To**: BR-003, UC-1

**Acceptance Criteria**:

- [ ] Given an order creation request, when processed, then an inventory reservation is attempted before payment authorisation; if reservation fails, the order is rejected with INSUFFICIENT_STOCK
- [ ] Given a cancelled or payment-failed order, when processed, then the inventory reservation is released within 60 seconds
- [ ] Given an inventory system outage during order creation, when the system detects unavailability, then order creation is rejected cleanly with appropriate error; no partial order state is persisted

**Priority**: MUST_HAVE

**Complexity**: HIGH

**Dependencies**: INT-003 (inventory integration)

---

#### FR-011: Logistics Partner Dispatch and Tracking

**Description**: The system MUST send dispatch instructions to logistics partners via a real-time API (replacing the current SFTP batch) and receive delivery status events from partners in real time. Multiple logistics partners MUST be supported via a common integration pattern.

**Relates To**: BR-008, UC-2, Principle 13 (`ARC-000-PRIN-v1.0`)

**Acceptance Criteria**:

- [ ] Given an order transitioning to PROCESSING state, when processed, then a dispatch instruction is sent to the assigned logistics partner API within 60 seconds
- [ ] Given a delivery status event from a logistics partner, when received, then the corresponding order state is updated within 5 minutes
- [ ] Given a logistics partner API outage, when a dispatch instruction cannot be sent, then it is held in a durable queue and retried with exponential backoff; operator is alerted after 3 failed retries
- [ ] Given a new logistics partner onboarding, when their API is registered in configuration, then orders can be dispatched to them without code changes

**Priority**: MUST_HAVE

**Complexity**: HIGH

**Dependencies**: INT-004 (logistics integration)

---

#### FR-012: Payment Authorisation and Capture Integration

**Description**: The system MUST integrate with the payment gateway to perform payment authorisation at order confirmation and payment capture at dispatch. Failed authorisations and captures MUST trigger defined compensating actions.

**Relates To**: BR-004, UC-1

**Acceptance Criteria**:

- [ ] Given a valid order submission, when payment authorisation is requested, then a response (success or failure) is received and processed within 10 seconds; order does not wait beyond this timeout
- [ ] Given payment authorisation success, when the order transitions to CONFIRMED, then the authorisation token is stored securely and never logged in plaintext
- [ ] Given payment capture failure at dispatch, when detected, then the order is flagged for manual finance review; dispatch is not blocked pending review flag

**Priority**: MUST_HAVE

**Complexity**: HIGH

**Dependencies**: INT-002 (payment gateway integration), NFR-SEC-004 (secrets management)

---

#### FR-013: ERP / Finance System Order-to-Cash Integration

**Description**: The system MUST publish financial order events (order confirmed, order cancelled, refund initiated) to the ERP/finance system in real time via event-driven integration, replacing the current nightly batch file exchange.

**Relates To**: BR-002, Principle 14 (`ARC-000-PRIN-v1.0`)

**Acceptance Criteria**:

- [ ] Given an order state change with financial significance (confirmed, cancelled, refunded), when processed, then the corresponding financial event is published to the ERP integration topic within 5 minutes
- [ ] Given an ERP integration failure, when detected, then undelivered events are held in a dead-letter queue and retried; Finance team is alerted for events older than 30 minutes
- [ ] Given a month-end close report, when generated, then it is reconciled automatically against the new platform event stream with no manual intervention required

**Priority**: MUST_HAVE

**Complexity**: HIGH

**Dependencies**: INT-001 (ERP integration)

---

#### FR-014: Returns and Refund Processing

**Description**: The system MUST support return initiation, RMA generation, receipt confirmation, and refund calculation and initiation. Return eligibility rules MUST be configurable per order type without code deployment.

**Relates To**: BR-007, UC-4

**Acceptance Criteria**:

- [ ] Given a delivered order within the configured return window, when a return is initiated, then an RMA reference is generated and provided to the customer within 60 seconds
- [ ] Given a warehouse receipt confirmation for a return, when processed, then a refund is initiated to the original payment method within 2 business days
- [ ] Given a return eligibility rule change, when applied, then it takes effect for new return requests without a code deployment

**Priority**: MUST_HAVE

**Complexity**: HIGH

---

#### FR-015: Order Notifications (Customer and Internal)

**Description**: The system MUST send automated notifications to customers at key order lifecycle events and to internal teams for operational alerts. Notification templates MUST be configurable without code deployment.

**Relates To**: BR-007, UC-1, UC-2

**Channels**: Email (customer), SMS (customer, optional), webhook (B2B customers), internal chat/email (operational alerts)

**Acceptance Criteria**:

- [ ] Given an OrderConfirmed event, when published, then a confirmation notification is sent to the customer within 5 minutes
- [ ] Given an OrderDispatched event, when published, then a dispatch notification with tracking reference is sent to the customer within 5 minutes
- [ ] Given a notification template update, when saved via admin interface, then the new template is used for subsequent notifications without code deployment

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-016: Anti-Corruption Layer for Legacy System Integration

**Description**: The system MUST implement an anti-corruption layer (ACL) for all integration with the legacy order management system during the dual-running migration period. The ACL MUST translate between legacy and modern data models without leaking legacy concepts into the modern domain.

**Relates To**: BR-001, Principle 15 (`ARC-000-PRIN-v1.0`)

**Acceptance Criteria**:

- [ ] Given a data entity from the legacy system, when translated by the ACL, then the resulting modern domain object contains no legacy field names, status codes, or error codes
- [ ] Given a legacy status code update, when received, then the ACL maps it to the correct modern order state within the defined mapping registry
- [ ] Given the ACL translation registry, when a legacy field has no modern equivalent, then the ACL logs a mapping warning and uses the defined default; no unmapped fields propagate to the modern domain

**Priority**: MUST_HAVE (Phase 1)

**Complexity**: HIGH

---

#### FR-017: Legacy Data Migration

**Description**: The system MUST migrate complete order history from the legacy system including all orders, line items, payment records, and audit events. Migration MUST be repeatable, validatable, and reversible per phase.

**Relates To**: BR-001, BR-005, Principle 11 (`ARC-000-PRIN-v1.0`)

**Acceptance Criteria**:

- [ ] Given a migration run, when complete, then a reconciliation report is generated comparing legacy record counts to migrated record counts by order state and date range; variance above 0.01% blocks phase sign-off
- [ ] Given a migration script, when re-run against the same source data, then the result is identical (idempotent)
- [ ] Given a migration run failure, when detected, then the migration halts and a rollback to the pre-migration state is completed automatically; no partial records remain in the new system

**Priority**: MUST_HAVE

**Complexity**: HIGH

---

#### FR-018: Operator Dashboard and Operational Metrics

**Description**: The system MUST provide an operator-facing dashboard displaying real-time order processing metrics including order volume, queue depths, error rates, and integration health status.

**Relates To**: BR-003, Principle 6 (`ARC-000-PRIN-v1.0`)

**Acceptance Criteria**:

- [ ] Given the operator dashboard, when viewed, then it displays: orders per hour (current vs. 7-day average), exception queue depth, integration health status for each connected system, and current order state distribution — all refreshed at 60-second intervals or less
- [ ] Given an integration health status change (any partner to DEGRADED or DOWN), when detected, then it is reflected on the dashboard within 2 minutes and an alert is sent to the configured channel

**Priority**: MUST_HAVE

**Complexity**: MEDIUM

---

#### FR-019: Admin Configuration Interface

**Description**: The system MUST provide an authenticated admin interface enabling authorised users to manage configurable business rules (return windows, cancellation eligibility, notification templates, logistics partner routing) without code deployment.

**Relates To**: FR-014, FR-015, FR-011

**Acceptance Criteria**:

- [ ] Given an admin user with the CONFIGURATION role, when they update a return window rule, then the new rule applies to all subsequent return requests within 5 minutes; existing in-progress returns are not affected
- [ ] Given an admin configuration change, when saved, then an audit record is created with the admin user identity, timestamp, field changed, previous value, and new value

**Priority**: SHOULD_HAVE

**Complexity**: MEDIUM

---

#### FR-020: Bulk Order Import (B2B)

**Description**: The system SHOULD support bulk order submission via API for B2B enterprise customers, processing multiple orders in a single request with per-order success/failure reporting.

**Relates To**: BR-007, FR-003

**Acceptance Criteria**:

- [ ] Given a bulk order import request containing up to 500 orders, when submitted, then each order is processed independently; a per-order success/failure response is returned
- [ ] Given a bulk import where 5 of 100 orders fail validation, when processed, then the 95 valid orders are confirmed and the 5 failures are returned with specific error details; the batch is not rolled back

**Priority**: SHOULD_HAVE

**Complexity**: MEDIUM

---

---

## Non-Functional Requirements

### Performance Requirements

#### NFR-P-001: Order Submission Response Time

**Requirement**: Order creation API MUST respond within 3 seconds at the 95th percentile under normal load. Order status query API MUST respond within 1 second at the 99th percentile.

**Measurement Method**: Application performance monitoring (APM) tracking p50, p95, p99 latency per endpoint; load tested before each phase go-live

**Load Conditions**:

- Normal load: 500 concurrent API consumers; 200 order submissions per minute
- Peak load: 1,500 concurrent consumers; 600 order submissions per minute (3× normal, seasonal surge model)
- Data volume: 10M+ order records in primary tables by Year 2

**Targets**:

- Order creation: p95 < 3 seconds, p99 < 5 seconds at peak load
- Order status query: p99 < 1 second at peak load
- Order search: p95 < 2 seconds for queries spanning up to 90 days

**Priority**: CRITICAL

**Stakeholder**: VP Operations, VP Commercial (G-3, G-4; Principle 16 `ARC-000-PRIN-v1.0`)

---

#### NFR-P-002: Order Processing Throughput

**Requirement**: The platform MUST sustain a minimum throughput of 600 order submissions per minute at peak load and MUST scale to 1,800 orders per minute (3× peak) without architectural changes.

**Scalability**: Horizontal scaling MUST add capacity linearly — doubling compute instances MUST increase throughput by at least 80% of the theoretical double (accounting for coordination overhead).

**Priority**: HIGH

**Stakeholder**: VP Operations, CTO (Principle 3 `ARC-000-PRIN-v1.0`)

---

### Availability and Resilience Requirements

#### NFR-A-001: Order Processing Uptime SLA

**Requirement**: The order processing platform MUST achieve 99.9% monthly uptime for all order creation, confirmation, and status query operations from Month 12 onwards. During Phases 1 and 2 (Months 1–11), the minimum uptime target on the new platform components is 99.5%.

- 99.9% uptime = maximum 43.8 minutes unplanned downtime per month
- Planned maintenance windows permitted between 02:00–06:00 local time on weekdays; maximum 4-hour window, maximum twice per month; must be pre-announced 5 business days in advance

**Priority**: CRITICAL

**Stakeholder**: VP Operations, Executive Sponsor (G-3; Principle 17 `ARC-000-PRIN-v1.0`)

---

#### NFR-A-002: Disaster Recovery

**RPO (Recovery Point Objective)**: Maximum 15 minutes of order data loss in any failure scenario. Orders confirmed before the failure event MUST be recoverable.

**RTO (Recovery Time Objective)**: Order processing tier must be restored within 4 hours of a complete platform failure. Order status read-only tier must be restored within 2 hours.

**Backup Requirements**:

- Continuous replication of order data to a geographically separate location
- Point-in-time recovery capability with minimum 15-minute granularity
- Backup retention: 7 years for order records (regulatory); 90 days for application logs

**Failover**:

- Automated failover for availability zone failures — no manual intervention required
- Regional failover may require manual initiation but must complete within the 4-hour RTO
- DR failover tested at minimum quarterly; results documented and reviewed by VP Operations

**Priority**: CRITICAL

**Stakeholder**: VP Operations, CISO (Principle 17 `ARC-000-PRIN-v1.0`)

---

#### NFR-A-003: Fault Tolerance and Graceful Degradation

**Requirement**: The system MUST gracefully degrade when non-critical dependencies fail. Order placement and confirmation MUST remain available even if notification services, analytics pipelines, or reporting systems are unavailable.

**Resilience Patterns Required**:

- [ ] Circuit breaker for every external integration (logistics, payment, ERP, notification)
- [ ] Retry with exponential backoff and jitter for transient failures (max 3 retries, max 30-second delay)
- [ ] Timeout on all outbound network calls (configurable per integration; default: 5 seconds)
- [ ] Bulkhead isolation: order processing capacity not shared with reporting or analytics workloads
- [ ] Dead-letter queue for all event consumers with alerting on queue depth threshold

**Degraded Mode**: If payment gateway is degraded, order creation enters a PENDING hold state with customer notification. Orders MUST NOT be silently lost.

**Priority**: CRITICAL

**Stakeholder**: VP Operations (Principle 4 `ARC-000-PRIN-v1.0`)

---

### Scalability Requirements

#### NFR-S-001: Horizontal Scaling

**Requirement**: All order processing components MUST scale horizontally by adding instances without code changes, configuration overhaul, or database schema changes.

**Growth Projections**:

- Year 1: 200 orders/minute average; 600 orders/minute peak
- Year 2: 300 orders/minute average; 900 orders/minute peak (50% growth)
- Year 3: 400 orders/minute average; 1,200 orders/minute peak (33% growth year-on-year)

**Scaling Triggers**: Auto-scale when CPU utilisation exceeds 70% or request queue depth exceeds 200 for 60 consecutive seconds

**Priority**: HIGH

**Stakeholder**: CTO, VP Operations (Principle 3 `ARC-000-PRIN-v1.0`)

---

#### NFR-S-002: Data Volume Scaling

**Requirement**: The platform MUST support a minimum of 50 million order records by Year 3 without degradation in query performance below the targets in NFR-P-001.

**Data Archival Strategy**: Orders older than 2 years move to warm storage (queryable, slower retrieval acceptable — p95 < 10 seconds); orders older than 7 years move to cold archival (not queryable via UI; available for compliance extraction).

**Priority**: HIGH

---

### Security Requirements

#### NFR-SEC-001: Authentication

**Requirement**: All human access to the order management platform MUST authenticate via the organisation's identity provider using industry-standard federated authentication protocols. Multi-factor authentication MUST be enforced for all operator, admin, and API management interfaces.

**Session Management**:

- Inactivity timeout: 30 minutes for operator web interfaces
- Absolute session timeout: 8 hours for all sessions
- Re-authentication required for: admin configuration changes, bulk data exports, payment reconciliation operations

**Priority**: CRITICAL

**Stakeholder**: CISO (Principle 5 `ARC-000-PRIN-v1.0`)

---

#### NFR-SEC-002: Authorisation

**Requirement**: The system MUST implement role-based access control (RBAC) with the principle of least privilege. Service accounts MUST be scoped to a single service's required permissions. No wildcard or overly-broad permission assignments permitted.

**Roles (minimum)**:

- ORDER_READ: Read-only order status and history
- ORDER_OPERATOR: Full order management operations (no config changes)
- ORDER_ADMIN: Configuration management and bulk operations
- INTEGRATION_SERVICE: Machine-to-machine integration (scoped per service)
- AUDIT_READ: Audit trail read access (compliance, legal)

**Priority**: CRITICAL

**Stakeholder**: CISO (Principle 5 `ARC-000-PRIN-v1.0`)

---

#### NFR-SEC-003: Data Encryption

**Requirement**: All data MUST be encrypted in transit and at rest. Payment tokens and customer PII MUST have application-level field encryption in addition to storage encryption.

**Encryption Requirements**:

- [ ] Data in transit: industry-standard transport encryption for all service-to-service and external communication
- [ ] Data at rest: all data stores and backup media encrypted with managed keys
- [ ] Payment token fields: application-level encryption; plaintext never written to any log or storage layer
- [ ] Key management: all encryption keys managed through a dedicated secrets/key management service; no hardcoded keys

**Priority**: CRITICAL

**Stakeholder**: CISO, Head of Compliance (Principle 5 `ARC-000-PRIN-v1.0`)

---

#### NFR-SEC-004: Secrets Management

**Requirement**: No secrets (API keys, database credentials, certificates, payment gateway tokens) MUST appear in source code, configuration files committed to version control, container images, or application logs. All secrets MUST be retrieved at runtime from a secrets management service.

**Acceptance Criteria**:

- [ ] Automated secret scanning runs in CI pipeline on every commit; any detected secret causes pipeline failure
- [ ] All integration credentials rotated at minimum every 90 days; rotation does not require application downtime
- [ ] Service accounts use short-lived credentials where supported by the target service

**Priority**: CRITICAL

**Stakeholder**: CISO (Principle 5 `ARC-000-PRIN-v1.0`)

---

#### NFR-SEC-005: Vulnerability Management

**Requirement**: All components MUST be free of critical and high-severity known vulnerabilities at the time of production deployment. Dependency and container scanning MUST run in the CI/CD pipeline as a mandatory quality gate.

**Remediation SLA**:

- Critical vulnerabilities: patched and deployed within 24 hours of disclosure
- High vulnerabilities: patched within 7 days
- Medium vulnerabilities: patched within 30 days

**Testing**:

- Dependency scanning (SCA): every build
- Static application security testing (SAST): every build
- Dynamic application security testing (DAST): every release candidate
- Penetration test: annually by qualified external party; additionally before major phase go-lives

**Priority**: CRITICAL

**Stakeholder**: CISO (BR-004; Principle 5 `ARC-000-PRIN-v1.0`)

---

### Compliance Requirements

#### NFR-C-001: PCI-DSS Compliance

**Requirement**: All components within PCI-DSS scope MUST be designed, implemented, and operated in compliance with PCI-DSS requirements applicable to the organisation's merchant level. Re-certification on the new platform MUST be achieved by Month 8.

**Compliance Requirements**:

- [ ] Payment card data never stored beyond authorisation token (no PAN, CVV, or expiry stored in any system log or database)
- [ ] Network segmentation isolates payment processing components from other workloads
- [ ] Audit logging of all access to payment-adjacent systems (who, what, when, result)
- [ ] QSA (Qualified Security Assessor) engaged by Month 5 for re-certification audit planning

**Priority**: CRITICAL

**Stakeholder**: CISO, Head of Compliance, CFO (BR-004; SD-6, SD-7)

---

#### NFR-C-002: GDPR Data Subject Rights

**Requirement**: The system MUST implement technical controls supporting all applicable GDPR data subject rights including right of access, right to erasure (right to be forgotten), right to portability, and right to rectification for customer personal data.

**Requirements**:

- [ ] Subject Access Request: all personal data attributable to a data subject queryable and exportable within the system in < 5 business days end-to-end (BR-005)
- [ ] Right to erasure: personal data fields erasable in compliance with retention obligations; legal hold flag prevents erasure for records under legal hold; automated confirmation of erasure completion
- [ ] Data portability: personal order data exportable in machine-readable format (JSON or CSV) on request
- [ ] Retention schedules: automated deletion of personal data after defined retention period (financial records: 7 years; marketing data: per consent terms)

**Priority**: CRITICAL

**Stakeholder**: Head of Compliance (BR-005; SD-7)

---

#### NFR-C-003: Immutable Audit Logging

**Requirement**: All order state changes, authentication events, admin configuration changes, and data access events MUST be recorded in an immutable, tamper-evident audit log. Audit logs MUST be retained for a minimum of 7 years.

**Audit Log Contents**:

- Actor identity (user ID or service name)
- Action performed
- Timestamp (UTC, millisecond precision)
- Resource affected (order ID, configuration key)
- Previous state / value
- New state / value
- Correlation ID / request ID
- Source IP or service endpoint
- Result (success / failure with error code)

**Integrity**: Audit records protected against modification — no UPDATE or DELETE operations permitted via any application or database interface; integrity verifiable via cryptographic means or equivalent

**Retention**: Security and audit logs: 7 years; Application logs: 90 days (minimum)

**Priority**: CRITICAL

**Stakeholder**: CISO, Head of Compliance, Internal Audit (Principle 8 `ARC-000-PRIN-v1.0`)

---

### Maintainability Requirements

#### NFR-M-001: Observability

**Requirement**: All platform components MUST emit structured telemetry (logs, metrics, distributed traces) sufficient to diagnose any production incident without requiring direct database or system access.

**Telemetry Requirements**:

- **Logging**: Structured JSON logs; correlation ID and order ID on every log line; log level configurable at runtime without restart
- **Metrics**: Request rate, error rate, latency percentiles (p50, p95, p99) per endpoint; queue depth per consumer; integration health per partner — all emitted in a standard metrics format compatible with the organisation's monitoring stack
- **Tracing**: Distributed trace context propagated across all service calls; full order creation-to-delivery trace reconstructable from trace data
- **Alerting**: SLO-based alerting with documented, actionable runbooks for each alert

**Business Metrics (required)**:
- Orders created/confirmed/cancelled/delivered per hour
- Order processing error rate per order type
- Integration success rate per partner

**Priority**: HIGH

**Stakeholder**: VP Operations, CTO (Principle 6 `ARC-000-PRIN-v1.0`)

---

#### NFR-M-002: Operational Documentation

**Requirement**: All services MUST have current operational runbooks covering: deployment, rollback, common failure modes and recovery, scaling procedures, and backup/restore.

**Requirements**:

- [ ] Runbooks for top 10 anticipated failure scenarios created before each phase go-live
- [ ] API documentation (OpenAPI specification) published and current for all external-facing APIs
- [ ] Architecture diagrams (C4 context and container level) maintained and reviewed at each phase gate
- [ ] All runbooks validated by VP Operations team before production use

**Priority**: HIGH

---

#### NFR-M-003: Infrastructure as Code

**Requirement**: All infrastructure MUST be defined as version-controlled code deployed through automated pipelines. No manual infrastructure changes in production environments.

- [ ] 100% of production infrastructure reproducible from code in version control
- [ ] Infrastructure drift detection alerts within 4 hours of any manual change detected
- [ ] Complete environment (new platform, equivalent to production) provisionable from code in under 2 hours

**Priority**: HIGH

**Stakeholder**: CTO (Principle 19 `ARC-000-PRIN-v1.0`)

---

### Interoperability Requirements

#### NFR-I-001: API Standards

**Requirement**: All externally consumed APIs MUST follow standard design conventions: versioned via URL path (e.g., `/v1/`), consistent error response schema, standard HTTP status codes, and documented via an OpenAPI 3.x specification published before the API is exposed to consumers.

**Versioning**: Breaking changes MUST be introduced in a new major version; previous version supported for minimum 12 months after new version GA. Non-breaking changes permitted in minor versions without new major version.

**Priority**: HIGH

**Stakeholder**: CTO, Logistics Partners (Principle 13 `ARC-000-PRIN-v1.0`)

---

#### NFR-I-002: Event Schema Versioning

**Requirement**: All domain events published to the event bus MUST have a schema registered in a schema registry. Schema evolution MUST follow backward-compatible rules; breaking schema changes require a new event type version and a migration plan for existing consumers.

**Priority**: HIGH

**Stakeholder**: CTO, Engineering Teams (Principle 14 `ARC-000-PRIN-v1.0`)

---

## Integration Requirements

### INT-001: ERP / Finance System Integration

**Purpose**: Replace the current nightly SFTP batch file exchange with real-time event-driven integration, eliminating the 1,200 monthly manual reconciliation events and enabling accurate real-time financial reporting.

**Integration Type**: Event-driven (publish; ERP consumes order financial events from event bus)

**Data Exchanged**:

- From Order Platform to ERP: OrderConfirmed (revenue recognition trigger), OrderCancelled (revenue reversal), RefundInitiated (liability event), RefundCompleted (cash movement)
- From ERP to Order Platform: Payment settlement confirmation (for reconciliation)

**Integration Pattern**: Asynchronous event publication; ERP acts as consumer from the order event bus topic

**Authentication**: Service-to-service mutual authentication via secrets management service

**Error Handling**: Events held in dead-letter queue on ERP consumer failure; Finance team alerted for events older than 30 minutes; maximum 72-hour retention before escalation to manual reconciliation

**SLA**: Event delivery within 5 minutes of order event; 99.5% delivery success rate

**Owner**: Finance / ERP team

**Priority**: MUST_HAVE (Phase 2)

---

### INT-002: Payment Gateway Integration

**Purpose**: Process payment authorisation at order confirmation and payment capture at dispatch; handle refund initiation for returns.

**Integration Type**: Real-time synchronous API (authorisation/capture); asynchronous webhook (settlement notifications)

**Data Exchanged**:

- From Order Platform to Gateway: Authorisation request (amount, currency, payment method token), capture request, void request, refund request
- From Gateway to Order Platform: Authorisation result, capture confirmation, settlement notification, dispute notification

**Integration Pattern**: Synchronous request/response for authorisation and capture; webhook events for settlement and disputes

**Authentication**: API key via secrets management service; webhook signature verification

**Error Handling**: Timeout after 10 seconds on authorisation calls; circuit breaker after 5 consecutive failures; payment token never logged

**SLA**: Authorisation response within 10 seconds; 99.9% gateway availability assumed (SLA from gateway provider)

**Owner**: Finance / Payment team

**Priority**: MUST_HAVE (Phase 1 — in PCI-DSS scope)

---

### INT-003: Inventory Management System Integration

**Purpose**: Reserve inventory atomically with order creation; release reservations on cancellation; receive stock availability updates.

**Integration Type**: Synchronous API (reservation request/response); event subscription (stock level updates)

**Data Exchanged**:

- From Order Platform to IMS: Reservation request (SKU, quantity, order ID), release request
- From IMS to Order Platform: Reservation confirmation with expiry, stock level events (low stock, restock)

**Integration Pattern**: Synchronous for reservation (within order creation transaction context); asynchronous events for stock level updates

**Error Handling**: IMS unavailability causes order creation rejection (not silent failure); reservation requests not retried if IMS is unavailable (reject order, do not retry with stale inventory state)

**SLA**: Reservation API response within 2 seconds; reservation confirmed within 1 second (p95)

**Owner**: Inventory / Warehouse team

**Priority**: MUST_HAVE (Phase 1)

---

### INT-004: Logistics / Fulfillment Partner Integration

**Purpose**: Replace nightly SFTP batch dispatch files with real-time API dispatch instructions; receive real-time delivery tracking events from logistics partners.

**Integration Type**: Real-time REST API (dispatch instructions); webhooks or polling (delivery events)

**Supported Partners (initial)**: Primary 3PL (existing); secondary 3PL (existing); future partners via self-service onboarding

**Data Exchanged**:

- From Order Platform to Partner: Dispatch instruction (order ID, items, delivery address, SLA tier, special instructions)
- From Partner to Order Platform: Dispatch acknowledgement, tracking number, IN_TRANSIT event, OUT_FOR_DELIVERY event, DELIVERED event, DELIVERY_FAILED event

**Integration Pattern**: Outbound: synchronous API call with durable retry queue on failure. Inbound: webhook endpoint with signature verification; events published to internal order event bus

**Partner Onboarding**: New partners onboarded via configuration (API endpoint, auth method, event mapping) without code deployment

**Authentication**: Per-partner API key or OAuth 2.0; inbound webhooks verified via HMAC signature

**Error Handling**: Failed dispatch instructions retried with exponential backoff (max 3 retries); operator alerted after 3 failures; dead-letter queue for undeliverable events

**SLA**: Dispatch instruction sent within 60 seconds of order entering PROCESSING state; delivery event reflected in order status within 5 minutes of receipt

**Owner**: Operations / Logistics team

**Priority**: MUST_HAVE (Phase 2 — required for order-to-ship SLA target)

---

### INT-005: CRM / Customer Notification Integration

**Purpose**: Synchronise order status to the CRM for customer service agent visibility; trigger customer notification workflows on order lifecycle events.

**Integration Type**: Event-driven (order events published; CRM and notification service consume)

**Data Exchanged**:

- From Order Platform to CRM: All order lifecycle events with customer ID linkage
- From Order Platform to Notification Service: OrderConfirmed, OrderDispatched, OrderDelivered, OrderCancelled, ReturnCompleted events with customer contact details

**Integration Pattern**: Asynchronous event subscription; notification service handles channel routing (email, SMS, webhook)

**Error Handling**: Notification failures are non-blocking for order processing (graceful degradation); failed notifications queued for retry; permanent failure alerts to Customer Service lead

**Priority**: SHOULD_HAVE (Phase 2)

---

## Data Requirements

### DR-001: Order Data Model

**Description**: The order data model MUST capture the complete commercial and operational context of each order, be extensible for new order types, and support efficient query by all required access patterns.

**Core Entities**: Order, OrderLineItem, OrderEvent (audit), Customer, DeliveryAddress, PaymentRecord, ReturnRequest, ReturnLineItem, InventoryReservation

**Key Attributes (Order)**:

| Attribute | Type | Required | Description | Classification |
|---|---|---|---|---|
| order_id | UUID | Yes | Immutable unique identifier | INTERNAL |
| external_reference | String(100) | No | Customer/partner order reference | INTERNAL |
| idempotency_key | String(255) | Yes | Duplicate prevention key | INTERNAL |
| channel | Enum | Yes | Submission channel (API/WEB/INTERNAL) | INTERNAL |
| customer_id | UUID | Yes | Link to customer identity | CONFIDENTIAL |
| state | Enum | Yes | Current order state | INTERNAL |
| currency | String(3) | Yes | ISO 4217 currency code | INTERNAL |
| total_amount | Decimal(19,4) | Yes | Order total | CONFIDENTIAL |
| created_at | Timestamp | Yes | UTC creation timestamp | INTERNAL |
| confirmed_at | Timestamp | No | UTC confirmation timestamp | INTERNAL |
| dispatched_at | Timestamp | No | UTC dispatch timestamp | INTERNAL |
| delivered_at | Timestamp | No | UTC delivery timestamp | INTERNAL |

**Data Classification**: Orders contain CONFIDENTIAL data (customer identity, amounts, delivery address); payment tokens are RESTRICTED.

**Data Volume**: Estimated 2M orders per year; 10M total records by Year 3 before archival

**Access Patterns**: Order by ID (high frequency); orders by customer (medium); orders by state (queue management); orders by date range (reporting, migration)

**Data Retention**: Order records retained for 7 years (financial regulation); customer PII fields erasable after retention period or on right-to-erasure request (subject to legal hold)

---

### DR-002: Order Event / Audit Log Data Model

**Description**: Every order state transition and manual action MUST be recorded as an immutable, append-only event record. Event records are never modified or deleted via any application interface.

**Key Attributes**:

| Attribute | Type | Required | Description |
|---|---|---|---|
| event_id | UUID | Yes | Unique event identifier |
| order_id | UUID | Yes | Parent order reference |
| event_type | Enum | Yes | Event type code |
| actor_id | String(255) | Yes | User ID or service name |
| actor_type | Enum | Yes | HUMAN or SERVICE |
| previous_state | Enum | No | State before transition |
| new_state | Enum | Yes | State after transition |
| event_timestamp | Timestamp | Yes | UTC millisecond precision |
| correlation_id | UUID | Yes | Request/trace correlation |
| metadata | JSON | No | Event-specific additional context |

**Data Retention**: 7 years; cold archival after Year 7; no deletion

---

### DR-003: Customer Personal Data

**Description**: The system MUST minimise personal data stored directly in the order management platform. Customer identity is owned by the identity system (integrated via customer_id). The order platform stores only the data required to fulfill and support orders.

**Personal Data Stored**:

- Delivery name and address (CONFIDENTIAL; linked to order, not customer profile)
- Contact email for order notifications (CONFIDENTIAL; reference only)
- Customer ID (pseudonymous reference to identity system)

**GDPR Controls**:

- Delivery name and address: erasable on right-to-erasure request (replaced with [ERASED] marker); order financial record preserved
- Contact email: erasable on right-to-erasure request
- Erasure confirmed by automated report to legal team within 24 hours of processing

**Data Retention**: Delivery address and contact data retained for 2 years after last order; financial order record (amounts, references) retained for 7 years; personal identifying fields erased at retention expiry or on erasure request

---

### DR-004: Legacy Data Migration

**Migration Scope**: All orders created in the legacy system within the past 7 years (financial retention requirement) plus all associated line items, payment records, and status history.

**Estimated Volume**: 5–8 million historical order records; 20–40 million line item records; 15–30 million audit/status events

**Migration Strategy**: Phased extraction and load aligned to migration phases; historical orders migrated in batches by date range; active (non-terminal state) orders migrated last, within the final cutover window

**Data Transformation**:

- Legacy status codes mapped to modern order states via documented mapping registry
- Legacy customer IDs mapped to modern customer_id via identity system lookup
- Legacy field naming conventions mapped to modern domain model via anti-corruption layer (FR-016)
- PAN/payment card data NOT migrated — authorisation tokens from legacy system not transferable; historical payment records stored as financial reference only

**Data Validation**:

- Pre-migration: count and checksum of legacy source records per batch
- Post-migration: reconciliation report comparing source counts to migrated counts; variance > 0.01% blocks phase sign-off
- Business rule validation: no order migrated in an invalid state; legacy status codes without a modern mapping flagged for manual review

**Rollback Plan**: Per-phase rollback; migrated records marked with migration_phase flag enabling targeted deletion; legacy system remains authoritative until phase sign-off

---

### DR-005: Data Quality Requirements

**Completeness**: All required fields (as defined in DR-001 schema) MUST be present for every order record; null values in required fields fail validation at API boundary, not in database

**Consistency**: Order total_amount MUST equal the sum of line item amounts at all times; any discrepancy flagged as a data integrity exception requiring manual review

**Timeliness**:

- Order state in API response MUST reflect the actual state within 5 minutes of last transition
- Financial events delivered to ERP within 5 minutes of order event (NFR for integration SLA)

**Lineage**: Transformation logic for data migration MUST be version-controlled and auditable; each migrated record traceable to its source record in the legacy system via legacy_order_id reference field

---

### DR-006: Data Classification Register

**Description**: All data elements in the new platform MUST be classified before system design is finalized. Classification determines encryption requirements, access controls, audit requirements, and retention rules.

| Data Category | Classification | Encryption | Access Control | Retention |
|---|---|---|---|---|
| Order ID, state, channel | INTERNAL | In-transit only | ORDER_READ and above | 7 years |
| Order amounts, line items | CONFIDENTIAL | In-transit + at-rest | ORDER_OPERATOR and above | 7 years |
| Customer delivery address | CONFIDENTIAL | In-transit + at-rest | ORDER_OPERATOR and above; erasable | 2 years |
| Payment authorisation token | RESTRICTED | In-transit + at-rest + field-level | ORDER_ADMIN, payment service only | Duration of authorisation only |
| Audit log records | INTERNAL | In-transit + at-rest | AUDIT_READ; immutable | 7 years |
| Integration credentials | RESTRICTED | Secrets vault | INTEGRATION_SERVICE (per service) | Rotated every 90 days |

---

## Constraints and Assumptions

### Technical Constraints

**TC-1**: The existing customer identity and authentication platform is out of scope for replacement; the new order management platform MUST integrate with it via its existing API.

**TC-2**: Payment gateway provider is a contractual incumbent for the duration of the programme; the integration MUST use the incumbent provider's current API version.

**TC-3**: The new platform MUST be deployed on the organisation's approved cloud provider (AWS), in the eu-west-1 or eu-west-2 regions to satisfy data residency requirements.

**TC-4**: All infrastructure changes MUST be deployable via the organisation's existing CI/CD toolchain; introduction of new toolchain components requires CTO approval.

**TC-5**: Legacy order management system MUST remain operational and fully supported during all migration phases until formal decommission sign-off.

---

### Business Constraints

**BC-1**: PCI-DSS re-certification deadline at Month 8 is fixed — it cannot be extended without regulatory consequence. Programme phasing MUST accommodate this constraint.

**BC-2**: The dual-running period (legacy + new platform simultaneously) must not exceed Month 18 for the core order processing functions; cost model does not sustain dual licensing beyond this point.

**BC-3**: No customer-visible service degradation during any migration phase. Any phase that degrades order processing availability below the legacy 99.0% baseline MUST be halted and rolled back.

**BC-4**: All data migrated from the legacy system must remain within the existing data residency footprint; no migration of personal data outside current jurisdictions.

---

### Assumptions

**A-1**: Legacy system data quality is sufficient for automated migration with < 5% records requiring manual remediation. If data quality assessment in Month 1 reveals > 5% requiring remediation, the migration timeline will be re-baselined.

**A-2**: Logistics partners will engage migration planning within 60 days of API preview distribution. If partners are unresponsive after 60 days, a compatibility adapter maintains SFTP integration through Month 18 at programme cost.

**A-3**: The inventory management system exposes a real-time reservation API capable of 600+ requests per minute. If the IMS cannot support this throughput, a caching layer will be required (adds Phase 1 scope).

**A-4**: Payment gateway supports the existing PCI-DSS merchant level on the new platform without requiring a separate PCI-DSS assessment for the gateway integration itself.

**A-5**: Engineering team capacity is protected at a minimum of 70% allocation to the modernization programme; legacy maintenance does not exceed 30% of engineering team time.

---

## Success Criteria and KPIs

### Business Success Metrics

| Metric | Baseline | Target | Timeline | Measurement Method |
|---|---|---|---|---|
| Order platform uptime | 99.0% (trailing 12 months) | >= 99.9% | Month 12+ | Application monitoring |
| Order-to-ship time (standard) | 48 hours average | 24 hours average | Month 18 | Order management analytics |
| Manual reconciliation events/month | ~1,200 | < 100 | Month 24 | Finance team count |
| MTTR (order processing incidents) | ~3 hours | < 30 minutes | Month 12 | Incident tracking system |
| Feature delivery lead time | 8 weeks | 2 weeks | Month 18 | CI/CD pipeline metrics |
| Order error rate | Baseline in Month 1 | -80% vs. baseline | Month 18 | Order analytics |
| Customer NPS (order experience) | Baseline in Month 1 | Baseline +15 | Month 18 | Quarterly surveys |
| Annual OMS TCO | Year 0 baseline | -30% | Month 24 | Finance sign-off |
| SAR fulfillment time | 47 days | < 5 days | Month 12 | Legal team SLA log |
| High-severity security findings | 3 open | 0 open | Month 8 | Security tracker |

---

### Technical Success Metrics

| Metric | Target | Measurement Method |
|---|---|---|
| Order creation API p95 latency | < 3 seconds at peak load | APM tooling |
| Order status API p99 latency | < 1 second | APM tooling |
| Order processing error rate | < 0.1% of transactions | Log aggregation |
| Deployment frequency | Daily (from Month 12) | CI/CD metrics |
| Change failure rate | < 10% (from Month 12) | Incident tracking |
| Integration delivery success rate | > 99.5% per partner | Integration monitoring |
| Infrastructure drift | 0 untracked changes | IaC drift detection |

---

## Requirement Conflicts & Resolutions

### Conflict C-1: Delivery Speed (CFO) vs. Migration Risk Tolerance (VP Operations)

**Conflicting Requirements**:

- **BR-002**: 30% TCO reduction by Month 24 — requires minimizing dual-running period (every additional month of parallel operation increases cost)
- **NFR-A-001**: 99.9% uptime; **BC-3**: No customer-visible degradation — VP Operations requires extended stabilization windows between phases before committing to cutover

**Stakeholders Involved**:

- **CFO**: Wants compressed migration timeline to minimize dual-running costs and hit ROI targets early
- **VP Operations**: Wants extended stabilization (8+ weeks per phase) due to legacy incident history; distrusts migration timelines that look good on paper

**Nature of Conflict**: CFO's cost targets require migrations phases to complete within 6-week windows including stabilization. Operations' risk tolerance requires 8–12-week stabilization periods. Cannot satisfy both without a mechanism change.

**Trade-off Analysis**:

| Option | Pros | Cons | Impact |
|---|---|---|---|
| **Option 1**: Prioritise speed (6-week phases) | CFO targets met; earlier TCO savings | Higher risk of forced rollback; Operations disengagement | CFO satisfied; Operations resistant |
| **Option 2**: Prioritise stability (12-week phases) | Lower risk; Operations confidence | Month 24 TCO target missed; extended dual-running cost | Operations satisfied; CFO budget exposure |
| **Option 3**: Objective exit criteria (agreed metrics, not fixed weeks) | Both satisfied when criteria met; incentivises quality | Requires upfront alignment on criteria; still uncertain timeline | Both somewhat satisfied |

**Resolution Strategy**: COMPROMISE — Option 3

**Decision**: Phase stabilization windows are governed by objective exit criteria agreed in Month 1 (uptime >= 99.5%, error rate < 0.5% of order volume, zero data integrity events, rollback tested) rather than fixed calendar periods. Minimum stabilization: 3 weeks per phase; maximum: 6 weeks before Operations must either approve or formally escalate with documented technical reason.

**Decision Authority**: Executive Sponsor (with Steering Committee input); documented in programme governance charter Month 1.

**Impact on Requirements**: NFR-A-001 exit criteria added as explicit phase gate checklist in `ARC-001-STKE-v1.0` governance section; BR-002 TCO timeline has ±2-month buffer built in contingency.

**Stakeholder Management**:

- **CFO**: Month 1 briefing on contingency budget for extended dual-running; 4-week buffer included in cost model
- **VP Operations**: Named co-author of phase exit criteria in Month 1; escalation path documented and time-bounded (5 business days)

---

### Conflict C-2: PCI-DSS Deadline (Compliance) vs. Technical Readiness (Engineering)

**Conflicting Requirements**:

- **BR-004**: PCI-DSS re-certification by Month 8 — fixed external deadline
- **FR-016** / **FR-017**: Anti-corruption layer design and data migration must be validated before PCI-DSS components are migrated

**Stakeholders Involved**:

- **Head of Compliance / CISO**: Month 8 deadline is immovable; failure has regulatory and financial consequence
- **CTO / Engineering**: Anti-corruption layer for PCI-DSS scoped components may not be production-ready by Month 7 if the design review is not completed by Month 2

**Nature of Conflict**: PCI-DSS scoped components may be more complex than other order components. Rushing them into Phase 1 to meet the certification deadline risks insufficient testing and a poor-quality anti-corruption layer.

**Resolution Strategy**: PHASE — with parallel track

**Decision**: PCI-DSS scoped component migration is treated as a parallel workstream within Phase 1, not deferred to Phase 2. A dedicated engineering squad focuses exclusively on PCI-DSS components from Month 1. If the squad determines by Month 3 that components cannot safely be migrated by Month 7, the Head of Compliance engages the QSA immediately to agree an interim compensating control extension on the legacy platform — this is the documented contingency plan, not a surprise.

**Decision Authority**: CISO and Head of Compliance (with Executive Sponsor notification)

**Impact on Requirements**: BR-004 acceptance criteria include a Month 3 checkpoint: "PCI-DSS scoped components migration feasibility confirmed or compensating control plan agreed with QSA."

---

### Conflict C-3: Engineering Capacity — Legacy Maintenance vs. New Platform Build

**Conflicting Requirements**:

- **BR-006**: Reduce feature delivery lead time to 2 weeks — requires maximum engineering focus on new platform
- **BC-5** (implied): Legacy system must remain stable during migration — requires engineering support for legacy maintenance and incidents

**Resolution Strategy**: INNOVATE — ring-fenced teams

**Decision**: A dedicated legacy maintenance squad (minimum 2 engineers; backfilled from contractor budget if needed) is ring-fenced before programme start. They handle all legacy maintenance and incidents. Modern platform team does not rotate into legacy maintenance during programme phases. CTO owns escalation if legacy incidents exceed maintenance squad capacity. This is a cost item explicitly budgeted in the programme business case.

**Decision Authority**: CTO (with CFO budget approval for contractor backfill)

---

## Timeline and Milestones

| Milestone | Description | Target | Dependencies |
|---|---|---|---|
| M-1: Programme Baseline | TCO baseline agreed; Phase exit criteria agreed; Engineering squads confirmed; PCI-DSS scope identified | Month 1 | Business case approved |
| M-2: Data Classification | All data entities classified; GDPR/PCI scope confirmed; Legacy data quality assessed | Month 2 | M-1 |
| M-3: Phase 1 Go-Live | Order creation and capture live on new platform; legacy handles fulfillment; ACL operational | Month 6 | M-2; Anti-corruption layer design approved |
| M-4: PCI-DSS Migration | PCI-DSS scoped components migrated; QSA audit submitted | Month 7 | M-3 |
| M-5: PCI-DSS Re-Certification | QSA re-certification letter received | Month 8 | M-4 |
| M-6: Phase 2 Go-Live | Fulfillment, dispatch, logistics API integration live; real-time status API live; customer portal launched | Month 12 | M-3; logistics partner API migration |
| M-7: Phase 3 Go-Live | ERP integration live; reporting and analytics migrated; 100% volume on new platform | Month 18 | M-6 |
| M-8: Legacy Decommission | Legacy platform decommissioned; 30% TCO reduction confirmed | Month 24 | M-7; 3 consecutive months at 99.9% uptime |

---

## Dependencies

| Dependency | Description | Owner | Target Date | Status | Impact if Delayed |
|---|---|---|---|---|---|
| Identity system API | New platform integrates with existing customer identity API; interface spec required | Identity team | Month 2 | Not started | HIGH — blocks FR-003 |
| Payment gateway API access | API credentials and sandbox environment for new integration | Finance / Payment team | Month 1 | Not started | HIGH — blocks FR-012, BR-004 |
| Logistics partner API agreement | Primary 3PL API specification and sandbox access | Operations / Logistics team | Month 3 | Not started | HIGH — blocks FR-011 |
| IMS throughput validation | Confirmation that IMS can sustain 600+ reservation requests/minute | Inventory / Warehouse team | Month 2 | Not started | MEDIUM — may require caching layer in Phase 1 |
| QSA engagement | QSA appointed for PCI-DSS re-certification planning | Head of Compliance | Month 5 | Not started | HIGH — blocks M-5 if late |
| Legacy data quality assessment | Full assessment of data quality in legacy system | Engineering (migration squad) | Month 2 | Not started | MEDIUM — informs migration timeline |

---

## Approval

### Requirements Review

| Reviewer | Role | Status | Date | Comments |
|---|---|---|---|---|
| Executive Sponsor | Programme authority | Pending | | |
| CFO / Finance Director | Financial accountability | Pending | | |
| VP Operations | Operational sign-off | Pending | | |
| CISO | Security review | Pending | | |
| Head of Compliance | Regulatory review | Pending | | |
| Enterprise Architect | Technical review | Pending | | |

### Sign-Off

By signing below, stakeholders confirm that requirements are complete, understood, and approved to proceed to design phase.

| Stakeholder | Signature | Date |
|---|---|---|
| Executive Sponsor | _________ | |
| CTO / CIO | _________ | |
| Enterprise Architect | _________ | |

---

## Appendices

### Appendix A: Glossary

| Term | Definition |
|---|---|
| ACL | Anti-Corruption Layer — architectural pattern isolating the modern domain model from the legacy system's data structures |
| ERP | Enterprise Resource Planning — the organisation's core finance and operations system |
| IMS | Inventory Management System |
| OMS | Order Management System |
| PAN | Primary Account Number — the credit/debit card number; never stored in the OMS |
| RMA | Return Merchandise Authorisation |
| RPO | Recovery Point Objective — maximum acceptable data loss |
| RTO | Recovery Time Objective — maximum acceptable time to restore service |
| SAR | Subject Access Request — GDPR right of access request |
| 3PL | Third-Party Logistics provider |
| TCO | Total Cost of Ownership |

### Appendix B: Reference Documents

- `ARC-001-STKE-v1.0` — Stakeholder Drivers & Goals Analysis
- `ARC-000-PRIN-v1.0` — Enterprise Architecture Principles

---

## External References

### Document Register

| Doc ID | Filename | Type | Source Location | Description |
|---|---|---|---|---|
| *None provided* | — | — | — | No external specification documents supplied at generation time. Place legacy system specs, RFP documents, or user research in `projects/001-order-management-modernization/external/` and re-run. |

### Citations

| Citation ID | Doc ID | Page/Section | Category | Quoted Passage |
|---|---|---|---|---|
| — | — | — | — | — |

---

**Generated by**: ArcKit `/arckit:requirements` command
**Generated on**: 2026-05-23 GMT
**ArcKit Version**: 5.0.4
**Project**: Legacy Order Management Modernization (Project 001)
**AI Model**: Claude Sonnet 4.6
**Generation Context**: Requirements derived from ARC-001-STKE-v1.0 (stakeholder goals G-1 through G-6, outcomes O-1 through O-4, drivers SD-1 through SD-12, conflicts C-1 through C-3) and ARC-000-PRIN-v1.0 (21 architecture principles). No external specification documents were available.
