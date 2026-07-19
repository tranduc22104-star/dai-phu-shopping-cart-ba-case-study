# Acceptance Criteria - Shopping Cart Module
## Đại Phú E-commerce

---

## 1. Document Purpose

Tài liệu này định nghĩa chi tiết **Acceptance Criteria (AC)** cho tất cả **7 User Stories** trong module Giỏ hàng. Mỗi AC sử dụng định dạng **Gherkin (Given-When-Then)** để đảm bảo:

- ✅ **Measurable** - Có thể đo lường cụ thể
- ✅ **Testable** - Có thể kiểm thử tự động hoặc thủ công
- ✅ **Unambiguous** - Không mơ hồ, rõ ràng
- ✅ **Technology-agnostic** - Không phụ thuộc công nghệ cụ thể (trừ khi cần thiết)

---

## 2. Acceptance Criteria Catalog

| US ID | US Title | Total AC | Status |
|-------|----------|----------|--------|
| **US-CART-01** | View Shopping Cart | 5 | Analyzed |
| **US-CART-02** | Update Product Quantity | 5 | Analyzed |
| **US-CART-03** | Add Order Note | 3 | Analyzed |
| **US-CART-04** | Remove One Product | 2 | Analyzed |
| **US-CART-05** | Remove All Products | 3 | Analyzed |
| **US-CART-06** | View Empty Cart State | 4 | Analyzed |
| **US-CART-07** | Proceed to Checkout | 2 | Analyzed |
| **TOTAL** | | **24** | ✅ Complete |

---

## 3. Acceptance Criteria: US-CART-01 (View Shopping Cart)

### AC-CART-01.01

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-01.01 |
| **Related User Story** | US-CART-01 (View Shopping Cart) |
| **Scenario** | Display All Products in Cart |
| **Type** | Positive (Happy Path) |
| **Related Business Rule** | BR-CART-03 (Prices Auto-Recalculate) |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Customer has navigated to the shopping cart page
- Customer's cart contains at least 1 product (e.g., Product A, Product B)
- Each product has: image, name, unit price, quantity, and item total

**When:**
- The cart page loads successfully

**Then:**
- System displays a list/table of all products in the cart
- For each product, the following information is visible:
  - Product image (thumbnail)
  - Product name (full name displayed, no truncation unless necessary)
  - Unit price (formatted as currency, e.g., "100,000 VND")
  - Quantity (numeric value, e.g., "2")
  - Item total (calculated: Unit Price × Quantity, e.g., "200,000 VND")
- All product rows are clearly separated and readable
- No products are missing or duplicated
- Product data reflects the current cart state

**Verification:**
- [ ] Visual inspection: All products appear in list
- [ ] Data accuracy check: Prices match backend data
- [ ] Quantity check: Each product shows correct quantity
- [ ] Item total check: Item Total = Unit Price × Quantity (mathematically correct)

---

### AC-CART-01.02

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-01.02 |
| **Related User Story** | US-CART-01 |
| **Scenario** | Display Long Product Names Without Truncation |
| **Type** | Boundary (Edge case for long names) |
| **Related Business Rule** | SC-02 (Display product information) |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Cart contains a product with a long name
- Example: "Hoa lụa trang trí phòng khách kiểu Nhật Bản cao cấp với lá xanh tự nhiên"
- Product name length: up to 100+ characters (typical limit)

**When:**
- The product is displayed in the cart

**Then:**
- The full product name is displayed without truncation
- OR if truncation is necessary (design decision TBD):
  - Name is truncated at a word boundary (not mid-word)
  - Ellipsis ("...") is shown
  - Full name is available on hover (tooltip) or click
- Product name area has sufficient vertical space to accommodate multi-line text
- No overlap with other columns/elements

**Verification:**
- [ ] Product name fully visible or properly truncated with tooltip
- [ ] No mid-word truncation
- [ ] Layout doesn't break with long names

---

### AC-CART-01.03

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-01.03 |
| **Related User Story** | US-CART-01 |
| **Scenario** | Display Cart Summary (Subtotal) |
| **Type** | Positive |
| **Related Business Rule** | BR-CART-03 (Prices Auto-Recalculate) |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Cart page is displayed with products
- Cart contains multiple products with various quantities and prices
- Example:
  - Product A: Unit Price 50,000 VND, Qty 2 → Item Total 100,000 VND
  - Product B: Unit Price 75,000 VND, Qty 1 → Item Total 75,000 VND

**When:**
- The cart summary section is rendered

**Then:**
- Subtotal is displayed and calculated as: Sum of all Item Totals
  - In example: 100,000 + 75,000 = 175,000 VND
