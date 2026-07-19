# Bối Cảnh Kinh Doanh

## 1. Business Context

Đại Phú là một doanh nghiệp chuyên kinh doanh hoa lụa, sản phẩm được sử dụng rộng rãi như quà tặng trong các sự kiện xã hội, lễ tết, và các dịp đặc biệt. Với sự phát triển của thương mại điện tử, Đại Phú đã triển khai một website thương mại điện tử để mở rộng thị trường bán hàng.

Dự án Business Analysis này tập trung vào việc phân tích và thiết kế module Giỏ hàng (Shopping Cart) cho website thương mại điện tử Đại Phú. Module Giỏ hàng là một thành phần quan trọng trong quy trình mua sắm trực tuyến, nơi khách hàng có thể quản lý các sản phẩm đã chọn trước khi thanh toán.

Dự án được thực hiện dưới sự hỗ trợ của Platihub, một công ty chuyên cung cấp dịch vụ tư vấn và phát triển phần mềm, với sự tham gia của một đội ngũ học sinh thực tập gồm 6 thành viên dưới sự lãnh đạo của ứng viên (Business Analyst Intern).

## 2. Đặc Điểm Hoạt Động Kinh Doanh

### 2.1. Lĩnh Vực Kinh Doanh

- **Sản phẩm chính**: Hoa lụa (artificial flowers)
- **Mục đích sử dụng**: Quà tặng, trang trí sự kiện, lễ tết
- **Kênh bán hàng**: Website thương mại điện tử (E-commerce)

### 2.2. Đặc Điểm Giao Dịch

- Khách hàng duyệt và lựa chọn sản phẩm trên website
- Khách hàng thêm sản phẩm vào giỏ hàng với số lượng tùy ý
- Trước khi thanh toán, khách hàng có cơ hội xem xét lại, chỉnh sửa số lượng, và xóa các sản phẩm
- Khách hàng có thể thêm ghi chú cho đơn hàng (ví dụ: hướng dẫn giao hàng, yêu cầu đặc biệt)
- Quy trình thanh toán diễn ra sau khi khách hàng xác nhận giỏ hàng

## 3. Đặc Điểm Sản Phẩm Hoa Lụa Dùng Làm Quà Tặng

### 3.1. Tính Chất Sản Phẩm

- **Loại hàng hóa**: Sản phẩm công nghệ cao (artifical flowers / hoa lụa)
- **Ngành hàng**: Quà tặng, trang trí
- **Đặc điểm chính**:
  - Tuổi thọ lâu dài (không cần chăm sóc như hoa tươi)
  - Đa dạng mẫu mã và màu sắc
  - Thích hợp cho nhiều dịp khác nhau
  - Có thể được đóng gói đẹp mắt cho mục đích quà tặng

### 3.2. Cách Sử Dụng

- **Các dịp phổ biến**: Tết Nguyên Đán, sinh nhật, kỷ niệm năm cưới, tặng khách hàng công ty
- **Nhóm khách hàng**: Cá nhân, doanh nghiệp, các cửa hàng bán lẻ
- **Yêu cầu đặc biệt**: Có thể yêu cầu đóng gói riêng, card tặng, hay lời nhắn cá nhân

### 3.3. Ý Nghĩa Kinh Doanh

- Sản phẩm có giá trị trung bình đến cao
- Khách hàng thường mua số lượng không quá lớn trong một đơn hàng
- Khách hàng cần có thời gian để lựa chọn và xem xét kỹ lưỡng
- Tính chất quà tặng yêu cầu chất lượng dịch vụ cao và độ chính xác trong thực hiện đơn hàng

## 4. Vai Trò của Shopping Cart trong Customer Journey

### 4.1. Vị Trí trong Quy Trình Mua Hàng
[1] Duyệt Sản Phẩm → [2] Thêm vào Giỏ Hàng → [3] Quản Lý Giỏ Hàng → [4] Thanh Toán → [5] Xác Nhận Đơn ↑ Shopping Cart Module

### 4.2. Các Chức Năng Chính

Module Giỏ hàng cho phép khách hàng:

- **Xem chi tiết**: Danh sách đầy đủ sản phẩm đã chọn, giá, số lượng
- **Chỉnh sửa**: Thay đổi số lượng từng sản phẩm
- **Loại bỏ**: Xóa sản phẩm không muốn mua
- **Tính toán**: Xem rõ tổng chi phí trước khi thanh toán
- **Ghi chú**: Thêm thông tin bổ sung cho đơn hàng
- **Xác nhận**: Tiến hành thanh toán khi sẵn sàng

