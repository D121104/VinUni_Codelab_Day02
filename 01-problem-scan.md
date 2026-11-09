# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

### 📝 List bài toán của tôi:

| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | **Xanh SM** | Tốn thời gian | Nhân viên CSKH có thể mất thời gian phân loại khiếu nại, tra cứu chuyến xe, đối chiếu chính sách và soạn phản hồi; các trường hợp hoàn tiền phải chuyển người có thẩm quyền xác nhận. |
| 2 | **Xanh SM** | Tốn thời gian | Khi kiểm tra ảnh bàn giao ca, việc phát hiện và so sánh vết xước/móp méo giữa các lần chụp có thể tốn thời gian hoặc bỏ sót dấu hiệu hư hỏng. |
| 3 | **Vinmec** | Pain từ người khác | Bác sĩ mất quá nhiều thời gian viết tóm tắt hồ sơ xuất viện (mất 20-30 phút/bệnh nhân, bác sĩ phàn nàn vì quá tải). |
| 4 | **Vinmec** | Lặp lại|Nhân viên tiếp nhận phải kiểm tra, nhập và đối chiếu thông tin CCCD, BHYT và giấy tờ bảo hiểm cho từng bệnh nhân, dễ phát sinh sai sót nhập liệu. |
| 5 | **Vinhomes** | Lặp lại + Tốn thời gian + Pain từ người khác | Lead từ web/ads/sự kiện bị phân loại thủ công chậm → bỏ sót hoặc giao Sales sai người. |
| 6 | **Vinhomes** | Tốn thời gian + AI có thể làm tốt hơn | Sales phải tra cứu thủ công mặt bằng, giá, pháp lý, ưu đãi → tư vấn chậm/sai thông tin. |
---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán từ Phase 1**: **#1 (Xanh SM – Xử lý khiếu nại)**, **#3 (Vinmec – Tóm tắt hồ sơ xuất viện)**, **#5 (Vinhomes – Phân loại và điều phối lead từ web/ads/sự kiện)**. Số thứ tự Quick Problem Card khớp với số bài toán trong Phase 1.

> **Lưu ý:** Workflow và các chỉ số chưa được đo kiểm là **[Giả định lab]**, không phải dữ liệu vận hành đã xác minh.

## Quick Problem Card #01 — Xanh SM – AI Complaint Resolution Agent

```text
┌──────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #01                                                   │
│                                                                          │
│ Bài toán: Xanh SM cần hỗ trợ tự động phân loại khiếu nại,                │
│ tra cứu chuyến đi và đề xuất phương án xử lý để giảm thời                │
│ gian giải quyết yêu cầu chăm sóc khách hàng.                             │
│                                                                          │
│ Công ty thành viên: [x] Xanh SM (GSM)                                    │
│                                                                          │
│ Ai đang đau? Nhân viên CSKH (quá tải), trưởng nhóm CSKH                  │
│ và bộ phận xử lý khiếu nại (tốn thời gian xác minh).                     │
│                                                                          │
│ Workflow thủ công hiện tại (4 bước giả định):                            │
│ 1. Tiếp nhận phản ánh từ khách hàng                                      │
│ → 2. Phân loại khiếu nại, tra cứu thông tin chuyến đi                    │
│ → 3. Đối chiếu chính sách, xác minh và chọn hướng xử lý                  │
│ → 4. Soạn phản hồi, gửi khách và cập nhật ticket                         │
│                                                                          │
│ Bước nào tốn nhất? Bước 2-3 (⏱ 6 phút/ticket)                            │
│ Tổng thời gian xử lý: 10 phút/ticket [Giả định lab]                      │
│                                                                          │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-4                           │
│ - LLM: Tự động phân loại nội dung khiếu nại                              │
│ - Function Calling: Truy xuất dữ liệu chuyến đi                          │
│ - RAG: Tra cứu chính sách và quy trình xử lý                             │
│ - AI Agent: Đề xuất phương án và soạn phản hồi nháp                      │
│ - Nhân viên kiểm tra, phê duyệt trước khi gửi                            │
│                                                                          │
│ Đo thành công bằng gì (Metric có số)?                                    │
│ Giảm thời gian xử lý từ 10 phút → ≤6 phút/ticket.                        │
│ Độ chính xác phân loại khiếu nại ≥95%.                                   │
│ Tỷ lệ đề xuất được nhân viên chấp nhận ≥85%.                             │
│ Tỷ lệ ticket mở lại không tăng so với baseline.                          │
│ (Các mục tiêu trên là giả định phục vụ pilot.)                           │
│                                                                          │
│ Quick Architecture:                                                      │
│ [x] Rule  [x] LLM  [x] RAG  [x] Agent                                    │
│ [x] Human-in-the-loop                                                    │
└──────────────────────────────────────────────────────────────────────────┘
```

## Quick Problem Card #03 — Vinmec – Hỗ trợ tóm tắt hồ sơ xuất viện

