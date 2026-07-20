# Non-functional Requirements Specification — Shopping Cart Module

Source: source-documents/source-material.md and repository BA documents

This document collects non-functional requirements (NFRs) for the Shopping Cart module. Each NFR entry includes: NFR ID, Category, Requirement Statement, Measurement/Acceptance Target, Rationale, Source, Priority, Verification Method, Status, and Notes.

Important: The internship report references a target "under 200ms" for some feedback timings. This is recorded below as a draft target. "Draft target from internship document – Needs stakeholder and technical confirmation." It is not presented as an approved SLA or measured value.

---

## 1. Performance

### NFR-CART-01
- Category: Performance
- Requirement Statement: User interactions that update cart quantities or remove items must not require a full page reload; UI updates should be incremental (partial update) to reflect changes.
- Measurement/Acceptance Target: Inventory of interactions (increase/decrease/remove) result in visible UI update within 200ms perceived feedback for the control and full updated totals within 1.5s on a typical 4G connection. Draft target from internship document – Needs stakeholder and technical confirmation.
- Rationale: Minimizes disruption to user flow, improves perceived responsiveness, and reduces unnecessary bandwidth and rendering cost.
- Source: source-documents/source-material.md (functional overview and internship notes).
- Priority: High
- Verification Method: Manual UI tests and automated end-to-end tests measuring DOM update latency and end-to-end response time on simulated network conditions; test cases TC_UPD_01 and TC_UI_01.
- Status: Draft from internship report
- Notes: The 200ms figure is a draft note from the internship report and must be validated with engineers and stakeholders before being used as an SLA.

### NFR-CART-02
- Category: Performance / Scalability
- Requirement Statement: The cart subsystem must be able to handle bursts of concurrent updates (e.g., many users updating cart items) without visible UI errors or data loss; server-side components should be horizontally scalable.
- Measurement/Acceptance Target: No data-loss/errors for expected baseline load; no more than 1% error rate under projected peak load (projected peak load to be provided). Needs stakeholder confirmation for exact load numbers.
- Rationale: Prepares the system for realistic traffic and prevents user impact during peak periods.
- Source: Derived requirement based on project scope and future extensibility needs (proposed from portfolio and internship context).
- Priority: Medium
- Verification Method: Load testing with defined traffic profiles once traffic profile is provided; monitoring error rates and successful update rates during tests.
- Status: Proposed for portfolio
- Notes: Requires inventory of expected concurrent users and traffic profile from stakeholders/engineering.

---

## 2. Reliability

### NFR-CART-03
- Category: Reliability
- Requirement Statement: Cart state must not be lost during rapid successive user operations (quick repeated increase/decrease/remove actions); operations must be applied in correct order or reconciled to avoid inconsistent totals.
- Measurement/Acceptance Target: 100% of standard test scenarios (including rapid user actions simulated by TC_UPD_01) complete without state inconsistency; reconciliation or conflict resolution applied when concurrent updates occur.
- Rationale: Prevents incorrect billing and poor UX due to race conditions.
- Source: Internship notes referencing "Không mất dữ liệu khi thao tác nhanh" and functional test cases.
- Priority: High
- Verification Method: Concurrency and race-condition tests, automated scenario scripts simulating rapid clicks, and manual exploratory testing.
- Status: Draft from internship report
- Notes: Implementation strategy (client-side queuing, optimistic UI, server reconciliation) to be agreed with technical team.

---

## 3. Usability

### NFR-CART-04
- Category: Usability
- Requirement Statement: UI shall provide clear, immediate feedback for quantity changes, removal actions, and errors (e.g., validation messages when attempting invalid quantities).
- Measurement/Acceptance Target: All interactive controls must provide visible feedback within 200ms for control-level response (Draft target from internship document – Needs stakeholder and technical confirmation); error messages must be descriptive and actionable.
- Rationale: Clear feedback reduces user confusion and error recovery time.
- Source: source-documents/source-material.md (functional overview) and internship notes.
- Priority: High
- Verification Method: UX review, usability testing with representative users, and TC_UI_01.
- Status: Draft from internship report
- Notes: Copy/text for messages and tone to be approved by product/stakeholder.

---

## 4. Compatibility

### NFR-CART-05
- Category: Compatibility
- Requirement Statement: Shopping Cart functionality must operate correctly on modern desktop and mobile browsers used by target users (desktop Chrome/Edge, mobile Chrome on Android, Safari on iOS). Progressive enhancement approach should be applied so core actions work if JavaScript is degraded.
- Measurement/Acceptance Target: Core cart flows (view, increase/decrease, remove, clear, proceed to checkout) pass on the latest two major versions of target browsers and a common set of mobile devices.
- Rationale: Ensures broad user coverage across devices and browsers.
- Source: Internship notes: “Hoạt động trên desktop và mobile.”
- Priority: High
- Verification Method: Cross-browser testing matrix, device lab/manual tests, and automated UI tests on emulators.
- Status: Draft from internship report
- Notes: Exact list of supported browsers/devices to be confirmed with stakeholders.

---

## 5. Responsiveness

### NFR-CART-06
- Category: Responsiveness
- Requirement Statement: UI updates and recalculation of item totals and cart subtotal must happen without full page reload and with minimal perceived delay when users adjust quantities.
- Measurement/Acceptance Target: Visual acknowledgment of the user action within 200ms (Draft target from internship document – Needs stakeholder and technical confirmation); recalculation and display of updated totals within 1.5s on a typical 4G connection.
- Rationale: Improves perceived performance and conversion by keeping users engaged.
- Source: source-documents/source-material.md and internship notes.
- Priority: High
- Verification Method: Measured DOM update times and end-to-end tests under simulated network conditions; TC_UPD_01 and TC_UI_01.
- Status: Draft from internship report
- Notes: Implementation may rely on client-side computation for immediate feedback with server reconciliation.