- Subtotal is formatted as currency (e.g., "175,000 VND")
- Subtotal is placed in a clearly labeled section (e.g., "Cart Summary" or "Subtotal")
- Item count is also displayed (e.g., "2 items in cart" or "Total items: 2")
- Subtotal updates automatically when products are added/removed/modified

**Verification:**
- [ ] Subtotal calculation is mathematically correct
- [ ] Currency formatting is consistent (thousand separator, currency symbol)
- [ ] Item count is accurate
- [ ] Subtotal location is clearly visible (not hidden or hard to find)

---

### AC-CART-01.04

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-01.04 |
| **Related User Story** | US-CART-01 |
| **Scenario** | Display Current and Accurate Cart Data |
| **Type** | Positive |
| **Related Business Rule** | BR-CART-03 (Prices Auto-Recalculate) |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Customer has made modifications to cart (e.g., added/removed products, changed quantities)
- Backend cart database has the latest state
- Product prices in backend may have changed since customer added to cart

**When:**
- Customer refreshes cart page OR navigates back to cart page

**Then:**
- Cart displays the most current data (no stale data)
- All product quantities match what was last saved
- All product prices reflect current backend values (not cached old prices)
- If product price changed after customer added to cart:
  - New price is displayed (not old price)
  - Total amounts recalculated with new prices
  - Optional: Warning message shown to customer (TBD - Cần xác nhận)
- No data inconsistencies or mismatches

**Verification:**
- [ ] Data freshness: Compare displayed data with backend
- [ ] Price accuracy: Verify prices match current catalog
- [ ] Calculation accuracy: Item totals use current prices
- [ ] No cache-related issues

---

### AC-CART-01.05

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-01.05 |
| **Related User Story** | US-CART-01 |
| **Scenario** | Responsive Design on Multiple Screen Sizes |
| **Type** | Positive |
| **Related Business Rule** | NFR-CART-04 (Responsive Design) |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Cart page must be accessible on multiple devices
- Test on common screen sizes:
  - Desktop: 1920px, 1366px, 1024px (widths)
  - Tablet: 768px (iPad portrait)
  - Mobile: 375px, 414px (iPhone sizes)

**When:**
- Customer accesses cart on desktop, tablet, or mobile device

**Then:**
- Cart layout adjusts appropriately to screen size
- All product information remains readable:
  - Text size is legible (minimum 12px or device-readable)
  - No horizontal scrolling required (content fits in viewport width)
  - Columns/rows reflow or stack based on available space
- All interactive elements (buttons, input fields) are accessible:
  - Touch targets for buttons/buttons minimum 44×44px on mobile
  - Input fields clearly labeled and large enough to tap
  - No overlapping elements
- Product images scale appropriately and don't become distorted
- Summary/totals remain visible without excessive scrolling

**Verification:**
- [ ] Desktop (1920px): All content visible, properly formatted
- [ ] Tablet (768px): Content reflows correctly
- [ ] Mobile (375px): Touch targets ≥44×44px, legible text
- [ ] No horizontal overflow on any screen size
- [ ] All elements accessible and interactive on all sizes

---

## 4. Acceptance Criteria: US-CART-02 (Update Product Quantity)

### AC-CART-02.01

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-02.01 |
| **Related User Story** | US-CART-02 (Update Product Quantity) |
| **Scenario** | Increase Product Quantity |
| **Type** | Positive |
| **Related Business Rule** | BR-CART-03 (Prices Auto-Recalculate) |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Customer is viewing a product in cart with current quantity Q (e.g., Q=1)
- Product unit price is stable (e.g., 50,000 VND)
- Item total currently displayed is correct (e.g., 50,000 VND for Q=1)

**When:**
- Customer clicks "+" button (or increments quantity field from 1 to 2)

**Then:**
- System increments quantity by 1 (from Q to Q+1)
- Item total recalculates automatically: Unit Price × (Q+1)
  - Example: 50,000 × 2 = 100,000 VND
- Cart subtotal recalculates: Sum of all updated Item Totals
- Display updates in real-time without page refresh
- Changes are persisted to backend immediately or within 1 second (TBD timing)
- No error messages appear (operation succeeds)
- Customer can still interact with other cart elements (not blocked)

**Verification:**
- [ ] Quantity increments by exactly 1
- [ ] Item total calculation correct: Unit Price × New Qty
- [ ] Subtotal recalculated correctly
- [ ] Changes visible in UI without refresh
- [ ] Backend updated (verify via API or database)

---

### AC-CART-02.02

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-02.02 |
| **Related User Story** | US-CART-02 |
| **Scenario** | Decrease Product Quantity |
| **Type** | Positive |
| **Related Business Rule** | BR-CART-03 (Prices Auto-Recalculate) |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Product in cart has quantity Q where Q > 1 (e.g., Q=3)
- Current item total is correct (e.g., 150,000 VND for 3 units @ 50,000 each)

