# Phạm Vi Dự Án (Project Scope)

## 1. Scope Purpose

Tài liệu Project Scope định nghĩa ranh giới của dự án Business Analysis cho module Giỏ hàng (Shopping Cart) của website Đại Phú. Mục đích của tài liệu này là:

- **Xác định rõ ràng** những gì được bao gồm (In Scope) và không bao gồm (Out of Scope) trong Phase 1
- **Ngăn chặn scope creep** bằng cách định nghĩa ranh giới rõ ràng
- **Quản lý kỳ vọng** của các stakeholders về phạm vi phân tích và tài liệu hóa
- **Hỗ trợ Planning & Estimation** để đánh giá công việc cần làm
- **Cung cấp Baseline** cho Change Control nếu có yêu cầu thay đổi
- **Giảm thiểu Risks** bằng cách làm rõ ranh giới và dependencies

---

## 2. Project Boundary

### 2.1. Phạm Vi Chính (Primary Scope)

**Module/Feature:** Shopping Cart (Giỏ Hàng)

**Business Area:** E-commerce - Order Management

**Phase:** Phase 1 (Initial Analysis & Design)

**Project Type:** Business Analysis & UI/UX Design Portfolio (không bao gồm implementation)

### 2.2. Ranh Giới Dự Án

```
┌─────────────────────────────────────────────────────────────────┐
│                        E-commerce Website                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌─────────────┐    ┌──────────────────────┐    ┌────────────┐ │
│  │   Product   │    │   Shopping Cart      │    │  Checkout  │ │
│  │   Browse    │ →  │   (Phase 1 Scope)    │ →  │   (Out)    │ │
│  │   (Out)     │    │                      │    │            │ │
│  └─────────────┘    └──────────────────────┘    └────────────┘ │
│                                                                 │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  Backend: Order Management, Payment, Inventory (Out)     │   │
│  └──────────────────────────────────────────────────────────┘   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                      Scope of Phase 1 BA Work                   │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Analysis  →  Design  →  Specification  →  Test Cases         │
│                                                                 │
│  ❌ NOT: Implementation, Testing, Deployment                   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 2.3. Khoảng Thời Gian

| Thuộc Tính | Chi Tiết |
|-----------|---------|
| **Internship Period** | Tháng 9 - Tháng 12, 2025 (4 tháng) |
| **Phase 1 Duration** | Cần xác nhận |
| **Phase 2+ Status** | Chưa lập kế hoạch (Out of Scope) |

---

## 3. Phase 1 Scope

### 3.1. Mục Tiêu Phase 1

| Mục Tiêu | Trạng Thái | Mô Tả |
|---------|----------|--------|
| **Requirement Elicitation** | Analyzed | Tiếp nhận & tổng hợp yêu cầu từ Supervisor, Customer, Developer |
| **User Flow Modeling** | Analyzed | Tạo sơ đồ quy trình xử lý khách hàng trong Giỏ hàng |
| **Use Case Specification** | Analyzed | Tạo tài liệu Use Case chi tiết |
| **Functional Requirements** | Analyzed | Xác định & tài liệu hóa functional requirements |
| **Non-Functional Requirements** | Analyzed | Xác định & tài liệu hóa NFR (performance, security, usability) |
| **Business Rules Definition** | Analyzed | Tài liệu hóa các quy tắc nghiệp vụ |
| **UI/UX Mockups** | Designed | Thiết kế mockups trên Figma |
| **User Stories** | Analyzed | Viết User Stories với format chuẩn |
| **Acceptance Criteria** | Analyzed | Xác định Acceptance Criteria chi tiết |
| **Functional Test Cases** | Analyzed | Tạo test cases kiểm thử chức năng |
| **Requirements Traceability** | Analyzed | Liên kết requirement ↔ test cases ↔ user stories |
| **Documentation** | Analyzed | Tài liệu hóa toàn bộ quá trình |

### 3.2. Deliverables Phase 1

| Deliverable | Status | Mô Tả |
|-----------|--------|--------|
| **User Process Flow** | Analyzed | Sơ đồ quy trình chi tiết |
| **Use Case Specification** | Analyzed | Tài liệu Use Case (actors, flows, preconditions, postconditions) |
| **SRS (Software Requirements Specification)** | Analyzed | Tài liệu yêu cầu phần mềm toàn diện |
| **Functional Requirements (FR-CART-XX)** | Analyzed | Danh sách các yêu cầu chức năng |
| **Non-Functional Requirements (NFR-CART-XX)** | Analyzed | Danh sách các yêu cầu phi chức năng |
| **Business Rules (BR-CART-XX)** | Analyzed | Các quy tắc nghiệp vụ |
| **User Stories (US-CART-XX)** | Analyzed | User Stories theo format: As a [user], I want [action], So that [benefit] |
| **Acceptance Criteria (AC-CART-XX)** | Analyzed | Tiêu chí chấp nhận chi tiết |
| **Figma Mockups** | Designed | Wireframes & mockups giao diện |
| **Functional Test Cases (TC-XX)** | Analyzed | Test cases kiểm thử chức năng |
| **Requirement Traceability Matrix** | Analyzed | Ma trận liên kết requirement ↔ user story ↔ test case |
| **Azure DevOps Work Items** | Analyzed | Các work items được tạo trên Azure DevOps |

---

## 4. In Scope

### 4.1. Chức Năng Shopping Cart Được Phân Tích (In Scope)

| ID | Chức Năng | Trạng Thái | Mô Tả |
|----|---------|-----------|--------|
| **SC-01** | **Xem danh sách sản phẩm trong giỏ hàng** | Analyzed | Hiển thị danh sách tất cả sản phẩm đã được thêm vào giỏ hàng |
| **SC-02** | **Hiển thị thông tin sản phẩm** | Analyzed | Hiển thị chi tiết: hình ảnh sản phẩm, tên, giá đơn vị, số lượng, thành tiền |
| **SC-03** | **Tăng số lượng sản phẩm** | Analyzed | Cho phép khách hàng tăng số lượng sản phẩm (thông qua nút +, input field, hoặc dropdown) |
| **SC-04** | **Giảm số lượng sản phẩm** | Analyzed | Cho phép khách hàng giảm số lượng sản phẩm (thông qua nút -, input field, hoặc dropdown) |
| **SC-05** | **Giới hạn số lượng tối thiểu** | Analyzed | Ngăn chặn số lượng không thể giảm dưới 1 (validation rule) |
| **SC-06** | **Tính thành tiền (item total)** | Analyzed | Tính toán tự động: Unit Price × Quantity = Item Total |
| **SC-07** | **Tính tạm tính (subtotal)** | Analyzed | Tính toán tổng của tất cả Item Total (chưa bao gồm tax, shipping) |
| **SC-08** | **Tính tổng tiền** | Analyzed | Tính toán tổng cộng = Subtotal + Tax + Shipping (nếu áp dụng) - Cần xác nhận |
| **SC-09** | **Nhập ghi chú đơn hàng (Order Note)** | Analyzed | Cho phép khách hàng nhập ghi chú cho đơn hàng (ví dụ: hướng dẫn giao hàng) |
| **SC-10** | **Validation ghi chú** | Analyzed | Ghi chú tối đa 256 ký tự, không để trống không bắt buộc |
| **SC-11** | **Xóa một sản phẩm** | Analyzed | Cho phép khách hàng xóa một sản phẩm khỏi giỏ hàng |
| **SC-12** | **Xóa toàn bộ giỏ hàng** | Analyzed | Cho phép xóa tất cả sản phẩm (với confirmation) |
| **SC-13** | **Confirmation Popup** | Designed | Hiển thị popup xác nhận trước khi xóa toàn bộ |
| **SC-14** | **Empty State** | Designed | Hiển thị giao diện khi giỏ hàng trống (với hướng dẫn quay lại shopping) |
| **SC-15** | **Chuyển sang bước thông tin giao hàng** | Analyzed | Nút "Checkout" / "Tiếp tục" chuyển khách hàng tới bước nhập thông tin giao hàng |

### 4.2. Tài liệu Hóa & Thiết Kế

| Công Việc | Trạng Thái | Mô Tả |
|----------|----------|--------|
| **Requirement Analysis** | Analyzed | Phân tích chi tiết các yêu cầu chức năng |
| **User Flow Diagram** | Analyzed | Tạo sơ đồ quy trình khách hàng |
| **Use Case Modeling** | Analyzed | Tạo tài liệu Use Case |
| **Mockup Design** | Designed | Thiết kế giao diện trên Figma |
| **Documentation** | Analyzed | Tài liệu hóa toàn bộ |
| **Test Case Design** | Analyzed | Tạo test cases chức năng |

### 4.3. Non-Functional Aspects (Nếu Được Phân Tích)

| Khía Cạnh | Trạng Thái | Mô Tả |
|----------|----------|--------|
| **Usability** | Analyzed | Giao diện dễ sử dụng, trực quan |
| **Performance** | Analyzed* | Cần xác nhận: yêu cầu response time, load time |
| **Accessibility** | Analyzed* | Cần xác nhận: hỗ trợ accessibility (a11y) |
| **Security** | Analyzed* | Cần xác nhận: requirements bảo mật tại giỏ hàng |
| **Browser Compatibility** | Analyzed* | Cần xác nhận: browsers được hỗ trợ |
| **Mobile Support** | Analyzed* | Cần xác nhận: responsive design cho mobile |

*Nếu được phân tích trong Phase 1; nếu không thì cần xác nhận

---

## 5. Out of Scope

### 5.1. Chức Năng Không Bao Gồm trong Phase 1

| ID | Chức Năng / Khía Cạnh | Lý Do | Trạng Thái |
|----|---------------------|-------|----------|
| **OOS-01** | **Thanh toán trực tuyến (Payment Processing)** | Thanh toán là một module riêng biệt, nằm ngoài module Giỏ hàng | Out of Phase 1 |
| **OOS-02** | **Xác thực khách hàng (Customer Authentication)** | Quản lý tài khoản & authentication là responsibility của riêng module | Out of Phase 1 |
| **OOS-03** | **Quản lý vận chuyển hoàn chỉnh (Full Shipping Management)** | Tính phí ship, chọn phương thức vận chuyển có thể là bước Checkout riêng | Out of Phase 1 |
| **OOS-04** | **Quản trị sản phẩm (Product Management)** | Thêm/sửa/xóa sản phẩm là responsibility của Admin/Product module | Out of Phase 1 |
| **OOS-05** | **Quản lý tồn kho hoàn chỉnh (Inventory Management)** | Kiểm tra tồn kho ngoài scope; giả sử backend API cung cấp | Out of Phase 1 |
| **OOS-06** | **Khuyến mãi & Coupon (Promotions & Discounts)** | Áp dụng khuyến mãi là responsibility của riêng module | Out of Phase 1 |
| **OOS-07** | **Lịch sử giỏ hàng (Cart History)** | Lịch sử, lưu giỏ hàng cho lần sau có thể là phase sau | Out of Phase 1 |
| **OOS-08** | **Đề xuất sản phẩm (Product Recommendations)** | Recommendation engine nằm ngoài scope giỏ hàng | Out of Phase 1 |
| **OOS-09** | **Tích hợp với CRM/ERP** | Tích hợp với hệ thống backend là ngoài scope BA; là trách nhiệm Developer | Out of Phase 1 |
| **OOS-10** | **Quản lý Multi-currency hoàn chỉnh** | Cần xác nhận: có hỗ trợ multiple currencies không | Needs Confirmation |

### 5.2. Implementation & Deployment (Out of Scope)

| Công Việc | Lý Do | Trạng Thái |
|----------|-------|----------|
| **Source Code Development** | Dự án chỉ tập trung vào BA & Design, không phát triển code | Out of Scope |
| **Frontend Implementation** | Phát triển HTML, CSS, JavaScript là responsibility của Developer | Out of Scope |
| **Backend Development** | Phát triển backend API, logic là responsibility của Developer | Out of Scope |
| **Database Development** | Thiết kế & phát triển database là responsibility của Technical Architect/DBA | Out of Scope |
| **Production Deployment** | Triển khai lên production là responsibility của DevOps/Ops Team | Out of Scope |
| **Complete UAT** | Thực hiện UAT hoàn chỉnh với end users có thể là phase sau | Out of Scope |
| **Post-go-live Analysis** | Thu thập metrics, analytic sau khi deploy là ngoài scope internship | Out of Scope |
| **Performance Testing** | Load testing, performance testing là responsibility của QA/Testing team | Out of Scope |
| **Security Testing** | Penetration testing, security audit là responsibility của Security team | Out of Scope |

### 5.3. Scope sau Phase 1 (Proposed for Future Phases)

| Công Việc | Mô Tả | Phase |
|----------|--------|-------|
| **Cart Persistence** | Lưu giỏ hàng (local storage hoặc database) để khách hàng quay lại sau | Phase 2+ |
| **Wishlists** | Danh sách yêu thích, giỏ hàng tạm thời | Phase 2+ |
| **Bulk Operations** | Thêm nhiều sản phẩm cùng lúc | Phase 2+ |
| **Advanced Filtering/Sorting** | Lọc, sắp xếp sản phẩm trong giỏ | Phase 2+ |
| **Gift Options** | Các tùy chọn quà tặng (gift wrap, gift message) | Phase 2+ |
| **Loyalty Points** | Tích điểm, sử dụng điểm | Phase 2+ |
| **Analytics & Reporting** | Báo cáo cart abandonment, conversion | Phase 2+ |

---

## 6. Functional Boundary

### 6.1. Bảng So Sánh In Scope vs Out of Scope

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                        SHOPPING CART FUNCTIONALITY                           │
├──────────────────────────────────────────────────────────────┬───────────────┤
│              IN SCOPE (Phase 1)                              │  OUT OF SCOPE │
├──────────────────────────────────────────────────────────────┼───────────────┤
│ ✅ View Cart Items                                           │ ❌ Payment    │
│ ✅ Display Product Info                                      │ ❌ Shipping   │
│ ✅ Quantity Management (+/-)                                 │ ❌ Promo Code │
│ ✅ Item Total Calculation                                    │ ❌ Inventory  │
│ ✅ Subtotal Calculation                                      │ ❌ Auth       │
│ ✅ Order Notes (Max 256 chars)                               │ ❌ History    │
│ ✅ Remove Item                                               │ ❌ Wishlist   │
│ ✅ Clear Cart (with confirmation)                            │ ❌ Recommend  │
│ ✅ Empty State UI                                            │ ❌ Multi-curr │
│ ✅ Proceed to Checkout                                       │ ❌ Analytics  │
│ ✅ UI Mockups (Figma)                                        │               │
│ ✅ Functional Test Cases                                     │               │
│ ✅ Documentation                                             │               │
└──────────────────────────────────────────────────────────────┴───────────────┘
```

