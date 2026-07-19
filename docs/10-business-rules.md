# Business Rule Catalog - Shopping Cart Module
## Đại Phú E-commerce

---

## 1. Document Purpose

Tài liệu Business Rule Catalog định nghĩa chi tiết tất cả các quy tắc kinh doanh (Business Rules) cho module Giỏ hàng. Mỗi quy tắc được tài liệu hóa với:

- **Rule ID & Name** – Mã định danh duy nhất và tên gọi
- **Rule Statement** – Phát biểu quy tắc rõ ràng
- **Rule Type** – Phân loại quy tắc (Business, Validation, Calculation, Display, UI)
- **Rationale** – Lý do tại sao quy tắc này cần thiết
- **Source** – Nguồn gốc quy tắc (User Story, AC, FR, Scope Functions)
- **Related Requirements** – Liên kết với US, FR, AC
- **Priority & Status** – Mức độ ưu tiên và trạng thái xác nhận
- **Notes** – Ghi chú bổ sung, điều kiện áp dụng, hoặc cảnh báo

**Phân Loại Quy Tắc:**

| Loại | Định Nghĩa | Ví Dụ |
|------|-----------|--------|
| **Business Rule** | Quy tắc điều khiển hành vi nghiệp vụ chung | Tính toán giá, xác nhận xóa |
| **Validation Rule** | Quy tắc kiểm tra tính hợp lệ của dữ liệu đầu vào | Min qty = 1, max notes = 256 chars |
| **Calculation Rule** | Quy tắc tính toán giá trị | Item Total = Unit Price × Qty |
| **Display Rule** | Quy tắc về cách hiển thị thông tin trên giao diện | Max 2 lines tên sản phẩm |
| **UI Rule** | Quy tắc về tương tác & trạng thái giao diện | Xóa hết phải xác nhận, disable nút "-" |

---

## 2. Business Rules Summary

| BR ID | Rule Name | Type | Priority | Status | Related US | Total Rules |
|-------|-----------|------|----------|--------|-----------|-------------|
| **BR-CART-01** | Minimum Quantity Validation | Validation | 🔴 Critical | ✅ Confirmed | US-02, US-04, US-05 | - |
| **BR-CART-02** | Positive Integer Quantity | Validation | 🔴 Critical | ✅ Confirmed | US-02, US-04, US-05 | - |
| **BR-PRICE-01** | Item Total Calculation | Calculation | 🔴 Critical | ✅ Confirmed | US-01, US-02 | - |
| **BR-CART-03** | Subtotal Calculation | Calculation | 🔴 Critical | ✅ Confirmed | US-01, US-02, US-04, US-05 | - |
| **BR-CART-04** | Grand Total Calculation | Calculation | 🔴 Critical | ✅ Confirmed | US-01 | - |
| **BR-NOTE-01** | Order Note Character Limit | Validation | 🟠 High | ✅ Confirmed | US-03 | - |
| **BR-CART-05** | Remove All Confirmation | Business | 🔴 Critical | ✅ Confirmed | US-05 | - |
| **BR-CART-06** | Cart Empty State Trigger | Business | 🟠 High | ✅ Confirmed | US-04, US-05, US-06 | - |
| **BR-CART-07** | Product Order (LIFO) | Display | 🟡 Medium | ⚠️ **Draft – Needs confirmation** | US-01 | - |
| **BR-CART-08** | Product Name Display Truncation | Display | 🟡 Medium | ⚠️ **Draft – Needs confirmation** | US-01 | - |
| **TOTAL** | | | | | | **8 Business Rules** |

---

## 3. Business Rules Detail

### 3.1. BR-CART-01: Minimum Quantity Validation

| Thuộc Tính | Giá Trị |
|-----------|--------|
| **Rule ID** | BR-CART-01 |
| **Rule Name** | Minimum Quantity Validation |
| **Rule Type** | ✅ **Validation Rule** |
| **Priority** | 🔴 **Critical** |
| **Status** | ✅ **Confirmed** |

#### 3.1.1. Rule Statement

```
Số lượng sản phẩm trong giỏ hàng phải >= 1 (tối thiểu 1 đơn vị).
Hệ thống không cho phép khách hàng giảm số lượng xuống dưới 1.

---

The minimum quantity for any product in the shopping cart must be 1 unit.
The system must prevent the quantity from being reduced below 1.
```

#### 3.1.2. Rationale

- **Business Reason:** Một sản phẩm trong giỏ hàng phải có ít nhất 1 đơn vị; 0 hoặc số âm không có nghĩa trong bối cảnh bán hàng
- **User Experience:** Nếu khách hàng không muốn sản phẩm, họ có thể xóa sản phẩm đó hoàn toàn (thay vì giảm xuống 0)
- **Data Integrity:** Tránh state không hợp lệ (empty line item) trong giỏ hàng

#### 3.1.3. Source

| Nguồn | Chi Tiết | Link |
|------|---------|------|
| **Project Scope** | SC-02: Prevent quantity from going below 1 | docs/04-project-scope.md |
| **User Story** | US-02: Update Product Quantity | docs/08-user-stories.md |
| **User Story** | US-04: Remove One Product | docs/08-user-stories.md |
| **User Story** | US-05: Remove All Products | docs/08-user-stories.md |
| **Source Material** | Shopping Cart Functions | source-documents/source-material.md (Line 44) |

#### 3.1.4. Related Requirements

| Type | ID | Requirement | Link |
|------|-----|-------------|------|
| **User Story** | US-02 | Update Product Quantity | docs/08-user-stories.md#US-CART-02 |
| **User Story** | US-04 | Remove One Product | docs/08-user-stories.md#US-CART-04 |
| **Acceptance Criteria** | AC-CART-02.03 | Minimum Quantity Enforcement | docs/09-acceptance-criteria.md#AC-CART-02.03 |
| **Functional Requirement** | FR-CART-07 | Enforce Minimum Quantity | docs/11-functional-requirements.md#FR-CART-07 |
| **Use Case** | UC-CART-02 | Update Product Quantity | docs/07-use-cases.md (cần xác nhận) |

