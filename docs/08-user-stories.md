# User Stories - Shopping Cart Module
## Đại Phú E-commerce

---

## 1. Document Purpose

Tài liệu này định nghĩa **7 User Stories chính** cho module Giỏ hàng trong Phase 1. Mỗi User Story viết theo định dạng Agile chuẩn:

```
As a [actor],
I want [action],
So that [business value]
```

Mỗi User Story được đánh giá theo **INVEST Principles** để đảm bảo chất lượng.

---

## 2. User Story Catalog

| US ID | Title | Priority | Status | Related Use Case |
|-------|-------|----------|--------|------------------|
| **US-CART-01** | View Shopping Cart | 🔴 Critical | Analyzed | UC-CART-01 |
| **US-CART-02** | Update Product Quantity | 🔴 Critical | Analyzed | UC-CART-02 |
| **US-CART-03** | Add Order Note | 🟠 High | Analyzed | UC-CART-03 |
| **US-CART-04** | Remove One Product | 🔴 Critical | Analyzed | UC-CART-04 |
| **US-CART-05** | Remove All Products | 🔴 Critical | Analyzed | UC-CART-05 |
| **US-CART-06** | View Empty Cart State | 🟠 High | Analyzed | UC-CART-01 (AF-01) |
| **US-CART-07** | Proceed to Checkout Information | 🔴 Critical | Analyzed | UC-CART-06 |

---

## 3. User Story: US-CART-01

### 3.1. User Story Card

| Attribute | Value |
|-----------|-------|
| **US ID** | US-CART-01 |
| **Title** | View Shopping Cart |
| **Priority** | 🔴 **Critical** |
| **Business Value** | HIGH - Khách hàng cần thấy tất cả sản phẩm đã chọn |
| **Phase** | Phase 1 |
| **Status** | ✅ Analyzed (Phase 1) |

### 3.2. User Story Statement

```gherkin
As a customer,
I want to view all products in my shopping cart with their details,
So that I can review my selected items before proceeding to checkout.

---

Là một khách hàng,
Tôi muốn xem tất cả sản phẩm trong giỏ hàng cùng với chi tiết của chúng,
Để tôi có thể xem lại các sản phẩm đã chọn trước khi tiếp tục thanh toán.
```

### 3.3. Acceptance Criteria

| AC ID | Criterion | Status |
|-------|-----------|--------|
| **AC-CART-01.01** | Display All Products in Cart | ✅ Analyzed |
| **AC-CART-01.02** | Display Cart Summary Information | ✅ Analyzed |
| **AC-CART-01.03** | Handle Empty Cart Handling | ✅ Analyzed |
| **AC-CART-01.04** | Display Current Cart Data | ✅ Analyzed |
| **AC-CART-01.05** | Support Multiple Screen Sizes | ✅ Analyzed |

### 3.4. Actor

| Attribute | Value |
|-----------|-------|
| **Primary Actor** | Customer (Khách hàng mua hàng) |
| **Secondary Actor** | System (Shopping Cart Module) |
| **Supporting Actor** | Backend API (cung cấp product data) |

### 3.5. Related Requirements

| Type | ID | Link | Status |
|------|-----|------|--------|
| **Business Need** | BN-CART-01 | Tài liệu hóa Functional Requirements | ✅ Linked |
| **Use Case** | UC-CART-01 | View and Manage Shopping Cart | ✅ Linked |
| **User Flow** | UF-CART-05, 06, 08 | View and Review Cart | ✅ Linked |
| **Business Rule** | BR-PRICE-01 | Item Total Calculation | ✅ Linked |
| **Business Rule** | BR-CART-03 | Subtotal Calculation | ✅ Linked |
| **Business Rule** | BR-CART-05 | Empty Cart → Empty State | ✅ Linked |
| **Scope Function** | SC-01, SC-02, SC-06, SC-07 | View cart, display info, calculations | ✅ Linked |
| **NFR** | NFR-CART-04 | Responsive Design | ✅ Linked |

### 3.6. Dependencies

| Dependency Type | Dependency | Impact | Status |
|-----------------|-----------|--------|--------|
| **Internal** | Product Listing Module | Must have product catalog ready | ⚠️ Assumed available |
| **Internal** | Backend API | Must provide product data & pricing | ⚠️ Assumed available |
| **External** | Internet Connectivity | Network available for data fetch | ✅ Assumed |

**Dependencies Met?** ⚠️ **TBD** - Cần xác nhận availability của dependencies

### 3.7. Business Value

| Aspect | Description | Impact |
|--------|-------------|--------|
| **Customer Benefit** | Full visibility of cart contents | Khách hàng có thể xem toàn bộ đơn hàng trước khi thanh toán |
| **Business Benefit** | Reduces cart errors & complaints | Giảm lỗi order, giảm phàn nàn từ khách hàng |
| **Technical Benefit** | Foundation for other cart operations | Cơ sở cho các chức năng khác (modify, remove) |

### 3.8. Definition of Ready Checklist