### 4.3. Tầm Quan Trọng Kinh Doanh

- **Giảm tỷ lệ bỏ giỏ hàng** (cart abandonment): Giao diện rõ ràng giúp khách hàng tự tin với quyết định mua hàng
- **Tăng độ chính xác**: Khách hàng có cơ hội kiểm tra lại đơn hàng, giảm khiếu nại và hoàn trả
- **Cải thiện trải nghiệm**: Cho phép khách hàng có quyền kiểm soát đầy đủ over quyết định mua hàng
- **Tăng giá trị đơn hàng**: Nhắc nhở khách hàng về các sản phẩm đã chọn có thể khuyến khích mua thêm

## 5. Business Problem

### 5.1. Vấn Đề Chính

Trước khi dự án này được thực hiện, module Giỏ hàng gặp phải một số vấn đề sau:

1. **Thiếu Quy Trình Rõ Ràng**
   - Chưa có định nghĩa rõ ràng về các bước xử lý giỏ hàng
   - Các quy tắc nghiệp vụ chưa được tài liệu hóa
   - Dẫn đến sự không nhất quán trong triển khai

2. **Yêu Cầu Chi Tiết Chưa Được Tài Liệu Hóa**
   - Functional Requirements chưa được liệt kê đầy đủ
   - Non-Functional Requirements chưa rõ (hiệu năng, bảo mật, khả dụng)
   - Khó khăn trong việc hướng dẫn phát triển

3. **Thiếu Thiết Kế Giao Diện**
   - Chưa có mockup rõ ràng cho module Giỏ hàng
   - Khó khăn trong việc lập kế hoạch phát triển giao diện
   - Không có hướng dẫn thống nhất cho UX/UI

4. **Tiêu Chí Kiểm Thử Chưa Xác Định**
   - Chưa có test case chi tiết
   - Khó khăn trong việc đảm bảo chất lượng

### 5.2. Tác Động

- **Cho khách hàng**: Trải nghiệm không ổn định, thiếu tin cậy
- **Cho doanh nghiệp**: Tăng chi phí phát triển, tăng thời gian triển khai
- **Cho nhóm phát triển**: Không rõ ràng về yêu cầu, dẫn đến lặp lại công việc

## 6. User Needs

### 6.1. Nhu Cầu của Khách Hàng (Customer)

Khách hàng mua hàng trên website cần:

1. **Xem rõ giỏ hàng của họ**
   - Danh sách đầy đủ sản phẩm đã chọn
   - Giá của từng sản phẩm
   - Tổng tiền trước khi thanh toán

2. **Quản lý sản phẩm dễ dàng**
   - Thay đổi số lượng sản phẩm
   - Xóa sản phẩm không muốn
   - Xem cập nhật giá tức thời

3. **Thêm thông tin đặc biệt**
   - Ghi chú cho đơn hàng (địa chỉ giao hàng, yêu cầu đặc biệt)
   - Giới hạn hợp lý (không quá dài)

4. **Tự tin trước khi thanh toán**
   - Biết rõ mình sẽ phải trả bao nhiêu
   - Có cơ hội kiểm tra lại trước khi xác nhận
   - Tiến hành thanh toán khi sẵn sàng

### 6.2. Nhu Cầu của Nhóm Phát Triển (Developer)

Nhóm phát triển cần:

1. **Yêu cầu rõ ràng và đầy đủ**
   - Các chức năng chi tiết (Functional Requirements)
   - Các ràng buộc kỹ thuật (Non-Functional Requirements)
   - Các quy tắc nghiệp vụ (Business Rules)

2. **Thiết kế giao diện cụ thể**
   - Mockup Figma rõ ràng
   - Layout, flow, interaction được định nghĩa

3. **Tiêu chí chấp nhận**
   - User Stories với Acceptance Criteria
   - Test Cases để xác minh

### 6.3. Nhu Cầu của Doanh Nghiệp (Business)

Doanh nghiệp cần:

1. **Tăng chất lượng trải nghiệm khách hàng**
   - Giảm tỷ lệ bỏ giỏ hàng (cart abandonment)
   - Tăng độ hài lòng khách hàng

