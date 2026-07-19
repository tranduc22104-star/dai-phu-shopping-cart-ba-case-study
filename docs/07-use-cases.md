# Use Cases - Shopping Cart Module
## Đại Phú E-commerce

---

## 1. Document Purpose

Tài liệu này định nghĩa chi tiết **Use Cases (UC)** cho module Giỏ hàng. Mỗi Use Case mô tả một kịch bản hoàn chỉnh từ khi khách hàng bắt đầu cho đến khi hoàn thành mục tiêu.

**Format Use Case:**
- **Basic Flow**: Happy path (kịch bản bình thường)
- **Alternative Flows**: Các biến thể (lựa chọn khác nhau)
- **Exception Flows**: Trường hợp lỗi/ngoại lệ

---

## 2. Use Case Catalog

| UC ID | Use Case Name | Primary Actor | Goal |
|-------|---------------|---------------|------|
| **UC-CART-01** | View and Manage Shopping Cart | Customer | Display cart contents and manage items |
| **UC-CART-02** | Update Product Quantity | Customer | Increase/decrease quantity with real-time updates |
| **UC-CART-03** | Add Order Note | Customer | Capture special requests/delivery instructions |
| **UC-CART-04** | Remove One Product | Customer | Delete single product from cart |
| **UC-CART-05** | Remove All Products | Customer | Clear entire cart with confirmation |
| **UC-CART-06** | Proceed to Checkout Information | Customer | Handoff from cart to checkout module |

---

## 3. Use Case: UC-CART-01

### 3.1. Use Case Overview

| Attribute | Value |
|-----------|-------|
| **UC ID** | UC-CART-01 |
| **Use Case Name** | View and Manage Shopping Cart |
| **Goal** | Customer can view all products in cart with details (name, price, quantity, total) and navigate to modify or checkout |
| **Primary Actor** | Customer (Khách hàng) |
| **Supporting Actors** | System (Shopping Cart Service), Backend API |
| **Trigger** | Customer clicks "Shopping Cart" link/icon OR navigates to cart URL |

### 3.2. Preconditions

- ✅ Customer has access to the shopping cart page
- ✅ Customer may have products in cart OR cart is empty
- ✅ System has internet connectivity to backend
- ✅ Product catalog data is available

### 3.3. Postconditions

**Success Case:**
- ✅ Cart page is displayed with all products
- ✅ Product information (name, price, qty, total) is current
- ✅ Cart summary (subtotal) is displayed and correct
- ✅ All action buttons available (increase qty, decrease qty, remove, etc.)

**Failure Case:**
- ✅ Error message displayed
- ✅ Cart page still accessible (graceful degradation)

### 3.4. Basic Flow

| Step | Actor | System | Data |
|------|-------|--------|------|
| 1 | Customer | Loads cart page | — |
| 2 | Customer | — | System retrieves cart data from backend |
| 3 | — | System | Displays list of all products in cart with: image, name, unit price, quantity, item total |
| 4 | — | System | Calculates and displays Cart Summary: subtotal (sum of item totals) |
| 5 | — | System | Displays item count: "3 items in cart" |
| 6 | — | System | Displays action buttons: increase qty, decrease qty, remove product, clear all, checkout |
| 7 | Customer | Views cart | Customer reviews all products and totals |
| 8 | Customer | Chooses action (modify qty, add note, remove item, proceed) | UC branches to UC-CART-02, 03, 04, or 06 |

### 3.5. Alternative Flows

**AF-01: Empty Cart**
- Precondition: Cart contains 0 products
- Step 1: System detects empty cart
- Step 2: System displays "Your cart is empty" message
- Step 3: System hides product list, subtotal, checkout button
- Step 4: System shows "Continue Shopping" button
- Step 5: Customer clicks "Continue Shopping" → navigates to product listing

**AF-02: Product No Longer Available**
- Precondition: Product in cart is no longer in catalog
- Step 1: System displays product with strikethrough OR warning icon
- Step 2: System shows message: "This product is no longer available"
- Step 3: System suggests "Remove this item" action
- Step 4: Customer can remove product OR proceed with other items

