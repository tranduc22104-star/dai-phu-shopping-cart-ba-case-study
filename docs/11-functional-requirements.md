# Functional Requirements Specification
## Shopping Cart Module - Đại Phú E-commerce

---

## 1. Document Purpose

Tài liệu này định nghĩa chi tiết **Functional Requirements (FR)** cho module Giỏ hàng. Mỗi FR mô tả một khả năng cụ thể mà **hệ thống phải cung cấp** để đáp ứng nhu cầu của khách hàng.

**Định dạng Requirement Statement:**
```
"Hệ thống phải [action/behavior]"
```

Mỗi FR:
- ✅ Độc lập, rõ ràng, có thể kiểm thử
- ✅ Không quy định công nghệ cụ thể (trừ khi cần thiết)
- ✅ Tách implementation note khỏi requirement
- ✅ Được prioritize theo MoSCoW (Must, Should, Could, Won't)

---

## 2. Functional Requirements Catalog

| FR ID | Requirement Name | Priority | Type | Status |
|-------|-----------------|----------|------|--------|
| **FR-CART-01** | Load and Display Product List | Must | Display | Analyzed |
| **FR-CART-02** | Display Product Information | Must | Display | Analyzed |
| **FR-CART-03** | Display Unit Price | Must | Display | Analyzed |
| **FR-CART-04** | Display Product Quantity | Must | Display | Analyzed |
| **FR-CART-05** | Increase Product Quantity | Must | Update | Analyzed |
| **FR-CART-06** | Decrease Product Quantity | Must | Update | Analyzed |
| **FR-CART-07** | Enforce Minimum Quantity | Must | Validation | Analyzed |
| **FR-CART-08** | Calculate Item Total | Must | Calculation | Analyzed |
| **FR-CART-09** | Calculate Subtotal | Must | Calculation | Analyzed |
| **FR-CART-10** | Display Grand Total | Must | Display | Analyzed |
| **FR-CART-11** | Accept Order Note Input | Should | Input | Analyzed |
| **FR-CART-12** | Validate Order Note | Should | Validation | Analyzed |
| **FR-CART-13** | Remove Single Product | Must | Delete | Analyzed |
| **FR-CART-14** | Remove All Products | Must | Delete | Analyzed |
| **FR-CART-15** | Display Confirmation Dialog | Must | UI | Analyzed |
| **FR-CART-16** | Display Empty Cart State | Must | Display | Analyzed |
| **FR-CART-17** | Proceed to Checkout | Must | Navigation | Analyzed |
| **FR-CART-18** | Persist Cart State | Should | Storage | Analyzed |
| **TOTAL** | | | | **18 FR** |

---

## 3. Functional Requirement: FR-CART-01

### 3.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-01 |
| **Requirement Name** | Load and Display Product List |
| **Priority** | 🔴 **Must** (Essential) |
| **Type** | Display / Data Retrieval |
| **Phase** | Phase 1 (Analyzed) |
| **Status** | ✅ Analyzed |

### 3.2. Requirement Statement

```
Hệ thống phải tải danh sách tất cả các sản phẩm 
trong giỏ hàng của khách hàng từ backend 
và hiển thị chúng trên giao diện cart page.
```

**English Translation:**
```
The system must load the list of all products 
in the customer's shopping cart from the backend 
and display them on the cart page interface.
```

### 3.3. Detailed Description

**Purpose:**
Cho phép khách hàng xem tất cả các sản phẩm họ đã thêm vào giỏ hàng.

**Scope:**
- Retrieve cart data from backend API/database
- Identify all products in customer's cart
- Parse product information (ID, name, quantity, etc.)
- Render product list on cart page

**Constraints:**
- Data must be current (not stale/cached from previous session)
- All products must be displayed (no omissions)
- No duplicate products in list
- Handle edge case: cart may be empty (0 products)

**Non-Constraints:**
- No specific technology required (REST API, GraphQL, or other)
- No specific frontend framework required (vanilla JS, React, Vue, etc.)
- Display format flexible (table, list, grid)

### 3.4. Source

| Source | Reference |
|--------|-----------|
| **Business Need** | BN-CART-01 (Tài liệu hóa Functional Requirements) |
| **User Flow** | UF-CART-05, UF-CART-06 (View Cart flows) |
| **Use Case** | UC-CART-01 (View and Manage Shopping Cart) |
| **User Story** | US-CART-01 (View Shopping Cart) |

### 3.5. Related Requirements

| Type | ID | Link | Relationship |
|------|-----|------|--------------|
| **Use Case** | UC-CART-01 | View Cart | Implemented by FR-CART-01 |
| **User Story** | US-CART-01 | View Shopping Cart | Fulfills US-CART-01 |
| **AC** | AC-CART-01.01 | Display All Products | Implements AC-CART-01.01 |
| **AC** | AC-CART-01.04 | Current Cart Data | Ensures data freshness |
| **Business Rule** | BR-CART-03 | Prices Auto-Recalculate | Data source |
| **Scope Function** | SC-01 | View products in cart | Direct implementation |

### 3.6. Verification Method

| Method | Details |
|--------|---------|
| **Functional Testing** | Verify products display correctly |
| **Data Verification** | Compare displayed data with backend |
| **Completeness Check** | Ensure no products omitted |
| **Emptiness Check** | Handle empty cart case |
| **Performance Test** | Load time acceptable (TBD threshold) |

### 3.7. Acceptance Criteria Reference

This FR is verified by:
- ✅ **AC-CART-01.01** - Display All Products in Cart
- ✅ **AC-CART-01.04** - Display Current and Accurate Cart Data

### 3.8. Status & Timeline

| Phase | Status | Timeline |
|-------|--------|----------|
| **Phase 1** | ✅ **ANALYZED** | Current |
| **Phase 2** | ⏳ Pending | Development |
| **Phase 3** | ⏳ Pending | Testing |
| **Phase 4+** | ⏳ Pending | Deployment |

### 3.9. Open Questions

| Question | Current Status | Resolution Path |
|----------|-----------------|-----------------|
| **Q1** | What API will provide product data? (REST, GraphQL, other?) | Cần xác nhận | Architecture decision |
| **Q2** | What's the maximum acceptable load time? | Cần xác nhận | NFR-CART-01 timing |
| **Q3** | Should cart data be cached locally? If yes, how often refresh? | Cần xác nhận | Caching strategy |
| **Q4** | How to handle product no longer in catalog? | Cần xác nhận | Error handling |

### 3.10. Implementation Notes

**Note:** These are suggestions, not requirements:
- Consider using pagination if cart > 100 items (TBD threshold)
- Could implement infinite scroll or lazy loading
- May cache cart data in session storage for performance
- Could use AJAX/fetch to load cart asynchronously

---

## 4. Functional Requirement: FR-CART-02

### 4.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-02 |
| **Requirement Name** | Display Product Information |
| **Priority** | 🔴 **Must** |
| **Type** | Display |
| **Status** | ✅ Analyzed |

### 4.2. Requirement Statement

```
Hệ thống phải hiển thị thông tin chi tiết 
của mỗi sản phẩm trong giỏ hàng bao gồm: 
hình ảnh, tên sản phẩm, và các chi tiết liên quan.
```

### 4.3. Detailed Description

**For each product in cart, display:**
- Product image/thumbnail
- Product name (full name, with fallback for long names)
- Product ID or SKU (if applicable)
- Other product attributes (color, size, variant - if stored)

**Requirements:**
- Information must be accurate and current
- Product name should not be truncated mid-word (if truncation needed)
- Product image must load successfully
- All product attributes relevant to customer must be visible

### 4.4. Source

| Source | Reference |
|--------|-----------|
| **Use Case** | UC-CART-01 (View and Manage Shopping Cart) |
| **User Story** | US-CART-01 (View Shopping Cart) |
| **Scope Function** | SC-02 (Display product information) |

### 4.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-01.01 | Display All Products in Cart |
| **AC** | AC-CART-01.02 | Display Long Product Names |
| **Business Rule** | BR-PROD-02 | Long Product Name Display Rule |

### 4.6. Verification Method

- Visual inspection: All product info visible
- Data accuracy: Compare with source data
- Format check: Names properly displayed (no truncation)

### 4.7. Status

**Phase 1:** ✅ Analyzed  
**Phase 2:** ⏳ Pending Development

### 4.8. Open Questions

| Question | Status |
|----------|--------|
| Should product description be shown? | Cần xác nhận |
| Max product name display length? | Cần xác nhận |
| Should customer reviews be shown in cart? | Cần xác nhận |

---

## 5. Functional Requirement: FR-CART-03

### 5.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-03 |
| **Requirement Name** | Display Unit Price |
| **Priority** | 🔴 **Must** |
| **Type** | Display |
| **Status** | ✅ Analyzed |

### 5.2. Requirement Statement

```
Hệ thống phải hiển thị đơn giá của mỗi sản phẩm 
trong giỏ hàng dưới dạng tiền tệ được định dạng.
```

### 5.3. Detailed Description

**Display unit price for each product:**
- Price formatted as currency (e.g., "50,000 VND" or "$50.00")
- Use consistent formatting throughout cart
- Price must be current (fetch from backend, not cached old price)
- Decimal places per currency standard (typically 0 for VND, 2 for USD)
- Show currency symbol or code (VND, USD, etc.)

### 5.4. Source

| Source | Reference |
|--------|-----------|
| **Use Case** | UC-CART-01 |
| **User Story** | US-CART-01 |
| **Scope Function** | SC-02, SC-06 (Display product info, calculations) |
| **Business Rule** | BR-CART-03 (Prices Auto-Recalculate) |

### 5.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-01.01 | Display Product List (includes unit price) |
| **AC** | AC-CART-01.04 | Current Cart Data (prices fresh) |
| **FR** | FR-CART-08 | Calculate Item Total (uses unit price) |

### 5.6. Verification Method

- Check price formatting (currency symbol, decimals)
- Verify prices match backend current prices
- Test currency conversion (if applicable)

### 5.7. Open Questions

| Question | Status |
|----------|--------|
| How many decimal places for VND? (0 vs 2) | Cần xác nhận |
| Should discount prices be shown separately? | Cần xác nhận |
| Should product be marked if price changed since added to cart? | Cần xác nhận |

---

## 6. Functional Requirement: FR-CART-04

### 6.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-04 |
| **Requirement Name** | Display Product Quantity |
| **Priority** | 🔴 **Must** |
| **Type** | Display |
| **Status** | ✅ Analyzed |

### 6.2. Requirement Statement

```
Hệ thống phải hiển thị số lượng (quantity) 
của mỗi sản phẩm trong giỏ hàng 
dưới dạng số nguyên dương (≥1).
```

### 6.3. Detailed Description

**Display quantity for each product:**
- Show current quantity as numeric value (e.g., "2", "10")
- Quantity must be ≥1 (per BR-CART-01)
- Quantity must be integer (per BR-CART-02, no decimals)
- Quantity should be editable (enable increase/decrease controls)

### 6.4. Source

| Source | Reference |
|--------|-----------|
| **Use Case** | UC-CART-01, UC-CART-02 |
| **User Story** | US-CART-01, US-CART-02 |
| **Scope Function** | SC-01, SC-03, SC-04 |
| **Business Rules** | BR-CART-01, BR-CART-02 |

### 6.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-01.01 | Display All Products (includes qty) |
| **AC** | AC-CART-02.01 | Increase Product Quantity |
| **FR** | FR-CART-05 | Increase Product Quantity |
| **FR** | FR-CART-06 | Decrease Product Quantity |

### 6.6. Verification Method

- Visual check: Quantity displayed as integer
- Boundary check: Qty ≥1
- Calculation check: Qty matches stored value

### 6.7. Open Questions

| Question | Status |
|----------|--------|
| Should quantity have a visual input field or button control? | Cần xác nhận |
| Max quantity per product? | Cần xác nhận |

---

## 7. Functional Requirement: FR-CART-05

### 7.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-05 |
| **Requirement Name** | Increase Product Quantity |
| **Priority** | 🔴 **Must** |
| **Type** | Update / Calculation |
| **Status** | ✅ Analyzed |

### 7.2. Requirement Statement

```
Hệ thống phải cho phép khách hàng tăng số lượng 
sản phẩm bằng cách nhấp nút "+" hoặc chỉnh sửa trực tiếp, 
và phải cập nhật thành tiền và tạm tính tương ứng.
```

### 7.3. Detailed Description

**When customer increases quantity:**
1. Accept user input (click "+" button OR direct edit)
2. Increment quantity by 1 (or new value if direct edit)
3. Validate new quantity (must be positive integer, optional max check)
4. Recalculate Item Total (Unit Price × New Qty) - FR-CART-08
5. Recalculate Subtotal (sum of all Item Totals) - FR-CART-09
6. Update display in real-time (no page refresh)
7. Persist changes to backend
8. Provide confirmation feedback to customer

### 7.4. Source

| Source | Reference |
|--------|-----------|
| **Use Case** | UC-CART-02 (Update Product Quantity - Increase Flow) |
| **User Story** | US-CART-02 (Update Product Quantity) |
| **Scope Function** | SC-03, SC-06, SC-07 |
| **Business Rules** | BR-CART-03 (Prices Auto-Recalculate) |

### 7.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-02.01 | Increase Product Quantity |
| **AC** | AC-CART-02.04 | Real-time Price Calculation |
| **FR** | FR-CART-08 | Calculate Item Total |
| **FR** | FR-CART-09 | Calculate Subtotal |

### 7.6. Verification Method

- Functional test: Quantity increments correctly
- Calculation test: Item Total recalculated (Unit Price × New Qty)
- Calculation test: Subtotal recalculated
- UI test: Display updates without refresh
- Data test: Backend updated

### 7.7. Open Questions

| Question | Status |
|----------|--------|
| Should there be a maximum quantity limit? | Cần xác nhận |
| How quickly should backend sync (real-time vs batch)? | Cần xác nhận |
| Should system notify customer of successful update? | Cần xác nhận |

---

## 8. Functional Requirement: FR-CART-06

### 8.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-06 |
| **Requirement Name** | Decrease Product Quantity |
| **Priority** | 🔴 **Must** |
| **Type** | Update / Calculation |
| **Status** | ✅ Analyzed |

### 8.2. Requirement Statement

```
Hệ thống phải cho phép khách hàng giảm số lượng sản phẩm 
xuống (tối thiểu 1), và phải cập nhật thành tiền và tạm tính.
```

### 8.3. Detailed Description

**When customer decreases quantity:**
1. Accept user input (click "-" button OR direct edit)
2. Decrement quantity by 1 (or new value if direct edit)
3. Validate new quantity (must be ≥1, enforced by FR-CART-07)
4. If validation fails (qty < 1), reject and inform customer
5. Recalculate Item Total (if qty decreased)
6. Recalculate Subtotal
7. Update display in real-time
8. Persist changes
9. Product stays in cart (not removed by decrease action alone)

### 8.4. Source

| Source | Reference |
|--------|-----------|
| **Use Case** | UC-CART-02 (Update Qty - Decrease Flow) |
| **User Story** | US-CART-02 |
| **Scope Function** | SC-04, SC-06, SC-07 |
| **Business Rules** | BR-CART-01 (Min Qty = 1), BR-CART-03 |

### 8.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-02.02 | Decrease Product Quantity |
| **AC** | AC-CART-02.03 | Enforce Minimum Quantity = 1 |
| **FR** | FR-CART-07 | Enforce Minimum Quantity |

### 8.6. Verification Method

- Functional test: Quantity decrements (but not below 1)
- Boundary test: Qty cannot go below 1
- Calculation test: Item Total & Subtotal updated
- Error handling test: Invalid decreases rejected

### 8.7. Open Questions

| Question | Status |
|----------|--------|
| Should "-" button be disabled when qty=1, or show error message? | Cần xác nhận |
| Should product be auto-removed when qty reaches 0? | Cần xác nhận |

---

## 9. Functional Requirement: FR-CART-07

### 9.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-07 |
| **Requirement Name** | Enforce Minimum Quantity |
| **Priority** | 🔴 **Must** |
| **Type** | Validation |
| **Status** | ✅ Analyzed |

### 9.2. Requirement Statement

```
Hệ thống phải ngăn chặn số lượng sản phẩm 
bằng 0 hoặc âm. Số lượng tối thiểu là 1.
```

### 9.3. Detailed Description

**Validation rule:**
- No product in cart can have quantity < 1
- If user attempts to set quantity to 0 or negative: reject and show error
- Methods to enforce:
  - Disable "-" button when qty=1
  - Show error message "Cannot reduce below 1"
  - Silent rejection (no action on attempt to go below 1)
- Implementation method TBD (Cần xác nhận)

### 9.4. Source

| Source | Reference |
|--------|-----------|
| **Business Rule** | BR-CART-01 (Minimum Quantity = 1) |
| **Scope Function** | SC-05 (Prevent quantity < 1) |

### 9.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-02.03 | Enforce Minimum Quantity of 1 |
| **AC** | AC-CART-02.04 | Reject Zero or Negative Input |
| **FR** | FR-CART-06 | Decrease Product Quantity |

### 9.6. Verification Method

- Boundary test: Cannot set qty to 0
- Boundary test: Cannot set qty to negative
- UI test: Error message or disabled state shown
- Business logic test: Backend rejects invalid qty

### 9.7. Open Questions

| Question | Status |
|----------|--------|
| Which enforcement method? (disable button / error message / silent) | Cần xác nhận |

---

## 10. Functional Requirement: FR-CART-08

### 10.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-08 |
| **Requirement Name** | Calculate Item Total |
| **Priority** | 🔴 **Must** |
| **Type** | Calculation |
| **Status** | ✅ Analyzed |

### 10.2. Requirement Statement

```
Hệ thống phải tính toán thành tiền (Item Total) 
của mỗi sản phẩm bằng công thức: 
Thành tiền = Đơn giá × Số lượng
```

### 10.3. Detailed Description

**Calculation:**
- Formula: Item Total = Unit Price × Quantity
- Example: 50,000 VND × 2 = 100,000 VND
- Calculation must use current unit price (not stale price)
- Result must be formatted as currency (matching FR-CART-03)
- Calculation must be accurate (no floating-point errors)
- Recalculate whenever quantity changes (FR-CART-05, FR-CART-06)
- Recalculate whenever unit price changes

### 10.4. Source

| Source | Reference |
|--------|-----------|
| **Business Rule** | BR-CART-03 (Item Total Calculation Rule) |
| **Scope Function** | SC-06 (Calculate item total) |

### 10.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-02.01 | Increase Qty (triggers recalc) |
| **AC** | AC-CART-02.02 | Decrease Qty (triggers recalc) |
| **AC** | AC-CART-02.04 | Real-time Price Calculation |
| **FR** | FR-CART-05 | Increase Product Quantity |
| **FR** | FR-CART-09 | Calculate Subtotal (uses Item Totals) |

### 10.6. Verification Method

- Calculation test: Item Total = Unit Price × Qty
- Accuracy test: Results mathematically correct
- Recalculation test: Updates when qty/price changes
- Formatting test: Currency format consistent

### 10.7. Open Questions

| Question | Status |
|----------|--------|
| How to handle floating-point precision? | Cần xác nhận |
| Should Item Total be displayed to 2 decimal places? | Cần xác nhận |

---

## 11. Functional Requirement: FR-CART-09

### 11.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-09 |
| **Requirement Name** | Calculate Subtotal |
| **Priority** | 🔴 **Must** |
| **Type** | Calculation |
| **Status** | ✅ Analyzed |

### 11.2. Requirement Statement

```
Hệ thống phải tính toán tạm tính (Subtotal) 
bằng tổng của tất cả thành tiền sản phẩm:
Tạm tính = Σ(Thành tiền của từng sản phẩm)
```

### 11.3. Detailed Description

**Calculation:**
- Formula: Subtotal = Sum of all Item Totals
- Example: 100,000 + 75,000 + 50,000 = 225,000 VND
- Includes all products in cart
- Exclude shipping, tax, discounts (if not included) - per requirement
- Display as currency (formatted)
- Recalculate whenever any Item Total changes
- Update display in real-time

### 11.4. Source

| Source | Reference |
|--------|-----------|
| **Business Rule** | BR-CART-04 (Subtotal Calculation Rule) |
| **Scope Function** | SC-07 (Calculate subtotal) |

### 11.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-01.03 | Display Cart Summary (includes subtotal) |
| **FR** | FR-CART-08 | Calculate Item Total (input to subtotal) |
| **FR** | FR-CART-10 | Display Grand Total |

### 11.6. Verification Method

- Calculation test: Subtotal = Σ(Item Totals)
- Accuracy test: Results correct
- Update test: Recalculates when products added/removed/modified

---

## 12. Functional Requirement: FR-CART-10

### 12.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-10 |
| **Requirement Name** | Display Grand Total |
| **Priority** | 🔴 **Must** |
| **Type** | Display / Calculation |
| **Status** | ✅ Analyzed |

### 12.2. Requirement Statement

```
Hệ thống phải hiển thị tổng tiền (Grand Total) 
của giỏ hàng. Tổng tiền = Tạm tính 
(vì chưa tính phí vận chuyển/thuế ở bước này).
```

### 12.3. Detailed Description

**Display:**
- Show Grand Total in cart summary section
- Format as currency (e.g., "225,000 VND")
- Label clearly as "Total" or "Grand Total"
- Currently: Grand Total = Subtotal (no shipping/tax added yet)
- Update in real-time when subtotal changes
- Place in prominent location (summary section)

**Note:** Shipping fees, taxes, discounts to be handled in Checkout module (out of scope for Shopping Cart)

### 12.4. Source

| Source | Reference |
|--------|-----------|
| **Business Rule** | BR-CART-05 (Grand Total Rule) |
| **Scope Function** | SC-07 (Subtotal/Total calculation) |

### 12.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-01.03 | Display Cart Summary |
| **FR** | FR-CART-09 | Calculate Subtotal |

### 12.6. Verification Method

- Display test: Grand Total visible in summary
- Value test: Grand Total = Subtotal (at this stage)
- Formatting test: Currency formatted correctly
- Update test: Recalculates when cart changes

---

## 13. Functional Requirement: FR-CART-11

### 13.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-11 |
| **Requirement Name** | Accept Order Note Input |
| **Priority** | 🟠 **Should** (Important, but not critical) |
| **Type** | Input |
| **Status** | ✅ Analyzed |

### 13.2. Requirement Statement

```
Hệ thống phải cho phép khách hàng nhập ghi chú 
cho đơn hàng trong một trường văn bản.
```

### 13.3. Detailed Description

**Input field:**
- Provide text input field (textarea or input) for order notes
- Field should be labeled "Order Notes" or similar
- Field should be optional (not required to checkout)
- Accept up to 256 characters (per BR-NOTE-01)
- Auto-save OR provide Save button (TBD)
- Show character count feedback (e.g., "45/256")

### 13.4. Source

| Source | Reference |
|--------|-----------|
| **Use Case** | UC-CART-03 (Add Order Note) |
| **User Story** | US-CART-03 (Add Order Note) |
| **Scope Function** | SC-09 (Order note functionality) |

### 13.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-03.01 | Enter Order Note (≤256) |
| **AC** | AC-CART-03.02 | Note = 256 Chars (boundary) |
| **FR** | FR-CART-12 | Validate Order Note |

### 13.6. Verification Method

- UI test: Input field visible and functional
- Input test: Text accepted and displayed
- Persistence test: Note saved with cart

---

## 14. Functional Requirement: FR-CART-12

### 14.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-12 |
| **Requirement Name** | Validate Order Note |
| **Priority** | 🟠 **Should** |
| **Type** | Validation |
| **Status** | ✅ Analyzed |

### 14.2. Requirement Statement

```
Hệ thống phải xác thực ghi chú đơn hàng 
không vượt quá 256 ký tự.
```

### 14.3. Detailed Description

**Validation rules:**
- Maximum length: 256 characters
- If note exceeds limit:
  - **Option A:** Truncate to 256 characters (auto-fix)
  - **Option B:** Show error message (user must fix)
  - **Option C:** Block paste if > 256 chars
  - (Implementation method TBD - Cần xác nhận)
- Display character count in real-time
- Only allow valid note (≤256 chars) to be saved to backend

### 14.4. Source

| Source | Reference |
|--------|-----------|
| **Business Rule** | BR-NOTE-01 (Order Note Character Limit) |
| **Scope Function** | SC-10 (Validate note) |

### 14.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-03.01 | Valid Note (≤256) |
| **AC** | AC-CART-03.02 | Note = 256 (boundary) |
| **AC** | AC-CART-03.03 | Note > 256 (rejected) |
| **FR** | FR-CART-11 | Accept Order Note Input |

### 14.6. Verification Method

- Boundary test: Accept note at exactly 256 chars
- Negative test: Reject note > 256 chars
- Error handling test: User informed of violation
- Persistence test: Only valid notes saved

---

## 15. Functional Requirement: FR-CART-13

### 15.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-13 |
| **Requirement Name** | Remove Single Product |
| **Priority** | 🔴 **Must** |
| **Type** | Delete / Update |
| **Status** | ✅ Analyzed |

### 15.2. Requirement Statement

```
Hệ thống phải cho phép khách hàng xóa một sản phẩm 
khỏi giỏ hàng bằng cách nhấp nút "Remove". 
Không cần xác nhận cho hành động này.
```

### 15.3. Detailed Description

**Remove single product:**
1. Customer clicks "Remove" button for specific product
2. No confirmation dialog shown (single item removal is quick action)
3. Product removed from cart immediately
4. Recalculate subtotal (remove item's contribution)
5. Update product list display (product disappears)
6. Update item count (e.g., "2 items" → "1 item")
7. Persist change to backend
8. Provide visual feedback (product smoothly removed)
9. If this was last product, transition to empty state (FR-CART-16)

### 15.4. Source

| Source | Reference |
|--------|-----------|
| **Use Case** | UC-CART-04 (Remove One Product) |
| **User Story** | US-CART-04 (Remove One Product) |
| **Scope Function** | SC-11 (Remove one product) |

### 15.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-04.01 | Remove Single Product |
| **AC** | AC-CART-04.02 | Last Item Removal (→ empty) |
| **FR** | FR-CART-09 | Calculate Subtotal (recalc after removal) |
| **FR** | FR-CART-16 | Display Empty Cart State |

### 15.6. Verification Method

- Functional test: Product removed correctly
- Data test: Subtotal recalculated
- Persistence test: Backend updated
- State test: Empty state shown if last item removed

---

## 16. Functional Requirement: FR-CART-14

### 16.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-14 |
| **Requirement Name** | Remove All Products |
| **Priority** | 🔴 **Must** |
| **Type** | Delete / Confirmation |
| **Status** | ✅ Analyzed |

### 16.2. Requirement Statement

```
Hệ thống phải cho phép khách hàng xóa toàn bộ 
sản phẩm trong giỏ hàng sau khi xác nhận 
bằng cách nhấp "Clear All" và cọn "Confirm".
```

### 16.3. Detailed Description

**Remove all products:**
1. Customer clicks "Clear All" button
2. Show confirmation dialog (FR-CART-15 - required, see business rule BR-CART-04)
3. If customer clicks "Confirm":
   - Remove ALL products from cart
   - Clear notes (if any)
   - Subtotal becomes 0
   - Transition to empty state (FR-CART-16)
   - Persist to backend (cart now empty)
4. If customer clicks "Cancel":
   - Close dialog, cart unchanged

### 16.4. Source

| Source | Reference |
|--------|-----------|
| **Use Case** | UC-CART-05 (Remove All Products) |
| **User Story** | US-CART-05 (Remove All Products) |
| **Business Rule** | BR-CART-04 (Clear All Requires Confirmation) |
| **Scope Function** | SC-12, SC-13 (Clear all, confirmation) |

### 16.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-05.01 | Display Confirmation Dialog |
| **AC** | AC-CART-05.02 | Confirm Clear (remove all) |
| **AC** | AC-CART-05.03 | Cancel Clear (preserve items) |
| **FR** | FR-CART-15 | Display Confirmation Dialog |
| **FR** | FR-CART-16 | Display Empty Cart State |

### 16.6. Verification Method

- Dialog test: Confirmation shown
- Functional test: All products removed on confirm
- Data test: Backend cleared
- State test: Empty state displayed
- Rollback test: All preserved if cancel

---

## 17. Functional Requirement: FR-CART-15

### 17.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-15 |
| **Requirement Name** | Display Confirmation Dialog |
| **Priority** | 🔴 **Must** |
| **Type** | UI / Confirmation |
| **Status** | ✅ Analyzed |

### 17.2. Requirement Statement

```
Hệ thống phải hiển thị hộp thoại xác nhận 
khi khách hàng yêu cầu xóa toàn bộ sản phẩm 
trong giỏ hàng.
```

### 17.3. Detailed Description

**Confirmation dialog:**
- Displayed when "Clear All" button clicked
- Title/Message: "Are you sure you want to remove all items?" (or similar)
- Provides two options:
  - "Confirm" / "Yes" button (primary destructive action)
  - "Cancel" / "No" button (safe, default focus)
- Dialog is modal (user cannot interact with cart while dialog open)
- Dialog cannot be dismissed by clicking outside (modal behavior - TBD if needed)
- Can be dismissed by Escape key (TBD if allowed)
- Dialog clearly indicates consequence of confirming

### 17.4. Source

| Source | Reference |
|--------|-----------|
| **Business Rule** | BR-CART-04 (Clear All Requires Confirmation) |
| **Scope Function** | SC-13 (Confirmation dialog) |
| **Use Case** | UC-CART-05 (Remove All Products) |

### 17.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-05.01 | Display Confirmation Dialog |
| **FR** | FR-CART-14 | Remove All Products |

### 17.6. Verification Method

- UI test: Dialog appears when "Clear All" clicked
- Content test: Message is clear and explicit
- Button test: "Confirm" and "Cancel" buttons present
- Interaction test: Dialog is modal

---

## 18. Functional Requirement: FR-CART-16

### 18.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-16 |
| **Requirement Name** | Display Empty Cart State |
| **Priority** | 🔴 **Must** |
| **Type** | Display / State |
| **Status** | ✅ Analyzed |

### 18.2. Requirement Statement

```
Hệ thống phải hiển thị trạng thái giỏ hàng trống 
khi không có sản phẩm nào trong giỏ hàng.
```

### 18.3. Detailed Description

**Empty cart state display:**
- Show when cart contains 0 products (either on initial visit or after clearing)
- Display message: "Your cart is empty" (or similar friendly message)
- Hide product list (no table/grid shown)
- Hide subtotal/total sections (or show as 0)
- Hide "Proceed to Checkout" button (disabled or hidden)
- Show "Continue Shopping" button (prominent call-to-action)
- "Continue Shopping" button navigates to product listing
- Empty state should be user-friendly and encouraging

### 18.4. Source

| Source | Reference |
|--------|-----------|
| **Business Rule** | BR-CART-05 (Empty Cart → Empty State) |
| **Scope Function** | SC-14 (Display empty-cart state) |
| **Use Case** | UC-CART-01 (AF-01 - Empty Cart Alternative Flow) |
| **User Story** | US-CART-06 (View Empty Cart State) |

### 18.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-06.01 | Display Empty Cart Message |
| **AC** | AC-CART-06.02 | Show Continue Shopping Button |
| **AC** | AC-CART-06.03 | Checkout Button Disabled |
| **AC** | AC-CART-06.04 | Empty State Persists |
| **FR** | FR-CART-13 | Remove Single Product (→ empty if last) |
| **FR** | FR-CART-14 | Remove All Products (→ empty) |

### 18.6. Verification Method

- Display test: Empty message shown when cart empty
- Button test: "Continue Shopping" available and clickable
- Checkout test: Checkout button disabled/hidden
- Navigation test: "Continue Shopping" navigates to product listing

---

## 19. Functional Requirement: FR-CART-17

### 19.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-17 |
| **Requirement Name** | Proceed to Checkout |
| **Priority** | 🔴 **Must** |
| **Type** | Navigation / Handoff |
| **Status** | ✅ Analyzed |

### 19.2. Requirement Statement

```
Hệ thống phải cho phép khách hàng chuyển từ giỏ hàng 
sang bước nhập thông tin thanh toán (Checkout) 
bằng cách nhấp nút "Proceed to Checkout".
```

### 19.3. Detailed Description

**Proceed to Checkout:**
1. Customer reviews final cart (all products, quantities, notes, totals visible)
2. Customer clicks "Proceed to Checkout" button
3. System validates cart:
   - Cart not empty (≥1 product)
   - All quantities valid (≥1)
   - Prices current (recalculated from backend)
   - Subtotal calculated correctly
4. If validation passes:
   - Transfer cart data to Checkout module (product list, subtotal, notes)
   - Navigate to Checkout page
   - Shopping Cart flow ends; Checkout flow begins
5. If validation fails:
   - Show error message to customer
   - Allow customer to return to cart to fix issues

### 19.4. Source

| Source | Reference |
|--------|-----------|
| **Use Case** | UC-CART-06 (Proceed to Checkout Information) |
| **User Story** | US-CART-07 (Proceed to Checkout Information) |
| **Scope Function** | SC-15 (Proceed to checkout) |

### 19.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-07.01 | Validate Cart Before Handoff |
| **AC** | AC-CART-07.02 | Navigate to Checkout Module |
| **Business Rules** | BR-CART-01, BR-CART-03 | Qty validation, price recalc |

### 19.6. Verification Method

- Validation test: Cart validated before handoff
- Navigation test: Successfully redirects to Checkout page
- Data test: Cart data transferred correctly
- Error test: Invalid carts rejected with clear error messages

### 19.7. Open Questions

| Question | Status |
|----------|--------|
| What's the exact handoff data format to Checkout? | Cần xác nhận |
| Should cart be cleared after handoff? | Cần xác nhận |
| How to handle Checkout module unavailability? | Cần xác nhận |

---

## 20. Functional Requirement: FR-CART-18

### 20.1. Requirement Metadata

| Attribute | Value |
|-----------|-------|
| **FR ID** | FR-CART-18 |
| **Requirement Name** | Persist Cart State |
| **Priority** | 🟠 **Should** (Important, dependent on evidence) |
| **Type** | Storage / Session |
| **Status** | ✅ Analyzed |

### 20.2. Requirement Statement

```
Hệ thống nên lưu trữ trạng thái giỏ hàng 
(sản phẩm, số lượng, ghi chú) 
sao cho khách hàng có thể quay lại 
và tìm thấy giỏ hàng vẫn còn nguyên vẹn 
nếu có bằng chứng từ stakeholder xác nhận.
```

### 20.3. Detailed Description

**Cart persistence:**
- Save cart data when changes occur (add, update qty, remove, add note)
- Persist to:
  - Backend database (primary) OR
  - Session storage (client-side) OR
  - Combination of both
  - (Architecture TBD - Cần xác nhận)
- When customer returns to cart page:
  - Load cart state from storage
  - Display saved products, quantities, notes
  - Recalculate totals from loaded data
- Persistence strategy: Server-side preferred for security/reliability
- Cart should survive:
  - Browser refresh (page reload)
  - Tab close and reopen
  - Session expiry handling (TBD)
  - Extended period between visits (duration TBD - Cần xác nhận)

**Note:** This requirement is marked "Should" pending evidence from stakeholder that cart persistence is explicitly required. If not explicitly requested, could be deprioritized.

### 20.4. Source

| Source | Reference |
|--------|-----------|
| **User Flow** | UF-CART-AF2 (Return to Cart After Modifications) |
| **Acceptance Criteria** | AC-CART-01.04 (Display Current Cart Data) |

### 20.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **AC** | AC-CART-01.04 | Display Current Cart Data (assumes persistence) |
| **AC** | AC-CART-06.04 | Empty State Persists |
| **FR** | FR-CART-01 | Load and Display Product List |

### 20.6. Verification Method

- Persistence test: Cart data saved after changes
- Reload test: Data remains after page refresh
- Duration test: Data persists across sessions (duration TBD)
- Data integrity test: Loaded data matches saved data

### 20.7. Open Questions

| Question | Current Status | Impact |
|----------|---|---|
| **Q1** | Is cart persistence explicitly required by stakeholder? | Cần xác nhận | Scope decision |
| **Q2** | Server-side or client-side persistence preferred? | Cần xác nhận | Architecture |
| **Q3** | How long should cart persist (1 day, 7 days, indefinite)? | Cần xác nhận | Implementation |
| **Q4** | Should cart be tied to customer account or just session? | Cần xác nhận | Design decision |

### 20.8. Implementation Notes

**Suggestions (not requirements):**
- Could use browser localStorage for client-side persistence
- Could implement server-side cart sessions
- Could use cookies to track cart
- Could implement cart recovery for logged-in customers

---

## 21. Functional Requirements by Priority (MoSCoW)

### 🔴 Must Have (Critical - 13 FR)

These are essential for Shopping Cart module functionality:
- FR-CART-01: Load and Display Product List
- FR-CART-02: Display Product Information
- FR-CART-03: Display Unit Price
- FR-CART-04: Display Product Quantity
- FR-CART-05: Increase Product Quantity
- FR-CART-06: Decrease Product Quantity
- FR-CART-07: Enforce Minimum Quantity
- FR-CART-08: Calculate Item Total
- FR-CART-09: Calculate Subtotal
- FR-CART-10: Display Grand Total
- FR-CART-13: Remove Single Product
- FR-CART-14: Remove All Products
- FR-CART-15: Display Confirmation Dialog
- FR-CART-16: Display Empty Cart State
- FR-CART-17: Proceed to Checkout
- **Total: 15 Must**

### 🟠 Should Have (Important - 2 FR)

These enhance usability but could be deferred if needed:
- FR-CART-11: Accept Order Note Input
- FR-CART-12: Validate Order Note
- FR-CART-18: Persist Cart State (pending confirmation)
- **Total: 3 Should**

### 🟡 Could Have (Nice to Have - 0 FR)

- None identified in Phase 1
- **Total: 0 Could**

### ⚫ Won't Have (Out of Scope - 0 FR)

- None identified
- **Total: 0 Won't**

---

## 22. Functional Requirements Traceability

| FR ID | US | UC | BR | AC | Status |
|-------|-----|-----|-----|-----|--------|
| **FR-CART-01** | US-01 | UC-01 | BR-03 | AC-01.01 | ✅ |
| **FR-CART-02** | US-01 | UC-01 | BR-03 | AC-01.01, 02 | ✅ |
| **FR-CART-03** | US-01 | UC-01 | BR-03 | AC-01.01 | ✅ |
| **FR-CART-04** | US-01, 02 | UC-01, 02 | BR-01 | AC-01.01, 02.01 | ✅ |
| **FR-CART-05** | US-02 | UC-02 | BR-03 | AC-02.01, 04 | ✅ |
| **FR-CART-06** | US-02 | UC-02 | BR-03 | AC-02.02, 04 | ✅ |
| **FR-CART-07** | US-02 | UC-02 | BR-01 | AC-02.03, 04 | ✅ |
| **FR-CART-08** | US-02 | UC-02 | BR-03 | AC-02.01, 02, 04 | ✅ |
| **FR-CART-09** | US-01, 02, 03 | UC-01, 02 | BR-04 | AC-01.03 | ✅ |
| **FR-CART-10** | US-01 | UC-01 | BR-05 | AC-01.03 | ✅ |
| **FR-CART-11** | US-03 | UC-03 | - | AC-03.01, 02 | ✅ |
| **FR-CART-12** | US-03 | UC-03 | BR-02 | AC-03.01, 02, 03 | ✅ |
| **FR-CART-13** | US-04 | UC-04 | BR-03 | AC-04.01, 02 | ✅ |
| **FR-CART-14** | US-05 | UC-05 | BR-04 | AC-05.01, 02, 03 | ✅ |
| **FR-CART-15** | US-05 | UC-05 | BR-04 | AC-05.01 | ✅ |
| **FR-CART-16** | US-06 | UC-01(AF) | BR-05 | AC-06.01, 02, 03, 04 | ✅ |
| **FR-CART-17** | US-07 | UC-06 | BR-01, 03 | AC-07.01, 02 | ✅ |
| **FR-CART-18** | US-01 | UC-01(AF) | - | AC-01.04 | ✅ |

---

## 23. Important Disclaimers

### ✅ What These Functional Requirements Represent

- ✅ Detailed, technology-agnostic specifications from Phase 1 analysis
- ✅ What the system **must do** (behavior-focused, not implementation-focused)
- ✅ Foundation for Phase 2 development
- ✅ Traceability to User Stories, Use Cases, Business Rules, AC
- ✅ Reference for QA test case design (Phase 3)

### ❌ What These Functional Requirements Do NOT Represent

- ❌ Implementation or developed code
- ❌ Choice of specific technology (framework, database, API type)
- ❌ Complete system specification (NFR, data model, interface design separate)
- ❌ Completed development work
- ❌ Passed testing or UAT
- ❌ Production-ready features

### ⏳ Implementation Status

- **Phase 1:** ✅ FR analyzed & documented
- **Phase 2:** ⏳ FR used for development planning & estimation
- **Phase 3:** ⏳ FR basis for test case design & QA testing
- **Phase 4+:** ⏳ FR validated post-deployment

---

## 24. Items Needing Stakeholder Confirmation

### Critical Technical Decisions

| Item | Question | Impact |
|------|----------|--------|
| **Architecture** | Backend API tech (REST, GraphQL, other)? | FR-CART-01, 17 |
| **Persistence** | Server-side or client-side cart storage? | FR-CART-18 |
| **Sync Timing** | Real-time sync or batch updates? | FR-CART-05, 06 |
| **Display Rule** | Disable "-" button vs error message for min qty? | FR-CART-07 |
| **Confirmation** | How to handle note > 256 chars? | FR-CART-12 |
| **Empty State** | Should recommend products be shown? | FR-CART-16 |

### Business Decisions

| Item | Question | Impact |
|------|----------|--------|
| **Persistence Scope** | Is cart persistence explicitly required? | FR-CART-18 |
| **Note Persistence** | Should order notes be saved with cart? | FR-CART-11 |
| **Product Order** | FIFO or LIFO or other sort? | FR-CART-01 |
| **Max Qty** | Any maximum quantity per product? | FR-CART-05, 06 |
| **Decimal Qty** | Accept decimal quantities (2.5 units)? | FR-CART-04, 05, 06 |

---

## 25. Related Documents

| Document | Link | Relevance |
|----------|------|-----------|
| **docs/06-user-flow.md** | User Flows | Behavioral basis for FR |
| **docs/07-use-cases.md** | Use Cases | Detailed flows for FR |
| **docs/08-user-stories.md** | User Stories | Customer-facing requirements |
| **docs/09-acceptance-criteria.md** | AC | Verification criteria for FR |
| **docs/10-business-rules.md** | Business Rules | Constraints for FR |
| **.github/copilot-instructions.md** | BA Standards | Documentation format |

---

## 26. Document Metadata

| Attribute | Value |
|-----------|-------|
| **Document Type** | Functional Requirements Specification |
| **Phase** | Phase 1 - Analysis Complete |
| **Status** | ✅ Complete |
| **Total Functional Requirements** | 18 |
| **Must Have** | 15 (83%) |
| **Should Have** | 3 (17%) |
| **Could Have** | 0 (0%) |
| **Won't Have** | 0 (0%) |
| **Classification** | Portfolio Documentation |
| **Last Updated** | Phase 1 Analysis |

---

## 27. Next Steps

### Phase 2 - Development Handover

- ✅ FR READY for Development Team sprint planning
- ✅ Each FR can be broken down into tasks/subtasks
- ✅ Development effort can be estimated per FR
- ✅ FR provides acceptance definition for code review

### Phase 3 - QA Testing

- ⏳ QA Team derives test cases from FR
- ⏳ Each FR becomes one or more test cases
- ⏳ Testing verifies implemented system matches FR
- ⏳ Test results map back to FR for traceability

### Phase 3+ - UAT & Deployment

- ⏳ Business users verify system meets FR
- ⏳ FR provides common language between all stakeholders
- ⏳ Final sign-off based on FR fulfillment

---

**Tài liệu này sẵn sàng cho Phase 2 Development Team.**

**Document Version:** 1.0  
**Status:** ✅ Ready for Development Handover  
**Next Reviewers:** Development Team Lead, Architecture Team, Business Stakeholders