✅ **Checklist để US sẵn sàng vào Sprint:**

- [x] **Clear Title & Description** - Tiêu đề & description rõ ràng
- [x] **Acceptance Criteria Defined** - AC-CART-01.01 ~ 01.05 defined
- [x] **Related Use Case Documented** - UC-CART-01 documented
- [x] **Business Rules Identified** - BR-PRICE-01, BR-CART-03, BR-CART-05 identified
- [x] **Dependencies Listed** - Product API, product catalog identified
- [x] **Non-Functional Requirements Considered** - Responsive design included
- [x] **Mockup/Design Available** - Figma design available (Phase 1)
- [x] **No Unknown Technical Risks** - Standard cart display functionality
- [ ] **Story Points Estimated** - TBD (Not estimated in Phase 1)
- [ ] **Sprint Assigned** - Cần xác nhận khi Phase 2 starts

**Ready Status:** ⏳ **Pending Sprint Assignment**

### 3.9. INVEST Principles Evaluation

| Principle | Evaluation | Notes |
|-----------|-----------|-------|
| **I - Independent** | ✅ YES | Không phụ thuộc vào US khác; có thể implement riêng lẻ |
| **N - Negotiable** | ✅ YES | Chi tiết UI (table vs card layout) có thể negotiate |
| **V - Valuable** | ✅ YES | Cung cấp giá trị cao cho khách hàng |
| **E - Estimable** | ✅ YES | Có thể estimate quy mô công việc |
| **S - Small** | ✅ YES | Có thể hoàn thành trong 1 sprint (5-8 days) |
| **T - Testable** | ✅ YES | Có thể test với AC-CART-01.01 ~ 01.05 |

**INVEST Score:** ✅ **6/6 - Excellent**

### 3.10. Open Questions

| ID | Question | Current Status | Resolution |
|----|----------|-----------------|----------|
| **Q1-US-01** | Nên hiển thị product description trong cart hay chỉ name? | Cần xác nhận | Design decision |
| **Q2-US-01** | Tối đa bao nhiêu sản phẩm trong giỏ hàng? | Cần xác nhận | Business rule |
| **Q3-US-01** | Nên sort sản phẩm theo thứ tự nào (added, alphabetical, price)? | Cần xác nhận | UX decision |
| **Q4-US-01** | Có nên display recommended products khi cart có ít sản phẩm? | Cần xác nhận | Phase 1 vs Phase 2+ |

### 3.11. Implementation Assumptions

| Assumption | Status | Notes |
|-----------|--------|-------|
| **A1** | Backend API returns current product data | ✅ Confirmed | Assumed available |
| **A2** | Cart data persisted server-side | ⚠️ Assumed | Architecture TBD |
| **A3** | Product prices don't change during session | ⚠️ Assumed | EF handled in UC-CART-06 |
| **A4** | No special formatting needed for product names | ✅ Confirmed | Plain text display |

### 3.12. Status & Timeline

| Phase | Status | Timeline | Details |
|-------|--------|----------|----------|
| **Phase 1** | ✅ **ANALYZED** | Current | US analyzed, AC defined, UC documented |
| **Phase 2** | ⏳ **PENDING** | TBD | Implementation (backend + frontend) |
| **Phase 3** | ⏳ **PENDING** | TBD | Testing & UAT |
| **Phase 4+** | ⏳ **PENDING** | TBD | Production deployment |

**Current Status:** ✅ **Ready for Phase 2 Development Handover**

---

## 4. User Story: US-CART-02

### 4.1. User Story Card

| Attribute | Value |
|-----------|-------|
| **US ID** | US-CART-02 |
| **Title** | Update Product Quantity |
| **Priority** | 🔴 **Critical** |
| **Business Value** | HIGH - Khách hàng cần linh hoạt điều chỉnh số lượng |
| **Phase** | Phase 1 |
| **Status** | ✅ Analyzed (Phase 1) |

### 4.2. User Story Statement

```gherkin
As a customer,
I want to increase or decrease the quantity of products in my cart,
So that I can adjust my order without contacting support staff.

---

Là một khách hàng,
Tôi muốn tăng hoặc giảm số lượng sản phẩm trong giỏ hàng,
Để tôi có thể điều chỉnh đơn hàng mà không cần liên hệ nhân viên hỗ trợ.
```

### 4.3. Acceptance Criteria

| AC ID | Criterion | Status |
|-------|-----------|--------|
| **AC-CART-02.01** | Increase Product Quantity | ✅ Analyzed |
| **AC-CART-02.02** | Decrease Product Quantity | ✅ Analyzed |
| **AC-CART-02.03** | Enforce Minimum Quantity = 1 | ✅ Analyzed |
| **AC-CART-02.04** | Real-time Price Calculation | ✅ Analyzed |
| **AC-CART-02.05** | Validate Quantity Input | ✅ Analyzed |

### 4.4. Actor

| Attribute | Value |
|-----------|-------|
| **Primary Actor** | Customer (Khách hàng) |
| **Secondary Actor** | System (Shopping Cart + Pricing Engine) |