#### 3.1.5. Implementation Notes

| Aspect | Giải Pháp Đề Xuất | Trạng Thái |
|--------|-----------------|-----------|
| **Client-side Enforcement** | Disable nút "-" (Decrease) khi quantity = 1 | ✅ Recommended |
| **Server-side Enforcement** | Validate qty >= 1 trước khi update database | ✅ Required |
| **User Feedback** | Hiển thị tooltip hoặc message khi user cố gắng giảm xuống 0 | ⚠️ Cần xác nhận |
| **Error Handling** | Return HTTP 400 Bad Request nếu qty < 1 | ⚠️ Cần xác nhận |

#### 3.1.6. Notes

- **Điều Kiện Áp Dụng:** Quy tắc này áp dụng cho mỗi sản phẩm trong giỏ hàng khi khách hàng cố gắng giảm số lượng
- **Edge Case:** Khi quantity = 1 và khách hàng nhấn "-", hệ thống phải:
  - **Option A (Recommended):** Disable nút "-" / không cho phép action
  - **Option B:** Xóa sản phẩm khỏi giỏ (tương tự Remove Single Product) – **needs confirmation**
- **Related Action:** Nếu khách hàng muốn xóa sản phẩm hoàn toàn, anh/chị có thể sử dụng nút "Remove" (BR-CART-05)

---

### 3.2. BR-CART-02: Positive Integer Quantity

| Thuộc Tính | Giá Trị |
|-----------|--------|
| **Rule ID** | BR-CART-02 |
| **Rule Name** | Positive Integer Quantity |
| **Rule Type** | ✅ **Validation Rule** |
| **Priority** | 🔴 **Critical** |
| **Status** | ✅ **Confirmed** |

#### 3.2.1. Rule Statement

```
Số lượng sản phẩm phải là số nguyên dương (1, 2, 3, ...).
Hệ thống không chấp nhận số thập phân (2.5), số âm (-1), hoặc zero (0).

---

Product quantity must be a positive integer (1, 2, 3, ...).
The system must reject decimal quantities (2.5), negative numbers (-1), or zero.
```

#### 3.2.2. Rationale

- **Business Reason:** Hoa lụa được bán theo đơn vị nguyên lẻ; không có nửa bó hoa hoặc âm số
- **Data Consistency:** Tránh state không hợp lệ trong tính toán giá cả
- **User Experience:** Giữ giao diện đơn giản (numeric input, không decimal)

#### 3.2.3. Source

| Nguồn | Chi Tiết | Link |
|------|---------|------|
| **Project Scope** | SC-01: Quantity must be positive integer | docs/04-project-scope.md |
| **Source Material** | Shopping Cart Functions | source-documents/source-material.md (Line 39-44) |

#### 3.2.4. Related Requirements

| Type | ID | Requirement | Link |
|------|-----|-------------|------|
| **User Story** | US-02 | Update Product Quantity | docs/08-user-stories.md#US-CART-02 |
| **Acceptance Criteria** | AC-CART-02.01, AC-CART-02.02 | Increase/Decrease Quantity | docs/09-acceptance-criteria.md |
| **Functional Requirement** | FR-CART-05, FR-CART-06 | Increase/Decrease Quantity | docs/11-functional-requirements.md |

#### 3.2.5. Implementation Notes

| Aspect | Giải Pháp Đề Xuất | Trạng Thái |
|--------|-----------------|-----------|
| **Input Validation** | Use HTML5 `<input type="number">` với step="1" | ✅ Recommended |
| **Decimal Prevention** | Prevent decimal input tại client-side | ✅ Required |
| **Server Validation** | Validate qty là integer trước update | ✅ Required |
| **Error Message** | "Số lượng phải là số nguyên dương" | ✅ Suggested |

#### 3.2.6. Notes

- **Scope Limitation:** Quy tắc hiện tại chỉ nhận integer. Nếu tương lai cần hỗ trợ decimal (e.g., 0.5 kg), cần thay đổi yêu cầu này
- **Database Representation:** Dùng `INTEGER` hoặc `INT` type; không dùng `DECIMAL` hoặc `FLOAT`

---

### 3.3. BR-PRICE-01: Item Total Calculation

| Thuộc Tính | Giá Trị |
|-----------|--------|
| **Rule ID** | BR-PRICE-01 |
| **Rule Name** | Item Total Calculation |
| **Rule Type** | ✅ **Calculation Rule** |
| **Priority** | 🔴 **Critical** |
| **Status** | ✅ **Confirmed** |

#### 3.3.1. Rule Statement

```
Thành tiền (Item Total) = Đơn giá (Unit Price) × Số lượng (Quantity)

Item Total = Unit Price × Quantity

Công thức:
  Item_Total = Unit_Price × Qty

Ví dụ:
  - Product A: Unit Price = 100,000 VND, Qty = 2
  - Item Total = 100,000 × 2 = 200,000 VND
```

#### 3.3.2. Rationale

- **Business Reason:** Tính toán chính xác giá trị từng sản phẩm trong giỏ
- **Transparency:** Khách hàng có thể thấy rõ giá tiền của từng sản phẩm
- **Foundation for Subtotal:** Thành tiền là input cho tính toán Subtotal

#### 3.3.3. Source

| Nguồn | Chi Tiết | Link |
|------|---------|------|
| **Project Scope** | SC-03: Calculate item total | docs/04-project-scope.md |
| **Source Material** | Shopping Cart Functions | source-documents/source-material.md (Line 45) |

