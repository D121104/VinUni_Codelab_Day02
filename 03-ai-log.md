# 📝 Phase 6 — AI Log & Reflection (Cá nhân)

> Nhật ký dùng AI làm **thought-partner** khi scoping bài toán **Vinhomes — Lead Score & Smart Routing Agent** (Card #01).  
> Công cụ đã dùng trong lab: Cursor / ChatGPT / Gemini (brainstorm, phản biện metric, soạn draft markdown).

---

## 1. Bối cảnh sử dụng AI

Trong lab, tôi dùng AI ở các bước:

1. **Phase 1–2:** Brainstorm 5 pain point Vinhomes (Lead Score, Sales Copilot, Nurturing, Content, Attribution) và điền Quick Problem Cards.
2. **Chọn deep-dive:** So sánh metric “loại bias” giữa Lead Routing vs Customer Nurturing.
3. **Phase 3–5:** Phác thảo workflow hiện tại, Problem Statement 6-field, Future-State (Rule + LLM/Score + HITL), và lý giải **NOT YET**.
4. **Ranh giới vận hành:** Stress-test ý tưởng adversarial (AI tự giao Sales / tự cam kết giá).

---

## 2. AI giúp gì? (Thought-partner hữu ích)

| Việc AI hỗ trợ tốt | Ví dụ cụ thể |
|---|---|
| Mở rộng ý tưởng theo 4 lenses | Gợi ý nhanh các bottleneck lead từ web/ads/sự kiện, không chỉ “làm chatbot”. |
| Chuẩn hóa format lab | Giữ đúng khung SCAN → Quick Card → Deep-Dive → Evaluate; metric có số. |
| Tách metric cứng vs metric mơ hồ | Gợi ý ưu tiên **Median Time-to-Assign**, coverage trong SLA, override rate thay vì “tăng doanh thu / CSAT” ngay pilot. |
| Làm rõ rủi ro “giao nhầm Sales” | Phân biệt bỏ sót lead (no owner) vs giao sai fit (có owner nhưng sai dự án/ngân sách). |
| Phác thảo Operational Boundary | Cấm tự ghi CRM, tự gửi tin, tự cam kết giá; bắt buộc HITL khi confidence thấp. |

**Nhận xét:** AI hữu ích nhất khi tôi đã có hướng bài toán (Vinhomes lead funnel) và nhờ nó **cấu trúc / phản biện**, không phải nhờ nó “tự nghĩ hộ toàn bộ đề tài”.

---

## 3. AI sai / hallucination ở đâu?

| Lỗi / thiên lệch của AI | Vì sao nguy hiểm với bài lab |
|---|---|
| Đưa số liệu vận hành Vinhomes như thể đã đo thật (lead/ngày, phút/lead, % chuyển đổi) | Dễ biến **[Giả định lab]** thành “bằng chứng” giả → lệch quyết định GO. |
| Đẩy giải pháp thành **Agent tự trị end-to-end** (tự score → tự assign → tự nhắn khách) | Vượt Operational Boundary; rủi ro brand/compliance cao hơn mức MVP. |
| Gợi ý KPI “tăng số căn chốt trong 30 ngày” làm primary metric | Chu kỳ BĐS dài, nhiều biến nhiễu → không loại được bias (đúng lời thầy: metric phải đo được rõ). |
| Đề xuất xây “nền tảng CRM mới” thay vì gắn workflow vào dữ liệu/CRM hiện có | Làm scope phình to, lệch mục tiêu lab (scoping + prototype ranh giới). |
| Khi so sánh idea, đôi khi thiên về story “Agentic đẹp” hơn **feasibility + metric** | Có thể chọn nhầm Nurturing thay vì Lead Score nếu không tự lọc. |

**Ví dụ hallucination điển hình:** AI ước “tiết kiệm hàng trăm triệu doanh thu/tháng nhờ giảm lead mồ côi” mà không tách rõ đây chỉ là **proxy upside**, không phải cash đã thu. Nếu không sửa, phần Evaluate sẽ trông như đã chứng minh ROI.

---

## 4. Tôi đã sửa prompt / ranh giới như thế nào?

### 4.1. Sửa cách hỏi (prompt)

- Thêm ràng buộc: *“Mọi con số phải gắn nhãn [Giả định lab]; không được viết như dữ liệu nội bộ Vinhomes đã xác minh.”*
- Ép metric loại bias: *“Chỉ đề xuất KPI đo bằng timestamp CRM / đếm được trong pilot ≤30 ngày.”*
- Ép kiến trúc MVP: *“Rule + LLM score dạng nháp + HITL; cấm Agent tự ghi CRM.”*
- Khi chọn idea: *“So sánh theo khả năng thuyết phục đầu tư bằng metric vận hành, không theo độ ‘Agentic’.”*

### 4.2. Sửa ranh giới nghiệp vụ (giữ trong deep-dive)

- AI **được:** đọc lead đã phân quyền, trích xuất dữ kiện có trong nguồn, chấm Intent Score **nháp**, gợi ý nhóm Sales hợp lệ.
- AI **cấm:** bịa ngân sách/SĐT, hứa giá/ưu đãi, tự gửi tin, tự ghi CRM, tự đổi chủ lead, tự phân công khi thiếu dữ liệu / nghi trùng.
- **Fallback:** JSON lỗi, thiếu field, hoặc confidence thấp → hàng đợi thủ công.

### 4.3. Kết quả sau khi sửa

- Chốt **Card #01 — Lead Score & Smart Routing** thay vì Nurturing (metric Time-to-Assign rõ hơn).
- Deep-dive giữ quyết định **NOT YET** cho production: có prototype/lab được, nhưng chưa đủ baseline & dữ liệu thật để GO.
- Báo cáo tách được: **cost-out giờ công (giả định)** vs **upside doanh thu (không dùng làm KPI chính)**.

---

## 5. Bài học cá nhân

1. **Problem first, AI second:** AI giỏi viết mạch lạc, nhưng dễ “làm đẹp” scope; người học phải giữ bottleneck và metric thật.
2. **Metric quyết định idea:** Một chỉ số trước–sau đo được (10 → ≤5 phút) thuyết phục hơn câu chuyện Agent phức tạp.
3. **HITL không phải điểm yếu:** Với lead và thông tin khách hàng, phê duyệt là điều kiện để lab an toàn và để sếp tin khi rót tiền pilot.
4. **Cách dùng AI tốt hơn lần sau:** Luôn yêu cầu AI liệt kê *giả định / rủi ro / cách đo*, rồi tự loại phần không kiểm chứng được trước khi đưa vào file nộp.

---

## 6. Tóm tắt 3 ý (đúng rubric I3)

| Câu hỏi rubric | Trả lời ngắn |
|---|---|
| **AI giúp gì?** | Brainstorm Vinhomes funnel, chuẩn hóa Quick Card/Deep-Dive, làm rõ metric Time-to-Assign và rủi ro giao nhầm Sales. |
| **AI sai gì?** | Bịa cảm giác “đã có số liệu thật”, phóng đại ROI, đề xuất Agent tự trị và KPI chốt căn không phù hợp pilot. |
| **Sửa gì?** | Prompt gắn nhãn giả định lab; khóa MVP = Score nháp + Rule + HITL; chốt Card #01 và quyết định **NOT YET** cho triển khai thực tế. |