```text
┌──────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #03                                           │
│                                                                  │
│ Bài toán: Bác sĩ mất thời gian tổng hợp diễn biến điều trị,       │
│ kết quả xét nghiệm và chỉ định để soạn tóm tắt xuất viện.        │
│                                                                  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM                     │
│                     [ ] Vinhomes [x] Vinmec                     │
│                                                                  │
│ Ai đang đau? Bác sĩ điều trị và nhân viên hồ sơ bệnh án.          │
│                                                                  │
│ Workflow hiện tại (4 bước giả định):                              │
│ 1. Mở hồ sơ và xem diễn biến điều trị                             │
│ -> 2. Tổng hợp chẩn đoán, xét nghiệm, thủ thuật                   │
│ -> 3. Soạn bản tóm tắt và hướng dẫn ra viện                      │
│ -> 4. Kiểm tra, chỉnh sửa, phê duyệt và lưu hồ sơ                 │
│                                                                  │
│ Bước tốn nhất? Bước 2-3 (20-30 phút/hồ sơ) [Giả định lab]        │
│                                                                  │
│ AI hỗ trợ bước 2-3: Tóm tắt nội dung từ hồ sơ được cấp quyền,     │
│ tạo bản nháp có dẫn nguồn để bác sĩ kiểm tra.                     │
│                                                                  │
│ Metric mục tiêu: Giảm 25 -> <=10 phút/hồ sơ;                     │
│ không bỏ sót thông tin lâm sàng quan trọng. [Giả định lab]       │
│                                                                  │
│ Quick Architecture: [x] Rule  [x] LLM  [ ] Agent                 │
│                     [x] Human Review                             │
│ Ranh giới: CẤM tự thêm dữ kiện y khoa hoặc tự phê duyệt.         │
└──────────────────────────────────────────────────────────────────┘
```

## Quick Problem Card #05 — Vinhomes – Phân loại và điều phối lead

```text
┌──────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #05                                           │
│                                                                  │
│ Bài toán: Lead từ web, ads và sự kiện cần được phân loại,         │
│ kiểm tra trùng lặp và giao cho Sales phù hợp kịp thời.          │
│                                                                  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM                     │
│                     [x] Vinhomes [ ] Vinmec                     │
│                                                                  │
│ Ai đang đau? Lead Operations, Sales Admin, tư vấn viên Sales     │
│ và khách hàng đang chờ được liên hệ.                             │
│                                                                  │
│ Workflow hiện tại (5 bước giả định):                              │
│ 1. Nhận lead từ web / quảng cáo / sự kiện                         │
│ -> 2. Tổng hợp biểu mẫu, hội thoại và thông tin liên hệ          │
│ -> 3. Kiểm tra trùng, phân loại nhu cầu / ngân sách               │
│ -> 4. Đề xuất hoặc phân công Sales phù hợp                       │
│ -> 5. Sales liên hệ và cập nhật CRM                              │
│                                                                  │
│ Bước tốn nhất? Bước 3-4: 8-15 phút/lead [Giả định lab]           │
│                                                                  │
│ AI hỗ trợ bước 3-4: Đọc nội dung tự do, phân loại nhu cầu,        │
│ gợi ý nhân viên phù hợp; quy tắc kiểm tra trùng và phân tuyến.    │
│                                                                  │
│ Metric mục tiêu: Giảm 10 -> <=5 phút/lead;                       │
│ 100% lead mới có trạng thái trong CRM. [Giả định lab]            │
│                                                                  │
│ Quick Architecture: [x] Rule  [x] LLM  [ ] Agent tự trị          │
│                     [x] Human Approval                           │
│ Ranh giới: CẤM tự cam kết giá / ưu đãi hoặc phân công trái       │
│ chính sách; nhân viên duyệt trường hợp ngoại lệ.                 │
└──────────────────────────────────────────────────────────────────┘
```

---

# 🗳️ Quyết định lựa chọn đề xuất

**Chọn Card #05 — Vinhomes: Phân loại và điều phối lead từ web/ads/sự kiện đến nhân viên Sales phù hợp** để thực hiện **Deep-Dive**.

## Lý do lựa chọn và loại bỏ các thẻ khác

- **Card #01 (Xanh SM – Hỗ trợ xử lý khiếu nại):** Có tiềm năng giảm thời gian phân loại, tra cứu chuyến đi và soạn phản hồi, nhưng cần truy cập dữ liệu giao dịch, chính sách hoàn tiền và phân quyền chặt chẽ. Các tình huống tranh chấp hoặc cam kết bồi thường có rủi ro cao; nhiều yêu cầu đơn giản có thể xử lý bằng API và quy tắc. Chưa ưu tiên cho MVP ngắn hạn.
- **Card #03 (Vinmec – Tóm tắt hồ sơ xuất viện):** Có thể tiết kiệm thời gian cho bác sĩ, nhưng đòi hỏi bảo vệ dữ liệu sức khỏe, kiểm tra tính đầy đủ và chính xác của nội dung y khoa, cùng cơ chế bác sĩ phê duyệt. Rủi ro bỏ sót hoặc bịa thông tin lâm sàng khiến việc triển khai thử nghiệm khó hơn.
- **Card #05 (Vinhomes – Phân loại và điều phối lead):** Quy trình đầu vào và đầu ra rõ ràng: thu lead từ web/ads/sự kiện, chuẩn hóa, kiểm tra trùng, phân loại nhu cầu và đề xuất phân công cho Sales. Có thể mô phỏng bằng dữ liệu tổng hợp, áp dụng Rule Engine cho các điều kiện phân tuyến và LLM để hiểu nội dung tự do. Đánh giá được bằng phút xử lý/lead, tỷ lệ lead có người phụ trách, tỷ lệ phân tuyến đúng và số lead bỏ sót; các quyết định ngoại lệ vẫn do nhân viên duyệt.

**Kết luận:** Nhóm ưu tiên **Card #05** vì có phạm vi MVP rõ, dễ tạo dữ liệu thử nghiệm, dễ so sánh với baseline rule-based và rủi ro được kiểm soát bằng quy tắc phân công cùng phê duyệt của nhân viên. Trước khi triển khai thực tế phải xác minh lưu lượng lead, thời gian phân tuyến hiện tại, dữ liệu được phép sử dụng và chính sách bảo vệ thông tin khách hàng.