#### 3.3.4. Related Requirements

| Type | ID | Requirement | Link |
|------|-----|-------------|------|
| **User Story** | US-01 | View Shopping Cart | docs/08-user-stories.md#US-CART-01 |
| **User Story** | US-02 | Update Product Quantity | docs/08-user-stories.md#US-CART-02 |
| **Acceptance Criteria** | AC-CART-01.01, AC-CART-02.01 | Display/Recalculate Item Total | docs/09-acceptance-criteria.md |
| **Functional Requirement** | FR-CART-08 | Calculate Item Total | docs/11-functional-requirements.md#FR-CART-08 |

#### 3.3.5. Implementation Notes

| Aspect | Giải Pháp Đề Xuất | Trạng Thái |
|--------|-----------------|-----------|
| **Calculation Timing** | Real-time: recalculate khi qty thay đổi | ✅ Recommended |
| **Precision** | Dùng DECIMAL(12,2) hoặc tương tự để tránh floating-point error | ✅ Required |
| **Rounding** | Round to 2 decimal places (tiền tệ) | ✅ Required |
| **Currency Display** | Hiển thị format: "100,000 VND" hoặc "100,000₫" | ⚠️ Cần xác nhận |

#### 3.3.6. Notes

- **Edge Case:** Nếu Unit Price thay đổi trong database (product repriced), Item Total phải được tính lại với giá mới
- **Assumption:** Unit Price được lấy từ Product Master data tại thời điểm view/update cart; không dùng historical price
- **Validation:** Item Total phải >= 0 (do Unit Price >= 0 và Qty >= 1)

---

### 3.4. BR-CART-03: Subtotal Calculation

| Thuộc Tính | Giá Trị |
|-----------|--------|
| **Rule ID** | BR-CART-03 |
| **Rule Name** | Subtotal Calculation |
| **Rule Type** | ✅ **Calculation Rule** |
| **Priority** | 🔴 **Critical** |
| **Status** | ✅ **Confirmed** |

#### 3.4.1. Rule Statement

```
Tạm tính (Subtotal) = Tổng tất cả Thành tiền (Sum of All Item Totals)

Subtotal = Sum of all Item_Total values in cart

Công thức:
  Subtotal = Σ (Unit_Price_i × Qty_i) for all products i in cart

Ví dụ:
  - Product A: Item Total = 200,000 VND
  - Product B: Item Total = 150,000 VND
  - Subtotal = 200,000 + 150,000 = 350,000 VND
```

#### 3.4.2. Rationale

- **Business Reason:** Tính toán tổng giá trị các sản phẩm trong giỏ (trước phí vận chuyển)
- **Transparency:** Khách hàng thấy rõ tổng hàng
- **Checkout Foundation:** Subtotal là input cho tính toán Grand Total (sau shipping)

#### 3.4.3. Source

| Nguồn | Chi Tiết | Link |
|------|---------|------|
| **Project Scope** | SC-04: Calculate cart subtotal | docs/04-project-scope.md |
| **Source Material** | Shopping Cart Functions | source-documents/source-material.md (Line 46) |

#### 3.4.4. Related Requirements

| Type | ID | Requirement | Link |
|------|-----|-------------|------|
| **User Story** | US-01 | View Shopping Cart | docs/08-user-stories.md#US-CART-01 |
| **User Story** | US-02 | Update Product Quantity | docs/08-user-stories.md#US-CART-02 |
| **User Story** | US-04 | Remove One Product | docs/08-user-stories.md#US-CART-04 |
| **User Story** | US-05 | Remove All Products | docs/08-user-stories.md#US-CART-05 |
| **Acceptance Criteria** | AC-CART-01.02 | Display Cart Summary | docs/09-acceptance-criteria.md |
| **Functional Requirement** | FR-CART-09 | Calculate Subtotal | docs/11-functional-requirements.md#FR-CART-09 |

#### 3.4.5. Implementation Notes

| Aspect | Giải Pháp Đề Xuất | Trạng Thái |
|--------|-----------------|-----------|
| **Calculation Timing** | Real-time: recalculate khi: qty change, item add, item remove | ✅ Recommended |
| **Precision** | DECIMAL(12,2) - consistent với Item Total | ✅ Required |
| **Empty Cart** | Subtotal = 0 nếu cart trống | ✅ Required |
| **Display** | Hiển thị tại cart summary section | ✅ Required |

#### 3.4.6. Notes

- **Order of Calculation:** Subtotal = Σ Item_Total; Item_Total = Unit_Price × Qty
- **Edge Case - Empty Cart:** Subtotal = 0 (sẽ trigger Empty State display per BR-CART-06)
- **Future Extension:** Nếu có discount, Subtotal = Σ Item_Total - Total_Discount

---

### 3.5. BR-CART-04: Grand Total Calculation

| Thuộc Tính | Giá Trị |
|-----------|--------|
| **Rule ID** | BR-CART-04 |
| **Rule Name** | Grand Total Calculation |
| **Rule Type** | ✅ **Calculation Rule** |
| **Priority** | 🔴 **Critical** |
| **Status** | ✅ **Confirmed** |

#### 3.5.1. Rule Statement

```
Tổng tiền (Grand Total) = Tạm tính (Subtotal) khi chưa tính phí vận chuyển

Grand Total (at Cart stage) = Subtotal (no shipping fee yet)

Công thức (Phase 1):
  Grand_Total_in_Cart = Subtotal
  
Lưu ý:
  Phí vận chuyển (Shipping Fee) sẽ được tính ở Checkout stage (Phase 2),
  không tính trong module Giỏ hàng.
```

#### 3.5.2. Rationale