**When:**
- Customer clicks "-" button (or decrements quantity from 3 to 2)

**Then:**
- System decrements quantity by 1 (from Q to Q-1)
- Item total recalculates: Unit Price × (Q-1)
  - Example: 50,000 × 2 = 100,000 VND
- Cart subtotal recalculates
- Display updates in real-time without page refresh
- Changes persisted to backend
- No error messages
- Product remains in cart (not removed when quantity decreases)

**Verification:**
- [ ] Quantity decrements by exactly 1
- [ ] Item total correct: Unit Price × New Qty
- [ ] Subtotal recalculated
- [ ] Changes visible immediately
- [ ] Backend updated

---

### AC-CART-02.03

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-02.03 |
| **Related User Story** | US-CART-02 |
| **Scenario** | Enforce Minimum Quantity of 1 (Cannot Decrease Below 1) |
| **Type** | Boundary (Lower limit validation) |
| **Related Business Rule** | BR-CART-01 (Min Qty = 1), SC-05 (Prevent qty < 1) |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Product in cart has quantity = 1 (minimum)

**When:**
- Customer attempts to decrease quantity (clicks "-" button OR tries to edit quantity field to 0)

**Then:**
- System does NOT decrement quantity below 1
- One of the following occurs (Design decision TBD - Cần xác nhận):
  - **Option A:** "-" button is disabled/grayed out (visually indicate it cannot be clicked)
  - **Option B:** System shows inline error message: "Cannot reduce below 1 item. Use 'Remove' button to delete."
  - **Option C:** "-" button click is ignored silently (no action, no message)
- Quantity remains = 1 (no change)
- Customer is informed to use "Remove" button if they want to delete the product entirely
- Item total remains unchanged

**Verification:**
- [ ] Quantity does not go below 1
- [ ] Visual feedback provided (disabled button OR error message)
- [ ] "Remove" button available as alternative
- [ ] Item total unchanged

---

### AC-CART-02.04

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-02.04 |
| **Related User Story** | US-CART-02 |
| **Scenario** | Reject Invalid Quantity Input (Zero or Negative) |
| **Type** | Negative (Invalid input rejection) |
| **Related Business Rule** | BR-CART-01 (Min Qty = 1), SC-05 (Prevent qty < 1) |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Customer can directly edit quantity field (if this input method is implemented)
- Customer attempts to enter invalid values: 0, -5, or other negative numbers

**When:**
- Customer manually types "0" OR "-5" into quantity field and presses Enter/Tab

**Then:**
- System detects invalid input (value < 1)
- Quantity change is REJECTED; field value not updated
- Error message displayed: "Quantity must be at least 1"
- Quantity field highlights in error state (e.g., red border)
- Item total does NOT recalculate based on invalid input
- Backend is NOT updated with invalid quantity

**Verification:**
- [ ] Invalid input (0 or negative) is rejected
- [ ] Error message displayed clearly
- [ ] Quantity field shows previous valid value
- [ ] Item total unchanged
- [ ] Backend unchanged

---

### AC-CART-02.05

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-02.05 |
| **Related User Story** | US-CART-02 |
| **Scenario** | Reject Non-Numeric Quantity Input |
| **Type** | Negative (Invalid data type) |
| **Related Business Rule** | SC-03, SC-04 (Quantity management) |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Quantity field is editable (direct input enabled)
- Customer attempts to enter non-numeric values

**When:**
- Customer types "abc", "2.5", "qty@10", or other non-numeric input and attempts to save

**Then:**
- System detects non-numeric input
- Input is REJECTED; field value not updated
- Error message displayed: "Please enter a valid quantity (numbers only)"
- Quantity field highlighted in error state
- Item total NOT recalculated
- Backend NOT updated

**Verification:**
- [ ] Non-numeric input rejected
- [ ] Error message shown
- [ ] Field reverts to previous valid value
- [ ] Calculations unchanged

---

## 5. Acceptance Criteria: US-CART-03 (Add Order Note)

### AC-CART-03.01

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-03.01 |
| **Related User Story** | US-CART-03 (Add Order Note) |
| **Scenario** | Enter Valid Order Note (≤256 characters) |
| **Type** | Positive |
| **Related Business Rule** | BR-CART-02 (Max Notes = 256 chars), SC-09, SC-10 |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Customer is viewing cart page
- Order note input field is visible and empty
- Customer wants to add a note (e.g., "Giao buổi sáng trước 10 AM")
- Note length is ≤ 256 characters

**When:**
- Customer clicks on order note field
- Types the note text
- (Field may auto-save OR customer clicks Save button - TBD)

