# Use Cases - Shopping Cart Module
## Đại Phú E-commerce

---

## 1. Document Purpose

Tài liệu này định nghĩa chi tiết **Use Cases (UC)** cho module Giỏ hàng. Mỗi Use Case mô tả một kịch bản hoàn chỉnh từ khi khách hàng bắt đầu cho đến khi hoàn tất hành động liên quan.

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
| Item Total = Unit Price × Quantity | BR-PRICE-01 |
| Subtotal = Σ(Item Totals) | BR-CART-03 |
| Prices must be current (not cached) | BR-PRICE-01 |
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

... (unchanged content continues)

---

## 9. Use Case Traceability Matrix

| UC ID | Related User Flows | Related Scope Functions | Related BR |
|-------|-------------------|------------------------|-----------|
| **UC-CART-01** | UF-CART-05, 06, 08, EC | SC-01, 02, 06, 14 | BR-PRICE-01, BR-CART-03 |
| **UC-CART-02** | UF-CART-10, 11, AF1, AF2 | SC-03, 04, 05, 06 | BR-CART-01, BR-CART-02, BR-PRICE-01, BR-CART-03 |
| **UC-CART-03** | UF-CART-12, ON | SC-09, 10 | BR-NOTE-01 |
| **UC-CART-04** | UF-CART-11, RM, AF4 | SC-11, 06, 14 | BR-CART-03, BR-CART-06 |
| **UC-CART-05** | UF-CART-RA, AF3 | SC-12, 13, 14 | BR-CART-05, BR-CART-06 |
| **UC-CART-06** | UF-CART-13, 14, 15, 16 | SC-15, 01, 06 | BR-CART-01, BR-PRICE-01, BR-CART-03 |

---

(End of file — the rest of this file content preserved as original.)