### 6.2. Bảng Chi Tiết In Scope vs Out of Scope

| # | Feature | In Scope | Out of Scope | Evidence | Notes |
|---|---------|----------|--------------|----------|-------|
| 1 | View Cart | ✅ SC-01 | | source-material.md | Display list of items |
| 2 | Display Product Info | ✅ SC-02 | | source-material.md | Show image, name, price, qty, total |
| 3 | Increase Quantity | ✅ SC-03 | | source-material.md | +1 button or input |
| 4 | Decrease Quantity | ✅ SC-04 | | source-material.md | -1 button or input |
| 5 | Min Quantity Check | ✅ SC-05 | | source-material.md | Prevent < 1 |
| 6 | Item Total | ✅ SC-06 | | source-material.md | Unit Price × Qty |
| 7 | Subtotal | ✅ SC-07 | | source-material.md | Sum of items |
| 8 | Total with Tax/Shipping | ✅ SC-08* | | docs/02 | *Needs confirmation |
| 9 | Order Notes | ✅ SC-09 | | source-material.md | Max 256 chars |
| 10 | Note Validation | ✅ SC-10 | | source-material.md | Character limit |
| 11 | Remove Item | ✅ SC-11 | | source-material.md | Delete 1 product |
| 12 | Clear All | ✅ SC-12 | | source-material.md | Delete all with confirmation |
| 13 | Confirmation Dialog | ✅ SC-13 | | docs/01 | Popup before delete |
| 14 | Empty State | ✅ SC-14 | | docs/01 | Show empty message |
| 15 | Checkout Button | ✅ SC-15 | | source-material.md | Proceed to next step |
| 16 | Payment | | ❌ OOS-01 | docs/02 | Separate module |
| 17 | Shipping Selection | | ❌ OOS-03 | docs/02 | Separate module |
| 18 | Promo/Coupon | | ❌ OOS-06 | docs/02 | Phase 2+ |
| 19 | Inventory Check | | ❌ OOS-05 | docs/02 | Backend API |
| 20 | Cart Persistence | | ❌ OOS-07 | docs/02 | Phase 2+ |

