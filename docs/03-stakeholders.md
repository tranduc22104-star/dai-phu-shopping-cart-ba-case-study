# Phân Tích Các Bên Liên Quan (Stakeholder Analysis)

## 1. Mục Đích của Stakeholder Analysis

Stakeholder Analysis nhằm xác định, phân loại và phân tích các bên liên quan (stakeholders) trong dự án Business Analysis cho module Giỏ hàng của website Đại Phú. Tài liệu này giúp:

- **Xác định rõ** các nhóm stakeholder và vai trò của họ trong dự án
- **Hiểu nhu cầu** của từng stakeholder để đảm bảo sự hài lòng
- **Quản lý mối quan hệ** giữa các bên liên quan
- **Lập kế hoạch trao đổi** thích hợp với từng nhóm
- **Phân định trách nhiệm** và ranh giới công việc

---

## 2. Stakeholder Identification

Các bên liên quan được xác định dựa trên:
- **Vai trò trong dự án**: Người tham gia trực tiếp trong phân tích, phát triển, kiểm thử
- **Nhu cầu kinh doanh**: Những người/nhóm quan tâm đến kết quả của dự án
- **Mức độ ảnh hưởng**: Những người có quyền quyết định hoặc phê duyệt

Dựa trên source-documents/source-material.md và docs/01-project-overview.md, các stakeholder chính được xác định như sau:

1. **Khách hàng (End-user)** - Người mua hàng trên website
2. **Business Analyst Intern (Ứng viên)** - Cá nhân tham gia dự án
3. **Team Members** - Các thành viên đội ngũ (5 người khác)
4. **Team Leader - Business Analyst Intern (Ứng viên)** - Vai trò lãnh đạo nhóm
5. **Developers** - Nhóm phát triển (ngoài phạm vi thực tập nhưng tiếp nhận yêu cầu)
6. **QA/Testers** - Nhóm kiểm thử (ngoài phạm vi thực tập nhưng sử dụng test cases)
7. **Internship Supervisor (Platihub)** - Người hướng dẫn tại doanh nghiệp
8. **Đại Phú (Business Owner)** - Doanh nghiệp mục tiêu

---

## 3. Stakeholder Register

