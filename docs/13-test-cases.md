# Test Cases — Shopping Cart Module

Source: source-documents/source-material.md, docs/* (BA deliverables)

Execution Status default: Not Executed / Needs confirmation (unless source provides explicit evidence of execution).

---

## TC_UI_01
- Test Case ID: TC_UI_01
- Title: Shopping Cart UI — Display and Empty-cart State
- Objective: Verify that the Shopping Cart page displays products with correct fields (image, name, unit price, quantity, item total), shows cart subtotal, and displays an empty-cart state with appropriate call-to-action when no items exist.
- Related Requirement: FR-CART-01, FR-CART-04, FR-CART-08
- Related Acceptance Criteria: AC-CART-01.01 (Cần xác nhận detail)
- Test Type: UI Testing / Functional Testing
- Priority: High
- Preconditions:
  - User has a valid session (or guest session) and at least one product in cart for main flow; additional scenario: cart is empty.
  - Test environment configured with test products and deterministic pricing data.
- Test Data:
  - Product A: unit price 100, quantity 2
  - Product B: unit price 50, quantity 1
  - Empty cart scenario: no products
- Test Steps:
  1. Navigate to Shopping Cart page.
  2. Observe product list: image, name, unit price, quantity control, item total for each product.
  3. Verify cart subtotal equals sum of item totals.
  4. Clear cart (if present) to reach empty-cart state or use an account with empty cart.
  5. Verify empty-cart message and presence of "Continue shopping" or equivalent CTA.
- Expected Result:
  - All product details are visible and correct; item totals and subtotal calculate correctly; empty-cart state displays expected message and CTA.
- Actual Result: N/A — Not executed
- Execution Status: Not Executed / Needs confirmation
- Notes: Source documents reference these checks but do not provide execution evidence. See TC_UI_01 mapping in SRS and RTM.

---

## TC_UI_02
- Test Case ID: TC_UI_02
- Title: Order Note Input — Length and Persistence
- Objective: Verify Order Note field accepts up to 256 characters, prevents entry beyond limit, and persists note with the order/cart.
- Related Requirement: FR-CART-05, BR-CART-02
- Related Acceptance Criteria: AC-CART-01.01 (Order Note <=256 chars)
- Test Type: Validation Testing / UI Testing
- Priority: Medium
- Preconditions:
  - Shopping Cart contains at least one product.
  - Test account or environment allows entering and saving order notes.
- Test Data:
  - Valid note: 100-character text
  - Boundary note: 256-character text
  - Invalid note: 257-character text
- Test Steps:
  1. Open Shopping Cart with at least one item.
  2. Enter Valid note (100 chars) and save/leave page; reopen cart and verify persistence.
  3. Enter Boundary note (256 chars) and attempt to save; verify acceptance.
  4. Enter Invalid note (257 chars) and verify UI prevents input or shows validation error.
- Expected Result:
  - Notes up to 256 chars accepted and persisted; 257+ chars rejected or truncated with clear feedback.
- Actual Result: N/A — Not executed
- Execution Status: Not Executed / Needs confirmation
- Notes: BR-CART-02 is specified in source material; implementation of persistence/storage needs confirmation.

---

## TC_UI_03
- Test Case ID: TC_UI_03
- Title: Clear Cart Confirmation Dialog
- Objective: Verify that "Clear cart" action prompts a confirmation dialog and that cancel and confirm behave appropriately.
- Related Requirement: FR-CART-07, BR-CART-03
- Related Acceptance Criteria: AC-CART-01.01 (Clear cart requires confirmation)
- Test Type: UI Testing / Negative Testing
- Priority: High
- Preconditions:
  - Shopping Cart contains multiple items.
- Test Data:
  - Cart with >1 items (Product A, Product B)
- Test Steps:
  1. Navigate to Shopping Cart.
  2. Click "Clear cart".
  3. Observe confirmation dialog.
  4. Click "Cancel" — verify cart remains unchanged.
  5. Click "Clear cart" again; click "Confirm" and verify cart is emptied and empty-cart state shown.
- Expected Result:
  - Confirmation dialog appears; cancel preserves cart; confirm empties cart and updates UI.
- Actual Result: N/A — Not executed
- Execution Status: Not Executed / Needs confirmation
- Notes: Source specifies this Business Rule; no evidence of execution.

---

## TC_UPD_01
- Test Case ID: TC_UPD_01
- Title: Quantity Update — Increase and Decrease Basic Flow
- Objective: Verify increasing and decreasing product quantity updates item total and cart subtotal; decreasing does not allow quantity < 1.
- Related Requirement: FR-CART-02, FR-CART-03, BR-CART-01, FR-CART-04
- Related Acceptance Criteria: AC-CART-01.01
- Test Type: Functional Testing / Validation Testing
- Priority: High
- Preconditions:
  - Shopping Cart contains at least one product with quantity >=1.
- Test Data:
  - Product A: unit price 100, initial quantity 1
- Test Steps:
  1. Open Shopping Cart.
  2. Increase quantity of Product A to 2; observe item total and subtotal update.
  3. Decrease quantity back to 1; observe update.
  4. Attempt to decrease quantity below 1 (e.g., from 1 to 0); verify system prevents action and shows validation message.
- Expected Result:
  - Quantity changes reflected in item total and subtotal; cannot reduce below 1; appropriate feedback shown.
- Actual Result: N/A — Not executed
- Execution Status: Not Executed / Needs confirmation
- Notes: Matches TC_UPD_01 referenced in BA docs. Inventory limit behavior (max) is "Cần xác nhận" and not part of this test.

---

## TC_UPD_02
- Test Case ID: TC_UPD_02
- Title: Quantity Update — Rapid Interaction and Concurrency
- Objective: Verify cart consistency when a user performs rapid successive updates (multiple quick increases/decreases) to the same item.
- Related Requirement: NFR-CART-03 (Reliability), FR-CART-02, BR-CART-01
- Related Acceptance Criteria: AC-CART-01.01
- Test Type: Stress Interaction Testing / Data Synchronization Testing
- Priority: High
- Preconditions:
  - Shopping Cart contains at least one product; test environment supports automation of rapid UI events or API calls.
- Test Data:
  - Product A: unit price 100, initial quantity 1
- Test Steps:
  1. Open Shopping Cart.
  2. Perform rapid sequence of increases (e.g., send 10 increase actions in quick succession) via UI or automated script.
  3. Observe final quantity, item total and subtotal.
  4. Repeat with rapid decrease actions including attempts to go below 1.
- Expected Result:
  - Final cart state is consistent and corresponds to applied operations; no data loss or inconsistent totals.
- Actual Result: N/A — Not executed
- Execution Status: Not Executed / Needs confirmation
- Notes: Source states "Không mất dữ liệu khi thao tác nhanh" as requirement; specific reconciliation strategy must be confirmed.

---

## TC_UPD_03
- Test Case ID: TC_UPD_03
- Title: Quantity Validation — Non-integer and Invalid Inputs
- Objective: Verify system prevents non-integer, text, negative, or excessively large quantity inputs.
- Related Requirement: FR-CART-02, NFR-CART-08 (Validation)
- Related Acceptance Criteria: AC-CART-01.01
- Test Type: Validation Testing / Negative Testing
- Priority: High
- Preconditions:
  - Shopping Cart with at least one item; UI supports direct quantity input or API accepts quantity values.
- Test Data:
  - Inputs: "abc", -1, 0, 1.5, 9999999
- Test Steps:
  1. Attempt to set quantity to each invalid input via UI or API.
  2. Observe validation behavior and messages.
- Expected Result:
  - Invalid inputs rejected with clear error messages; only valid integer >=1 accepted.
- Actual Result: N/A — Not executed
- Execution Status: Not Executed / Needs confirmation
- Notes: Confirm whether fractional quantities are allowed (likely not) and if there is a maximum quantity limit.

---

## TC_UPD_04
- Test Case ID: TC_UPD_04
- Title: Client-side vs Server-side Calculation Consistency
- Objective: Verify that item total and cart subtotal calculations performed on the client match server-calculated totals after updates (no rounding discrepancies or mismatch).
- Related Requirement: FR-CART-04, NFR-CART-07 (Data Integrity)
- Related Acceptance Criteria: AC-CART-01.01
- Test Type: Data Synchronization Testing / Functional Testing
- Priority: High
- Preconditions:
  - Test environment where both client and server calculations can be observed/logged.
- Test Data:
  - Product A: unit price 19.99, quantity changes to introduce rounding scenarios (e.g., quantity 3)
- Test Steps:
  1. Update quantity on client and record client-displayed totals.
  2. Trigger server-side reconciliation or reload cart from server and record server totals.
  3. Compare client vs server totals including rounding behavior.
- Expected Result:
  - Client and server totals match within defined rounding rules; no discrepancies.
- Actual Result: N/A — Not executed
- Execution Status: Not Executed / Needs confirmation
- Notes: Rounding rules and currency format must be confirmed (Item in NFRs needing confirmation).

---

## TC_UPD_05
- Test Case ID: TC_UPD_05
- Title: Quantity Update — Inventory Limit Handling
- Objective: Verify behavior when user attempts to increase quantity beyond available inventory (business response and UI behavior).
- Related Requirement: FR-CART-02, UC-CART-01 (Alternate flow A2), NFR items (inventory behavior)
- Related Acceptance Criteria: AC-CART-01.01 (inventory behavior needs confirmation)
- Test Type: Boundary Testing / Negative Testing
- Priority: Medium
- Preconditions:
  - Inventory system or test data available to set product stock to a known limit (e.g., stock = 3).
- Test Data:
  - Product A: unit price 100, stock = 3
- Test Steps:
  1. Attempt to increase Product A quantity to 4 via UI.
  2. Observe UI and system response: error message, limit enforcement, backorder option, etc.
- Expected Result:
  - System enforces inventory constraints according to stakeholder-defined policy (e.g., prevents increase and displays message). If backordering allowed, appropriate flow shown.
- Actual Result: N/A — Not executed
- Execution Status: Not Executed / Needs confirmation
- Notes: Inventory policy is marked "Cần xác nhận" in source and must be clarified.

---

## TC_DEL_01
- Test Case ID: TC_DEL_01
- Title: Remove Single Item — UI and Totals Update
- Objective: Verify removing a single product updates the cart UI and recalculates item totals and cart subtotal correctly.
- Related Requirement: FR-CART-06, FR-CART-04
- Related Acceptance Criteria: AC-CART-01.01
- Test Type: Functional Testing / UI Testing
- Priority: High
- Preconditions:
  - Shopping Cart contains at least two products.
- Test Data:
  - Product A (100, qty 1), Product B (50, qty 1)
- Test Steps:
  1. Open Shopping Cart.
  2. Remove Product A using the UI control.
  3. Verify Product A is removed and cart subtotal updated accordingly.
- Expected Result:
  - Product removed; remaining products displayed; subtotal equals remaining item totals.
- Actual Result: N/A — Not executed
- Execution Status: Not Executed / Needs confirmation
- Notes: Matches TC_DEL_01 referenced in BA docs.

---

## TC_DEL_02
- Test Case ID: TC_DEL_02
- Title: Remove Single Item — Undo/Recover (if supported)
- Objective: If the UI supports undo for deletion, verify undo restores the item and totals; if not supported, verify appropriate messaging.
- Related Requirement: FR-CART-06
- Related Acceptance Criteria: AC-CART-01.01 (undo behavior not specified)
- Test Type: Usability Testing / Negative Testing
- Priority: Low
- Preconditions:
  - Shopping Cart with at least two items.
- Test Data:
  - Product A, Product B
- Test Steps:
  1. Remove Product A.
  2. If an "Undo" option appears, click Undo and verify Product A is restored and totals revert.
  3. If no Undo option, verify deletion is final and UI communicates permanence.
- Expected Result:
  - Undo restores item if feature exists; otherwise user is clearly informed deletion is final.
- Actual Result: N/A — Not executed
- Execution Status: Not Executed / Needs confirmation
- Notes: Undo behavior not described in source; this test is contingent on product decision.

---

## TC_DEL_03
- Test Case ID: TC_DEL_03
- Title: Remove Item During Rapid Updates
- Objective: Verify removing an item while rapid quantity updates or concurrent sessions are occurring does not create inconsistent cart state.
- Related Requirement: NFR-CART-03 (Reliability), FR-CART-06
- Related Acceptance Criteria: AC-CART-01.01
- Test Type: Stress Interaction Testing / Data Synchronization Testing
- Priority: High
- Preconditions:
  - Shopping Cart with the target item present; test harness capable of simulating concurrent updates.
- Test Data:
  - Product A, initial qty 2
- Test Steps:
  1. Start rapid update sequence increasing Product A quantity.
  2. While updates are in-flight, issue a Remove Product A action.
  3. Observe resulting cart state and server records.
- Expected Result:
  - Cart state is consistent (product removed or updates reconciled in defined order); no ghost items or incorrect totals.
- Actual Result: N/A — Not executed
- Execution Status: Not Executed / Needs confirmation
- Notes: Requires technical orchestration to simulate concurrency.

---

## TC_DEL_04
- Test Case ID: TC_DEL_04
- Title: Clear Cart via API and UI Consistency
- Objective: Verify that clearing the cart via API or alternate client is reflected in the UI across sessions/devices and vice versa.
- Related Requirement: FR-CART-07, NFR-CART-03 (Data Synchronization)
- Related Acceptance Criteria: AC-CART-01.01
- Test Type: Data Synchronization Testing / Functional Testing
- Priority: Medium
- Preconditions:
  - User with cart present, ability to perform API calls in test environment.
- Test Data:
  - Cart with multiple items
- Test Steps:
  1. Clear cart via API call for the test user.
  2. Refresh or open Shopping Cart UI in another session/device and verify the cart is emptied.
  3. Conversely, clear cart in UI and verify API reflects empty cart.
- Expected Result:
  - Cart state is synchronized across API and UI; no stale data shown.
- Actual Result: N/A — Not executed
- Execution Status: Not Executed / Needs confirmation
- Notes: Requires API test environment and session synchronization behavior confirmation.

---

# Test Coverage Summary

- Requirements covered by test cases:
  - FR-CART-01: TC_UI_01
  - FR-CART-02/03: TC_UPD_01, TC_UPD_02, TC_UPD_03, TC_UPD_04, TC_UPD_05
  - FR-CART-04: TC_UI_01, TC_UPD_04
  - FR-CART-05: TC_UI_02
  - FR-CART-06: TC_DEL_01, TC_DEL_02, TC_DEL_03
  - FR-CART-07: TC_UI_03, TC_DEL_04
  - FR-CART-08: TC_UI_01
  - FR-CART-09 (Proceed to Checkout): covered partially by TC_UI_01 (flow to Checkout needs confirmation)
  - NFR-CART-03 (Reliability): TC_UPD_02, TC_DEL_03
  - NFR-CART-07 (Data Integrity): TC_UPD_04
  - NFR-CART-08 (Validation): TC_UPD_03

Notes: Coverage is mapped to functional and non-functional requirements where appropriate. Several NFRs require additional test definitions once stakeholders confirm targets (e.g., performance SLA, supported browsers, inventory limits).

---

# Requirement Coverage Gaps

1. Performance SLA verification: No explicit performance/load tests defined because stakeholder numeric targets (e.g., traffic profiles, confirmed 200ms target) are missing. (Gap: NFR-CART-01, NFR-CART-02, NFR-CART-06)
2. Cross-device/session synchronization under real-world conditions: limited coverage until API/session behavior is specified. (Gap: FR-CART-09, TC_DEL_04 needs execution and environment)
3. Rounding/currency and tax/discount scenarios: Detailed financial edge-cases and rounding scenarios not fully covered (Gap: NFR-CART-07, FR-CART-04).
4. Accessibility test cases (keyboard navigation, screen-reader flows) are not present and must be added once accessibility targets are confirmed. (Gap: NFR-CART-11)
5. Security-focused negative testing (e.g., tampered API calls, injection attempts) for cart operations not covered. (Gap: NFR-CART-09)

---

# Proposed Additional Test Cases

These are new test cases proposed to address identified gaps. They are not present in the original BA report and are suggestions for completeness.

## PTC_PERF_01 — Performance: Perceived Feedback Latency
- Objective: Measure perceived feedback time for quantity control UI (per draft 200ms target) and end-to-end update times under defined network profiles.
- Rationale: Validates the draft performance target recorded in the internship report.
- Priority: High
- Notes: Requires stakeholder agreement on the exact performance target and test environment.

## PTC_LOAD_01 — Load/Scalability: Concurrent Cart Updates
- Objective: Load test server-side cart update endpoints with projected peak RPS to validate error rates and behavior under load.
- Rationale: Ensures system can scale without data loss.
- Priority: High
- Notes: Requires traffic profile from stakeholders.

## PTC_INV_01 — Inventory Limit and Backorder Scenarios
- Objective: Validate behavior when requested quantity exceeds available inventory, including backorder or reservation policies.
- Rationale: Business rules for inventory are marked "Cần xác nhận" and need explicit tests.
- Priority: High
- Notes: Requires inventory policy confirmation.

## PTC_ACC_01 — Accessibility: Keyboard and Screen Reader Flow
- Objective: Verify core cart flows (quantity change, remove, clear, proceed to checkout) are operable via keyboard and usable with screen readers.
- Rationale: Fulfills accessibility NFR once level is confirmed.
- Priority: Medium
- Notes: Requires target WCAG level confirmation.

## PTC_SEC_01 — Security: API Tampering and Authorization
- Objective: Verify cart modification endpoints require proper authorization and are resilient to tampered client inputs.
- Rationale: Ensures cart cannot be manipulated by unauthorized clients.
- Priority: High
- Notes: Requires security acceptance criteria from stakeholders.

## PTC_ROUND_01 — Financial Rounding and Discount Edge Cases
- Objective: Validate rounding rules across combinations of quantities, discounts, and taxes to ensure consistent totals.
- Rationale: Addresses data integrity gap for monetary calculations.
- Priority: High
- Notes: Needs rounding, tax and discount rules from stakeholders.

---

# Notes on Execution Status

- All test cases above are marked "Not Executed / Needs confirmation" by default because the provided source documents (source-material.md and BA deliverables) do not provide explicit execution evidence for any individual test case.
- If you can supply test execution logs, CI results, or test reports, I will update the Actual Result and Execution Status fields accordingly.

---

References:
- source-documents/source-material.md
- docs/SRS-shopping-cart.md
- docs/12-non-functional-requirements.md