---

## 7. Assumptions

### 7.1. Giả Định Chức Năng

| ID | Giả Định | Mô Tả | Evidence Level |
|----|----------|--------|-----------------|
| **ASM-01** | Backend API có sẵn | Giả sử Backend đã cung cấp API để lấy sản phẩm, tính giá, validate | Assumed for portfolio |
| **ASM-02** | Product data có sẵn | Sản phẩm đã có trong database, BA chỉ tập trung vào cart logic | Confirmed by source |
| **ASM-03** | Checkout là bước tiếp theo | Sau khi xác nhận giỏ hàng, khách hàng chuyển sang bước nhập shipping info | Confirmed by source |
| **ASM-04** | Khách hàng sẽ xem giỏ hàng trước thanh toán | Giỏ hàng là bước bắt buộc trong customer journey | Mentioned in docs/02 |
| **ASM-05** | Số lượng sản phẩm < 20 | Giả sử số lượng sản phẩm trong giỏ thường không quá 20 | Assumed for portfolio |
| **ASM-06** | Phí vận chuyển tính tại Checkout | Tính phí vận chuyển & áp dụng discount là ngoài scope Shopping Cart | Assumed for portfolio |
| **ASM-07** | Tax tính tại Checkout hoặc backend | Tính thuế nằm ngoài scope giỏ hàng | Assumed for portfolio |