**AF-03: Price Changed Since Added**
- Precondition: Product price changed after customer added to cart
- Step 1: System recalculates item total with new price
- Step 2: System displays new price (not old price)
- Step 3: Optional: System shows warning "Price changed" (TBD - Cần xác nhận)
- Step 4: Subtotal updated with new totals

### 3.6. Exception Flows

**EF-01: Network Error**
- Precondition: Backend API unavailable OR network timeout
- Step 1: System detects error loading cart data
- Step 2: System displays error message: "Unable to load cart. Please try again."
- Step 3: System shows cached data if available OR empty cart
- Step 4: "Retry" button provided

**EF-02: Data Integrity Issue**
- Precondition: Cart data inconsistent (e.g., quantity mismatch)
- Step 1: System detects inconsistency
- Step 2: System reloads cart data from server
- Step 3: System displays refreshed cart OR error message
- Step 4: Customer notified of issue

### 3.7. Business Rules

| Rule | Reference |
|------|-----------|
| Item Total = Unit Price × Quantity | BR-CART-03 |
| Subtotal = Σ(Item Totals) | BR-CART-04 |
| Prices must be current (not cached) | BR-CART-03 |
| Quantity must be ≥1 | BR-CART-01 |

### 3.8. Related User Flows

| User Flow | Reference |
|-----------|-----------|
| UF-CART-05 | View Cart - Happy Path |
| UF-CART-06 | View Cart with Multiple Products |
| UF-CART-08 | View Cart Summary |
| UF-CART-EC | Empty Cart State |

### 3.9. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **Scope Function** | SC-01 | View products in cart |
| **Scope Function** | SC-02 | Display product information |
| **Scope Function** | SC-06 | Display subtotal |
| **Scope Function** | SC-14 | Display empty-cart state |

### 3.10. Validation Status

| Item | Status |
|------|--------|
| **UC Definition** | ✅ Complete |
| **Flows** | ✅ Complete (Basic + 3 AF + 2 EF) |
| **Business Rules** | ✅ Linked |
| **Requirements** | ✅ Traced |
| **Stakeholder Review** | ⏳ Pending |

### 3.11. Open Questions

| Question | Current Status |
|----------|-----------------|
| Should unavailable products be removed automatically? | Cần xác nhận |
| Should price change notification be shown to customer? | Cần xác nhận |
| How long should cart data be cached? | Cần xác nhận |

---

## 4. Use Case: UC-CART-02

### 4.1. Use Case Overview

| Attribute | Value |
|-----------|-------|
| **UC ID** | UC-CART-02 |
| **Use Case Name** | Update Product Quantity |
| **Goal** | Customer can increase or decrease product quantity in cart with real-time calculation updates |
| **Primary Actor** | Customer |
| **Supporting Actors** | System (Pricing Engine), Backend |
| **Trigger** | Customer clicks "+" button (increase) OR "-" button (decrease) OR edits quantity field directly |

### 4.2. Preconditions

- ✅ Cart page is displayed with products (UC-CART-01 completed)
- ✅ Product quantity currently displayed (≥1)
- ✅ Customer can see increase/decrease buttons
- ✅ Backend pricing service available

### 4.3. Postconditions

**Success Case:**
- ✅ Product quantity updated correctly
- ✅ Item Total recalculated (Unit Price × New Qty)
- ✅ Subtotal recalculated (Σ new Item Totals)
- ✅ Changes persisted to backend
- ✅ Display updated without page refresh

**Failure Case:**
- ✅ Quantity change rejected
- ✅ Error message shown
- ✅ Cart state unchanged

### 4.4. Basic Flow