### 4.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **Business Need** | BN-CART-01 | Tài liệu hóa Functional Requirements |
| **Use Case** | UC-CART-02 | Update Product Quantity |
| **User Flow** | UF-CART-10, AF1 | Modify Quantity Flows |
| **Business Rule** | BR-CART-01 | Minimum Qty = 1 |
| **Business Rule** | BR-CART-02 | Positive Integer Quantity |
| **Business Rule** | BR-PRICE-01 | Item Total Calculation |
| **Business Rule** | BR-CART-03 | Subtotal Calculation |
| **Scope Function** | SC-03, SC-04, SC-05, SC-06, SC-07 | Quantity & calculation functions |

### 4.6. Dependencies

| Dependency | Type | Status |
|-----------|------|--------|
| **US-CART-01** | Prerequisite | Cart must be displayed first |
| **Backend Pricing API** | External | Must provide accurate pricing |
| **Real-time Sync Service** | External | Must sync changes to backend |

### 4.7. Business Value

- **Customer Benefit:** Khách hàng có thể tự điều chỉnh mà không cần hỗ trợ
- **Business Benefit:** Giảm workload support, tăng customer autonomy
- **Technical Benefit:** Foundation cho order adjustment features

### 4.8. Definition of Ready

- [x] Acceptance Criteria clearly defined (AC-CART-02.01 ~ 02.05)
- [x] Use Case documented (UC-CART-02)
- [x] Business rules identified (BR-CART-01, BR-CART-02, BR-PRICE-01, BR-CART-03)
- [x] Input validation strategy defined
- [x] Real-time calculation approach designed
- [x] Error handling for network failures covered
- [ ] Story Points estimated - TBD
- [ ] Sprint assigned - TBD

**Ready Status:** ⏳ **Pending Sprint Assignment**

### 4.9. INVEST Principles Evaluation

| Principle | Evaluation | Notes |
|-----------|-----------|-------|
| **I - Independent** | ✅ YES | Độc lập; không phụ thuộc vào US khác |
| **N - Negotiable** | ✅ YES | Input method (button vs field) có thể negotiate |
| **V - Valuable** | ✅ YES | Cung cấp giá trị cao |
| **E - Estimable** | ✅ YES | Có thể estimate công việc |
| **S - Small** | ✅ YES | Có thể hoàn thành trong 1 sprint |
| **T - Testable** | ✅ YES | Testable qua AC-CART-02.01 ~ 02.05 |

**INVEST Score:** ✅ **6/6 - Excellent**

### 4.10. Open Questions

| ID | Question | Current Status |
|----|----------|------------------|
| **Q1-US-02** | Có max quantity limit không? Nếu có, giá trị bao nhiêu? | Cần xác nhận |
| **Q2-US-02** | Làm thế nào để handle rapid clicks? (debounce/throttle?) | Cần xác nhận |
| **Q3-US-02** | Chấp nhận decimal quantities (2.5) hay chỉ integers? | Cần xác nhận |
| **Q4-US-02** | Có nên notify user nếu giá sản phẩm thay đổi? | Cần xác nhận |

### 4.11. Status

**Current Status:** ✅ **Ready for Phase 2 Development Handover**

---

## 5. User Story: US-CART-03

### 5.1. User Story Card

| Attribute | Value |
|-----------|-------|
| **US ID** | US-CART-03 |
| **Title** | Add Order Note |
| **Priority** | 🟠 **High** |
| **Business Value** | MEDIUM - Cho phép khách hàng ghi yêu cầu đặc biệt |
| **Phase** | Phase 1 |
| **Status** | ✅ Analyzed (Phase 1) |

### 5.2. User Story Statement

```gherkin
As a customer,
I want to add a note to my order,
So that I can communicate special requests (delivery time, gift wrap, etc.) to the seller.

---

Là một khách hàng,
Tôi muốn thêm ghi chú cho đơn hàng,
Để tôi có thể ghi lại yêu cầu đặc biệt (thời gian giao, đóng gói, v.v.) cho người bán.
```

### 5.3. Acceptance Criteria

| AC ID | Criterion | Status |
|-------|-----------|--------|
| **AC-CART-03.01** | Enter Order Note (proposed) | ✅ Analyzed |
| **AC-CART-03.02** | Validate 256 Character Limit (proposed) | ✅ Analyzed |
| **AC-CART-03.03** | Display Character Counter (proposed) | ✅ Analyzed |
| **AC-CART-03.04** | Show Note in Order Summary (proposed) | ✅ Analyzed |

### 5.4. Actor

| Attribute | Value |
|-----------|-------|
| **Primary Actor** | Customer |
| **Secondary Actor** | System (Shopping Cart Module) |

### 5.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **Business Need** | BN-CART-01 | Tài liệu hóa Functional Requirements |
| **Use Case** | UC-CART-03 | Add Order Note |
| **User Flow** | UF-CART-12, UF-CART-ON | Add notes flows |
| **Business Rule** | BR-NOTE-01 | Order Note Character Limit (Max 256) |
| **Scope Function** | SC-09, SC-10 | Order note functionality |