### 7.2. Giả Định Kỹ Thuật

| ID | Giả Định | Mô Tả | Evidence Level |
|----|----------|--------|-----------------|
| **ASM-08** | Real-time price update | Giá hiển thị update tức thời nếu backend cung cấp API | Assumed for portfolio |
| **ASM-09** | Responsive design | Mockup được thiết kế cho desktop; responsive design là trách nhiệm Developer | Assumed for portfolio |
| **ASM-10** | Validation trên client & server | BA chỉ specify validation rules; Developer implement | Assumed for portfolio |
| **ASM-11** | Cart stored server-side hoặc client-side | Architecture decision nằm ngoài scope BA | Needs confirmation |
| **ASM-12** | Không hỗ trợ multiple currencies | Phase 1 giả sử chỉ 1 currency; multiple currency là Phase 2+ | Needs confirmation |

### 7.3. Giả Định Tổ Chức

| ID | Giả Định | Mô Tả | Evidence Level |
|----|----------|--------|-----------------|
| **ASM-13** | Developer sẽ follow Requirement Document | Giả sử Developer tuân theo tài liệu BA | Assumed for portfolio |
| **ASM-14** | QA sẽ test dựa trên Test Cases | QA sử dụng Test Cases do BA tạo | Assumed for portfolio |
| **ASM-15** | Supervisor sẽ review & approve | Internship Supervisor phê duyệt phase completion | Confirmed by source |