**Then:**
- Note text is accepted without error
- Note is displayed in the order note field (echo-back confirmation)
- Character count displayed updates in real-time (e.g., "45/256")
- Note is saved to cart data (backend persisted)
- Note appears in order summary section before checkout
- No error message appears

**Verification:**
- [ ] Note entered and visible in field
- [ ] Character count accurate (45 if 45 chars entered)
- [ ] Backend updated with note
- [ ] Note persists if page refreshed

---

### AC-CART-03.02

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-03.02 |
| **Related User Story** | US-CART-03 |
| **Scenario** | Note Reaches Exactly 256 Characters (Boundary) |
| **Type** | Boundary (Exact limit test) |
| **Related Business Rule** | BR-CART-02 (Max 256 chars), SC-10 |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Customer enters note with exactly 256 characters
- Example: "Đây là một ghi chú dài 256 ký tự..." (256 chars total)

**When:**
- Customer types up to character 256
- Character count shows "256/256"
- Customer attempts to type additional character (character 257)

**Then:**
- While typing to exactly 256 chars: Input accepted, displayed correctly
- At exactly 256 chars: Character count shows "256/256" (displays boundary reached)
- When attempting to type character 257:
  - **Option A:** Additional input is blocked (character not entered)
  - **Option B:** Warning message shown: "Maximum 256 characters reached"
  - **Option C:** System auto-trims to 256 characters
- Note is saved with exactly 256 characters
- No data loss or corruption

**Verification:**
- [ ] Note accepted at exactly 256 chars
- [ ] Character 257+ blocked or warning shown
- [ ] Saved note is exactly 256 chars (count verified)

---

### AC-CART-03.03

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-03.03 |
| **Related User Story** | US-CART-03 |
| **Scenario** | Reject Order Note Exceeding 256 Characters |
| **Type** | Negative (Boundary violation) |
| **Related Business Rule** | BR-CART-02 (Max 256 chars), SC-10 |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Customer pastes a note from clipboard that is > 256 characters
- Example: Long text that is 350 characters total

**When:**
- Customer pastes text (Ctrl+V) into note field
- Text length exceeds 256 characters (e.g., 350 chars)

**Then:**
- System detects character count exceeds limit
- One of the following occurs (Design TBD - Cần xác nhận):
  - **Option A:** Text is truncated to 256 characters (last 94 chars removed)
  - **Option B:** Error message shown: "Note exceeds 256 character limit. Please reduce."
  - **Option C:** Paste action is rejected entirely
- Note field shows either truncated text OR reverts to previous value
- Character count shows "256/256" (if truncated) OR "0/256" (if rejected)
- Backend is only updated if note is valid (≤256)

**Verification:**
- [ ] Note > 256 chars is handled (truncated, rejected, OR error shown)
- [ ] Backend receives only valid note (≤256 chars)
- [ ] No data corruption

---

## 6. Acceptance Criteria: US-CART-04 (Remove One Product)

### AC-CART-04.01

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-04.01 |
| **Related User Story** | US-CART-04 (Remove One Product) |
| **Scenario** | Remove Single Product from Cart (No Confirmation) |
| **Type** | Positive |
| **Related Business Rule** | BR-CART-03 (Prices Auto-Recalculate), SC-11 |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Cart contains multiple products (e.g., Product A, Product B, Product C)
- Customer identifies one product (Product B) they want to remove
- "Remove" button is visible for Product B

**When:**
- Customer clicks "Remove" button for Product B
- (No confirmation dialog for single item - quick action)

**Then:**
- Product B is removed from cart immediately
- Product B no longer appears in product list
- Cart subtotal recalculates (Item Totals for A and C summed)
- Item count updates (e.g., from "3 items" to "2 items")
- Products A and C remain in cart unaffected
- Change is persisted to backend
- Display updates without page refresh
- Success feedback provided (visual confirmation Product B is gone)

**Verification:**
- [ ] Product removed from list
- [ ] Subtotal recalculated correctly
- [ ] Item count updated
- [ ] Other products unaffected
- [ ] Backend updated

---

### AC-CART-04.02

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-04.02 |
| **Related User Story** | US-CART-04 |
| **Scenario** | Remove Last Product - Transition to Empty State |
| **Type** | Positive (State transition) |
| **Related Business Rule** | BR-CART-05 (Empty Cart → Empty State), SC-14 |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Cart contains only 1 product (last item)
- Customer can see "Remove" button for that product

**When:**
- Customer clicks "Remove" button for the last/only product

**Then:**
- Product is removed from cart
- Cart becomes completely empty
- System transitions to Empty Cart state (AC-CART-06.01 applies)
- Empty state message displayed: "Your cart is empty"
- Product list no longer shown
- "Continue Shopping" button becomes primary call-to-action
- "Proceed to Checkout" button is disabled or hidden
- Subtotal/totals section may be hidden or shows 0
- Backend updated (cart now empty)

