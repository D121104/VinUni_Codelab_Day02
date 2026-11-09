# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

### 📝 List bài toán của tôi:

> Focus cá nhân: **Vinhomes — AI Sales & Marketing** (Lead Score → Sales Copilot → Nurturing → Content → Attribution).

| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | **Vinhomes** | Lặp lại + Tốn thời gian + Pain từ người khác | Lead từ web/ads/landing/sự kiện bị phân loại thủ công chậm → bỏ sót, thiếu Lead Intent Score, hoặc giao Sales sai người. |
| 2 | **Vinhomes** | Tốn thời gian + AI có thể tốt hơn | Sales phải tra cứu thủ công mặt bằng, giá, pháp lý, ưu đãi → tư vấn chậm/sai thông tin. |
| 3 | **Vinhomes** | Lặp lại + Tốn thời gian + AI có thể tốt hơn | Khách quan tâm nhưng chưa mua không được nurture đúng nhu cầu/đúng lúc → rớt chuyển đổi. |
| 4 | **Vinhomes** | Lặp lại + Tốn thời gian + AI có thể tốt hơn | Marketing sản xuất content cho nhiều dự án/phân khúc (Diamond–Happy Home) thủ công → chậm và dễ sai brand/giá. |
| 5 | **Vinhomes** | Tốn thời gian + AI có thể tốt hơn + Pain từ người khác | Khó đo kênh/chiến dịch nào thực sự tạo giao dịch → phân bổ ngân sách marketing kém hiệu quả. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán từ Phase 1**: **#1 (Vinhomes – Lead Score & Smart Routing)**, **#2 (Vinhomes – Sales Knowledge Copilot)**, **#3 (Vinhomes – Customer Nurturing Agent)**. Số thứ tự Quick Problem Card khớp với số bài toán trong Phase 1.

> **Lưu ý:** Workflow và các chỉ số chưa được đo kiểm là **[Giả định lab]**, không phải dữ liệu vận hành đã xác minh.

## Quick Problem Card #01 — Vinhomes – Lead Score & Smart Routing Agent

```text
┌──────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #01                                                   │
│                                                                          │
│ Bài toán: Lead marketing chậm phân loại — giao sai Sales.                │
│ Lead từ web/ads/sự kiện cần được chấm Intent Score, kiểm tra trùng       │
│ và đề xuất Sales phù hợp kịp thời.                                       │
│                                                                          │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM                             │
│                     [x] Vinhomes [ ] Vinmec                              │
│                                                                          │
│ Ai đang đau? Lead Ops / Sales Admin (quá tải phân loại),                 │
│ Sales Consultant (nhận lead muộn/sai fit), khách chờ liên hệ.            │
│                                                                          │
│ Workflow thủ công hiện tại (5 bước giả định):                            │
│ 1. Lead phát sinh từ web / ads / landing / sự kiện                       │
│ → 2. Thu thập form, chat, ghi chú thủ công                               │
│ → 3. Nhân viên đọc & phân loại nhu cầu / ngân sách / dự án               │
│ → 4. Phân công Sales theo kinh nghiệm cá nhân                            │
│ → 5. Sales gọi / chat và cập nhật CRM                                    │
│                                                                          │
│ Bước nào tốn nhất? Bước 3-4 (⏱ 8-15 phút/lead) [Giả định lab]            │
│ Median Time-to-Assign baseline: ~10 phút/lead                            │
│                                                                          │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3-4                           │
│ - LLM: Phân tích form/hội thoại → nhu cầu, ngân sách, dự án              │
│ - Agent: Chấm Lead Intent Score + đề xuất Sales phù hợp                  │
│ - Rule: Kiểm tra trùng lead, SLA, ràng buộc phân tuyến                   │
│ - HITL: Lead Ops duyệt trước khi giao (tránh giao nhầm Sales)            │
│                                                                          │
│ Đo thành công bằng gì (Metric có số)? [Giả định lab]                     │
│ - Median Time-to-Assign: 10 phút → ≤5 phút (-50%)                        │
│ - ≥95% lead được phân loại / có Intent Score tự động                     │
│ - 100% lead mới có owner + trạng thái xử lý trong CRM                    │
│ - Override rate (người sửa đề xuất Sales) <20%                           │
│                                                                          │
│ Quick Architecture:                                                      │
│ [x] Rule  [x] LLM  [x] Agent  [x] Human-in-the-loop                      │
│ Ranh giới: CẤM tự cam kết giá/ưu đãi; CẤM tự giao Sales không qua duyệt │
│ với lead ngoại lệ / độ tin cậy thấp.                                     │
└──────────────────────────────────────────────────────────────────────────┘
```

## Quick Problem Card #02 — Vinhomes – Sales Knowledge Copilot