| Step | Actor | System | Data |
|------|-------|--------|------|
| 1 | Customer | Locates product and clicks "+" button | — |
| 2 | Customer | — | System receives increase quantity request |
| 3 | — | System | Increments quantity by 1 (from Q to Q+1) |
| 4 | — | System | Fetches current Unit Price from backend |
| 5 | — | System | Calculates new Item Total: Unit Price × (Q+1) |
| 6 | — | System | Recalculates Subtotal: Σ(all Item Totals) |
| 7 | — | System | Sends update to backend, persists change |
| 8 | — | System | Updates display in real-time: new quantity, new item total, new subtotal |
| 9 | Customer | Views updated cart | Cart reflects new quantity and totals |

### 4.5. Alternative Flows

**AF-01: Decrease Quantity**
- Precondition: Customer clicks "-" button, quantity currently > 1
- Step 1: System receives decrease quantity request
- Step 2: System decrements quantity by 1 (from Q to Q-1)
- Step 3: Steps 4-9 same as Basic Flow
- Result: Quantity, Item Total, Subtotal all updated

**AF-02: Direct Edit Quantity**
- Precondition: Quantity field is editable (customer types new value)
- Step 1: Customer clears current quantity and types new value (e.g., "5")
- Step 2: System validates input: must be integer, ≥1
- Step 3: If valid: Steps 4-9 same as Basic Flow
- Step 4: If invalid: See Exception Flow EF-02

**AF-03: Rapid Clicks (Debouncing)**
- Precondition: Customer clicks "+" multiple times rapidly
- Step 1: System receives multiple increment requests
- Step 2: System debounces/throttles requests (consolidates into single update)
- Step 3: Backend receives only final quantity value
- Step 4: Display updates once with final result
- Result: No duplicate updates, clean final state

### 4.6. Exception Flows

**EF-01: Quantity = 1 (Minimum Reached)**
- Precondition: Customer clicks "-" when quantity = 1
- Step 1: System detects quantity would go below minimum (1)
- Step 2: System rejects change, shows message: "Minimum quantity is 1. Use 'Remove' to delete."
- Step 3: Quantity remains = 1
- Step 4: Cart unchanged

**EF-02: Invalid Input**
- Precondition: Customer enters non-numeric or zero/negative value
- Step 1: System validates input
- Step 2: If invalid: System shows error "Please enter a valid quantity (whole numbers only, minimum 1)"
- Step 3: Input field highlights red
- Step 4: Quantity reverts to previous valid value
- Step 5: Cart unchanged

**EF-03: Price Changed During Update**
- Precondition: Product price changed on backend while customer is updating qty
- Step 1: System fetches current price
- Step 2: System recalculates with new price
- Step 3: System updates display with new calculation
- Step 4: Optional: Notification "Price updated" (TBD)

**EF-04: Network Error**
- Precondition: Backend save fails (network timeout)
- Step 1: System detects save failed
- Step 2: System reverts quantity to previous value
- Step 3: System shows error: "Update failed. Please try again."
- Step 4: Quantity and totals unchanged
- Step 5: Customer can retry

### 4.7. Business Rules

| Rule | Reference |
|------|-----------|
| Min Qty = 1 | BR-CART-01 |
| Qty must be positive integer | BR-CART-02 |
| Item Total = Unit Price × Qty | BR-CART-03 |
| Subtotal = Σ(Item Totals) | BR-CART-04 |
| Use current/latest prices | BR-CART-03 |

### 4.8. Related User Flows

| User Flow | Reference |
|-----------|-----------|
| UF-CART-10 | Increase Product Quantity |
| UF-CART-11 | Decrease Product Quantity |
| UF-CART-AF1 | Min Qty Reached |
| UF-CART-AF2 | Invalid Quantity Input |

### 4.9. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **Scope Function** | SC-03 | Increase quantity |
| **Scope Function** | SC-04 | Decrease quantity |
| **Scope Function** | SC-05 | Prevent qty < 1 |
| **Scope Function** | SC-06 | Recalculate totals |

### 4.10. Validation Status

| Item | Status |
|------|--------|
| **UC Definition** | ✅ Complete |
| **Flows** | ✅ Complete (Basic + 3 AF + 4 EF) |
| **Qty Validation** | ✅ Covered (min=1, integer, non-negative) |
| **Calculation** | ✅ Covered (item total, subtotal update) |
| **Data Sync** | ✅ Covered (persist to backend) |
| **Rapid Clicks** | ✅ Covered (AF-03 debouncing) |