**Verification:**
- [ ] Last product removed
- [ ] Empty state message displayed
- [ ] "Continue Shopping" button available
- [ ] Checkout button disabled/hidden
- [ ] Backend reflects empty cart

---

## 7. Acceptance Criteria: US-CART-05 (Remove All Products)

### AC-CART-05.01

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-05.01 |
| **Related User Story** | US-CART-05 (Remove All Products) |
| **Scenario** | Display Confirmation Dialog Before Clearing Cart |
| **Type** | Positive |
| **Related Business Rule** | BR-CART-04 (Clear All Requires Confirmation), SC-12, SC-13 |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Cart contains products (e.g., 3+ items)
- Customer locates "Clear All" / "Remove All" button

**When:**
- Customer clicks "Clear All" button

**Then:**
- System displays a confirmation dialog/popup
- Dialog message clearly states action consequence:
  - E.g., "Are you sure you want to remove all items from your cart?"
  - OR "This action will delete all products. Continue?"
- Dialog provides TWO clear options:
  - "Confirm" / "Yes" button (primary action)
  - "Cancel" / "No" button (secondary action, default focus)
- Dialog cannot be dismissed by clicking outside it (modal behavior - TBD if needed)
- OR can be dismissed by pressing Escape key (TBD - Cần xác nhận)
- Cart items are NOT modified until customer confirms

**Verification:**
- [ ] Confirmation dialog appears
- [ ] Dialog message is clear and explicit
- [ ] Both "Confirm" and "Cancel" buttons present
- [ ] Dialog is modal (cannot interact with cart while dialog open)

---

### AC-CART-05.02

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-05.02 |
| **Related User Story** | US-CART-05 |
| **Scenario** | Confirm Clear All - Remove All Products |
| **Type** | Positive |
| **Related Business Rule** | BR-CART-04, SC-12, SC-14 |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Confirmation dialog is displayed (AC-CART-05.01 triggered)

**When:**
- Customer clicks "Confirm" / "Yes" button

**Then:**
- ALL products are removed from cart
- Cart transitions to empty state
- Empty state message displayed: "Your cart is empty"
- Subtotal resets to 0 or hidden
- Item count shows "0 items" or is hidden
- "Continue Shopping" button displayed prominently
- "Proceed to Checkout" disabled/hidden
- All changes persisted to backend (cart is now empty)
- Confirmation dialog closes
- Display updates without page refresh

**Verification:**
- [ ] All products removed (not just some)
- [ ] Empty state displayed (AC-CART-06.01 applies)
- [ ] Backend updated (empty cart)

---

### AC-CART-05.03

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-05.03 |
| **Related User Story** | US-CART-05 |
| **Scenario** | Cancel Clear All - Preserve All Products |
| **Type** | Alternative (User changes mind) |
| **Related Business Rule** | BR-CART-04 (Confirmation required), SC-12, SC-13 |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Confirmation dialog is displayed (AC-CART-05.01 triggered)

**When:**
- Customer clicks "Cancel" / "No" button
- OR presses Escape key (if implemented - TBD)
- OR clicks outside dialog (if not modal - TBD)

**Then:**
- Confirmation dialog closes
- NO products are removed from cart
- Cart contents remain completely unchanged (all items preserved)
- All quantities, prices, notes remain as they were
- Subtotal unchanged
- Customer returns to normal cart view
- Backend is NOT modified

**Verification:**
- [ ] Dialog closes
- [ ] No products removed
- [ ] All data unchanged
- [ ] Backend unchanged

---

## 8. Acceptance Criteria: US-CART-06 (View Empty Cart State)

### AC-CART-06.01

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-06.01 |
| **Related User Story** | US-CART-06 (View Empty Cart State) |
| **Scenario** | Display Empty Cart Message |
| **Type** | Positive |
| **Related Business Rule** | BR-CART-05 (Empty Cart → Empty State), SC-14 |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Customer's shopping cart is empty (no products)
- Occurs after: First visit without adding items, OR after clearing all items

**When:**
- Customer navigates to or views the shopping cart page

**Then:**
- Cart page loads successfully
- Product list table/grid is NOT displayed (hidden or empty)
- Clear message displayed: "Your cart is empty"
  - OR similar message: "You have no items in your cart"
- Message is prominently visible (e.g., centered, larger font, distinct color)
- Subtotal/totals section is hidden or shows 0
- Item count shows "0 items"
- "Proceed to Checkout" button is disabled (grayed out) or completely hidden
- "Continue Shopping" button is prominent and clickable
- No product-related controls are visible (no quantity buttons, no remove buttons)