2. **Giảm chi phí phát triển**
   - Yêu cầu rõ ràng từ đầu
   - Giảm lặp lại và sửa đổi

3. **Tăng tốc độ triển khai**
   - Nhóm phát triển hiểu rõ yêu cầu
   - Quy trình kiểm thử hiệu quả

## 7. Business Needs

Dự án này xác định ba nhu cầu kinh doanh chính sau:

### BN-CART-01: Tài Liệu Hóa Yêu Cầu Chi Tiết của Module Giỏ Hàng

| Thuộc tính | Giá trị |
|-----------|--------|
| **ID** | BN-CART-01 |
| **Tên Nhu Cầu** | Tài liệu hóa Functional Requirements và Non-Functional Requirements |
| **Mô Tả** | Cần tạo tài liệu toàn diện về các yêu cầu chức năng (Functional Requirements) và yêu cầu phi chức năng (Non-Functional Requirements) của module Giỏ hàng. Tài liệu này sẽ làm cơ sở cho quá trình phát triển và kiểm thử. |
| **Đối Tượng Hưởng Lợi** | Nhóm phát triển, Nhóm QA, Nhóm kinh doanh |
| **Giá Trị Mong Đợi** | Giảm sự không rõ ràng, giảm chi phí lặp lại phát triển, tăng tốc độ triển khai, cải thiện chất lượng sản phẩm |
| **Trạng Thái Xác Nhận** | Đã xác nhận từ source-documents/source-material.md |

### BN-CART-02: Thiết Kế Giao Diện Rõ Ràng (Mockup & Wireframe)

| Thuộc tính | Giá trị |
|-----------|--------|
| **ID** | BN-CART-02 |
| **Tên Nhu Cầu** | Tạo Mockup và Wireframe cho module Giỏ hàng trên Figma |
| **Mô Tả** | Cần thiết kế giao diện chi tiết cho module Giỏ hàng trên Figma, bao gồm: danh sách sản phẩm, điều khiển số lượng, nút xóa, tính toán giá, ghi chú đơn hàng, và nút chuyển sang thanh toán. Thiết kế phải tuân theo các yêu cầu UX/UI hiện đại. |
| **Đối Tượng Hưởng Lợi** | Nhóm phát triển Frontend, Nhóm UX/UI, Nhóm kinh doanh |
| **Giá Trị Mong Đợi** | Hướng dẫn rõ ràng cho phát triển Frontend, giảm thời gian phát triển, tăng tính nhất quán trong giao diện người dùng, cải thiện trải nghiệm người dùng |
| **Trạng Thái Xác Nhận** | Đã xác nhận từ source-documents/source-material.md |

### BN-CART-03: Xác Định Tiêu Chí Kiểm Thử Chi Tiết (Test Cases)

| Thuộc tính | Giá trị |
|-----------|--------|
| **ID** | BN-CART-03 |
| **Tên Nhu Cầu** | Tạo Test Cases chức năng cho module Giỏ hàng |
| **Mô Tả** | Cần phát triển tập hợp toàn diện các Test Cases để kiểm thử tất cả các chức năng của module Giỏ hàng. Các Test Cases phải bao gồm: view cart, tăng/giảm số lượng, xóa sản phẩm, tính toán giá, thêm ghi chú, và chuyển sang thanh toán. |
| **Đối Tượng Hưởng Lợi** | Nhóm QA, Nhóm phát triển, Nhóm kinh doanh |
| **Giá Trị Mong Đợi** | Đảm bảo chất lượng cao cho module, giảm số lượng lỗi trong sản phẩm cuối cùng, cải thiện độ tin cậy của hệ thống, hỗ trợ UAT trong tương lai |
| **Trạng Thái Xác Nhận** | Đã xác nhận từ source-documents/source-material.md |

## 8. Project Objectives

Dự án này có những mục tiêu chính sau:

### 8.1. Mục Tiêu Phân Tích

1. **Phân tích chi tiết module Giỏ hàng**
   - Xác định tất cả các chức năng cần thiết
   - Tìm hiểu nhu cầu của khách hàng, doanh nghiệp, và nhóm phát triển
   - Tạo tài liệu yêu cầu toàn diện

2. **Lập mô hình quy trình**
   - Tạo User Process Flow miêu tả các bước xử lý của khách hàng
   - Định nghĩa các Use Case chi tiết
   - Xác định các điểm quyết định (decision points)

