# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)

**Bài toán được lựa chọn:** Card #01 — **Vinhomes: Lead Score & Smart Routing Agent** (phân loại / chấm Intent Score và đề xuất Sales phù hợp từ lead website/quảng cáo/sự kiện).


## 3.1. Current-State Workflow Mapping (25 min)

**Kịch bản workflow hiện tại (5 bước):**

```text
┌────────────────────┐  🔄  ┌────────────────────┐
│ BƯỚC 1             │ ───→ │ BƯỚC 2             │
│ Nhận lead từ web,  │      │ Gom form, ghi chú, │
│ ads, sự kiện       │      │ nội dung chat      │
│ Ai: Marketing      │      │ Ai: Sales Admin    │
│ ⏱ 1 phút/lead     │      │ ⏱ 2 phút/lead     │
│ In: Form/chat      │      │ In: Lead đa nguồn  │
│ Out: Lead thô      │      │ Out: Lead chuẩn hóa│
└────────────────────┘      └─────────┬──────────┘
                                     │
                                     ▼
                          ┌────────────────────┐
                          │ BƯỚC 3 🔴         │
                          │ Kiểm tra trùng,    │
                          │ đọc & chấm Intent  │
                          │ Score / nhu cầu    │
                          │ Ai: Lead Ops       │
                          │ ⏱ 4 phút/lead     │
                          │ In: Form + chat    │
                          │ Out: Nhãn + Score  │
                          └─────────┬──────────┘
                                     │ 🔄
                                     ▼
                          ┌────────────────────┐
                          │ BƯỚC 4 🔴         │
                          │ Chọn nhóm/nhân viên│
                          │ Sales phù hợp      │
                          │ Ai: Sales Admin    │
                          │ ⏱ 2 phút/lead     │
                          │ In: Score + quy tắc│
                          │ Out: Gợi ý phân công│
                          └─────────┬──────────┘
                                     │ 🔄
                                     ▼
                          ┌────────────────────┐
                          │ BƯỚC 5             │
                          │ Giao Sales, cập    │
                          │ nhật CRM và liên hệ│
                          │ Ai: Sales/CRM      │
                          │ ⏱ 1 phút thao tác  │
                          │ In: Phân công      │
                          │ Out: Trạng thái CRM│
                          └────────────────────┘

🔴 Bottleneck: Bước 3 và 4 (6 phút/lead).
🔄 Handoff: Marketing → Sales Admin → Lead Ops → Sales → CRM.
⏱ Tổng thời gian thao tác nội bộ: 1 + 2 + 4 + 2 + 1 = 10 phút/lead.
```

**Lưu ý đo lường:** 10 phút/lead là tổng **thời gian thao tác nhân viên** giả định, không bao gồm thời gian đợi Sales gọi khách, thời gian chờ phản hồi từ khách hay độ trễ hệ thống. Cần đo riêng các thời gian chờ này trong thực tế để tránh cộng trùng.

**Điểm nghẽn chính:** Đọc nội dung tự do, suy ra nhu cầu và **chấm Lead Intent Score** (Bước 3), sau đó ánh xạ Score/nhu cầu sang nhóm Sales theo quy tắc doanh nghiệp (Bước 4). Lead thiếu dữ liệu hoặc nghi trùng cần được đưa vào hàng đợi rà soát, không tự đoán thông tin.

## 3.2. Problem Statement (6-field) & Metrics (15 min)