- **Business Reason:** Trong Giỏ hàng (Phase 1), khách hàng thấy tổng hàng chưa tính phí vận chuyển
- **Scope Separation:** Phí vận chuyển được tính sau khi khách hàng confirm giỏ và chọn địa chỉ giao hàng (Checkout phase)
- **User Experience:** Khách hàng biết được giá hàng trước khi đến bước checkout chọn shipping

#### 3.5.3. Source

| Nguồn | Chi Tiết | Link |
|------|---------|------|
| **Project Scope** | SC-05: Display Grand Total (without shipping) | docs/04-project-scope.md |

#### 3.5.4. Related Requirements

| Type | ID | Requirement | Link |
|------|-----|-------------|------|
| **User Story** | US-01 | View Shopping Cart | docs/08-user-stories.md#US-CART-01 |
| **Acceptance Criteria** | AC-CART-01.02 | Display Cart Summary | docs/09-acceptance-criteria.md |
| **Functional Requirement** | FR-CART-10 | Display Grand Total | docs/11-functional-requirements.md#FR-CART-10 |

#### 3.5.5. Implementation Notes

| Aspect | Giải Pháp Đề Xuất | Trạng Thái |
|--------|-----------------|-----------|
| **Calculation** | Grand_Total = Subtotal (Phase 1) | ✅ Confirmed |
| **Future Phase** | Grand_Total = Subtotal + Shipping_Fee (Phase 2+) | 📋 Out of Scope Phase 1 |
| **Display Label** | "Tạm tính" or "Tổng tiền" (clarify in design) | ⚠️ Cần xác nhận |
| **Precision** | DECIMAL(12,2) | ✅ Required |

#### 3.5.6. Notes

- **Phase 1 Limitation:** Quy tắc này chỉ áp dụng trong Phase 1 (Giỏ hàng module). Shipping fee sẽ được thêm vào Phase 2 (Checkout)
- **Terminology:** Label "Tạm tính" (Subtotal/Temporary Total) được khuyến khích để phân biệt với "Tổng tiền cuối cùng" (Final Grand Total với shipping)
- **Future-proofing:** Architecture phải cho phép mở rộng công thức sau khi thêm shipping, taxes, discounts

---

### 3.6. BR-NOTE-01: Order Note Character Limit

| Thuộc Tính | Giá Trị |
|-----------|--------|
| **Rule ID** | BR-NOTE-01 |
| **Rule Name** | Order Note Character Limit |
| **Rule Type** | ✅ **Validation Rule** |
| **Priority** | 🟠 **High** |
| **Status** | ✅ **Confirmed** |

#### 3.6.1. Rule Statement

```
Ghi chú đơn hàng (Order Note) tối đa 256 ký tự.
Hệ thống không cho phép khách hàng nhập vượt quá 256 ký tự.

---

Order notes must not exceed 256 characters.
The system must reject or truncate notes longer than 256 characters.
```

#### 3.6.2. Rationale

- **Business Reason:** Ghi chú dùng để cung cấp hướng dẫn giao hàng, yêu cầu đặc biệt (e.g., "Giao vào tối sau 6PM", "Không cần packaging đẹp")
- **Data Constraint:** 256 characters là điểm cân bằng giữa flexibility và database storage efficiency
- **UI Constraint:** Textarea với giới hạn ký tự giúp giao diện không bị méo

#### 3.6.3. Source

| Nguồn | Chi Tiết | Link |
|------|---------|------|
| **Project Scope** | SC-06: Add order note with max 256 characters | docs/04-project-scope.md |
| **Source Material** | Shopping Cart Functions | source-documents/source-material.md (Line 47) |

#### 3.6.4. Related Requirements

| Type | ID | Requirement | Link |
|------|-----|-------------|------|
| **User Story** | US-03 | Add Order Note | docs/08-user-stories.md#US-CART-03 |
| **Acceptance Criteria** | AC-CART-03.01, AC-CART-03.02 | Accept & Validate Order Note | docs/09-acceptance-criteria.md |
| **Functional Requirement** | FR-CART-11, FR-CART-12 | Accept & Validate Order Note | docs/11-functional-requirements.md |

#### 3.6.5. Implementation Notes

| Aspect | Giải Pháp Đề Xuất | Trạng Thái |
|--------|-----------------|-----------|
| **Client-side** | HTML5 `<textarea maxlength="256">` | ✅ Recommended |
| **Server-side** | Validate length <= 256 trước save database | ✅ Required |
| **Excess Input Handling** | **Option A:** Reject & show error; **Option B:** Truncate silently | ⚠️ Cần xác nhận |
| **Character Count Display** | Show live counter: "245/256 characters" | ⚠️ Suggested |
| **Error Message** | "Ghi chú không được vượt quá 256 ký tự" | ✅ Suggested |

#### 3.6.6. Notes

- **Character Definition:** 256 ký tự tính cả Unicode (tiếng Việt, emoji); không phải 256 bytes
- **Whitespace:** Ghi chú có thể chứa spaces, line breaks; không trim/normalize
- **Optional Field:** Order Note là tùy chọn (không bắt buộc); customer có thể để trống
- **Database Field:** Dùng VARCHAR(256) hoặc TEXT với constraint CHECK (LENGTH(note) <= 256)

---

### 3.7. BR-CART-05: Remove All Confirmation

| Thuộc Tính | Giá Trị |
|-----------|--------|
| **Rule ID** | BR-CART-05 |
| **Rule Name** | Remove All Confirmation |
| **Rule Type** | ✅ **Business Rule** |
| **Priority** | 🔴 **Critical** |
| **Status** | ✅ **Confirmed** |

#### 3.7.1. Rule Statement