### 5.6. Dependencies

| Dependency | Type | Status |
|-----------|------|--------|
| **US-CART-01** | Prerequisite | Cart must be displayed |
| **Character Limit Validation** | Internal | Must implement char validation |

### 5.7. Business Value

- **Customer Benefit:** Có thể ghi lại yêu cầu đặc biệt (delivery time, packaging requests)
- **Business Benefit:** Giảm miscommunication, tăng customer satisfaction
- **Technical Benefit:** Structured data capture for order management

### 5.8. Definition of Ready

- [x] AC defined & clear
- [x] UC documented
- [x] Character limit specified (256 chars)
- [x] Validation approach designed
- [x] Error handling covered
- [ ] Story Points estimated - TBD
- [ ] Sprint assigned - TBD

**Ready Status:** ⏳ **Pending Sprint Assignment**

### 5.9. INVEST Principles Evaluation

| Principle | Evaluation | Notes |
|-----------|-----------|-------|
| **I - Independent** | ✅ YES | Độc lập, không phụ thuộc vào US khác |
| **N - Negotiable** | ✅ YES | Note field styling, placement có thể negotiate |
| **V - Valuable** | ✅ YES | Cung cấp giá trị cho khách hàng |
| **E - Estimable** | ✅ YES | Có thể estimate |
| **S - Small** | ✅ YES | Có thể hoàn thành trong 1 sprint |
| **T - Testable** | ✅ YES | Testable qua AC |

**INVEST Score:** ✅ **6/6 - Excellent**

### 5.10. Open Questions

| ID | Question | Current Status |
|----|----------|------------------|
| **Q1-US-03** | Nên allow special characters (emoji, HTML)? | Cần xác nhận |
| **Q2-US-03** | Có nên sanitize input để prevent XSS? | Cần xác nhận |
| **Q3-US-03** | Note có bắt buộc phải nhập không? | Cần xác nhận |

### 5.11. Status

**Current Status:** ✅ **Ready for Phase 2 Development Handover**

---

## 6. User Story: US-CART-04

### 6.1. User Story Card

| Attribute | Value |
|-----------|-------|
| **US ID** | US-CART-04 |
| **Title** | Remove One Product |
| **Priority** | 🔴 **Critical** |
| **Business Value** | HIGH - Khách hàng có thể điều chỉnh đơn hàng |
| **Phase** | Phase 1 |
| **Status** | ✅ Analyzed (Phase 1) |

### 6.2. User Story Statement

```gherkin
As a customer,
I want to remove a product from my shopping cart,
So that I can adjust my order if I change my mind about a product.

---

Là một khách hàng,
Tôi muốn xóa một sản phẩm khỏi giỏ hàng,
Để tôi có thể điều chỉnh đơn hàng nếu tôi đổi ý về một sản phẩm.
```

### 6.3. Acceptance Criteria

| AC ID | Criterion | Status |
|-------|-----------|--------|
| **AC-CART-04.01** | Remove Single Product (proposed) | ✅ Analyzed |
| **AC-CART-04.02** | Update Totals After Removal (proposed) | ✅ Analyzed |
| **AC-CART-04.03** | Handle Last Item Removal (proposed) | ✅ Analyzed |
| **AC-CART-04.04** | No Confirmation for Single Item (proposed) | ✅ Analyzed |

### 6.4. Actor

| Attribute | Value |
|-----------|-------|
| **Primary Actor** | Customer |
| **Secondary Actor** | System (Shopping Cart) |

### 6.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **Business Need** | BN-CART-01 | Tài liệu hóa Functional Requirements |
| **Use Case** | UC-CART-04 | Remove One Product |
| **User Flow** | UF-CART-11, UF-CART-RM, UF-CART-AF4 | Remove item flows |
| **Business Rule** | BR-PRICE-01 | Item Total Calculation |
| **Business Rule** | BR-CART-03 | Subtotal Calculation |
| **Business Rule** | BR-CART-05 | Empty Cart → Empty State |
| **Scope Function** | SC-11, SC-06, SC-07 | Remove product, recalculate |

### 6.6. Dependencies

| Dependency | Type | Status |
|-----------|------|--------|
| **US-CART-01** | Prerequisite | Cart must be displayed |
| **Backend Sync** | External | Changes must persist |

### 6.7. Business Value

- **Customer Benefit:** Nhanh chóng điều chỉnh order; không cần support
- **Business Benefit:** Tăng autonomy, giảm support request
- **Technical Benefit:** Foundation cho cart management

### 6.8. Definition of Ready

- [x] AC defined
- [x] UC documented
- [x] UX decision: no confirmation for single item
- [x] Last item removal → empty state
- [ ] Story Points estimated - TBD
- [ ] Sprint assigned - TBD

**Ready Status:** ⏳ **Pending Sprint Assignment**

### 6.9. INVEST Principles Evaluation