| **STK-ID** | **Stakeholder / Vai Trò** | **Internal / External** | **Mối Quan Tâm Chính** | **Mức Độ Ảnh Hưởng** | **Nhu Cầu Thông Tin** | **Trách Nhiệm Chính** | **Cách Thức Trao Đổi** | **Evidence Level** | **Status** |
|-----------|------------------------|---------------------|---------------------|------------------|------------------|-----------------|--------------------|--------------------|----------|
| **STK-01** | **Khách Hàng (End-user)** | External | Trải nghiệm mua sắm, dễ sử dụng, giao diện rõ ràng, quản lý giỏ hàng đơn giản | Trung bình | - Giao diện dễ hiểu<br/>- Hướng dẫn sử dụng<br/>- Quy trình thanh toán rõ ràng | - Sử dụng module Giỏ hàng<br/>- Cung cấp phản hồi về trải nghiệm | - Qua giao diện website<br/>- Qua customer support<br/>- Feedback form (khi có) | Confirmed by source | Active |
| **STK-02** | **Business Analyst Intern (Ứng viên)** | Internal | Hoàn thành dự án, tạo tài liệu chất lượng, phát triển kỹ năng Business Analysis | Cao | - Yêu cầu từ Supervisor<br/>- Feedback từ Supervisor<br/>- Feedback từ nhóm<br/>- Công cụ và hướng dẫn | - **Cá nhân**:<br/>  - Tiếp nhận yêu cầu từ Supervisor, Customer, Developer<br/>  - Phân tích module Giỏ hàng<br/>  - Tạo User Flow, Use Case Specification<br/>  - Viết Functional & Non-functional Requirements<br/>  - Viết User Stories, Acceptance Criteria<br/>  - Thiết kế mockup Figma<br/>  - Tạo Test Cases<br/>  - Theo dõi tiến độ Azure DevOps<br/>  - Tổng hợp feedback<br/><br/>- **Nhóm trưởng**:<br/>  - Điều phối nhóm 6 thành viên<br/>  - Phân công công việc<br/>  - Tổ chức requirement meetings<br/>  - Theo dõi tiến độ nhóm<br/>  - Kiểm tra deliverables<br/>  - Tổng hợp feedback Supervisor<br/>  - Giao công việc chỉnh sửa | - Email, Slack, GitHub<br/>- Requirement discussion meetings<br/>- 1-on-1 với Supervisor<br/>- Team stand-ups<br/>- Code/document review | Confirmed by source | Active |
| **STK-03** | **Team Members (5 thành viên)** | Internal | Hoàn thành công việc được giao, học hỏi kỹ năng, hỗ trợ dự án | Trung bình đến cao | - Phân công công việc rõ ràng<br/>- Hướng dẫn từ Team Leader<br/>- Feedback trước khi gửi Supervisor<br/>- Công cụ cần thiết | - Thực hiện phần công việc được giao (do Team Leader phân công)<br/>- Tham gia requirement discussion meetings<br/>- Cập nhật tiến độ trên Azure DevOps<br/>- Nhận feedback và chỉnh sửa<br/>- Hỗ trợ Team Leader | - Requirement meetings<br/>- Slack/Email<br/>- GitHub discussions<br/>- Azure DevOps updates | Confirmed by source | Active |
| **STK-04** | **Team Leader - Business Analyst Intern (Ứng viên)** | Internal | Quản lý nhóm, đạt mục tiêu dự án, chất lượng deliverables | Cao | - Phản hồi từ Supervisor<br/>- Tiến độ nhóm<br/>- Feedback Supervisor<br/>- Công cụ quản lý (Azure DevOps) | - Phân công công việc cho 5 thành viên<br/>- Tổ chức requirement meetings<br/>- Giám sát tiến độ thực hiện<br/>- Kiểm tra kết quả deliverables<br/>- Tiếp nhận feedback từ Supervisor<br/>- Phân công lại công việc chỉnh sửa<br/>- Gửi deliverables cho Supervisor | - Azure DevOps (tracking)<br/>- Team meetings hàng tuần<br/>- Slack/Email<br/>- 1-on-1 với Supervisor<br/>- Team stand-ups | Confirmed by source | Active |
| **STK-05** | **Internship Supervisor (Platihub)** | Internal | Hướng dẫn dự án, đảm bảo chất lượng, phê duyệt deliverables | Cao | - Tiến độ dự án<br/>- Chất lượng deliverables<br/>- Vấn đề gặp phải<br/>- Yêu cầu từ phía kinh doanh | - Hướng dẫn Team Leader<br/>- Review deliverables trước khi hoàn thiện<br/>- Cung cấp feedback chỉnh sửa<br/>- Phê duyệt các phase hoàn thành<br/>- Cấp phát yêu cầu từ phía kinh doanh<br/>- Hỗ trợ khi có vấn đề phát sinh | - 1-on-1 với Team Leader<br/>- Email<br/>- Requirement discussion meetings (khi cần)<br/>- Review meetings | Confirmed by source | Active |
| **STK-06** | **Nhóm Developer (Development Team)** | External | Nhận yêu cầu rõ ràng, thiết kế phù hợp, test cases cụ thể | Trung bình | - User Stories, Acceptance Criteria<br/>- Functional & Non-functional Requirements<br/>- Mockups Figma<br/>- Business Rules<br/>- Yêu cầu kỹ thuật<br/>- Clarification khi cần | - Nhận yêu cầu chi tiết từ BA<br/>- Hỏi clarification khi cần<br/>- Cập nhật tiến độ trên Azure DevOps<br/>- Phản hồi về tính khả thi kỹ thuật<br/>- Gửi phản hồi khi phát hiện gap | - Azure DevOps work items<br/>- Email<br/>- Requirement handover meeting<br/>- Slack (khi cần clarification) | Confirmed by source | Active |
| **STK-07** | **Nhóm QA / Testers** | External | Có test cases chi tiết, tiêu chí chấp nhận rõ ràng, requirements traceability | Trung bình | - Test Cases chi tiết<br/>- Acceptance Criteria<br/>- Functional Requirements<br/>- Business Rules<br/>- Mockups<br/>- Clarification khi cần | - Nhận Test Cases từ BA<br/>- Thực hiện kiểm thử theo Test Cases<br/>- Báo cáo bugs tìm thấy<br/>- Xác nhận khi bug được fix<br/>- Cập nhật test results | - Test case documents<br/>- Azure DevOps (test results)<br/>- Email<br/>- Bug tracking system | Confirmed by source | Active |
| **STK-08** | **Đại Phú (Business Owner)** | External | Trải nghiệm khách hàng cải thiện, requirements phù hợp kinh doanh, quality cao | Cao | - Phân tích hoàn thành<br/>- Mockups giao diện<br/>- Tiến độ dự án<br/>- Dự kiến kết quả kinh doanh | - Cung cấp yêu cầu kinh doanh (qua Supervisor)<br/>- Phê duyệt hướng thiết kế<br/>- Phê duyệt phase hoàn thành<br/>- Phản hồi về requirements | - Review meetings (qua Supervisor)<br/>- Email (qua Supervisor)<br/>- Figma design review (khi cần)<br/>- Requirement approval | Mentioned in process documentation | Active |