```
Khi khách hàng muốn xóa toàn bộ sản phẩm khỏi giỏ hàng, hệ thống phải
yêu cầu xác nhận bằng cách hiển thị confirmation dialog.
Chỉ khi khách hàng confirm (nhấn "Yes" hoặc "OK"), mới thực hiện xóa.
Nếu khách hàng hủy (nhấn "Cancel" hoặc "No"), giỏ hàng không bị xóa.

---

When a customer attempts to remove all products from the cart,
the system must display a confirmation dialog.
Only upon explicit confirmation, the cart is cleared.
If the user cancels, the cart remains unchanged.
```

#### 3.7.2. Rationale

- **Business Reason:** Xóa toàn bộ giỏ là action có tác động lớn; cần xác nhận để tránh nhấn sai
- **User Experience:** Confirmation dialog giúp ngăn chặn accidental deletion
- **Data Integrity:** Đảm bảo intent của user trước khi thay đổi cart state

#### 3.7.3. Source

| Nguồn | Chi Tiết | Link |
|------|---------|------|
| **Project Scope** | SC-08: Remove all products with confirmation | docs/04-project-scope.md |
| **Source Material** | Shopping Cart Functions | source-documents/source-material.md (Line 49) |

#### 3.7.4. Related Requirements

| Type | ID | Requirement | Link |
|------|-----|-------------|------|
| **User Story** | US-05 | Remove All Products | docs/08-user-stories.md#US-CART-05 |
| **Acceptance Criteria** | AC-CART-05.01, AC-CART-05.02, AC-CART-05.03 | Remove All with Confirmation | docs/09-acceptance-criteria.md |
| **Functional Requirement** | FR-CART-14, FR-CART-15 | Remove All & Display Confirmation | docs/11-functional-requirements.md |
| **Use Case** | UC-CART-05 | Remove All Products | docs/07-use-cases.md (cần xác nhận) |

#### 3.7.5. Implementation Notes

| Aspect | Giải Pháp Đề Xuất | Trạng Thái |
|--------|-----------------|-----------|
| **Dialog Type** | Native browser confirm() hoặc custom modal dialog | ✅ Either acceptable |
| **Dialog Content** | Title: "Xác nhận"; Message: "Bạn có chắc chắn muốn xóa tất cả sản phẩm?" | ✅ Suggested |
| **Buttons** | Confirm button: "Xóa hết" / "Yes"; Cancel button: "Hủy" / "No" | ✅ Suggested |
| **Dismissible** | Dialog có thể dismiss bằng Escape key hoặc click outside? | ⚠️ Cần xác nhận |
| **Backend Validation** | Verify user intent trước delete tại server (optional) | ⚠️ Suggested |

#### 3.7.6. Notes

- **Edge Case:** Nếu cart đã rỗng, nút "Remove All" phải disabled hoặc hidden
- **Post-Deletion:** Sau khi xóa, display Empty State (BR-CART-06) và trigger navigation back to shopping
- **Undo:** Quy tắc hiện tại không hỗ trợ undo; nếu cần, là out of scope Phase 1
- **Analytics (Future):** Có thể track "Remove All" events cho business intelligence

---

### 3.8. BR-CART-06: Cart Empty State Trigger

| Thuộc Tính | Giá Trị |
|-----------|--------|
| **Rule ID** | BR-CART-06 |
| **Rule Name** | Cart Empty State Trigger |
| **Rule Type** | ✅ **Business Rule** |
| **Priority** | 🟠 **High** |
| **Status** | ✅ **Confirmed** |

#### 3.8.1. Rule Statement

```
Khi giỏ hàng không còn sản phẩm nào (0 items), hệ thống phải:
1. Ẩn danh sách sản phẩm
2. Ẩn cart summary (subtotal, grand total)
3. Hiển thị "Empty State" message (e.g., "Giỏ hàng trống")
4. Hiển thị nút "Continue Shopping" để quay lại duyệt sản phẩm

---

When the cart contains 0 products, the system must:
1. Hide the product list
2. Hide cart summary (subtotal, grand total)
3. Display an Empty State message
4. Display a "Continue Shopping" button
```

#### 3.8.2. Rationale

- **User Experience:** Empty state cung cấp clear visual feedback & guidance cho user tiếp tục shopping
- **Business Value:** Nút "Continue Shopping" giúp user quay lại duyệt sản phẩm → tăng conversion
- **UI Consistency:** Theo UI/UX best practices, empty state là standard pattern

#### 3.8.3. Source

| Nguồn | Chi Tiết | Link |
|------|---------|------|
| **Project Scope** | SC-09: Display empty-cart state | docs/04-project-scope.md |
| **Source Material** | Shopping Cart Functions | source-documents/source-material.md (Line 50) |

#### 3.8.4. Related Requirements

| Type | ID | Requirement | Link |
|------|-----|-------------|------|
| **User Story** | US-01 | View Shopping Cart | docs/08-user-stories.md#US-CART-01 |
| **User Story** | US-04 | Remove One Product | docs/08-user-stories.md#US-CART-04 |
| **User Story** | US-05 | Remove All Products | docs/08-user-stories.md#US-CART-05 |
| **User Story** | US-06 | View Empty Cart State | docs/08-user-stories.md#US-CART-06 |
| **Acceptance Criteria** | AC-CART-01.03, AC-CART-06.01, AC-CART-06.02, AC-CART-06.03 | Empty State Handling | docs/09-acceptance-criteria.md |
| **Functional Requirement** | FR-CART-16 | Display Empty Cart State | docs/11-functional-requirements.md#FR-CART-16 |

#### 3.8.5. Implementation Notes