| Principle | Evaluation | Notes |
|-----------|-----------|-------|
| **I - Independent** | ✅ YES | Độc lập |
| **N - Negotiable** | ✅ YES | Animation style, icon có thể negotiate |
| **V - Valuable** | ✅ YES | Cung cấp giá trị cao |
| **E - Estimable** | ✅ YES | Có thể estimate |
| **S - Small** | ✅ YES | Có thể hoàn thành 1 sprint |
| **T - Testable** | ✅ YES | Testable qua AC |

**INVEST Score:** ✅ **6/6 - Excellent**

### 6.10. Status

**Current Status:** ✅ **Ready for Phase 2 Development Handover**

---

## 7. User Story: US-CART-05

### 7.1. User Story Card

| Attribute | Value |
|-----------|-------|
| **US ID** | US-CART-05 |
| **Title** | Remove All Products |
| **Priority** | 🔴 **Critical** |
| **Business Value** | HIGH - Complete reset capability |
| **Phase** | Phase 1 |
| **Status** | ✅ Analyzed (Phase 1) |

### 7.2. User Story Statement

```gherkin
As a customer,
I want to remove all products from my shopping cart with confirmation,
So that I can completely reset my cart if needed.

---

Là một khách hàng,
Tôi muốn xóa tất cả sản phẩm khỏi giỏ hàng (kèm xác nhân),
Để tôi có thể reset hoàn toàn giỏ hàng nếu cần.
```

### 7.3. Acceptance Criteria

| AC ID | Criterion | Status |
|-------|-----------|--------|
| **AC-CART-05.01** | Show Confirmation Dialog (proposed) | ✅ Analyzed |
| **AC-CART-05.02** | Handle Confirm Action (proposed) | ✅ Analyzed |
| **AC-CART-05.03** | Handle Cancel Action (proposed) | ✅ Analyzed |
| **AC-CART-05.04** | Transition to Empty State (proposed) | ✅ Analyzed |

### 7.4. Actor

| Attribute | Value |
|-----------|-------|
| **Primary Actor** | Customer |
| **Secondary Actor** | System |

### 7.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **Business Need** | BN-CART-01 | Functional Requirements |
| **Use Case** | UC-CART-05 | Remove All Products |
| **User Flow** | UF-CART-RA, UF-CART-AF3 | Remove all flows |
| **Business Rule** | BR-CART-04 | Clear All Requires Confirmation |
| **Business Rule** | BR-CART-05 | Empty Cart → Empty State |
| **Scope Function** | SC-12, SC-13, SC-14 | Clear all, confirmation, empty state |

### 7.6. Dependencies

| Dependency | Type | Status |
|-----------|------|--------|
| **US-CART-01** | Prerequisite | Cart must be displayed |

### 7.7. Business Value

- **Customer Benefit:** Complete control over cart reset
- **Business Benefit:** Prevents accidental clears (confirmation required)
- **Technical Benefit:** Data protection through confirmation

### 7.8. Definition of Ready

- [x] AC defined
- [x] UC documented
- [x] Confirmation dialog required (BR-CART-04)
- [x] Cancel handling defined
- [ ] Story Points estimated - TBD
- [ ] Sprint assigned - TBD

**Ready Status:** ⏳ **Pending Sprint Assignment**

### 7.9. INVEST Principles Evaluation

| Principle | Evaluation | Notes |
|-----------|-----------|-------|
| **I - Independent** | ✅ YES | Độc lập |
| **N - Negotiable** | ✅ YES | Dialog message, button text có thể negotiate |
| **V - Valuable** | ✅ YES | Cung cấp giá trị |
| **E - Estimable** | ✅ YES | Có thể estimate |
| **S - Small** | ✅ YES | Có thể hoàn thành 1 sprint |
| **T - Testable** | ✅ YES | Testable qua AC |

**INVEST Score:** ✅ **6/6 - Excellent**

### 7.10. Status

**Current Status:** ✅ **Ready for Phase 2 Development Handover**

---

## 8. User Story: US-CART-06

### 8.1. User Story Card

| Attribute | Value |
|-----------|-------|
| **US ID** | US-CART-06 |
| **Title** | View Empty Cart State |
| **Priority** | 🟠 **High** |
| **Business Value** | MEDIUM - Proper empty state UX |
| **Phase** | Phase 1 |
| **Status** | ✅ Analyzed (Phase 1) |

### 8.2. User Story Statement

```gherkin
As a customer,
I want to see a clear message when my shopping cart is empty,
So that I know my cart is empty and I can easily return to shopping.

---

Là một khách hàng,
Tôi muốn thấy thông điệp rõ ràng khi giỏ hàng của tôi trống,
Để tôi biết rằng giỏ hàng trống và có thể dễ dàng quay lại mua sắm.
```

### 8.3. Acceptance Criteria

| AC ID | Criterion | Status |
|-------|-----------|--------|
| **AC-CART-06.01** | Display Empty State Message (proposed) | ✅ Analyzed |
| **AC-CART-06.02** | Show Continue Shopping Button (proposed) | ✅ Analyzed |
| **AC-CART-06.03** | Clear Product List (proposed) | ✅ Analyzed |
| **AC-CART-06.04** | Disable Checkout Button (proposed) | ✅ Analyzed |