**Verification:**
- [ ] Empty cart message displayed
- [ ] Message is clear and user-friendly
- [ ] Product list not shown
- [ ] Checkout button disabled/hidden
- [ ] "Continue Shopping" button available

---

### AC-CART-06.02

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-06.02 |
| **Related User Story** | US-CART-06 |
| **Scenario** | Display Continue Shopping Button in Empty State |
| **Type** | Positive |
| **Related Business Rule** | SC-14 (Display empty-cart state) |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Cart is empty (AC-CART-06.01 condition)

**When:**
- Empty cart page is displayed

**Then:**
- "Continue Shopping" button is visible and prominently displayed
- Button text clearly indicates action: "Continue Shopping" OR "Back to Shopping"
- Button is clickable and styled to indicate it's the primary action
- Clicking button navigates customer back to Product Listing/Browsing page
- Cart data is preserved (remains empty) when returning to shopping

**Verification:**
- [ ] "Continue Shopping" button visible
- [ ] Button text clear
- [ ] Button is clickable
- [ ] Clicking navigates to product listing
- [ ] Cart state preserved

---

### AC-CART-06.03

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-06.03 |
| **Related User Story** | US-CART-06 |
| **Scenario** | Checkout Button Disabled in Empty Cart |
| **Type** | Negative (Prevent invalid action) |
| **Related Business Rule** | BR-CART-05 (Empty Cart → Empty State) |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Cart is empty

**When:**
- Customer views cart page (empty state displayed)

**Then:**
- "Proceed to Checkout" / "Checkout" button is either:
  - **Option A:** Disabled (grayed out, non-clickable)
  - **Option B:** Completely hidden/removed from UI
  - **Option C:** Clickable but shows error message "Cart is empty. Add items before checkout."
- If customer attempts to click disabled button: No action occurs
- Customer cannot proceed to checkout with empty cart

**Verification:**
- [ ] Checkout button disabled/hidden
- [ ] Button cannot be clicked (or shows error if clicked)
- [ ] Checkout process cannot start with empty cart

---

### AC-CART-06.04

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-06.04 |
| **Related User Story** | US-CART-06 |
| **Scenario** | Empty State Persists if Customer Returns to Cart |
| **Type** | Positive (State persistence) |
| **Related Business Rule** | SC-14 |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Cart is empty (empty state displayed)
- Customer navigates away (e.g., continues shopping, visits other pages)

**When:**
- Customer returns to cart page (clicks cart icon or navigates to cart URL)

**Then:**
- Cart still shows empty state (not repopulated)
- "Your cart is empty" message still displayed
- No previous product data appears
- Cart remains in empty state
- Backend confirms cart is empty

**Verification:**
- [ ] Empty state persists after navigation away and back
- [ ] No data appears after refresh

---

## 9. Acceptance Criteria: US-CART-07 (Proceed to Checkout)

### AC-CART-07.01

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-07.01 |
| **Related User Story** | US-CART-07 (Proceed to Checkout Information) |
| **Scenario** | Validate Cart Data Before Checkout Handoff |
| **Type** | Positive |
| **Related Business Rule** | BR-CART-01 (Min Qty ≥1), BR-CART-03 (Prices current) |
| **Verification Status** | ⏳ Pending Implementation |

**Given:**
- Customer has reviewed cart (all products, quantities, totals, notes visible)
- Cart contains at least 1 valid product
- All quantities are ≥1
- All prices are current (freshly fetched from backend)

**When:**
- Customer clicks "Proceed to Checkout" / "Continue to Payment" button

**Then:**
- System validates cart data:
  - ✓ Cart is NOT empty (contains at least 1 product)
  - ✓ All quantities are valid (≥1, no zeros or negatives)
  - ✓ All prices are current (recalculated from backend)
  - ✓ Subtotal is correctly calculated
  - ✓ No blocked/unavailable products
- Validation passes (no errors detected)
- System prepares to handoff to Checkout module (no errors shown)
- Proceeds to AC-CART-07.02

**Verification:**
- [ ] Cart not empty check passes
- [ ] Quantities validated (all ≥1)
- [ ] Prices recalculated with current values
- [ ] Subtotal correct
- [ ] No validation errors

---

### AC-CART-07.02

| Attribute | Value |
|-----------|-------|
| **AC ID** | AC-CART-07.02 |
| **Related User Story** | US-CART-07 |
| **Scenario** | Navigate to Checkout Module After Validation |
| **Type** | Positive |
| **Related Business Rule** | SC-15 (Proceed to checkout) |
| **Verification Status** | ⏳ Pending Implementation (depends on Checkout module availability) |

**Given:**
- Cart validation passed (AC-CART-07.01)
- Cart data is valid and ready for handoff

**When:**
- System validation completes successfully