### 8.2. Mục Tiêu Tài Liệu Hóa

1. **Tạo tài liệu yêu cầu**
   - Viết Functional Requirements (FR-CART-XX)
   - Viết Non-Functional Requirements (NFR-CART-XX)
   - Xác định Business Rules (BR-CART-XX)

2. **Tạo User Stories và Acceptance Criteria**
   - Viết User Stories (US-CART-XX) theo định dạng: As a [user], I want [action], So that [benefit]
   - Xác định Acceptance Criteria chi tiết cho từng User Story

### 8.3. Mục Tiêu Thiết Kế

1. **Thiết kế giao diện**
   - Tạo Wireframe và Mockup trên Figma
   - Đảm bảo tính thân thiện với người dùng (User-Friendly)
   - Tính nhất quán với design system của website

### 8.4. Mục Tiêu Kiểm Thử

1. **Phát triển Test Cases**
   - Tạo Test Cases chức năng (Functional Test Cases)
   - Xác định các trường hợp thử nghiệm (test scenarios)
   - Đảm bảo bao phủ đầy đủ (test coverage)

### 8.5. Mục Tiêu Quản Lý Dự Án

1. **Chuyển giao yêu cầu**
   - Truyền đạt yêu cầu chi tiết cho nhóm phát triển
   - Đảm bảo hiểu rõ giữa các bên liên quan

2. **Theo dõi tiến độ**
   - Sử dụng Azure DevOps để quản lý work items
   - Theo dõi tiến độ phát triển

## 9. Expected Business Value

### 9.1. Giá Trị Kỳ Vọng (Tiềm Năng)

Mặc dù dự án chưa được triển khai lên production và không có dữ liệu đo lường thực tế, các giá trị kỳ vọng sau đây được xác định dựa trên tốt nhất thực hành (best practices) trong ngành:

**Lưu ý**: Các giá trị sau là kỳ vọng (expected), không phải là kết quả đã đạt được.

#### 9.1.1. Cho Khách Hàng

- **Trải nghiệm cải thiện**: Giao diện rõ ràng, dễ sử dụng giúp khách hàng tự tin hơn trong quyết định mua hàng
- **Giảm tỷ lệ lỗi**: Khách hàng có cơ hội kiểm tra lại đơn hàng trước khi thanh toán, giảm khiếu nại và yêu cầu hoàn trả
- **Tăng sự hài lòng**: Quy trình mua hàng rõ ràng, không bí ẩn

#### 9.1.2. Cho Doanh Nghiệp

- **Giảm cart abandonment**: Giao diện rõ ràng có thể giúp giảm tỷ lệ khách hàng bỏ giỏ hàng
- **Tăng chất lượng**: Yêu cầu chi tiết dẫn đến sản phẩm chất lượng cao hơn
- **Giảm chi phí**: Yêu cầu rõ ràng từ đầu giảm chi phí sửa đổi sau này

#### 9.1.3. Cho Nhóm Phát Triển

- **Giảm sự không rõ ràng**: Yêu cầu chi tiết giúp nhóm hiểu rõ phải làm gì
- **Tăng hiệu quả**: Giảm lặp lại, tăng tốc độ phát triển
- **Cải thiện chất lượng code**: Yêu cầu rõ ràng dẫn đến code tốt hơn

### 9.2. Cách Đo Lường (Metrics - Tiềm Năng)

**Cần xác nhận**: Các chỉ số sau đây là những chỉ số tiềm năng mà doanh nghiệp có thể theo dõi sau triển khai:

- **Cart Abandonment Rate**: Tỷ lệ khách hàng rời bỏ giỏ hàng (hiện tại: cần xác nhận)
- **Conversion Rate**: Tỷ lệ chuyển đổi từ xem sản phẩm sang hoàn thành đơn hàng (hiện tại: cần xác nhận)
- **Customer Satisfaction Score**: Điểm hài lòng khách hàng (hiện tại: cần xác nhận)
- **Number of Support Tickets**: Số lượng vé hỗ trợ liên quan đến giỏ hàng (hiện tại: cần xác nhận)
- **Development Cycle Time**: Thời gian từ phân tích đến triển khai (hiện tại: cần xác nhận)

### 9.3. Khẩn Cấp Nhưng Cần Lưu Ý

**Điều quan trọng**: 