### 8.4. Actor

| Attribute | Value |
|-----------|-------|
| **Primary Actor** | Customer |
| **Secondary Actor** | System |

### 8.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **Business Need** | BN-CART-01 | Functional Requirements |
| **Use Case** | UC-CART-01 (AF-01) | Empty Cart Handling |
| **User Flow** | UF-CART-EC | Empty Cart Flow |
| **Business Rule** | BR-CART-05 | Empty Cart → Empty State |
| **Scope Function** | SC-14 | Display empty-cart state |

### 8.6. Dependencies

| Dependency | Type | Status |
|-----------|------|--------|
| **US-CART-01** | Prerequisite | Cart display first |
| **Product Listing Module** | External | Link to product browsing |

### 8.7. Business Value

- **Customer Benefit:** Clear guidance when cart is empty
- **Business Benefit:** Encourages continued shopping (recovery)
- **Technical Benefit:** Proper state management

### 8.8. Definition of Ready

- [x] AC defined
- [x] UC documented
- [x] UX message defined ("Your cart is empty")
- [x] Call-to-action defined ("Continue Shopping")
- [ ] Story Points estimated - TBD
- [ ] Sprint assigned - TBD

**Ready Status:** ⏳ **Pending Sprint Assignment**

### 8.9. INVEST Principles Evaluation

| Principle | Evaluation | Notes |
|-----------|-----------|-------|
| **I - Independent** | ✅ YES | Độc lập |
| **N - Negotiable** | ✅ YES | Message, styling, layout có thể negotiate |
| **V - Valuable** | ✅ YES | Cung cấp giá trị UX |
| **E - Estimable** | ✅ YES | Có thể estimate |
| **S - Small** | ✅ YES | Có thể hoàn thành 1 sprint |
| **T - Testable** | ✅ YES | Testable qua AC |

**INVEST Score:** ✅ **6/6 - Excellent**

### 8.10. Status

**Current Status:** ✅ **Ready for Phase 2 Development Handover**

---

## 9. User Story: US-CART-07

### 9.1. User Story Card

| Attribute | Value |
|-----------|-------|
| **US ID** | US-CART-07 |
| **Title** | Proceed to Checkout Information |
| **Priority** | 🔴 **Critical** |
| **Business Value** | HIGH - Handoff to next step |
| **Phase** | Phase 1 (Handoff point) |
| **Status** | ✅ Analyzed (Phase 1) |

### 9.2. User Story Statement

```gherkin
As a customer,
I want to proceed from my shopping cart to the checkout information step,
So that I can enter my delivery details and complete my purchase.

---

Là một khách hàng,
Tôi muốn chuyển từ giỏ hàng sang bước nhập thông tin thanh toán,
Để tôi có thể nhập thông tin giao hàng và hoàn thành mua sắm.
```

### 9.3. Acceptance Criteria

| AC ID | Criterion | Status |
|-------|-----------|--------|
| **AC-CART-07.01** | Validate Cart Before Handoff (proposed) | ✅ Analyzed |
| **AC-CART-07.02** | Display Proceed Button (proposed) | ✅ Analyzed |
| **AC-CART-07.03** | Transfer Cart Data (proposed) | ✅ Analyzed |
| **AC-CART-07.04** | Navigate to Checkout Module (proposed) | ✅ Analyzed |

### 9.4. Actor

| Attribute | Value |
|-----------|-------|
| **Primary Actor** | Customer |
| **Secondary Actor** | Shopping Cart System |
| **Supporting Actor** | Checkout Module (receives data) |

### 9.5. Related Requirements

| Type | ID | Link |
|------|-----|------|
| **Business Need** | BN-CART-01 | Functional Requirements |
| **Use Case** | UC-CART-06 | Proceed to Checkout Information |
| **User Flow** | UF-CART-13 ~ 16 | Final review & proceed flows |
| **Business Rule** | BR-CART-01, BR-CART-02, BR-PRICE-01, BR-CART-03 | Qty validation, price recalculation |
| **Scope Function** | SC-15 | Proceed to checkout button |

### 9.6. Dependencies

| Dependency | Type | Status |
|-----------|------|--------|
| **US-CART-01** | Prerequisite | Cart must be displayed |
| **Checkout Module** | External | Must be ready (Phase 2+) |
| **Cart Validation Logic** | Internal | Must validate before handoff |

**Status:** ⚠️ **Checkout module availability TBD for Phase 2**

### 9.7. Business Value

- **Customer Benefit:** Seamless transition from shopping to checkout
- **Business Benefit:** Complete shopping cart-to-checkout flow
- **Technical Benefit:** Clear module boundary & handoff point

### 9.8. Definition of Ready