---

## 4. Interest–Influence Classification

Mô hình Interest-Influence giúp xác định cách thức quản lý mối quan hệ với từng stakeholder:

```
                    HIGH INFLUENCE
                          ↑
         ┌─────────────────┼─────────────────┐
         │                 │                 │
         │    Manage      │  Manage         │
      LOW│   Closely      │  Closely        │HIGH
   INTEREST│                │                 │INTEREST
         │  STK-08        │  STK-04         │
         │  Đại Phú       │  Team Leader-BA│
         │                │                 │
         │                │                 │
         │                │  STK-05        │
         │                │  Supervisor    │
         │                │                 │
    ─────┼────────────────┼────────────────┼─────
         │                │                 │
    LOW │ Monitor        │  Keep            │HIGH
   INTEREST│                │  Informed       │INFLUENCE
         │                │                 │
         │  STK-01        │  STK-06, 07    │
         │  Customer      │  Dev, QA       │
         │                │                 │
         │                │  STK-02, 03    │
         │                │  BA Team       │
         │                │                 │
         └─────────────────┼─────────────────┘
                          ↓
                     LOW INFLUENCE

```

**Giải thích:**

| Vị Trí | Chiến Lược | Stakeholders | Mô Tả |
|-------|-----------|-------------|--------|
| **Manage Closely (1)** | - Trao đổi thường xuyên<br/>- Hỗ trợ tối đa<br/>- Quyết định cùng với họ | STK-04, STK-05 | Team Leader & Supervisor có ảnh hưởng cao, quan tâm cao |
| **Manage Closely (2)** | - Phê duyệt yêu cầu<br/>- Review phase hoàn thành<br/>- Trao đổi về hướng dự án | STK-08 | Đại Phú quan tâm cao nhưng ảnh hưởng gián tiếp (qua Supervisor) |
| **Keep Informed** | - Cập nhật định kỳ<br/>- Gửi deliverables<br/>- Hỏi ý kiến khi cần | STK-02, STK-03, STK-06, STK-07 | BA Team, Developers, QA có ảnh hưởng trong phạm vi chuyên môn |
| **Monitor** | - Hiểu nhu cầu<br/>- Thu thập feedback<br/>- Cập nhật khi có thay đổi lớn | STK-01 | Khách hàng quan tâm nhưng ảnh hưởng gián tiếp qua giao diện |

---

## 5. Stakeholder Needs

### 5.1. Khách Hàng (STK-01)

**Nhu Cầu Chính:**
1. **Dễ sử dụng**: Giao diện rõ ràng, trực quan, không cần hướng dẫn phức tạp
2. **Thông tin đầy đủ**: Xem rõ sản phẩm, giá, số lượng, tổng tiền
3. **Kiểm soát**: Thêm, xóa, chỉnh sửa số lượng sản phẩm dễ dàng
4. **An toàn**: Yên tâm với quy trình thanh toán
5. **Ghi chú**: Thêm yêu cầu đặc biệt cho đơn hàng

### 5.2. Business Analyst Intern (STK-02)

**Nhu Cầu Cá Nhân:**
1. **Yêu cầu rõ ràng**: Hiểu rõ công việc cần làm, phạm vi, mục tiêu
2. **Hướng dẫn**: Lãnh đạo từ Supervisor, hỗ trợ khi gặp khó khăn
3. **Công cụ**: Đủ công cụ (Figma, Azure DevOps, Markdown)
4. **Phản hồi**: Feedback xây dựng từ Supervisor, nhóm
5. **Học hỏi**: Cơ hội phát triển kỹ năng Business Analysis

**Nhu Cầu Nhóm Trưởng:**
1. **Hiểu rõ nhóm**: Biết năng lực, khả năng của từng thành viên
2. **Công cụ quản lý**: Azure DevOps, Slack, GitHub
3. **Hỗ trợ từ Supervisor**: Trao đổi về chiến lược, vấn đề phát sinh
4. **Phản hồi kịp thời**: Feedback ngay để điều chỉnh