- Dự án này **không** có dữ liệu đo lường thực tế (no verified post-go-live metrics)
- Website **chưa** được xác nhận triển khai lên production
- **Không** có dữ liệu thực tế về revenue, conversion rate, hay khách hàng feedback
- Các giá trị kỳ vọng trên dựa trên tốt nhất thực hành, không phải kết quả đã đạt được

## 10. Assumptions

### 10.1. Giả Định Kinh Doanh

| Giả Định | Mô Tả | Trạng Thái |
|---------|-------|-----------|
| **A1** | Khách hàng sẽ luôn xem giỏ hàng trước khi thanh toán | Hợp lý |
| **A2** | Số lượng sản phẩm trong giỏ hàng thông thường là dưới 20 | Cần xác nhận |
| **A3** | Khách hàng chủ yếu mua từ desktop hoặc mobile | Cần xác nhận |
| **A4** | Website sẽ hỗ trợ nhiều tiền tệ trong tương lai | Cần xác nhận |

### 10.2. Giả Định Kỹ Thuật

| Giả Định | Mô Tả | Trạng Thái |
|---------|-------|-----------|
| **A5** | Backend API sẽ xử lý tính toán giá chính xác | Hợp lý |
| **A6** | Dữ liệu sản phẩm được lưu trữ trong database | Hợp lý |
| **A7** | Giỏ hàng có thể được lưu trữ trên server hoặc client | Cần xác nhận |
| **A8** | Hệ thống sẽ validate dữ liệu trước khi lưu | Hợp lý |

### 10.3. Giả Định Tổ Chức

| Giả Định | Mô Tả | Trạng Thái |
|---------|-------|-----------|
| **A9** | Nhóm phát triển sẵn sàng nhận yêu cầu | Hợp lý |
| **A10** | Internship Supervisor sẽ phê duyệt deliverable | Hợp lý |
| **A11** | Khách hàng sẽ cung cấp phản hồi định kỳ | Cần xác nhận |

## 11. Constraints

### 11.1. Ràng Buộc Phạm Vi (Scope)

| Ràng Buộc | Mô Tả |
|----------|-------|
| **C1** | Dự án chỉ tập trung vào Phase 1 của module Giỏ hàng |
| **C2** | Không phát triển source code; chỉ tài liệu hóa yêu cầu |
| **C3** | Không tạo infrastructure hoặc deployment configuration |
| **C4** | Chỉ tập trung vào Business Analysis và UI/UX Design |

### 11.2. Ràng Buộc Thời Gian

| Ràng Buộc | Mô Tả |
|----------|-------|
| **C5** | Thời gian thực tập: 4 tháng (Tháng 9 - Tháng 12, 2025) |
| **C6** | Phải hoàn thành Phase 1 Analysis trước khi bắt đầu phát triển |

### 11.3. Ràng Buộc Tài Nguyên

| Ràng Buộc | Mô Tả |
|----------|-------|
| **C7** | Đội ngũ: 6 thành viên học sinh thực tập |
| **C8** | Hỗ trợ từ 1 Internship Supervisor |
| **C9** | Công cụ: Figma, Azure DevOps, Markdown |

### 11.4. Ràng Buộc Kỹ Thuật

| Ràng Buộc | Mô Tả |
|----------|-------|
| **C10** | Mockup phải được tạo trên Figma (công cụ chính) |
| **C11** | Tài liệu phải được viết bằng Markdown |
| **C12** | Work items phải được quản lý trên Azure DevOps |

## 12. Project Limitations

### 12.1. Giới Hạn Phạm Vi (Scope Limitations)

| Giới Hạn | Mô Tả |
|---------|-------|
| **L1** | Dự án không phát triển source code website (HTML, CSS, JavaScript, Backend, Database) |
| **L2** | Dự án không phát triển CI/CD pipeline hoặc deployment configuration |
| **L3** | Chỉ tập trung vào Business Analysis, Requirement Definition, UI/UX Design, và Test Case Design |
| **L4** | Dự án chỉ đề xuất các giải pháp; không triển khai thực tế |

### 12.2. Giới Hạn Triển Khai (Deployment Limitations)

| Giới Hạn | Mô Tả |
|---------|-------|
| **L5** | Website chưa được xác nhận là đã triển khai lên production |
| **L6** | Không có dữ liệu về production deployment hoặc live users |
| **L7** | Không thực hiện User Acceptance Testing (UAT) hoàn chỉnh |