| Aspect | Giải Pháp Đề Xuất | Trạng Thái |
|--------|-----------------|-----------|
| **Trigger Condition** | cart.items.length === 0 | ✅ Required |
| **Empty State UI** | Centered message + icon + CTA button | ✅ Recommended |
| **Message Text** | "Giỏ hàng của bạn trống" hoặc tương tự | ✅ Suggested |
| **Continue Shopping Button** | Link/Button back to product listing | ✅ Required |
| **Checkout Button** | Disabled or hidden when empty | ✅ Required |
| **Summary Section** | Hidden when empty | ✅ Required |

#### 3.8.6. Notes

- **Trigger Points:** Empty state được trigger bởi:
  - Khách hàng vừa xóa sản phẩm cuối cùng (Remove Single, UC-CART-04)
  - Khách hàng vừa xóa toàn bộ (Remove All, UC-CART-05)
  - Khách hàng access cart lần đầu (chưa add sản phẩm nào)
- **Navigation:** Nút "Continue Shopping" phải link/redirect tới product listing page
- **Persistence:** Nếu user refresh trang khi cart trống, empty state vẫn hiển thị

---

### 3.9. BR-CART-07: Product Order (LIFO) ⚠️ Draft

| Thuộc Tính | Giá Trị |
|-----------|--------|
| **Rule ID** | BR-CART-07 |
| **Rule Name** | Product Order (LIFO - Last In First Out) |
| **Rule Type** | ✅ **Display Rule** |
| **Priority** | 🟡 **Medium** |
| **Status** | ⚠️ **Draft – Needs confirmation** |

#### 3.9.1. Rule Statement

```
Sản phẩm được thêm gần đây nhất sẽ được hiển thị ở vị trí trên cùng (top).
Sản phẩm được thêm sớm nhất sẽ hiển thị ở cuối cùng (bottom).

Quy tắc này tuân theo LIFO (Last In First Out) order.

---

Products added most recently should be displayed at the top.
Products added earliest should be displayed at the bottom.
This follows LIFO (Last In First Out) ordering.

Example:
  Time 1: Add Product A → Cart: [A]
  Time 2: Add Product B → Cart: [B, A]
  Time 3: Add Product C → Cart: [C, B, A]  (C on top, A at bottom)
```

#### 3.9.2. Rationale

- **UX Rationale:** LIFO order giúp customer dễ nhìn thấy sản phẩm mới nhất (thường là chính focus gần đây)
- **Alternative Rationale:** Tùy vào preference; có thể dùng FIFO (First In First Out) hoặc user-defined sort
- **⚠️ Cần Xác Nhận:** Không có source tường minh trong documentation; quy tắc này là **proposed assumption**

#### 3.9.3. Source

| Nguồn | Chi Tiết | Link |
|------|---------|------|
| **Proposed** | Inferred from UX best practices; **not explicitly confirmed in docs** | - |
| **To Confirm** | Do stakeholders prefer LIFO, FIFO, or user-sortable order? | docs/04-project-scope.md (SC-01) |

#### 3.9.4. Related Requirements

| Type | ID | Requirement | Link |
|------|-----|-------------|------|
| **User Story** | US-01 | View Shopping Cart | docs/08-user-stories.md#US-CART-01 |
| **Acceptance Criteria** | AC-CART-01.01 | Display All Products in Cart | docs/09-acceptance-criteria.md |
| **Functional Requirement** | FR-CART-01 | Load and Display Product List | docs/11-functional-requirements.md |

#### 3.9.5. Implementation Notes

| Aspect | Giải Pháp Đề Xuất | Trạng Thái |
|--------|-----------------|-----------|
| **Database** | Store timestamp (added_at) for each cart item | ✅ Recommended |
| **Sorting** | ORDER BY added_at DESC (newest first) | ✅ If LIFO chosen |
| **Alternative** | ORDER BY added_at ASC (oldest first) = FIFO | ⚠️ Need stakeholder decision |
| **Sorting Option** | Allow customer to re-order items manually? | ⚠️ Out of Phase 1 scope |

#### 3.9.6. Notes

- **⚠️ Confirmation Needed:** Quy tắc này **chưa được stakeholder xác nhận chính thức**. Cần hỏi Đại Phú hoặc Supervisor:
  - Nên order LIFO hay FIFO hay có thứ tự khác?
  - Có cần cho phép user manual reorder items không?
- **Alternative Orderings:**
  - **FIFO:** Products added first appear first
  - **User-defined:** Drag & drop reorder
  - **Product Name:** Sort alphabetically
  - **Price:** Sort by price
- **Current Assumption:** LIFO (Last In First Out) là assumption ban đầu

---

### 3.10. BR-CART-08: Product Name Display Truncation ⚠️ Draft

| Thuộc Tính | Giá Trị |
|-----------|--------|
| **Rule ID** | BR-CART-08 |
| **Rule Name** | Product Name Display Truncation |
| **Rule Type** | ✅ **Display Rule** |
| **Priority** | 🟡 **Medium** |
| **Status** | ⚠️ **Draft – Needs confirmation** |

#### 3.10.1. Rule Statement

```
Tên sản phẩm được hiển thị trên tối đa hai dòng (max 2 lines).
Nếu tên sản phẩm dài vượt quá 2 dòng, phần tiếp theo sẽ được cắt ngắn
và hiển thị dấu "..." (ellipsis).

---

Product names are displayed on a maximum of 2 lines.
If a product name exceeds 2 lines, it will be truncated with "..." (ellipsis).

Example:
  Line 1: "Hoa hồng đỏ lụa cao cấp với lá xanh"
  Line 2: "và cỏ baby's breath trắng"
  If longer → "Hoa hồng đỏ lụa cao cấp với lá xanh và cỏ baby's breath..."
```

#### 3.10.2. Rationale