### 5.3. Team Members (STK-03)

**Nhu Cầu:**
1. **Phân công rõ ràng**: Biết chính xác phần công việc, timeline, deliverables
2. **Hướng dẫn**: Được hỗ trợ, hỏi khi không hiểu
3. **Công cụ**: Có đủ công cụ làm việc
4. **Feedback**: Kiểm tra công việc trước khi gửi Supervisor
5. **Học hỏi**: Hiểu phương pháp, kỹ năng Business Analysis

### 5.4. Internship Supervisor (STK-05)

**Nhu Cầu:**
1. **Tiến độ rõ ràng**: Biết dự án tiến triển thế nào, có vấn đề gì
2. **Chất lượng deliverables**: Tài liệu chuyên nghiệp, hoàn chỉnh
3. **Giao tiếp**: Team Leader cập nhật khi có vấn đề
4. **Phê duyệt**: Quy trình review-approve rõ ràng

### 5.5. Nhóm Developer (STK-06)

**Nhu Cầu:**
1. **Requirements rõ ràng**: Hiểu chính xác phải xây dựng gì
2. **Thiết kế cụ thể**: Mockups Figma chi tiết, interaction specs
3. **User Stories & AC**: Acceptance Criteria rõ ràng để code
4. **Clarification**: Hỏi BA khi có ambiguity
5. **Traceability**: Biết requirement nào là từ đâu

### 5.6. Nhóm QA/Testers (STK-07)

**Nhu Cầu:**
1. **Test Cases chi tiết**: Rõ ràng các bước test, expected results
2. **Acceptance Criteria**: Biết tiêu chí chấp nhận từng requirement
3. **Mockups**: Hình ảnh giao diện tham khảo
4. **Business Rules**: Quy tắc nghiệp vụ để xây dựng test scenarios
5. **Traceability**: Liên kết test case ↔ requirement

### 5.7. Đại Phú - Business Owner (STK-08)

**Nhu Cầu:**
1. **Phân tích hoàn chỉnh**: Yêu cầu tài liệu toàn diện, chuyên nghiệp
2. **Thiết kế hợp lý**: Mockups phù hợp với business, user-friendly
3. **Quality cao**: Chắc chắn tài liệu sẽ dẫn đến sản phẩm tốt
4. **Tiến độ**: Dự án hoàn thành đúng thời gian
5. **Giá trị kinh doanh**: Tài liệu sẽ giúp tăng conversion, giảm cart abandonment

---

## 6. Stakeholder Responsibilities

### 6.1. Khách Hàng (STK-01)

| Trách Nhiệm | Mô Tả |
|-----------|--------|
| **Sử dụng module** | Sử dụng Giỏ hàng qua giao diện website |
| **Cung cấp phản hồi** | Cần xác nhận: Cơ chế feedback khi nào, ở đâu, như thế nào |

### 6.2. Business Analyst Intern - Cá Nhân (STK-02)

| Trách Nhiệm | Mô Tả | Status |
|-----------|--------|--------|
| **Tiếp nhận yêu cầu** | Tiếp nhận từ Supervisor, Customer feedback, Developer feedback | **Đã thực hiện** |
| **Phân tích module** | Phân tích chi tiết chức năng Giỏ hàng | **Đã thực hiện** |
| **Tạo User Flow** | Vẽ sơ đồ quy trình xử lý | **Đã thực hiện** |
| **Tạo Use Case Specification** | Viết chi tiết Use Cases | **Đã thực hiện** |
| **Tạo Requirements** | Viết Functional & Non-Functional Requirements, Business Rules | **Đã thực hiện** |
| **Viết User Stories & AC** | Tạo User Stories với Acceptance Criteria rõ ràng | **Đã thực hiện** |
| **Thiết kế Figma mockups** | Thiết kế & cập nhật mockups | **Đã thực hiện** |
| **Chuyển giao yêu cầu** | Truyền đạt requirements cho Developer | **Đã thực hiện** |
| **Theo dõi tiến độ** | Theo dõi trên Azure DevOps | **Đã thực hiện** |
| **Tổng hợp phản hồi** | Xem xét feedback, tổng hợp từ các bên | **Đã thực hiện** |
| **Tạo Test Cases** | Viết functional test cases | **Đã thực hiện** |

### 6.3. Business Analyst Intern - Team Leader (STK-04)