### 4.11. Open Questions

| Question | Current Status |
|----------|-----------------|
| Should debouncing be immediate or delayed? | Cần xác nhận |
| Should "-" button be disabled at qty=1 or show error message? | Cần xác nhận |
| Is there a maximum quantity per product? | Cần xác nhận |

---

## 5. Use Case: UC-CART-03

### 5.1. Use Case Overview

| Attribute | Value |
|-----------|-------|
| **UC ID** | UC-CART-03 |
| **Use Case Name** | Add Order Note |
| **Goal** | Customer can add a note/special request to the order (e.g., delivery instructions, gift wrap request) |
| **Primary Actor** | Customer |
| **Supporting Actors** | System (Order Note Handler) |
| **Trigger** | Customer clicks "Add Note" / "Order Note" field OR scrolls to order note section |

### 5.2. Preconditions

- ✅ Cart page displayed (UC-CART-01 completed)
- ✅ Order note input field visible (empty or with previous note)
- ✅ Cart contains at least 1 product

### 5.3. Postconditions

**Success Case:**
- ✅ Note text entered and displayed in field
- ✅ Character count updated
- ✅ Note saved with cart data
- ✅ Note persists if customer navigates away and returns
- ✅ Note displayed in order summary before checkout

**Failure Case:**
- ✅ Note exceeding 256 chars rejected or truncated
- ✅ Error message shown if applicable
- ✅ Previous note content preserved

### 5.4. Basic Flow

| Step | Actor | System | Data |
|------|-------|--------|------|
| 1 | Customer | Clicks in order note field | — |
| 2 | Customer | Types note text (e.g., "Giao buổi sáng trước 10 AM") | — |
| 3 | — | System | Validates input in real-time: current length ≤ 256 |
| 4 | — | System | Updates character counter: "23/256" |
| 5 | Customer | Continues typing | Note text accumulates |
| 6 | — | System | Note auto-saved to cart (TBD: auto vs manual save) |
| 7 | Customer | Leaves note field | Note is saved |
| 8 | — | System | Note persisted to backend with cart data |

### 5.5. Alternative Flows

**AF-01: Clear/Delete Note**
- Precondition: Note field contains text
- Step 1: Customer selects all text and deletes (Ctrl+A, Delete)
- Step 2: System detects empty field
- Step 3: Character counter shows "0/256"
- Step 4: Empty note saved to backend
- Result: Note removed from cart

**AF-02: Edit Existing Note**
- Precondition: Cart already contains a note
- Step 1: Note text displayed in field
- Step 2: Customer modifies text (add/remove/change content)
- Step 3: Steps 3-8 same as Basic Flow
- Result: New note text saved, old text replaced

### 5.6. Exception Flows