### 12.3. Giới Hạn Dữ Liệu (Data Limitations)

| Giới Hạn | Mô Tả |
|---------|-------|
| **L8** | Không có verified revenue data hoặc conversion rate improvement |
| **L9** | Không có stakeholder feedback từ end users |
| **L10** | Không có post-go-live business metrics |
| **L11** | Không có customer satisfaction scores hoặc usage statistics |

### 12.4. Giới Hạn Thời Gian (Timeline Limitations)

| Giới Hạn | Mô Tả |
|---------|-------|
| **L12** | Thời gian thực tập: 4 tháng; có thể không đủ để hoàn thành tất cả phases |
| **L13** | Chỉ Phase 1 được phân tích chi tiết; các phases sau chưa xác định |

### 12.5. Giới Hạn Tài Nguyên (Resource Limitations)

| Giới Hạn | Mô Tả |
|---------|-------|
| **L14** | Đội ngũ gồm học sinh thực tập; kinh nghiệm có thể hạn chế |
| **L15** | Một Internship Supervisor hỗ trợ toàn bộ dự án |
| **L16** | Công cụ hạn chế: Figma, Azure DevOps, Markdown (không sử dụng Enterprise tools) |

## 13. Items Needing Confirmation

Những thông tin sau đây cần được xác nhận từ các bên liên quan:

### 13.1. Thông Tin Kinh Doanh

| Mục | Mô Tả | Dữ Liệu Hiện Tại |
|-----|-------|-----------------|
| **B1** | Khách hàng mục tiêu chính | Cần xác nhận |
| **B2** | Sản phẩm tiêu biểu (số lượng SKU) | Cần xác nhận |
| **B3** | Giá trị đơn hàng trung bình | Cần xác nhận |
| **B4** | Tần suất mua hàng của khách hàng | Cần xác nhận |
| **B5** | Chính sách hoàn trả | Cần xác nhận |
| **B6** | Điều khoản ghi chú đơn hàng (ví dụ: loại ghi chú nào được phép) | Cần xác nhận |

### 13.2. Thông Tin Kỹ Thuật

| Mục | Mô Tả | Dữ Liệu Hiện Tại |
|-----|-------|-----------------|
| **T1** | Công nghệ backend sẽ sử dụng | Cần xác nhận |
| **T2** | Công nghệ frontend sẽ sử dụng | Cần xác nhận |
| **T3** | Database sẽ sử dụng | Cần xác nhận |
| **T4** | Yêu cầu về hiệu năng (response time, throughput) | Cần xác nhận |
| **T5** | Yêu cầu về bảo mật | Cần xác nhận |
| **T6** | Cách lưu trữ giỏ hàng (server-side hay client-side) | Cần xác nhận |
| **T7** | Hỗ trợ multiple currencies | Cần xác nhận |
| **T8** | Hỗ trợ multiple languages | Cần xác nhận |

### 13.3. Thông Tin Tổ Chức

| Mục | Mô Tả | Dữ Liệu Hiện Tại |
|-----|-------|-----------------|
| **O1** | Lịch trình phát triển chi tiết | Cần xác nhận |
| **O2** | Phản hồi từ Internship Supervisor | Cần xác nhận |
| **O3** | Phản hồi từ Customer/Stakeholder | Cần xác nhận |
| **O4** | Phản hồi từ Developer Team | Cần xác nhận |
| **O5** | Tiêu chí chấp nhận cho Phase 1 | Cần xác nhận |
| **O6** | Kế hoạch cho các phases sau | Cần xác nhận |

### 13.4. Thông Tin Triển Khai

| Mục | Mô Tả | Dữ Liệu Hiện Tại |
|-----|-------|-----------------|
| **D1** | Kế hoạch UAT | Cần xác nhận |
| **D2** | Kế hoạch triển khai production | Cần xác nhận |
| **D3** | Kế hoạch hỗ trợ post-go-live | Cần xác nhận |
| **D4** | Kế hoạch thu thập metrics | Cần xác nhận |

---

**Ghi chú**: Tài liệu này được tạo bằng cơ sở trên source-documents/source-material.md, README.md, docs/01-project-overview.md, và .github/copilot-instructions.md. Các thông tin không có bằng chứng rõ ràng được đánh dấu "Cần xác nhận". Dự án này là một portfolio Business Analysis, không phải một hệ thống được triển khai production.