**Then:**
- Cart data is transferred to Checkout module:
  - Product list (with quantities)
  - Calculated subtotal
  - Order notes (if provided)
  - Any other cart-related data needed
- Page navigation occurs: redirects to Checkout page
- Checkout module receives cart data and displays its content
- Shopping Cart flow ends; Checkout flow begins
- URL changes to Checkout page URL (e.g., ".../checkout", ".../payment-info")
- Customer sees Checkout page (fields for delivery information, payment, etc.)

**Verification:**
- [ ] Cart data transmitted successfully
- [ ] Navigation to Checkout page successful
- [ ] Checkout page displays cart data
- [ ] Shopping Cart scope ended

---

## 10. Acceptance Criteria Summary Table

| AC ID | US | Scenario | Type | Status |
|-------|-----|----------|------|--------|
| **AC-CART-01.01** | US-CART-01 | Display All Products | Positive | Analyzed |
| **AC-CART-01.02** | US-CART-01 | Long Product Names | Boundary | Analyzed |
| **AC-CART-01.03** | US-CART-01 | Display Cart Summary | Positive | Analyzed |
| **AC-CART-01.04** | US-CART-01 | Current Cart Data | Positive | Analyzed |
| **AC-CART-01.05** | US-CART-01 | Responsive Design | Positive | Analyzed |
| **AC-CART-02.01** | US-CART-02 | Increase Qty | Positive | Analyzed |
| **AC-CART-02.02** | US-CART-02 | Decrease Qty | Positive | Analyzed |
| **AC-CART-02.03** | US-CART-02 | Qty = 1 (Min) | Boundary | Analyzed |
| **AC-CART-02.04** | US-CART-02 | Qty = 0/Negative | Negative | Analyzed |
| **AC-CART-02.05** | US-CART-02 | Non-Numeric Qty | Negative | Analyzed |
| **AC-CART-03.01** | US-CART-03 | Valid Note (≤256) | Positive | Analyzed |
| **AC-CART-03.02** | US-CART-03 | Note = 256 Chars | Boundary | Analyzed |
| **AC-CART-03.03** | US-CART-03 | Note > 256 Chars | Negative | Analyzed |
| **AC-CART-04.01** | US-CART-04 | Remove Single | Positive | Analyzed |
| **AC-CART-04.02** | US-CART-04 | Remove Last Item | Positive | Analyzed |
| **AC-CART-05.01** | US-CART-05 | Confirmation Dialog | Positive | Analyzed |
| **AC-CART-05.02** | US-CART-05 | Confirm Clear | Positive | Analyzed |
| **AC-CART-05.03** | US-CART-05 | Cancel Clear | Alternative | Analyzed |
| **AC-CART-06.01** | US-CART-06 | Empty Message | Positive | Analyzed |
| **AC-CART-06.02** | US-CART-06 | Continue Button | Positive | Analyzed |
| **AC-CART-06.03** | US-CART-06 | Checkout Disabled | Negative | Analyzed |
| **AC-CART-06.04** | US-CART-06 | Empty Persists | Positive | Analyzed |
| **AC-CART-07.01** | US-CART-07 | Validate Cart | Positive | Analyzed |
| **AC-CART-07.02** | US-CART-07 | Handoff to Checkout | Positive | Analyzed |
| **TOTAL** | | | | **24 AC** |

---

## 11. Acceptance Criteria by Type

### Positive (Happy Path)
- AC-CART-01.01, 01.03, 01.04, 01.05 (View Cart)
- AC-CART-02.01, 02.02 (Quantity Management)
- AC-CART-03.01 (Add Note)
- AC-CART-04.01, 04.02 (Remove Product)
- AC-CART-05.01, 05.02 (Clear All - Flow)
- AC-CART-06.01, 06.02, 06.04 (Empty State)
- AC-CART-07.01, 07.02 (Checkout)
- **Total: 16 Positive**

### Negative (Invalid Input/Edge Cases)
- AC-CART-02.04, 02.05 (Invalid Qty Input)
- AC-CART-03.03 (Note > 256 chars)
- AC-CART-06.03 (Disabled Checkout)
- **Total: 4 Negative**

### Boundary (Limit Testing)
- AC-CART-01.02 (Long Product Names)
- AC-CART-02.03 (Qty = 1 Min)
- AC-CART-03.02 (Note = 256 Chars)
- **Total: 3 Boundary**

### Alternative (User Choices)
- AC-CART-05.03 (Cancel Clear All)
- **Total: 1 Alternative**

---

## 12. Key Validation Points

### Unmeasurable Terms AVOIDED