| Trách Nhiệm | Mô Tả | Status |
|-----------|--------|--------|
| **Điều phối nhóm** | Điều phối 6 thành viên | **Đã thực hiện** |
| **Phân công công việc** | Phân chia công việc cho từng thành viên | **Đã thực hiện** |
| **Tổ chức meetings** | Tổ chức requirement discussion meetings | **Đã thực hiện** |
| **Theo dõi tiến độ** | Giám sát tiến độ nhóm | **Đã thực hiện** |
| **Kiểm tra deliverables** | Review outputs trước khi gửi Supervisor | **Đã thực hiện** |
| **Tổng hợp feedback** | Tiếp nhận feedback từ Supervisor | **Đã thực hiện** |
| **Giao công việc chỉnh sửa** | Phân công lại công việc chỉnh sửa | **Đã thực hiện** |

### 6.4. Team Members (STK-03)

| Trách Nhiệm | Mô Tả |
|-----------|--------|
| **Thực hiện công việc được giao** | Hoàn thành phần công việc (phân tích, viết tài liệu, thiết kế, test cases) |
| **Tham gia meetings** | Tham gia requirement discussions, stand-ups |
| **Cập nhật tiến độ** | Update status trên Azure DevOps |
| **Nhận feedback & chỉnh sửa** | Chỉnh sửa dựa trên feedback |
| **Hỗ trợ nhóm** | Hỗ trợ Team Leader và các thành viên khác |

### 6.5. Internship Supervisor (STK-05)

| Trách Nhiệm | Mô Tả |
|-----------|--------|
| **Hướng dẫn** | Hướng dẫn Team Leader về chiến lược, phương pháp |
| **Review deliverables** | Kiểm tra tài liệu trước hoàn thiện |
| **Cung cấp feedback** | Phản hồi chỉnh sửa, cải thiện |
| **Phê duyệt** | Phê duyệt phase hoàn thành |
| **Cấp phát yêu cầu** | Cung cấp yêu cầu từ phía kinh doanh (Đại Phú) |
| **Hỗ trợ vấn đề** | Giải quyết khi có vấn đề phát sinh |

### 6.6. Nhóm Developer (STK-06)

| Trách Nhiệm | Mô Tả |
|-----------|--------|
| **Nhận yêu cầu** | Tiếp nhận User Stories, Acceptance Criteria, Requirements từ BA |
| **Hỏi clarification** | Clarify ambiguities với BA |
| **Cập nhật tiến độ** | Update progress trên Azure DevOps |
| **Phản hồi tính khả thi** | Phản hồi nếu requirement không khả thi kỹ thuật |
| **Gửi phản hồi gap** | Báo cáo nếu thiếu thông tin |

### 6.7. Nhóm QA/Testers (STK-07)

| Trách Nhiệm | Mô Tả |
|-----------|--------|
| **Nhận Test Cases** | Tiếp nhận từ BA |
| **Thực hiện kiểm thử** | Chạy test theo Test Cases |
| **Báo cáo bugs** | Báo cáo lỗi phát hiện |
| **Xác nhận fixes** | Xác nhận khi bug được fix |
| **Update test results** | Cập nhật kết quả kiểm thử |

### 6.8. Đại Phú - Business Owner (STK-08)

| Trách Nhiệm | Mô Tả |
|-----------|--------|
| **Cung cấp yêu cầu** | Cung cấp requirements kinh doanh (qua Supervisor) |
| **Phê duyệt hướng** | Phê duyệt hướng thiết kế, mockups |
| **Phê duyệt phase** | Phê duyệt phase hoàn thành |
| **Phản hồi requirements** | Cung cấp feedback về requirements |

---

## 7. Communication Approach

### 7.1. Kênh Trao Đổi Chính

| Kênh | Mục Đích | Tần Suất | Người Tham Gia |
|-----|---------|---------|-----------------|
| **Azure DevOps** | Tracking work items, updates tiến độ, comments trên tasks | Hàng ngày | Toàn bộ team, Developers, QA |
| **Email** | Thông báo chính thức, gửi deliverables, phản hồi chính thức | Khi cần | Supervisor, Team Leader, Business Owner |
| **Slack / Discord** | Chat nhanh, Q&A, clarifications | Hàng ngày | Team members, BA, Developers |
| **GitHub** | Source control, documentation, reviews | Khi cần | BA Team, Developers |
| **Requirement Discussion Meetings** | Thảo luận yêu cầu, giải quyết vấn đề, alignment | Hàng tuần (dự kiến) | Team Leader, Team Members, Supervisor (khi cần) |
| **Figma** | Design review, mockup feedback, comments trực tiếp | Khi cần | BA, UX/UI, Developers, Stakeholders |
| **1-on-1 Meetings** | Hướng dẫn cá nhân, feedback chi tiết, vấn đề riêng | Định kỳ | Team Leader ↔ Supervisor<br/>Team Leader ↔ Team Members |