- [x] AC defined
- [x] UC documented
- [x] Validation strategy defined
- [x] Handoff contract defined (what data to send)
- [ ] Checkout module API specifications - TBD
- [ ] Story Points estimated - TBD
- [ ] Sprint assigned - TBD

**Ready Status:** ⏳ **Pending Checkout Module Specs**

### 9.9. INVEST Principles Evaluation

| Principle | Evaluation | Notes |
|-----------|-----------|-------|
| **I - Independent** | ⚠️ PARTIAL | Depends on Checkout module readiness |
| **N - Negotiable** | ✅ YES | Button text, error messages có thể negotiate |
| **V - Valuable** | ✅ YES | Cung cấp giá trị (next step in flow) |
| **E - Estimable** | ✅ YES | Có thể estimate (validation + handoff) |
| **S - Small** | ✅ YES | Có thể hoàn thành 1 sprint |
| **T - Testable** | ✅ YES | Testable qua AC |

**INVEST Score:** ⚠️ **5/6 - Good (needs Checkout module)**

### 9.10. Open Questions

| ID | Question | Current Status |
|----|----------|------------------|
| **Q1-US-07** | Checkout module API specifications nên gì? | Cần xác nhận |
| **Q2-US-07** | Có nên clear cart sau handoff thành công? | Cần xác nhận |
| **Q3-US-07** | Làm thế nào để handle Checkout module unavailable? | Cần xác nhận |

### 9.11. Status

**Current Status:** ⏳ **Pending Checkout Module Coordination**

---

## 10. User Story Summary Matrix

| US ID | Title | Priority | Actor | INVEST | Dependencies | Status |
|-------|-------|----------|-------|--------|-------------|--------|
| **US-CART-01** | View Shopping Cart | 🔴 Critical | Customer | ✅ 6/6 | Product API | Ready |
| **US-CART-02** | Update Qty | 🔴 Critical | Customer | ✅ 6/6 | US-01 | Ready |
| **US-CART-03** | Add Order Note | 🟠 High | Customer | ✅ 6/6 | US-01 | Ready |
| **US-CART-04** | Remove One Product | 🔴 Critical | Customer | ✅ 6/6 | US-01 | Ready |
| **US-CART-05** | Remove All Products | 🔴 Critical | Customer | ✅ 6/6 | US-01 | Ready |
| **US-CART-06** | View Empty State | 🟠 High | Customer | ✅ 6/6 | US-01 | Ready |
| **US-CART-07** | Proceed to Checkout | 🔴 Critical | Customer | ⚠️ 5/6 | Checkout Module | Pending |

---

## 11. Dependency Map

```
┌─────────────────┐
│  US-CART-01     │ (View Shopping Cart)
│  VIEW CART      │ ← Foundation US
└────────┬────────┘
         │
    ┌────┴──────────────────────┬───────────────┬───────────────┐
    │                           │               │               │
    ▼                           ▼               ▼               ▼
┌──────────────┐  ┌──────────────────┐  ┌──────────────┐  ┌──────────[...]
│ US-CART-02   │  │ US-CART-03       │  │ US-CART-04   │  │ US-CART-06   │
│ UPDATE QTY   │  │ ADD ORDER NOTE   │  │ REMOVE PROD  │  │ EMPTY STATE  │
└──────────────┘  └──────────────────┘  └──────────────┘  └──────────[...]

┌──────────────────────────────────────┐
│ US-CART-05 (REMOVE ALL)              │
│ Can be parallel with US-02, 03, 04   │
└──────────────────────────────────────┘

All above depend on → US-CART-01 (Foundation)
       │
       ▼
┌──────────────────────────────┐
│ US-CART-07 (PROCEED)         │
│ CHECKOUT (Phase 2+ handoff)  │
└──────────────────────────────┘
       │
       ▼
   Checkout Module (Out of Scope)
```

---

## 12. Development Priorities

### Recommended Sprint Order (Phase 2+)

| Sprint | User Stories | Rationale | Estimated Effort |
|--------|-------------|----------|------------------|
| **Sprint 1** | US-CART-01 | Foundation for all others | High |
| **Sprint 2** | US-CART-02, 04 | Core cart operations | High |
| **Sprint 2-3** | US-CART-03, 06 | Secondary operations | Medium |
| **Sprint 3** | US-CART-05 | Destructive action (needs careful impl) | Medium |
| **Sprint 4** | US-CART-07 | Handoff to Checkout (requires coordination) | Medium-High |

**Note:** Effort estimates not provided in Phase 1. TBD in Phase 2 planning.

---

## 13. Quality Criteria

### Definition of Done (DoD) for Each US

Mỗi User Story được coi là **DONE** khi:

- ✅ **Code Review Passed** - Code reviewed & approved
- ✅ **All AC Passed** - Tất cả acceptance criteria vượt test
- ✅ **Unit Tests Written** - Coverage ≥ 80%
- ✅ **Integration Tests Passed** - Integration với modules khác OK
- ✅ **Performance Meets NFR** - NFR-CART-04 responsive design verified
- ✅ **No Critical Bugs** - Không có critical/blocker bugs
- ✅ **Documentation Updated** - Code comments, API docs updated
- ✅ **Peer Review Complete** - Peer review from team member
- ⏳ **UAT Ready** - Ready for QA/UAT (Phase 3)