| Field | Nội dung |
|---|---|
| **1. Actor / Operator** | Lead Operations, Sales Admin và nhân viên tư vấn Sales; bộ phận Marketing cung cấp lead đầu vào. |
| **2. Current Workflow** | Nhận lead từ website/quảng cáo/sự kiện → tập hợp form/chat → kiểm tra trùng, phân loại nhu cầu và chấm Intent Score → đề xuất nhóm/nhân viên Sales → xác nhận phân công và cập nhật CRM. Kịch bản giả định mất **10 phút thao tác/lead [Giả định lab]** (Median Time-to-Assign baseline). |
| **3. Bottleneck** | Bước 3–4, **6 phút/lead [Giả định lab]**: đọc mô tả nhu cầu không cấu trúc, đối chiếu ngân sách/khu vực, chấm Intent Score, nhận diện thiếu dữ liệu và phân tuyến đúng. |
| **4. Business Impact** | Chưa có số liệu tổn thất thực tế. **[Giả định lab]** 100 lead/ngày × 5 phút tiết kiệm × 26 ngày ÷ 60 = **216,67 giờ công/tháng**; quy đổi 120.000đ/giờ = **26.000.000đ/tháng** công suất lao động giải phóng. Đây chưa phải tiền mặt tiết kiệm hoặc doanh thu tăng thêm. |
| **5. Success Metric** | Mục tiêu pilot **[Giả định lab]**: Median Time-to-Assign **10 → ≤5 phút/lead**; ≥95% lead có Intent Score; ≥90% đề xuất phân loại/phân tuyến được nhân viên xác nhận đúng (override rate &lt;20%); **100%** lead thử nghiệm có owner + trạng thái; **0** hành động vượt quyền. So sánh với **Rule-based baseline**, không chỉ so với thủ công. |
| **6. Operational Boundary** | AI được **đọc lead đã phân quyền, trích xuất dữ kiện có trong nguồn, chấm Intent Score dạng nháp, gợi ý nhãn nhu cầu và nhóm Sales hợp lệ, xuất nháp để duyệt**. **CẤM:** tự bịa ngân sách/thông tin liên hệ, hứa giá/ưu đãi, tự gửi tin, tự ghi CRM, tự đổi chủ lead, tự phân công trái quy tắc / không qua HITL khi độ tin cậy thấp. Nhân viên có thẩm quyền duyệt ngoại lệ; ứng dụng kiểm soát quyền ghi và danh mục nhóm Sales. |

## 3.3. Future-State Flow & AI Fit (25 min)

**AI-Fit Matrix:**

- [x] **Rule / State-Machine:** chuẩn hóa trường, kiểm tra định dạng, phát hiện trùng dựa trên khóa được phép, áp quy tắc phân tuyến và kiểm soát quyền ghi.
- [x] **LLM Feature:** đọc mô tả/hội thoại tự do, trích xuất nhu cầu, **chấm Lead Intent Score**, tạo nhãn và lý do gợi ý **dạng nháp**.
- [ ] **Agentic Loop tự trị:** MVP dùng Agent **hỗ trợ chấm điểm + đề xuất** trong vòng HITL; **không** cho mô hình tự quyết định và tự ghi CRM.

**Future-State Flow:**

```text
┌──────────────────────┐      ┌───────────────────────────┐
│ 1. Lead vào hệ thống │ ───→ │ 2. 🔵 Rule chuẩn hóa,     │
│    web/ads/sự kiện   │      │ kiểm tra trường và trùng │
└──────────────────────┘      └─────────────┬─────────────┘
                                            │
                                            ▼
                              ┌───────────────────────────┐
                              │ 3. 🔵 LLM / Score Agent   │
                              │ Trích xuất intent, khu vực│
                              │ ngân sách nếu được nêu;   │
                              │ chấm Intent Score + nhãn  │
                              │ + mức bất định (nháp)     │
                              └─────────────┬─────────────┘
                                            │
                                            ▼
                              ┌───────────────────────────┐
                              │ 4. 🔵 Rule Engine         │
                              │ Kiểm tra Score/nhãn, nhóm │
                              │ Sales hợp lệ, routing     │
                              └─────────────┬─────────────┘
                                            │
                                            ▼
                              ┌───────────────────────────┐
                              │ 5. 🟢 Lead Ops / Admin   │
                              │ duyệt nháp / sửa / từ chối│
                              └─────────────┬─────────────┘
                                            │
                                            ▼
                              ┌───────────────────────────┐
                              │ 6. Hệ thống ghi CRM theo │
                              │ quyền sau khi được duyệt │
                              └───────────────────────────┘

↩️ Fallback: Nếu mô hình lỗi, trả JSON không hợp lệ, thiếu thông tin,
   nghi trùng hoặc không chắc chắn → đưa vào hàng đợi xử lý thủ công.
   Không tự gửi tin, tự gán Sales hoặc ghi CRM khi chưa duyệt.
```

---

---

# 🏁 Phase 5 — EVALUATE (Nhóm, 20 min)

## 5.1. AI Readiness Checklist

- [ ] **Có dữ liệu mẫu/log sạch để test?** Chưa xác nhận có dữ liệu lead nội bộ được cấp quyền và gán nhãn; có thể tạo **dữ liệu tổng hợp** để kiểm thử chức năng ban đầu, nhưng không dùng để chứng minh hiệu quả thực tế.
- [x] **Rủi ro AI sai có thể thiết kế kiểm soát?** Có phương án Rule Engine, danh mục nhóm Sales hợp lệ, **chế độ nháp**, nhân viên duyệt và fallback; **chưa kiểm chứng thực nghiệm** hiệu quả các biện pháp này.
- [ ] **Stakeholder sẵn sàng thay đổi workflow?** Chưa có xác nhận của Lead Operations, Sales Admin, Sales Manager hoặc chủ hệ thống CRM.