- **UI Constraint:** Giới hạn 2 dòng giúp giỏ hàng không bị quá dài, layout được kiểm soát
- **Content:** Phần tên sản phẩm quan trọng sẽ hiển thị đủ (thường 2 dòng là đủ)
- **Hover/Tooltip:** User có thể hover để xem full tên (tùy chọn)
- **⚠️ Cần Xác Nhận:** Không có source tường minh; assumption dựa trên UI best practices

#### 3.10.3. Source

| Nguồn | Chi Tiết | Link |
|------|---------|------|
| **Proposed** | Inferred from UI/UX design best practices; **not explicitly stated in docs** | - |
| **To Confirm** | Should product names be truncated? 2 lines or other limit? | docs/04-project-scope.md (Mockup design TBD) |

#### 3.10.4. Related Requirements

| Type | ID | Requirement | Link |
|------|-----|-------------|------|
| **User Story** | US-01 | View Shopping Cart | docs/08-user-stories.md#US-CART-01 |
| **Acceptance Criteria** | AC-CART-01.01 | Display All Products in Cart | docs/09-acceptance-criteria.md |
| **Functional Requirement** | FR-CART-02 | Display Product Information | docs/11-functional-requirements.md |

#### 3.10.5. Implementation Notes

| Aspect | Giải Pháp Đề Xuất | Trạng Thái |
|--------|-----------------|-----------|
| **CSS Solution** | Use `overflow: hidden; text-overflow: ellipsis; display: -webkit-box; -webkit-line-clamp: 2` | ✅ Recommended |
| **Character Limit** | ~80-100 characters per line (depending on font size) | ⚠️ Design spec TBD |
| **Hover Tooltip** | Show full name on hover (optional UX enhancement) | ✅ Recommended |
| **Alternative** | Allow user to expand / show full name on click | ⚠️ Out of Phase 1 |

#### 3.10.6. Notes

- **⚠️ Confirmation Needed:** Quy tắc này **chưa được xác nhận chính thức**. Cần:
  - Confirm số dòng tối đa (2 dòng hay khác?)
  - Confirm cách handle text dài (ellipsis hay tooltip hay expand?)
  - Confirm font size & line height (ảnh hưởng ký tự/dòng)
- **Design Dependency:** Quy tắc này phụ thuộc vào Figma mockups & responsive design specs
- **Responsive:** Trên mobile, limit dòng có thể thay đổi (1 dòng hay 2 dòng?)

---

## 4. Business Rules Impact Analysis

### 4.1. Cross-Functional Dependencies

| Rule | Depends On | Impacts | Notes |
|------|-----------|---------|-------|
| **BR-CART-01** | - | BR-PRICE-01, BR-CART-03, BR-CART-04 | Min qty constraint enables price calculations |
| **BR-CART-02** | - | BR-PRICE-01, BR-CART-03, BR-CART-04 | Integer qty enables reliable calculations |
| **BR-PRICE-01** | BR-CART-02 | BR-CART-03, BR-CART-04 | Item total = unit price × integer qty |
| **BR-CART-03** | BR-PRICE-01, BR-CART-01 | BR-CART-04 | Subtotal = sum of item totals |
| **BR-CART-04** | BR-CART-03 | Display summary section | Grand total = subtotal (Phase 1) |
| **BR-NOTE-01** | - | FR-CART-11, FR-CART-12 | Character limit enforced at input & server |
| **BR-CART-05** | - | FR-CART-14, FR-CART-15 | Confirmation dialog for destructive action |
| **BR-CART-06** | BR-CART-01, BR-CART-05 | FR-CART-16 | Empty state triggered when 0 items |
| **BR-CART-07** | - | FR-CART-01 (sort order) | LIFO ordering on product display |
| **BR-CART-08** | - | FR-CART-02 (display format) | 2-line truncation on product names |

### 4.2. User Journey Impact

| Rule | Triggers During | Impact on User Journey |
|------|-------------------|----------------------|
| **BR-CART-01** | View Cart, Update Qty | Prevents qty < 1; user must remove item instead |
| **BR-CART-02** | Update Qty | Ensures valid numeric input; user cannot enter 2.5 or -1 |
| **BR-PRICE-01** | View Cart, Update Qty, Remove Item | Recalculates & displays updated price immediately |
| **BR-CART-03** | Add Item, Update Qty, Remove Item | Subtotal updates in real-time |
| **BR-CART-04** | Any cart change | Grand total always visible & current |
| **BR-NOTE-01** | Add/Edit Note | User sees character count; cannot exceed 256 chars |
| **BR-CART-05** | Click "Remove All" button | Confirmation dialog prevents accidental clearing |
| **BR-CART-06** | Remove last item or clear cart | Empty state provides clear feedback & CTA |
| **BR-CART-07** | View cart | Newest items appear at top (if LIFO confirmed) |
| **BR-CART-08** | View cart with long product names | Names truncated to 2 lines; full name on hover |

---

## 5. Validation & Testing Coverage

### 5.1. Test Coverage by Business Rule

| Rule | Total Test Cases | Test Types | Status |
|------|------------------|-----------|--------|
| **BR-CART-01** | 3 | Boundary (qty=1, qty=0 prevented), State | TC_UPD_01, TC_UPD_02 |
| **BR-CART-02** | 2 | Data Type (integer only), Boundary | TC_UPD_01 |
| **BR-PRICE-01** | 3 | Calculation, Data accuracy, Real-time update | TC_UI_01 |
| **BR-CART-03** | 3 | Calculation, Multi-item sum, Empty cart | TC_UI_01 |
| **BR-CART-04** | 2 | Display, Calculation, Post-change verify | TC_UI_01 |
| **BR-NOTE-01** | 3 | Input validation, Length check, Exceed limit | Cần tạo |
| **BR-CART-05** | 3 | Dialog confirmation, Positive/negative path | TC_DEL_01 |
| **BR-CART-06** | 3 | State trigger, Empty display, CTA availability | TC_DEL_01 |
| **BR-CART-07** | 2 | Display order (LIFO), Multiple items | ⚠️ Pending confirmation |
| **BR-CART-08** | 2 | Text truncation, Hover/tooltip, Responsive | ⚠️ Pending confirmation |