### 7.2. Lịch Trình Trao Đổi (Dự Kiến)

| Giai Đoạn | Kênh Chính | Tần Suất | Nội Dung |
|---------|-----------|---------|---------|
| **Phase 1: Analysis** | Requirement meetings + Email | Hàng tuần | Discuss requirements, clarify needs |
| **Phase 2: Design** | Figma reviews + Email | 2 lần/tuần | Design reviews, mockup feedback |
| **Phase 3: Handover** | Email + Meeting | 1 lần | Deliver to Developers, Q&A |
| **Phase 4: Testing** | Azure DevOps + Email | Hàng tuần | Test results, bug tracking |

### 7.3. Cách Thức Trao Đổi Theo Stakeholder

#### STK-01: Khách Hàng
- **Kênh**: Website interface, customer support
- **Tần Suất**: Khi sử dụng module
- **Nội Dung**: User guidance, feedback collection

#### STK-02 & STK-04: Business Analyst Intern (Cá Nhân & Team Leader)
- **Kênh**: Azure DevOps, Slack, Email, GitHub
- **Tần Suất**: Hàng ngày
- **Nội Dung**: Task updates, comments, clarifications

#### STK-03: Team Members
- **Kênh**: Azure DevOps, Slack, Email
- **Tần Suất**: Hàng ngày (updates), hàng tuần (meetings)
- **Nội Dung**: Work assignments, feedback, progress

#### STK-05: Internship Supervisor
- **Kênh**: Email (chính thức), 1-on-1 meetings, Azure DevOps (khi review)
- **Tần Suất**: 1-on-1 hàng tuần, Email khi cần
- **Nội Dung**: Updates, feedback, approvals, guidance

#### STK-06: Developers
- **Kênh**: Azure DevOps, Email, Slack (khi cần clarification)
- **Tần Suất**: Khi handover, khi cần clarify
- **Nội Dung**: Requirements, User Stories, Mockups, Q&A

#### STK-07: QA/Testers
- **Kênh**: Azure DevOps (test results), Email (test cases)
- **Tần Suất**: Khi handover Test Cases, hàng tuần (results)
- **Nội Dung**: Test Cases, AC, Business Rules, test results

#### STK-08: Đại Phú - Business Owner
- **Kênh**: Email (qua Supervisor), Review meetings
- **Tần Suất**: Khi phase hoàn thành, khi cần approval
- **Nội Dung**: Phase approvals, design feedback, requirements confirmation

---

## 8. Responsibility Boundaries

### 8.1. Ranh Giới Trách Nhiệm

#### ✅ Phạm Vi Trách Nhiệm của BA Team

| Công Việc | Mô Tả |
|----------|--------|
| **Requirement Elicitation** | Tiếp nhận, phân tích, tổng hợp yêu cầu từ Supervisor, Customer, Developer |
| **User Flow & Use Case** | Tạo sơ đồ quy trình và tài liệu use case |
| **Functional Requirements** | Xác định và tài liệu hóa yêu cầu chức năng |
| **Non-Functional Requirements** | Xác định & tài liệu hóa NFR (performance, security, usability) |
| **Business Rules** | Tài liệu hóa các quy tắc nghiệp vụ |
| **User Stories & AC** | Viết US theo format, AC rõ ràng |
| **Mockups & Wireframes** | Thiết kế trên Figma (UI/UX specification) |
| **Functional Test Cases** | Tạo test cases kiểm thử chức năng |
| **Requirement Traceability** | Liên kết requirement ↔ test cases, user stories |
| **Documentation** | Tài liệu hóa toàn bộ quá trình |

#### ❌ Ngoài Phạm Vi Trách Nhiệm

| Công Việc | Lý Do |
|----------|--------|
| **Phát triển source code** | Không phải trách nhiệm BA; là trách nhiệm của Developer |
| **Triển khai production** | Không phải trách nhiệm BA; là trách nhiệm Ops/DevOps |
| **Thực hiện UAT** | Không phần cho phạm vi internship; là trách nhiệm của Business Owner + QA |
| **Thiết kế technical architecture** | Trách nhiệm Technical Lead / Solution Architect |
| **Quản lý infrastructure** | Trách nhiệm DevOps / Infrastructure Team |