---

## 6. Data Integrity

### NFR-CART-07
- Category: Data Integrity
- Requirement Statement: Calculations for item total and cart subtotal must be accurate and consistent across client and server; rounding rules and currency handling must be specified and followed.
- Measurement/Acceptance Target: Calculation discrepancies must be zero for canonical test data; rounding behavior documented and consistent.
- Rationale: Prevents financial errors and disputes.
- Source: source-documents/source-material.md ("Dữ liệu tính tiền chính xác").
- Priority: High
- Verification Method: Unit tests for calculation functions, end-to-end tests with representative pricing (including taxes/discounts if applicable), and TC_UI_01.
- Status: Draft from internship report
- Notes: Exact rounding rules and currency code/format need stakeholder confirmation (listed under Items Needing Confirmation).

---

## 7. Validation

### NFR-CART-08
- Category: Validation
- Requirement Statement: The system must prevent invalid quantities (e.g., negative numbers, zero, non-integer values) from being accepted and persisted.
- Measurement/Acceptance Target: UI and API validation prevent invalid quantities; attempts to submit invalid quantities must be rejected with a clear error message. Automated tests must cover integer/non-integer/negative/zero inputs.
- Rationale: Ensures data quality and prevents erroneous order processing.
- Source: source-documents/source-material.md ("Không ghi quantity không hợp lệ").
- Priority: High
- Verification Method: Unit and integration tests on validation logic; TC_UPD_01.
- Status: Confirmed in source
- Notes: Validation rules (e.g., integer-only) to be codified with engineering.

---

## 8. Security

### NFR-CART-09
- Category: Security
- Requirement Statement: Sensitive payment or authentication data must not be stored in the cart state on the client; the cart must not expose sensitive user credentials. Security controls must follow organization policies.
- Measurement/Acceptance Target: No sensitive payment data stored in cart payloads; security review confirms compliance with organizational policy. Exact standards (e.g., PCI-DSS) are not assumed and must be confirmed if required.
- Rationale: Reduces risk of data leakage and compliance issues.
- Source: Internship notes (security listed as a NFR area) — draft. No explicit security standard provided in source documents.
- Priority: High
- Verification Method: Security review, code inspection, and security testing.
- Status: Draft from internship report / Needs stakeholder confirmation
- Notes: Do not assume PCI or other standards without stakeholder confirmation.

---

## 9. Maintainability

### NFR-CART-10
- Category: Maintainability
- Requirement Statement: Cart code and integration points should be modular, documented, and instrumented to support debugging, monitoring, and future feature changes (e.g., inventory limits, promotions).
- Measurement/Acceptance Target: Internal documentation exists for data contracts and major functions; automated tests cover critical flows. Code review checklists include maintainability criteria.
- Rationale: Lowers long-term support cost and enables faster iteration.
- Source: Proposed for portfolio based on internship context and expected developer handoff.
- Priority: Medium
- Verification Method: Documentation review, test coverage metrics, and code review outcomes.
- Status: Proposed for portfolio
- Notes: Level of required documentation and test coverage targets to be agreed with engineering leads.

---

## 10. Accessibility

### NFR-CART-11
- Category: Accessibility
- Requirement Statement: The Shopping Cart UI should meet at least WCAG 2.1 AA standards for key interactive components (controls for quantity change, remove, clear, and proceed to checkout) unless stakeholders specify otherwise.
- Measurement/Acceptance Target: Key cart pages score against automated accessibility checks with remediation items tracked; manual verification for keyboard navigation and screen reader usage for core flows.
- Rationale: Ensures inclusivity for users with disabilities and reduces legal/regulatory risk.
- Source: Internship notes (NFR list included Accessibility) — exact level not specified in source.
- Priority: Medium
- Verification Method: Accessibility audits (automated + manual), and acceptance testing for core flows.
- Status: Needs stakeholder confirmation
- Notes: Specific WCAG level (e.g., AA) is proposed but must be confirmed by stakeholders.

---

## 11. Items Needing Confirmation

A collated list of items that require stakeholder and/or technical confirmation before these NFRs can be finalized:

1. Exact numeric targets for performance: whether the "under 200ms" draft target should be adopted and whether the 1.5s figure is acceptable as end-to-end update latency.
2. Supported browsers and versions / device matrix for compatibility testing.
3. Load/traffic profiles for scalability and performance tests (expected concurrent users, peak requests per second).
4. Rounding rules, currency code, and display format for prices (locale specifics).
5. Inventory management behavior when user increases quantity beyond available stock (business rule and UX).
6. Security standards required (e.g., whether PCI-DSS applies) and any organizational policies to follow.
7. Accessibility standard target (e.g., WCAG 2.1 AA) to be confirmed by stakeholders.

---

References:
- source-documents/source-material.md (project source material)
- docs/SRS-shopping-cart.md (System-level mapping)
- User Stories and Test Cases in docs/

Status legend:
- Confirmed in source — explicitly present and supported by source material
- Draft from internship report — recorded in internship deliverables but not finalized
- Proposed for portfolio — recommended by BA for future-proofing and handoff
- Needs stakeholder confirmation — requires stakeholder / technical inputs