### 5.2. Test Case Mapping

| Test Case ID | Rules Covered | Reference |
|--------------|--------------|-----------|
| **TC_UI_01** | BR-CART-01, BR-PRICE-01, BR-CART-03, BR-CART-04 | Verify cart display & calculations |
| **TC_UPD_01** | BR-CART-01, BR-CART-02 | Prevent qty < 1, ensure integer input |
| **TC_DEL_01** | BR-CART-05, BR-CART-06 | Confirm remove all, trigger empty state |
| **Cần tạo** | BR-NOTE-01 | Test character limit, validation |
| **Pending** | BR-CART-07, BR-CART-08 | Test LIFO order & text truncation |

---

## 6. Items Requiring Stakeholder Confirmation

### 6.1. Critical Confirmations

| Item | Rule | Question | Impact | Priority |
|------|------|----------|--------|----------|
| **BR-CART-01 UI Behavior** | BR-CART-01 | When qty=1, disable "-" button or remove item? | User experience | 🔴 Critical |
| **BR-NOTE-01 Excess Handling** | BR-NOTE-01 | If note > 256 chars: block input or truncate? | Data handling | 🟠 High |
| **BR-CART-07 Product Order** | BR-CART-07 | Should products display LIFO, FIFO, or sortable? | Display logic | 🟡 Medium |
| **BR-CART-08 Line Limit** | BR-CART-08 | Should product names truncate at 2 lines or other limit? | UI design | 🟡 Medium |

### 6.2. Design & Technical Confirmations

| Item | Rule | Question | Impact | Priority |
|------|------|----------|--------|----------|
| **BR-PRICE-01 Precision** | BR-PRICE-01 | Currency rounding: 2 decimals always? Banker's rounding? | Financial accuracy | 🔴 Critical |
| **BR-CART-04 Shipping** | BR-CART-04 | Confirm shipping fee added in Checkout phase, not Cart? | Scope clarity | 🔴 Critical |
| **BR-CART-05 Dialog** | BR-CART-05 | Native confirm() dialog or custom modal design? | Implementation | 🟠 High |
| **BR-CART-06 Empty UX** | BR-CART-06 | Empty state design: message, icon, CTA button text? | UX design | 🟠 High |

---

## 7. Reference & Links

### 7.1. Related Documents

| Document | Link | Relevance |
|----------|------|-----------|
| **Project Scope** | docs/04-project-scope.md | Source of SC-XX functions |
| **User Stories** | docs/08-user-stories.md | US-CART-XX linked to rules |
| **Acceptance Criteria** | docs/09-acceptance-criteria.md | AC-CART-XX validation criteria |
| **Functional Requirements** | docs/11-functional-requirements.md | FR-CART-XX system behavior |
| **User Flow** | docs/06-user-flow.md | User interaction scenarios |
| **Source Material** | source-documents/source-material.md | Shopping Cart Functions list |

### 7.2. External Standards

| Standard | Topic | Relevance |
|----------|-------|-----------|
| **IIBA BA Guide** | Business Rules Definition | Best practices for BR documentation |
| **IEEE 830** | Requirements Specification | Requirement format & traceability |
| **Agile Testing** | Test Case Design | AC → Test Case mapping |

---

## 8. Change Log

| Version | Date | Changes | Author | Status |
|---------|------|---------|--------|--------|
| **1.0** | 2026-07-19 | Initial Business Rule Catalog | BA Team | Draft |
| | | - 8 Business Rules defined | | |
| | | - 2 rules marked "Draft – Needs confirmation" | | |
| | | - Impact analysis completed | | |
| | | - Test coverage mapped | | |

---

## 9. Document Metadata

| Attribute | Value |
|-----------|-------|
| **Document Type** | Business Rule Catalog |
| **Module** | Shopping Cart (Module Giỏ Hàng) |
| **Phase** | Phase 1 - Analysis Complete |
| **Status** | ✅ Analyzed (2 rules pending confirmation) |
| **Total Rules** | 8 (6 Confirmed, 2 Draft) |
| **Language** | Vietnamese (Primary) + English (Reference) |
| **Format** | Markdown with tables & examples |
| **Audience** | Business Analyst, Developers, QA, Stakeholders |
| **Classification** | Portfolio Documentation |
| **Last Updated** | 2026-07-19 |

---

## 10. Important Disclaimers

### ✅ What This Catalog Represents

- ✅ Comprehensive Business Rules for Phase 1 Shopping Cart module
- ✅ Rules derived from User Stories, Acceptance Criteria, & Project Scope
- ✅ Technology-agnostic specifications (flexible for multiple implementations)
- ✅ Foundation for detailed requirements & test case design
- ✅ Traceability to source documents & related artifacts

### ⚠️ Items Requiring Confirmation

- ⚠️ **BR-CART-07 (LIFO Order):** Needs stakeholder confirmation on product ordering logic
- ⚠️ **BR-CART-08 (Name Truncation):** Needs design confirmation on 2-line limit & responsive behavior
- ⚠️ Multiple implementation decisions pending stakeholder clarification (see Section 6)

### ❌ What This Catalog Does NOT Represent

- ❌ Implemented code or functional system
- ❌ Database schema design (that is a separate technical specification)
- ❌ UI/UX design details (see Figma mockups for visual specifications)
- ❌ Complete system specification (NFR, API contracts, data model separate)
- ❌ Passed testing or validation
- ❌ Production-ready rules (pending Phase 2+ implementation & UAT)

---

**End of Document**