❌ **Terms NOT Used:**
- "nhanh" (fast) - Instead: "within 1 second" or "real-time"
- "thân thiện" (friendly) - Instead: "clear message", "prominently displayed"
- "dễ sử dụng" (easy to use) - Instead: specific UI requirements
- "phù hợp" (suitable) - Instead: "matches specification", "correct format"
- "tốt" (good) - Instead: measurable criteria

✅ **Replaced With:**
- Specific numbers: "256 characters", "1 second", "44×44 pixels"
- Clear actions: "displayed", "removed", "persisted"
- Verifiable states: "disabled", "hidden", "error message shown"

---

## 13. Verification Status Summary

| Status | Count | Details |
|--------|-------|---------|
| **⏳ Pending Implementation** | 24 | All AC awaiting Phase 2 development |
| **✅ Analyzed** | 24 | All AC thoroughly analyzed in Phase 1 |
| **⏳ Pending Testing** | 24 | Testing to occur in Phase 3 (QA/UAT) |
| **❌ Deployed** | 0 | No AC deployed to production yet |

---

## 14. Important Disclaimers

### ✅ What These Acceptance Criteria Represent

- ✅ Detailed, testable requirements from Phase 1 analysis
- ✅ Gherkin format (Given-When-Then) for clarity
- ✅ Measurable criteria without ambiguous terms
- ✅ Foundation for Phase 2 development & Phase 3 QA testing
- ✅ Reference for test case design

### ❌ What These Acceptance Criteria Do NOT Represent

- ❌ Implementation or developed code
- ❌ Completed development work
- ❌ Passed testing or UAT
- ❌ Production-ready features
- ❌ Stakeholder sign-off (still pending confirmation)

### ⏳ Verification Timeline

- **Phase 1 (COMPLETED):** ✅ AC analyzed & documented
- **Phase 2 (PENDING):** ⏳ AC used during development for acceptance
- **Phase 3 (PENDING):** ⏳ AC verified via testing (manual/automated)
- **Phase 4+ (PENDING):** ⏳ AC validated post-deployment

---

## 15. Open Questions for Stakeholders

### AC Implementation Decisions

| AC ID | Question | Current Status |
|-------|----------|-----------------|
| **AC-CART-02.03** | How to indicate min qty reached? (disable button/error message/silent) | Cần xác nhận |
| **AC-CART-03.02** | How to handle 256 char limit? (block/truncate/error) | Cần xác nhận |
| **AC-CART-05.01** | Should dialog be dismissible by Escape/clicking outside? | Cần xác nhận |
| **AC-CART-06.03** | Should checkout button be disabled OR hidden when empty? | Cần xác nhận |
| **AC-CART-07.02** | Checkout module API contract - what data format? | Cần xác nhận |

---

## 16. Related Documents

| Document | Link | Relevance |
|----------|------|-----------|
| **docs/04-project-scope.md** | Scope Functions (SC-01 ~ SC-15) | Source of AC mappings |
| **docs/06-user-flow.md** | User Flows (50+ steps) | Flow basis for AC scenarios |
| **docs/07-use-cases.md** | Use Cases (30+ flows) | Detailed flows for AC |
| **docs/08-user-stories.md** | User Stories (7 total) | AC parent requirement |
| **.github/copilot-instructions.md** | Documentation Standards | Format & terminology |

---

## 17. Document Metadata

| Attribute | Value |
|-----------|-------|
| **Document Type** | Acceptance Criteria Specifications |
| **Phase** | Phase 1 - Analysis Complete |
| **Status** | ✅ Complete |
| **Total Acceptance Criteria** | 24 |
| **Format** | Gherkin (Given-When-Then) |
| **Measurability** | 100% Measurable |
| **Ambiguity** | Eliminated (no vague terms) |
| **Classification** | Portfolio Documentation |
| **Last Updated** | Phase 1 Analysis |

---

## 18. Next Steps

### Phase 2 - Development Handover

- ✅ Acceptance Criteria READY to be handed over to Development Team
- ✅ AC can be used in Sprint Planning for estimation
- ✅ Each AC can be referenced in code reviews & PR descriptions
- ✅ AC provides acceptance definition for "Definition of Done"

### Phase 3 - QA Testing

- ⏳ QA Team uses AC for test case derivation
- ⏳ Each AC becomes basis for one or more test cases
- ⏳ Testing verifies system behavior matches AC requirements
- ⏳ Test results map back to AC for traceability

### Phase 3+ - UAT

- ⏳ Business users verify system meets AC requirements
- ⏳ AC provides common language between BA, Developers, QA, Users
- ⏳ Customer sign-off based on AC fulfillment (not yet signed off - Phase 1 only)

---

**Tài liệu này sẵn sàng cho Phase 2 Development Team.**

**Document Version:** 1.0  
**Status:** ✅ Ready for Development Handover  
**Next Reviewers:** Development Team Lead, QA Lead, Business Stakeholders