### 8.2. Ranh Giới Giữa Cá Nhân & Nhóm

#### Cá Nhân (Business Analyst Intern)

**Trách Nhiệm Cá Nhân:**
- Tiếp nhận yêu cầu từ Supervisor, Customer, Developer (cá nhân)
- Phân tích module Giỏ hàng (cá nhân)
- Tạo User Flow (cá nhân hoặc chỉ đạo nhóm)
- Tạo Use Case Specification (cá nhân hoặc chỉ đạo nhóm)
- Tạo Functional & Non-functional Requirements (cá nhân hoặc chỉ đạo nhóm)
- Viết User Stories & Acceptance Criteria (cá nhân hoặc chỉ đạo nhóm)
- Thiết kế Figma mockups (cá nhân)
- Chuyển giao yêu cầu cho Developer (cá nhân)
- Theo dõi tiến độ Azure DevOps (cá nhân)
- Tổng hợp feedback & tạo test cases (cá nhân)

#### Nhóm (Dưới Sự Chỉ Đạo của Team Leader)

**Trách Nhiệm Nhóm:**
- Hỗ trợ cá nhân BA trong phân tích chi tiết
- Tham gia requirement discussion meetings
- Thực hiện phần công việc được giao
- Kiểm tra chéo (peer review) các tài liệu
- Hỗ trợ testing, xác minh requirements

### 8.3. Ranh Giới Giữa BA Team & Người Hướng Dẫn

#### BA Team (STK-02, STK-03, STK-04)

- ✅ **Thực hiện công việc BA**: Phân tích, tài liệu hóa, thiết kế
- ✅ **Lên kế hoạch chi tiết**: Timeline, task breakdown
- ✅ **Quản lý nội bộ nhóm**: Phân công, review peer
- ❌ **Phê duyệt chính thức**: Không

#### Internship Supervisor (STK-05)

- ✅ **Hướng dẫn chiến lược**: Phương pháp, approach
- ✅ **Review & phê duyệt**: Deliverables, phase completion
- ✅ **Giải quyết vấn đề lớn**: Escalation, guidance
- ✅ **Cấp phát yêu cầu**: Từ phía kinh doanh
- ❌ **Thực hiện chi tiết công việc**: Không (guidance only)

---

## 9. Assumptions

### 9.1. Giả Định Về Stakeholders

| ID | Giả Định | Mô Tả | Evidence Level |
|----|----------|--------|-----------------|
| **SA-01** | Internship Supervisor luôn có sẵn khi cần guidance | Assumption dựa trên vai trò hướng dẫn | Assumed for portfolio |
| **SA-02** | Developers sẽ tuân theo requirements tài liệu BA cung cấp | Assumption dựa trên best practice | Assumed for portfolio |
| **SA-03** | QA/Testers sẽ sử dụng Test Cases do BA tạo | Assumption dựa trên workflow tiêu chuẩn | Assumed for portfolio |
| **SA-04** | Khách hàng sẽ sử dụng module Giỏ hàng theo design flow | Assumption dựa trên user journey | Assumed for portfolio |
| **SA-05** | Đại Phú sẽ phê duyệt các phase khi hoàn thành | Assumption dựa trên business governance | Assumed for portfolio |
| **SA-06** | Team Members sẽ hỗ trợ BA trong phân tích | Assumption dựa trên team structure | Confirmed by source |
| **SA-07** | Azure DevOps được sử dụng để track work items | Assumption dựa trên tool được chỉ định | Confirmed by source |

---

## 10. Items Needing Confirmation

### 10.1. Xác Nhận Về Stakeholder

| ID | Mục | Câu Hỏi | Current Status |
|----|-----|--------|-----------------|
| **SC-01** | Khách hàng | Cách thức khách hàng cung cấp feedback chính thức là gì? (survey, support ticket, focus group) | Cần xác nhận |
| **SC-02** | Khách hàng | Ai đại diện cho khách hàng trong các meetings? | Cần xác nhận |
| **SC-03** | Developer | Tên chính thức của Nhóm Developer là gì? | Cần xác nhận |
| **SC-04** | Developer | Ai là technical lead / main contact từ Developer Team? | Cần xác nhận |
| **SC-05** | QA/Testers | Tên chính thức của Nhóm QA là gì? | Cần xác nhận |
| **SC-06** | QA/Testers | Ai là QA lead / main contact? | Cần xác nhận |
| **SC-07** | Business Owner | Tên chính thức của Business Owner / PM từ Đại Phú là gì? | Cần xác nhận |
| **SC-08** | Supervisor | Tên đầy đủ của Internship Supervisor | Cần xác nhận |