**Note:** DoD chi tiết sẽ được refine trong Phase 2 sprint planning.

---

## 14. Items Needing Confirmation

### Technical Decisions

| Item | Current Status | Priority | Impact |
|------|-----------------|----------|--------|
| Backend pricing API specs | Cần xác nhận | Critical | US-CART-02 |
| Cart data persistence strategy | Cần xác nhận | Critical | US-CART-01, 02, 04, 05 |
| Real-time sync approach | Cần xác nhận | High | US-CART-02, 04, 05 |
| Checkout module API contract | Cần xác nhận | Critical | US-CART-07 |

### Business Decisions

| Item | Current Status | Priority | Impact |
|------|-----------------|----------|--------|
| Max quantity per product | Cần xác nhận | High | US-CART-02 |
| Undo for single item removal | Cần xác nhận | Medium | US-CART-04 |
| Recommended products in empty state | Cần xác nhận | Low | US-CART-06 |
| Order note validation rules | Cần xác nhận | Medium | US-CART-03 |

---

## 15. Important Disclaimers

### ✅ What These User Stories Represent

- ✅ Analyzed & documented requirements from Phase 1
- ✅ Clear acceptance criteria for Phase 2 development
- ✅ Foundation for test case design (Phase 3)
- ✅ Portfolio demonstration of BA skills (Agile/Scrum approach)

### ❌ What These User Stories Do NOT Represent

- ❌ Implemented features
- ❌ Completed development work
- ❌ Passed UAT or user testing
- ❌ Production-ready features
- ❌ Story point estimates (to be done in Phase 2 planning)

### ⏳ Implementation Status

**Phase 1 (COMPLETED):**
- ✅ User Stories analyzed & written
- ✅ INVEST principles evaluated
- ✅ AC defined & documented
- ✅ Dependencies identified

**Phase 2 (PENDING):**
- ⏳ Story point estimation in sprint planning
- ⏳ Sprint assignment & scheduling
- ⏳ Development & code implementation
- ⏳ Code review & testing

**Phase 3+ (PENDING):**
- ⏳ QA testing & UAT
- ⏳ Deployment preparation
- ⏳ Production release

---

## 16. Assumptions

| Assumption | Status | Notes |
|-----------|--------|-------|
| Backend APIs available by Phase 2 | ⚠️ Assumed | Product API, pricing service |
| Checkout module will be developed Phase 2+ | ✅ Confirmed | Out of scope for Phase 1 |
| Network connectivity available | ✅ Confirmed | Standard assumption |
| Customer wants autonomy (no support calls) | ✅ Confirmed | Business need stated |
| Confirmation required for destructive actions | ✅ Confirmed | BR-CART-04 |

---

## 17. References

- **docs/04-project-scope.md:** Shopping Cart functions (SC-01 ~ SC-15)
- **docs/06-user-flow.md:** User flows mapped to User Stories
- **docs/07-use-cases.md:** Use Cases (UC-CART-01 ~ UC-CART-06)
- **docs/09-acceptance-criteria.md:** Acceptance Criteria details
- **source-documents/source-material.md:** Project context & constraints
- **.github/copilot-instructions.md:** Documentation standards

---

## 18. Document Metadata

| Attribute | Value |
|-----------|-------|
| **Document Type** | User Stories |
| **Phase** | Phase 1 - Analysis Complete |
| **Status** | ✅ Complete |
| **Total User Stories** | 7 (US-CART-01 ~ US-CART-07) |
| **INVEST Evaluation** | All 6/6 or 5/6 (excellent) |
| **Classification** | Portfolio Documentation |
| **Last Updated** | Phase 1 Analysis |

---

## 19. Agile/Scrum Alignment

### User Story Format ✅

Tất cả User Stories follow chuẩn format **Agile/Scrum:**
```
As a [role],
I want [capability],
So that [business value]
```

### INVEST Principles Evaluation ✅

Tất cả 7 User Stories đánh giá theo **INVEST Principles:**
- **I**ndependent (Độc lập)
- **N**egotiable (Có thể thương lượng)
- **V**aluable (Có giá trị)
- **E**stimable (Có thể ước lượng)
- **S**mall (Nhỏ, vào 1 sprint)
- **T**estable (Có thể test)

### Ready for Sprint Planning ✅

Tất cả User Stories được đánh dấu:
- ✅ **Definition of Ready checklist** hoàn thành
- ✅ **Acceptance Criteria** rõ ràng & testable
- ✅ **Dependencies** xác định
- ⏳ **Story Points** pending estimation (Phase 2)

---

**Tài liệu này sẵn sàng để chuyển cho Phase 2 Development Team cho Sprint Planning.**

**Document Version:** 1.0  
**Status:** ✅ Ready for Handover  
**Next Step:** Phase 2 Sprint Planning & Development