## 5.2. Quyết định cuối cùng của nhóm

- [ ] **GO (Bắt đầu tích hợp vận hành)**
- [x] **NOT YET (Cần xác lập baseline và chuẩn bị dữ liệu)**
- [ ] **NO-GO (Không khả thi / Rule-based tốt hơn)**

### Justification — Lý giải dựa trên nghiệp vụ, kỹ thuật và chi phí

> **NOT YET cho triển khai thực tế; tiếp tục thiết kế và thử nghiệm prototype offline trong phạm vi lab.** Card #01 (**Lead Score & Smart Routing**) có quy trình đầu vào/đầu ra rõ, có thể kiểm chứng bằng dữ liệu tổng hợp và kiến trúc hỗn hợp **Rule Engine + LLM/Score Agent (nháp) + phê duyệt HITL**. Tuy nhiên, chưa có số liệu lead/ngày, baseline Time-to-Assign, chất lượng Intent Score/nhãn, chi phí thực tế hoặc bằng chứng mô hình tốt hơn Rule-based. Vì vậy chưa đủ cơ sở kết luận GO cho tích hợp CRM sản xuất.
>
> Theo **[Giả định lab]**: 100 lead/ngày × 5 phút tiết kiệm × 26 ngày ÷ 60 = 216,67 giờ/tháng; quy đổi 120.000đ/giờ = **26.000.000đ/tháng**; trừ **3.000.000đ/tháng** chi phí AI giả định, **Impact ròng = 23.000.000đ/tháng**. B = 0 và C = 0 vì chưa có bằng chứng tiết kiệm chi phí sự cố hoặc tăng doanh thu. Con số này chưa phản ánh tiết kiệm tiền mặt và không phải ROI đã được chứng minh.
>
> Hệ thống chỉ được đưa đề xuất; **0 lần** tự ý cam kết giá/ưu đãi, gửi liên hệ khách hoặc thay đổi CRM/chủ sở hữu lead trái quyền. Quy tắc kỹ thuật ở tầng ứng dụng và phê duyệt của người có trách nhiệm là bắt buộc; prompt không thể thay thế cơ chế phân quyền.

## 5.3. Điều kiện nâng trạng thái lên GO

| Hạng mục | Tiêu chí cần xác minh trước GO | Tình trạng hiện tại |
|---|---|---|
| Dữ liệu | Có bộ lead được cấp quyền và nhãn chuẩn, phân nhóm kênh/khu vực, dữ liệu được bảo vệ phù hợp | **Chưa xác minh** |
| Baseline | Đo được số lead/ngày, thời gian xử lý/lead, tỷ lệ phân tuyến sai và chi phí thực tế | **Chưa đo** |
| So sánh phương án | Cùng tập lead thử nghiệm cho thủ công, Rule-only và Rule + LLM; AI mang lại lợi ích tăng thêm | **Chưa thử nghiệm** |
| Mục tiêu thời gian | Median Time-to-Assign từ 10 xuống ≤5 phút/lead **[mục tiêu giả định]**, đo cả thời gian người duyệt | **Chưa kiểm chứng** |
| Chất lượng | ≥95% lead có Intent Score; ≥90% gợi ý được xác nhận đúng / override &lt;20% **[mục tiêu giả định]** | **Chưa kiểm chứng** |
| An toàn | **0** lần tự cam kết giá/ưu đãi, tự nhắn khách, tự ghi CRM, tự phân công trái quyền | **Chưa kiểm chứng** |
| Tổ chức | Có chủ quy trình và người phụ trách bảo mật/CRM chấp thuận pilot | **Chưa xác nhận** |
| Kinh tế | Tính lại Impact = giờ công quy đổi + chi phí tránh được + công suất tăng có chứng minh − chi phí chạy; không trùng lợi ích | **Chỉ có giả định lab** |

**Kết luận cuối:** **NOT YET** cho triển khai thực tế. **Được tiếp tục thử nghiệm offline** để xác nhận khả năng phân loại lead tự do và kiểm soát ranh giới; nếu Rule-based đạt hiệu quả tương đương hoặc tốt hơn về chi phí và chất lượng, ưu tiên phương án không dùng LLM.