### 10.2. Xác Nhận Về Nhu Cầu & Mối Quan Tâm

| ID | Mục | Câu Hỏi | Current Status |
|----|-----|--------|-----------------|
| **SC-09** | Khách hàng | Nhu cầu ưu tiên nhất của khách hàng là gì? (Dễ sử dụng / Nhanh / An toàn) | Cần xác nhận |
| **SC-10** | Business Owner | Metric chính để đo thành công dự án là gì? (conversion rate, cart abandonment rate, customer satisfaction) | Cần xác nhận |
| **SC-11** | Developer | Yêu cầu kỹ thuật chi tiết (framework, database, API design) | Cần xác nhận |

### 10.3. Xác Nhận Về Trao Đổi & Quy Trình

| ID | Mục | Câu Hỏi | Current Status |
|----|-----|--------|-----------------|
| **SC-12** | Trao Đổi | Lịch meeting Requirement Discussion dự kiến là bao giờ? | Cần xác nhận |
| **SC-13** | Trao Đổi | Frequency của 1-on-1 với Supervisor bao giờ? | Cần xác nhận |
| **SC-14** | Trao Đổi | Kênh Slack/Email nào được sử dụng? | Cần xác nhận |
| **SC-15** | Quy Trình | Quy trình review & approval của Supervisor là gì? | Cần xác nhận |
| **SC-16** | Quy Trình | Deadline hoàn thành Phase 1 khi nào? | Cần xác nhận |

### 10.4. Xác Nhận Về Ranh Giới Trách Nhiệm

| ID | Mục | Câu Hỏi | Current Status |
|----|-----|--------|-----------------|
| **SC-17** | Ranh Giới | BA có trách nhiệm kiểm thử hay không? (hay chỉ viết test cases) | Cần xác nhận |
| **SC-18** | Ranh Giới | Ai chịu trách nhiệm training khách hàng cuối cùng? | Cần xác nhận |
| **SC-19** | Ranh Giới | Ai quyết định approve chỉnh sửa mocking? (Supervisor, Business Owner) | Cần xác nhận |

---

## 11. Summary

### 11.1. Số Lượng Stakeholders

| Loại | Số Lượng | Status |
|------|---------|--------|
| Internal (Trong công ty, dự án) | 4 (STK-02, 03, 04, 05) | Active |
| External (Ngoài dự án nhưng liên quan) | 4 (STK-01, 06, 07, 08) | Active |
| **Tổng Cộng** | **8** | |

### 11.2. Mức Độ Ảnh Hưởng

| Mức Độ | Stakeholders | Số Lượng |
|--------|-------------|---------|
| Cao | Team Leader-BA (STK-04), Supervisor (STK-05), Business Owner (STK-08) | 3 |
| Trung Bình | Customer (STK-01), Team Members (STK-03), Developers (STK-06), QA (STK-07) | 4 |
| Thấp | - | - |

### 11.3. Nhu Cầu Thông Tin

| Nhóm | Thông Tin Chính |
|------|-----------------|
| **Khách Hàng** | Giao diện, user guide |
| **BA Team** | Requirements, feedback, tools |
| **Supervisor** | Deliverables, progress, issues |
| **Developers** | Specifications, user stories, mockups, Q&A channels |
| **QA/Testers** | Test cases, AC, business rules |
| **Business Owner** | Phase approvals, design feedback |

---

## 12. References

- **source-documents/source-material.md**: Candidate role, individual & team responsibilities, project deliverables
- **docs/01-project-overview.md**: Team structure, individual responsibilities, team responsibilities
- **docs/02-business-context.md**: Business problem, business needs, user needs
- **.github/copilot-instructions.md**: Restrictions, documentation standards

---

**Ghi Chú:**
- Tài liệu này được tạo dựa trên source materials có sẵn
- Tất cả assumptions được đánh dấu rõ ràng "Assumed for portfolio"
- Tất cả items cần xác nhận được liệt kê ở mục 10
- Tuân thủ các quy chuẩn từ .github/copilot-instructions.md