---

## 8. Constraints

### 8.1. Ràng Buộc Phạm Vi (Scope Constraints)

| ID | Constraint | Mô Tả | Impact |
|----|-----------|--------|--------|
| **C-01** | Phase 1 only | Dự án chỉ tập trung vào Phase 1; Phase 2+ chưa lập kế hoạch | Giới hạn chức năng, không thể phân tích hết |
| **C-02** | BA & Design only | Không phát triển source code; BA chỉ tài liệu hóa & thiết kế | Không có sản phẩm hoàn chỉnh để test |
| **C-03** | No implementation | Không xây dựng backend API, không implement frontend code | Cần giả sử API có sẵn |
| **C-04** | No deployment | Không triển khai lên production | Không có live environment để kiểm chứng |

### 8.2. Ràng Buộc Thời Gian (Time Constraints)

| ID | Constraint | Mô Tả | Impact |
|----|-----------|--------|--------|
| **C-05** | 4-month internship | Thực tập từ Tháng 9 đến Tháng 12, 2025 | Có thể không đủ thời gian cho multiple phases |
| **C-06** | Phase 1 completion deadline | Cần xác nhận deadline chính xác cho Phase 1 | Ảnh hưởng planning |
| **C-07** | Review & revision time | Thời gian cho Supervisor review & team revision | Giảm thời gian phân tích |

### 8.3. Ràng Buộc Tài Nguyên (Resource Constraints)

| ID | Constraint | Mô Tả | Impact |
|----|-----------|--------|--------|
| **C-08** | Team size: 6 members | Đội ngũ 6 thành viên học sinh thực tập | Kinh nghiệm có thể hạn chế |
| **C-09** | 1 Supervisor | Chỉ 1 người hướng dẫn | Có thể bottleneck review |
| **C-10** | Tools: Figma, Azure DevOps, Markdown | Công cụ hạn chế, không enterprise tools | Giới hạn khả năng phân tích |

### 8.4. Ràng Buộc Kỹ Thuật (Technical Constraints)

| ID | Constraint | Mô Tả | Impact |
|----|-----------|--------|--------|
| **C-11** | No backend code | BA không viết backend code; giả sử API có sẵn | Không thể verify API fully |
| **C-12** | No frontend code | BA không viết frontend code; Mockup only | Không thể test interaction |
| **C-13** | Mockup in Figma | Mockup phải trên Figma (công cụ chính) | Giới hạn về high-fidelity prototype |
| **C-14** | Documentation in Markdown | Tài liệu phải viết bằng Markdown | Giới hạn format documentation |

---

## 9. Dependencies

### 9.1. Internal Dependencies (Trong Dự Án)

| ID | Dependency | From | To | Impact |
|----|-----------|------|-----|--------|
| **DEP-01** | Requirements → User Stories | Analysis Phase | US Writing | Không thể viết US trước khi có requirements |
| **DEP-02** | Requirements → Test Cases | Analysis Phase | Test Design | Test cases phải dựa trên requirements |
| **DEP-03** | Mockups → Figma Design | Design Decision | Mockup Phase | Cần quyết định design trước khi mockup |
| **DEP-04** | User Flow → Use Cases | Flow Modeling | UC Specification | Use cases phải consistent với user flow |
| **DEP-05** | Business Rules → Acceptance Criteria | Rule Definition | AC Writing | AC phải reflect business rules |
| **DEP-06** | Phase 1 Analysis → Developer Handover | Phase 1 Complete | Handover | Phải hoàn thành analysis trước handover |