```text
┌──────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #02                                                   │
│                                                                          │
│ Bài toán: Sales mất nhiều thời gian tra cứu tài liệu dự án →             │
│ tư vấn chậm hoặc sai thông tin giá / pháp lý / ưu đãi.                   │
│                                                                          │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM                             │
│                     [x] Vinhomes [ ] Vinmec                              │
│                                                                          │
│ Ai đang đau? Sales Consultant / Sales Advisor.                           │
│                                                                          │
│ Workflow thủ công hiện tại (5 bước giả định):                            │
│ 1. Nhận yêu cầu khách (ngân sách, loại căn, dự án)                       │
│ → 2. Mở PDF / Excel / slide nội bộ để tìm thông tin                      │
│ → 3. So sánh thủ công các lựa chọn                                       │
│ → 4. Soạn câu trả lời / tư vấn khách                                     │
│ → 5. Xác nhận lại với team sản phẩm khi nghi ngờ                         │
│                                                                          │
│ Bước nào tốn nhất? Bước 2-3 (⏱ 10-20 phút/lượt) [Giả định lab]           │
│                                                                          │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-4                           │
│ - RAG + LLM trên Project Knowledge Base (có citation nguồn/phiên bản)    │
│ - Gợi ý so sánh căn / dự án theo ngân sách và nhu cầu                    │
│                                                                          │
│ Đo thành công bằng gì (Metric có số)? [Giả định lab]                     │
│ - Thời gian tìm thông tin: 15 phút → ≤6 phút (-60%)                      │
│ - ≥90% câu hỏi phổ biến có câu trả lời kèm nguồn kiểm chứng              │
│ - Giảm số case tư vấn sai giá / pháp lý / ưu đãi                         │
│                                                                          │
│ Quick Architecture:                                                      │
│ [ ] Rule  [x] LLM  [x] RAG  [ ] Agent tự trị                             │
│ [x] Human Review (Sales kiểm trước khi chốt với khách)                   │
│ Ranh giới: CẤM bịa giá/chính sách; chỉ trả lời từ tài liệu đã duyệt.     │
└──────────────────────────────────────────────────────────────────────────┘
```

## Quick Problem Card #03 — Vinhomes – Customer Nurturing Agent

```text
┌──────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #03                                                   │
│                                                                          │
│ Bài toán: Khách quan tâm nhưng chưa mua không được nurture đúng          │
│ nhu cầu / đúng lúc → mất cơ hội chuyển đổi (Lead → Site Visit).          │
│                                                                          │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM                             │
│                     [x] Vinhomes [ ] Vinmec                              │
│                                                                          │
│ Ai đang đau? Sales Consultant + Customer Care; khách chờ thông tin.      │
│                                                                          │
│ Workflow thủ công hiện tại (5 bước giả định):                            │
│ 1. Ghi nhận trạng thái khách trên CRM / Excel                            │
│ → 2. Sales tự nhớ lịch follow-up                                         │
│ → 3. Soạn tin nhắn / email thủ công                                      │
│ → 4. Gửi thông tin dự án / chính sách                                    │
│ → 5. Cập nhật phản hồi & quyết định bước tiếp                            │
│                                                                          │
│ Bước nào tốn nhất? Bước 2-3 (⏱ 5-10 phút/khách/lượt) [Giả định lab]      │
│                                                                          │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-5                           │
│ - Agent: Đề xuất lịch chăm sóc theo trạng thái + Intent Score            │
│ - LLM: Soạn tin cá nhân hóa theo nhu cầu / dự án                         │
│ - HITL: Sales duyệt trước khi gửi (tránh spam / sai brand)               │
│                                                                          │
│ Đo thành công bằng gì (Metric có số)? [Giả định lab]                     │
│ - Tăng 20% tỷ lệ khách phản hồi sau follow-up                            │
│ - Giảm 50% thời gian chăm sóc thủ công                                   │
│ - Tăng tỷ lệ Lead → Site Visit                                           │
│                                                                          │
│ Quick Architecture:                                                      │
│ [x] Rule  [x] LLM  [x] Agent  [x] Human-in-the-loop                      │
│ Ranh giới: CẤM tự gửi tin cho khách khi chưa có phê duyệt Sales;         │
│ CẤM cam kết giá / ưu đãi ngoài tài liệu được phép.                       │
└──────────────────────────────────────────────────────────────────────────┘
```

---

# 🗳️ Quyết định lựa chọn đề xuất

**Chọn Card #01 — Vinhomes: Lead Score & Smart Routing Agent** (phân loại / chấm điểm lead từ web/ads/sự kiện và đề xuất Sales phù hợp) để thực hiện **Deep-Dive**.

## Lý do lựa chọn và loại bỏ các thẻ khác

- **Card #02 (Sales Knowledge Copilot):** Dễ prototype (RAG + LLM), metric rõ (thời gian tra cứu, độ chính xác có citation), nhưng gần “hỗ trợ tư vấn” hơn là nút thắt doanh thu ngay khi lead vừa vào. Phù hợp làm module tiếp theo trong cùng nền tảng.
- **Card #03 (Customer Nurturing Agent):** Tiềm năng Agentic cao và gần chuyển đổi, nhưng KPI (reply rate, Lead → Site Visit) phụ thuộc chu kỳ BĐS dài, dễ bias; rủi ro brand/compliance khi gửi tin tự động cao hơn → phù hợp phase sau khi đã có Intent Score ổn định.
- **#4 Content Factory & #5 Attribution (chỉ ở Phase 1):** #4 impact trung bình với doanh thu trực tiếp; #5 phụ thuộc data CRM/campaign rất cao, khó chứng minh trong MVP lab.
- **Card #01 (Lead Score & Smart Routing):** Gần doanh thu nhất ngay đầu funnel. Metric loại bias rõ: **Median Time-to-Assign 10 → ≤5 phút**, **≥95% lead có Intent Score**, **100% lead có owner/trạng thái**, kèm **override rate &lt;20%** để kiểm soát giao nhầm Sales. Có thể mô phỏng bằng dữ liệu tổng hợp; Rule Engine xử lý trùng/SLA, LLM/Agent hiểu nội dung tự do và chấm điểm; HITL duyệt ngoại lệ.

**Kết luận:** Ưu tiên **Card #01** vì phạm vi MVP rõ, đo được bằng timestamp CRM (không phụ thuộc khảo sát cảm tính), dễ so sánh baseline thủ công vs AI+HITL, và là nền cho các agent Sales/Nurturing phía sau. Trước triển khai thực tế cần xác minh lưu lượng lead, baseline thời gian phân tuyến, dữ liệu được phép dùng và chính sách bảo vệ thông tin khách hàng.