**EF-01: Note Exceeds 256 Characters**
- Precondition: Customer types or pastes text that exceeds 256 chars
- Step 1: System detects character count > 256
- Step 2: One of the following (TBD - Cần xác nhận):
  - **Option A:** Auto-truncate to 256 chars
  - **Option B:** Show error "Max 256 characters. Please shorten."
  - **Option C:** Block additional input (can't type beyond 256)
- Step 3: Character counter shows "256/256" (or error state)
- Step 4: Only valid text (≤256) saved to backend

**EF-02: Special Characters**
- Precondition: Customer types special characters (emoji, HTML tags, etc.)
- Step 1: System sanitizes input (removes or escapes harmful characters)
- Step 2: Note saved with sanitized text
- Step 3: Display shows cleaned text

### 5.7. Business Rules

| Rule | Reference |
|------|-----------|
| Note max length = 256 characters | BR-NOTE-01 |
| Note is optional (not required) | SC-09 |

### 5.8. Related User Flows

| User Flow | Reference |
|-----------|-----------|
| UF-CART-12 | Add Order Note |
| UF-CART-ON | Order Note Validation |

### 5.9. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **Scope Function** | SC-09 | Order note input |
| **Scope Function** | SC-10 | Order note validation |

### 5.10. Validation Status

| Item | Status |
|------|--------|
| **UC Definition** | ✅ Complete |
| **Flows** | ✅ Complete (Basic + 2 AF + 2 EF) |

---

## 6. Use Case: UC-CART-04

### 6.1. Use Case Overview

| Attribute | Value |
|-----------|-------|
| **UC ID** | UC-CART-04 |
| **Use Case Name** | Remove One Product |
| **Goal** | Customer can delete a single product from cart without confirmation (quick action) |
| **Primary Actor** | Customer |
| **Supporting Actors** | System |
| **Trigger** | Customer clicks "Remove" button for a specific product |

### 6.2. Preconditions

- ✅ Cart page displayed with products (UC-CART-01)
- ✅ Product has visible "Remove" button
- ✅ Cart contains ≥1 product

### 6.3. Postconditions

**Success Case:**
- ✅ Product removed from cart immediately
- ✅ Product row/card disappears from display
- ✅ Subtotal recalculated
- ✅ Item count updated (e.g., "3 items" → "2 items")
- ✅ Change persisted to backend
- ✅ If last item removed: Cart transitions to Empty State (AF-01)

**Failure Case:**
- ✅ Error message displayed
- ✅ Product remains in cart

### 6.4. Basic Flow

| Step | Actor | System | Data |
|------|-------|--------|------|
| 1 | Customer | Identifies product to remove | — |
| 2 | Customer | Clicks "Remove" button for that product | — |
| 3 | — | System | Receives remove request |
| 4 | — | System | Removes product from cart data structure |
| 5 | — | System | Recalculates Subtotal (sum of remaining Item Totals) |
| 6 | — | System | Updates Item Count (e.g., 3 → 2 items) |
| 7 | — | System | Persists change to backend |
| 8 | — | System | Updates display: product row disappears, subtotal updates, item count updates |
| 9 | Customer | Views updated cart | Product removed, totals recalculated |

### 6.5. Alternative Flows

**AF-01: Remove Last Item (Transition to Empty State)**
- Precondition: Cart contains only 1 product, customer clicks "Remove"
- Step 1-4: Same as Basic Flow
- Step 5: Subtotal becomes 0 (or hidden)
- Step 6: Item Count becomes 0 (or hidden)
- Step 7-8: Same as Basic Flow
- Step 9: System transitions to Empty Cart State:
  - Product list hidden
  - "Your cart is empty" message displayed
  - "Checkout" button disabled/hidden
  - "Continue Shopping" button becomes primary action

**AF-02: Undo (if implemented)**
- Precondition: Product just removed, "Undo" button visible
- Step 1: Customer clicks "Undo" within timeout (e.g., 5 seconds)
- Step 2: System restores product to original position
- Step 3: Subtotal recalculated with restored product
- Step 4: Display updated
- Note: TBD if Undo is in scope for Phase 1

### 6.6. Exception Flows

**EF-01: Backend Error**
- Precondition: Backend remove fails (database error, timeout)
- Step 1: System detects error
- Step 2: System reverts cart to previous state (product remains)
- Step 3: Error message displayed: "Failed to remove item. Please try again."
- Step 4: Cart unchanged

### 6.7. Business Rules

| Rule | Reference |
|------|-----------|
| Subtotal recalculates after removal | BR-CART-04 |
| No confirmation required for single item | SC-11 |
| Last item removal triggers empty state | BR-DEL-02 |

### 6.8. Related User Flows

| User Flow | Reference |
|-----------|-----------|
| UF-CART-11 | Remove One Product |
| UF-CART-RM | Remove Product Flow |
| UF-CART-AF4 | Transition to Empty State |

### 6.9. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **Scope Function** | SC-11 | Remove one product |
| **Scope Function** | SC-06 | Recalculate totals |
| **Scope Function** | SC-14 | Display empty state |

### 6.10. Validation Status

| Item | Status |
|------|--------|
| **UC Definition** | ✅ Complete |
| **Flows** | ✅ Complete (Basic + 2 AF + 1 EF) |

---

## 7. Use Case: UC-CART-05

### 7.1. Use Case Overview

| Attribute | Value |
|-----------|-------|
| **UC ID** | UC-CART-05 |
| **Use Case Name** | Remove All Products |
| **Goal** | Customer can clear entire cart with confirmation to prevent accidental deletion |
| **Primary Actor** | Customer |
| **Supporting Actors** | System |
| **Trigger** | Customer clicks "Clear All" / "Remove All" button |

### 7.2. Preconditions

- ✅ Cart page displayed (UC-CART-01)
- ✅ Cart contains ≥1 product
- ✅ "Clear All" button visible

### 7.3. Postconditions

**Success Case (Confirm):**
- ✅ ALL products removed from cart
- ✅ Cart becomes empty (0 products)
- ✅ Empty Cart State displayed
- ✅ Changes persisted to backend
- ✅ Order notes cleared (if any)

**Success Case (Cancel):**
- ✅ Confirmation dialog closed
- ✅ Cart unchanged (all products remain)
- ✅ All quantities, notes, totals unchanged

### 7.4. Basic Flow

| Step | Actor | System | Data |
|------|-------|--------|------|
| 1 | Customer | Locates and clicks "Clear All" button | — |
| 2 | — | System | Displays confirmation dialog |
| 3 | — | System | Dialog shows: "Are you sure you want to remove all items from your cart?" |
| 4 | — | System | Dialog provides two buttons: "Confirm" and "Cancel" |
| 5 | Customer | Reviews warning and clicks "Confirm" | — |
| 6 | — | System | Receives confirmation |
| 7 | — | System | Removes ALL products from cart data |
| 8 | — | System | Clears order notes (if any) |
| 9 | — | System | Sets subtotal to 0 |
| 10 | — | System | Persists empty cart to backend |
| 11 | — | System | Closes confirmation dialog |
| 12 | — | System | Transitions to Empty Cart State |
| 13 | Customer | Sees "Your cart is empty" message | Cart cleared |

### 7.5. Alternative Flows

**AF-01: Cancel Clear All**
- Precondition: Confirmation dialog displayed
- Step 1: Customer clicks "Cancel" button
- Step 2: System closes dialog
- Step 3: Cart returns to previous state (unchanged)
- Step 4: All products, quantities, notes remain
- Step 5: Subtotal unchanged
- Result: No action taken

**AF-02: Dismiss Dialog (Escape Key)**
- Precondition: Confirmation dialog displayed
- Step 1: Customer presses Escape key (or clicks outside dialog - TBD)
- Step 2: System detects dismissal
- Step 3: Same as AF-01: Dialog closes, cart unchanged
- Note: TBD if Escape key dismisses or if dialog is modal-only

### 7.6. Exception Flows

**EF-01: Backend Error**
- Precondition: Backend clear fails
- Step 1: System detects error during delete
- Step 2: System reverts to previous cart state
- Step 3: Confirmation dialog closes
- Step 4: Error message displayed: "Failed to clear cart. Please try again."
- Step 5: Cart remains with all products

### 7.7. Business Rules

| Rule | Reference |
|------|-----------|
| Clear All requires confirmation dialog | BR-DEL-01 |
| Empty cart transitions to Empty State | BR-DEL-02 |

### 7.8. Related User Flows

| User Flow | Reference |
|-----------|-----------|
| UF-CART-RA | Remove All Products |
| UF-CART-AF3 | Cancel Remove All |

### 7.9. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **Scope Function** | SC-12 | Clear all products |
| **Scope Function** | SC-13 | Confirmation dialog |
| **Scope Function** | SC-14 | Display empty state |

### 7.10. Validation Status

| Item | Status |
|------|--------|
| **UC Definition** | ✅ Complete |
| **Flows** | ✅ Complete (Basic + 2 AF + 1 EF) |
| **Confirmation** | ✅ Covered (dialog, confirm/cancel) |
| **Empty State** | ✅ Covered (post-delete transition) |

---

## 8. Use Case: UC-CART-06

### 8.1. Use Case Overview

| Attribute | Value |
|-----------|-------|
| **UC ID** | UC-CART-06 |
| **Use Case Name** | Proceed to Checkout Information |
| **Goal** | Customer transitions from Shopping Cart to Checkout module to enter delivery/payment information |
| **Primary Actor** | Customer |
| **Supporting Actors** | System, Checkout Module |
| **Trigger** | Customer clicks "Proceed to Checkout" / "Continue to Payment" button |

### 8.2. Preconditions

- ✅ Cart page displayed (UC-CART-01 completed)
- ✅ Cart contains ≥1 product (not empty)
- ✅ "Proceed to Checkout" button visible and enabled
- ✅ Checkout module available

### 8.3. Postconditions

**Success Case:**
- ✅ Cart data validated (qty ≥1, prices current, subtotal correct)
- ✅ Cart data transferred to Checkout module
- ✅ Checkout page displays with cart information (products, subtotal)
- ✅ Customer redirected to checkout URL
- ✅ Shopping Cart flow ends; Checkout flow begins

**Failure Case:**
- ✅ Validation error detected
- ✅ Error message displayed
- ✅ Customer remains on cart page
- ✅ Cart unchanged

### 8.4. Basic Flow

| Step | Actor | System | Data |
|------|-------|--------|------|
| 1 | Customer | Reviews final cart (products, quantities, notes, totals) | — |
| 2 | Customer | Clicks "Proceed to Checkout" button | — |
| 3 | — | System | Receives checkout request |
| 4 | — | System | Validates cart data: not empty, all qty ≥1, prices current, subtotal correct |
| 5 | — | System | If validation passes: Continue to step 6. If fails: See Exception EF-01 |
| 6 | — | System | Prepares cart data handoff: product list, quantities, subtotal, order notes |
| 7 | — | System | Transfers data to Checkout module via API/session |
| 8 | — | System | Redirects to Checkout page (URL change) |
| 9 | Checkout System | Receives and displays cart data | — |
| 10 | Customer | Sees Checkout page with cart information | Checkout flow begins |

### 8.5. Alternative Flows

**AF-01: Empty Cart Attempted**
- Precondition: Customer clicks "Proceed" but cart is empty
- Step 1: System detects empty cart
- Step 2: System shows error: "Your cart is empty. Add items before checkout."
- Step 3: System remains on cart page
- Step 4: Customer must add products or continue shopping

### 8.6. Exception Flows

**EF-01: Validation Failed**
- Precondition: One or more validation checks fail
- Examples:
  - Quantity issue: Product has qty = 0 (impossible state)
  - Price issue: Price inconsistency detected
  - Empty cart: After clear but page not updated
- Step 1: System detects validation error
- Step 2: System shows error message indicating issue
- Step 3: System remains on cart page
- Step 4: System highlights problematic product
- Step 5: Customer must fix issue (e.g., remove invalid product) before retrying

**EF-02: Checkout Module Unavailable**
- Precondition: Checkout module down OR unreachable
- Step 1: System attempts handoff
- Step 2: System detects error (timeout, 5xx error)
- Step 3: System shows error: "Checkout currently unavailable. Please try again."
- Step 4: System remains on cart page (cart data preserved)
- Step 5: Customer can retry or continue shopping

**EF-03: Network Error During Handoff**
- Precondition: Network timeout or disconnect during data transfer
- Step 1: System detects error
- Step 2: System reverts to cart page
- Step 3: Error message: "Connection lost. Please check your internet and try again."
- Step 4: Cart data unchanged

### 8.7. Business Rules

| Rule | Reference |
|------|-----------|
| Qty must be ≥1 for all products | BR-CART-01 |
| Prices must be current | BR-CART-03 |
| Subtotal must be correct | BR-CART-04 |
| Cannot checkout with empty cart | BR-CART-05 (implicit) |

### 8.8. Related User Flows

| User Flow | Reference |
|-----------|-----------|
| UF-CART-13 | Review Final Cart |
| UF-CART-14 | Proceed to Checkout |
| UF-CART-15 | Cart Validation |
| UF-CART-16 | Handoff to Checkout |

### 8.9. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **Scope Function** | SC-15 | Proceed to checkout button |
| **Scope Function** | SC-01 | View cart (final review) |
| **Scope Function** | SC-06 | Display totals for review |

### 8.10. Validation Status

| Item | Status |
|------|--------|
| **UC Definition** | ✅ Complete |
| **Flows** | ✅ Complete (Basic + 1 AF + 3 EF) |
| **Validation** | ✅ Covered (data checks before handoff) |
| **Handoff** | ✅ Covered (data transfer to Checkout) |

### 8.11. Open Questions

| Question | Current Status |
|----------|-----------------|
| What's the exact handoff data format to Checkout? | Cần xác nhận |
| Should cart be cleared after successful checkout? | Cần xác nhận |
| How to handle payment/order failures (retry cart)? | Out of Scope (Checkout module) |

---

## 9. Use Case Traceability Matrix

| UC ID | Related User Flows | Related Scope Functions | Related BR |
|-------|-------------------|------------------------|-----------|
| **UC-CART-01** | UF-CART-05, 06, 08, EC | SC-01, 02, 06, 14 | BR-CART-03, 04 |
| **UC-CART-02** | UF-CART-10, 11, AF1, AF2 | SC-03, 04, 05, 06 | BR-CART-01, 02, 03, 04 |
| **UC-CART-03** | UF-CART-12, ON | SC-09, 10 | BR-NOTE-01 |
| **UC-CART-04** | UF-CART-11, RM, AF4 | SC-11, 06, 14 | BR-CART-04, DEL-02 |
| **UC-CART-05** | UF-CART-RA, AF3 | SC-12, 13, 14 | BR-DEL-01, DEL-02 |
| **UC-CART-06** | UF-CART-13, 14, 15, 16 | SC-15, 01, 06 | BR-CART-01, 03, 04 |

---

## 10. Use Case Dependencies

```
UC-CART-01 (View Cart)
    ↓
    ├─→ UC-CART-02 (Update Qty)
    ├─→ UC-CART-03 (Add Note)
    ├─→ UC-CART-04 (Remove One) → AF-01: Empty State
    ├─→ UC-CART-05 (Remove All)  → AF: Empty State
    │
    └─→ UC-CART-06 (Proceed Checkout)
            ↓
        Checkout Module (Phase 2+)
```

**Reading the diagram:**
- UC-CART-01 is foundation (customer must view cart first)
- UC-CART-02, 03, 04, 05 can occur from UC-CART-01 (in any order)
- UC-CART-04 or UC-CART-05 can lead to Empty State
- UC-CART-06 is the final transition (leads to Checkout module)

---

## 11. Important Disclaimers

### ✅ What These Use Cases Represent

- ✅ Detailed flows from Phase 1 analysis
- ✅ Behavior-focused (what system does, not how it's built)
- ✅ Foundation for Phase 2 development
- ✅ Reference for QA test case design
- ✅ Common language for stakeholders

### ❌ What These Use Cases Do NOT Represent

- ❌ Implementation details (technology choices)
- ❌ Database design
- ❌ UI mockups
- ❌ Completed development
- ❌ Tested/deployed features

---

## 12. Document Metadata

| Attribute | Value |
|-----------|-------|
| **Document Type** | Use Cases Specification |
| **Phase** | Phase 1 - Analysis Complete |
| **Status** | ✅ Complete |
| **Total Use Cases** | 6 |
| **Total Flows** | Basic: 6, Alternative: 11, Exception: 11 (28 total) |
| **Classification** | Portfolio Documentation |
| **Last Updated** | Phase 1 Analysis |

---

**Document Version:** 1.0  
**Status:** ✅ Ready for Development Handover  
**Next Steps:** Use Cases ready for Phase 2 development planning