### 9.2. External Dependencies (Ngoài Dự Án)

| ID | Dependency | From | To | Impact |
|----|-----------|------|-----|--------|
| **DEP-07** | Supervisor Approval | Supervisor | Phase Completion | Phải được Supervisor phê duyệt mới hoàn thành phase |
| **DEP-08** | Business Requirements | Đại Phú / Supervisor | Analysis Phase | Yêu cầu kinh doanh phải rõ ràng |
| **DEP-09** | Developer Feedback | Developer Team | Requirement Clarification | Developer feedback để clarify technical feasibility |
| **DEP-10** | Product Information | Product Database | Cart Display | Cần product data để design cart item display |
| **DEP-11** | Backend API Availability | Developer Team | Test Cases | Giả sử backend API có sẵn (trong Phase 2+) |

### 9.3. Phase Dependencies

| ID | Dependency | Current | Next | Status |
|----|-----------|---------|------|--------|
| **DEP-12** | Phase 1 → Phase 2 | Requirement Analysis & Design | Implementation | Out of Scope |
| **DEP-13** | Phase 2 → Phase 3 | Development | Testing | Out of Scope |
| **DEP-14** | Phase 3 → Phase 4 | Testing & Fixes | Deployment | Out of Scope |

---

## 10. Scope Change Control

### 10.1. Change Request Process

Nếu có yêu cầu thay đổi scope, process sau phải tuân thủ:

```
┌──────────────────┐
│ Change Requested │
└────────┬─────────┘
         │
         ↓
┌──────────────────────────────────────┐
│ 1. Document Change Request            │
│    - What is changing?                │
│    - Why?                             │
│    - Impact on current work?          │
└────────┬───────���─────────────────────┘
         │
         ↓
┌──────────────────────────────────────┐
│ 2. Impact Assessment                  │
│    - Timeline impact                  │
│    - Resource impact                  │
│    - Scope impact                     │
│    - Risk assessment                  │
└────────┬─────────────────────────────┘
         │
         ↓
┌──────────────────────────────────────┐
│ 3. Approval Gate                      │
│    - Team Lead reviews                │
│    - Supervisor approval needed       │
│    - Business Owner confirmation      │
└────────┬─────────────────────────────┘
         │
    ┌────┴─────┐
    │           │
    ↓           ↓
┌────────┐  ┌────────┐
│Approved│  │Rejected│
└────┬───┘  └────────┘
     │
     ↓
┌──────────────────────────────────────┐
│ 4. Update Scope Document              │
│    - Update In Scope / Out of Scope   │
│    - Version control                  │
│    - Notify stakeholders              │
└──────────────────────────────────────┘
```

### 10.2. Change Classification

| Type | Cách Xử Lý | Ví Dụ |
|------|-----------|--------|
| **Minor Change** | Team Lead approval | Thay đổi UI element text |
| **Medium Change** | Supervisor approval | Thêm 1 validation rule nhỏ |
| **Major Change** | Business Owner + Supervisor approval | Thêm chức năng mới hoàn toàn (e.g., wishlist) |
| **Scope Creep** | Reject & schedule for Phase 2 | Đề xuất feature không planned |

### 10.3. Change Log Template

| Date | Requested By | Change Description | Type | Status | Approved By |
|------|-------------|-------------------|------|--------|------------|
| YYYY-MM-DD | Name | [Change description] | Minor/Medium/Major | Approved/Rejected | Name |

---

## 11. Acceptance Boundary

### 11.1. Phase 1 Acceptance Criteria

Dự án Phase 1 được coi là **hoàn thành** khi tất cả các tiêu chí sau được đáp ứng:

| ID | Tiêu Chí | Trạng Thái | Chứng Minh |
|----|---------|----------|-----------|
| **ACC-01** | User Flow Diagram hoàn thành & được phê duyệt | Analyzed | Diagram file in GitHub |
| **ACC-02** | Use Case Specification hoàn thành | Analyzed | UC document in GitHub |
| **ACC-03** | Functional Requirements được liệt kê & phê duyệt | Analyzed | FR-CART-XX list |
| **ACC-04** | Non-Functional Requirements được liệt kê & phê duyệt | Analyzed | NFR-CART-XX list |
| **ACC-05** | Business Rules được định nghĩa | Analyzed | BR-CART-XX list |
| **ACC-06** | User Stories được viết (US-CART-XX) | Analyzed | US document |
| **ACC-07** | Acceptance Criteria được xác định (AC-CART-XX.XX) | Analyzed | AC document |
| **ACC-08** | Figma Mockups được thiết kế & phê duyệt | Designed | Figma link |
| **ACC-09** | Functional Test Cases được tạo (TC-XX) | Analyzed | Test case document |
| **ACC-10** | Requirement Traceability Matrix hoàn thành | Analyzed | Traceability matrix |
| **ACC-11** | SRS Document hoàn thành | Analyzed | SRS document |
| **ACC-12** | Tất cả Deliverables được Supervisor phê duyệt | Analyzed | Supervisor approval email |
| **ACC-13** | Azure DevOps Work Items được tạo & organize | Analyzed | ADO board |

### 11.2. Definition of Done (DoD)

Mỗi requirement được coi là **"Done"** khi:

1. ✅ **Analyzed**: Phân tích kỹ lưỡng, tài liệu hóa rõ ràng
2. ✅ **Documented**: Ghi lại trong User Stories, Acceptance Criteria, Test Cases
3. ✅ **Reviewed**: Được peer-review hoặc Supervisor review
4. ✅ **Approved**: Được phê duyệt bởi Supervisor
5. ✅ **Traceable**: Có traceability link đến test cases

### 11.3. Rejection Criteria

Phase 1 sẽ **KHÔNG** được chấp nhận nếu:

- ❌ Deliverables không hoàn thành
- ❌ Tài liệu không chuyên nghiệp / chứa lỗi
- ❌ Requirement không rõ ràng / ambiguous
- ❌ Test Cases không cover các scenarios chính
- ❌ Mockups không reflect requirements
- ❌ Traceability không đủ

---

## 12. Items Needing Confirmation

### 12.1. Scope Confirmation

| ID | Câu Hỏi | Current Status | Notes |
|----|---------|-----------------|-------|
| **SC-01** | **Định nghĩa chính xác "Shopping Cart Module" là gì?** | Analyzed từ source | Nhưng cần xác nhận phạm vi chi tiết |
| **SC-02** | **Phase 1 có bao gồm những chức năng nào chính xác?** | In Scope list | Cần confirmation từ Supervisor |
| **SC-03** | **Có các phase sau Phase 1 không?** | Assumed Phase 2+ exists | Cần xác nhận lộ trình tổng thể |
| **SC-04** | **Phase 1 deadline khi nào?** | Cần xác nhận | Ảnh hưởng planning & estimation |
| **SC-05** | **Scope của Phase 2 sẽ bao gồm gì?** | Out of Scope Phase 1 | Planning phase sau |

### 12.2. Chức Năng Confirmation

| ID | Câu Hỏi | Current Status | Notes |
|----|---------|-----------------|-------|
| **FC-01** | **Tính "Total with Tax/Shipping" có nên bao gồm trong Shopping Cart không?** | SC-08 | Cần xác nhận: là trách nhiệm Cart hay Checkout |
| **FC-02** | **Hỗ trợ multiple currencies từ Phase 1 không?** | OOS-10 | Cần xác nhận: Phase 1 hay Phase 2+ |
| **FC-03** | **Có hỗ trợ quantity input via text field hay dropdown hay chỉ +/- button?** | Designed | Cần xác nhận preference |
| **FC-04** | **Ghi chú đơn hàng (Order Note) có bắt buộc không?** | Optional | Cần xác nhận business rule |
| **FC-05** | **Có hỗ trợ promo code / coupon trong Phase 1 không?** | OOS-06 | Assumed Out of Scope |
| **FC-06** | **Cart persistence: client-side (localStorage) hay server-side (database)?** | ASM-11 | Architecture decision |

### 12.3. Technical Confirmation

| ID | Câu Hỏi | Current Status | Notes |
|----|---------|-----------------|-------|
| **TC-01** | **Backend API có sẵn hay BA phải specify API contract?** | Assumed available | Cần xác nhận API readiness |
| **TC-02** | **Có yêu cầu real-time synchronization không?** | Assumed normal | Cần xác nhận performance requirement |
| **TC-03** | **Responsive design requirement: mobile/tablet/desktop?** | ASM-09 | Cần xác nhận breakpoints |
| **TC-04** | **Browser compatibility: support which browsers?** | Analyzed | Cần xác nhận target browsers |
| **TC-05** | **Accessibility requirement: WCAG 2.1 AA level?** | Analyzed | Cần xác nhận a11y standards |

### 12.4. Deliverable Confirmation

| ID | Câu Hỏi | Current Status | Notes |
|----|---------|-----------------|-------|
| **DC-01** | **Deliverables format & detail level expected?** | Defined | Cần confirm expectations |
| **DC-02** | **Figma mockup fidelity: wireframe hay high-fidelity?** | Designed | Cần xác nhận level of detail |
| **DC-03** | **Test Cases: functional only hay include non-functional?** | Functional | Cần xác nhận scope |
| **DC-04** | **Traceability Matrix: manual hoặc tool-based?** | Manual (GitHub) | Cần xác nhận method |
| **DC-05** | **Version control & documentation structure** | GitHub | Cần xác nhận repository structure |

### 12.5. Stakeholder Confirmation

| ID | Câu Hỏi | Current Status | Notes |
|----|---------|-----------------|-------|
| **StK-01** | **Ai chính thức đại diện cho Business Owner?** | Internship Supervisor | Cần xác nhận contact person |
| **StK-02** | **Ai contact từ Developer Team khi clarify?** | Cần xác nhận | Cần technical lead name |
| **StK-03** | **Quy trình feedback từ phía kinh doanh là gì?** | Cần xác nhận | Frequency, channel |
| **StK-04** | **Khách hàng (end-user) nào có thể được interview?** | Needs confirmation | User research availability |
| **StK-05** | **Có kick-off meeting với tất cả stakeholders không?** | Cần xác nhận | Align expectations |

### 12.6. Timeline Confirmation

| ID | Câu Hỏi | Current Status | Notes |
|----|---------|-----------------|-------|
| **TL-01** | **Phase 1 duration: 4 weeks / 6 weeks / 8 weeks?** | Cần xác nhận | Affects work breakdown |
| **TL-02** | **Internship Supervisor availability cho review?** | Weekly (dự kiến) | Cần confirm frequency |
| **TL-03** | **Milestone dates cho Phase 1?** | Cần xác nhận | Planning baseline |
| **TL-04** | **Phase 1 delivery date?** | Cần xác nhận | Hard deadline |
| **TL-05** | **Buffer time cho revision dự kiến bao nhiêu?** | Cần xác nhận | Risk management |

---

## 13. Summary

### 13.1. Scope Overview

| Aspect | Detail |
|--------|--------|
| **Project** | Business Analysis & UI/UX Design for Shopping Cart Module - Phase 1 |
| **In Scope Functions** | 15 core shopping cart functions (SC-01 ~ SC-15) |
| **Out of Scope** | Payment, shipping, promos, inventory, authentication, multi-currency, deployment |
| **Deliverables** | 12 major deliverables (Flow, UC, FR/NFR, BR, US, AC, Mockups, Test Cases, etc.) |
| **Team** | 6 member team led by Business Analyst Intern, supervised by Internship Supervisor |
| **Duration** | 4 months internship (Tháng 9-12, 2025); Phase 1 duration TBD |
| **Constraints** | Phase 1 only, BA & Design only (no implementation), 4-month window, limited resources |

### 13.2. Scope Status

| Category | Analyzed | Designed | Out of Scope | Needs Conf. |
|----------|----------|----------|-------------|------------|
| **Functional** | 14/15 | 1/15 | 10 items | 3 items |
| **Non-Functional** | 5* items | - | - | 5 items |
| **Deliverables** | 11/12 | 1/12 | - | - |
| **Phase 1** | Complete | Complete | - | Timeline |

*Partially analyzed; details need confirmation

### 13.3. Risk Areas

| Risk | Impact | Mitigation |
|------|--------|-----------|
| **Scope Creep** | Can exceed timeline | Strict change control, clear boundaries |
| **Unclear Requirements** | Low quality deliverables | Regular clarification, Supervisor review |
| **Resource Constraints** | Cannot complete all work | Team prioritization, phasing |
| **Timeline Pressure** | Rushed analysis & design | Early baseline, buffer time |
| **Stakeholder Misalignment** | Rejected deliverables | Kick-off meeting, regular updates |

---

## 14. References

- **source-documents/source-material.md**: Core functions, deliverables, limitations
- **docs/01-project-overview.md**: Project objectives, scope summary, limitations
- **docs/02-business-context.md**: Business problems, objectives, constraints
- **docs/03-stakeholders.md**: Stakeholder needs, responsibilities, communication
- **.github/copilot-instructions.md**: Documentation standards, restrictions

---

**Ghi Chú:**
- Tài liệu này định nghĩa ranh giới Phase 1 dựa trên source materials
- Tất cả "Out of Scope" items được liệt kê và giải thích lý do
- "Needs confirmation" items được đánh dấu rõ ràng
- Distinction giữa "Analyzed", "Designed", "Proposed", "Implemented" được duy trì
- Tuân thủ .github/copilot-instructions.md standards
- Không claim implementation, deployment, hay hoàn thành UAT
