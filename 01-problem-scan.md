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
| 2 | **Xanh SM** | Lặp lại | Quy trình tiếp nhận và xác minh hồ sơ tài xế cần kiểm tra nhiều giấy tờ, đối chiếu thông tin và xác nhận điều kiện, gây tốn thời gian và dễ phát sinh sai sót. |
| 3 | **Xanh SM** | Pain từ người khác | Điều phối xe điện đến trạm sạc chưa tối ưu có thể gây thời gian chờ kéo dài, tăng quãng đường chạy rỗng và giảm thời gian khai thác xe. |
| 4 | **Xanh SM** | AI-upgrade | Theo dõi tình trạng xe và lên lịch bảo dưỡng dựa trên kiểm tra định kỳ có thể bỏ sót dấu hiệu hỏng hóc sớm, gây thời gian dừng xe ngoài kế hoạch. |
| 5 | **Xanh SM** | Lặp lại | Đối soát dữ liệu chuyến đi, thanh toán, khuyến mãi và thu nhập tài xế từ nhiều nguồn có thể phát sinh sai lệch, cần kiểm tra thủ công và làm chậm quy trình tài chính. |
| 6 | **Xanh SM** | AI-upgrade | Nhu cầu đặt xe biến động theo khu vực/khung giờ có thể gây mất cân bằng cung–cầu, tăng thời gian khách chờ và quãng đường xe chạy rỗng nếu dự báo, phân bổ chưa hiệu quả. |
| 7 | **Xanh SM** | Tốn thời gian | Khi kiểm tra ảnh bàn giao ca, việc phát hiện và so sánh vết xước/móp méo giữa các lần chụp có thể tốn thời gian hoặc bỏ sót dấu hiệu hư hỏng. |
| 8 | **Xanh SM** | AI-upgrade | Phát hiện hành vi bất thường như hủy chuyến có chủ đích, kéo dài quãng đường hoặc thao tác sai trên ứng dụng cần phân tích nhiều dữ liệu hành trình, gây khó khăn cho việc giám sát chất lượng dịch vụ trên quy mô lớn. |
| 9 | **Xanh SM** | Pain từ người khác | Theo dõi chất lượng đào tạo và đánh giá năng lực tài xế dựa trên kết quả kiểm tra, phản hồi khách hàng và lịch sử vận hành có thể thiếu tính cá nhân hóa, khiến việc phát hiện tài xế cần đào tạo bổ sung chưa kịp thời. |
| 10 | **Xanh SM** | Tốn thời gian | Quản lý yêu cầu đặt xe doanh nghiệp, hợp đồng dịch vụ và lịch đưa đón đoàn khách có thể cần tổng hợp thông tin từ nhiều kênh, gây tốn thời gian lập phương án vận chuyển và dễ sai sót khi thay đổi lịch trình. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

---


# 3 QUICK PROBLEM CARDS – XANH SM
---

### QUICK PROBLEM CARD #01 – AI Vehicle Damage Detection

```text
┌────────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #01 – AI Vehicle Damage Detection                       │
│                                                                            │
│ Bài toán (1 câu):                                                          │
│ Tự động phát hiện và so sánh dấu hiệu hư hỏng ngoại thất xe từ hình ảnh    │
│ trước/sau ca làm việc nhằm giảm thời gian kiểm tra và hạn chế bỏ sót bất   │
│ thường.                                                                    │
│                                                                            │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM                               │
│                     [ ] Vinhomes  [ ] Vinmec  [ ] Khác                     │
│                                                                            │
│ Ai đang đau (Actor):                                                       │
│ • Tài xế bàn giao ca.                                                      │
│ • Nhân viên kiểm tra phương tiện.                                          │
│ • Quản lý đội xe.                                                          │
│                                                                            │
│ Workflow hiện tại (giả định):                                              │
│ 1. Tài xế chụp ảnh xe khi bàn giao ca.                                     │
│ 2. Nhân viên xem ảnh và so sánh với lần kiểm tra trước.                    │
│ 3. Xác định dấu hiệu trầy xước, móp méo hoặc bất thường.                   │
│ 4. Lập biên bản, yêu cầu xác minh nếu phát hiện hư hỏng.                   │
│                                                                            │
│ Bước tốn thời gian/lỗi nhất:                                               │
│ • Bước 2–3: Xem, so sánh và xác định hư hỏng; 5 phút/lượt.                 │
│ • Rủi ro: Bỏ sót vết nhỏ, ảnh mờ hoặc ánh sáng khác nhau.                  │
│                                                                            │
│ AI hỗ trợ ở bước nào:                                                      │
│ • Bước 2–3: Computer Vision phát hiện dấu hiệu hư hỏng.                    │
│ • So sánh ảnh, khoanh vùng thay đổi và chuyển nhân viên xác minh.          │
│                                                                            │
│ Metric mục tiêu (giả định lab):                                            │
│ • Thời gian kiểm tra: 5 phút → ≤2 phút/lượt.                               │
│ • Recall phát hiện hư hỏng nhìn thấy rõ ≥95%.                              │
│ • Tỷ lệ cảnh báo sai ≤10% trên trường hợp không hư hỏng.                   │
│ • Không tăng bỏ sót hư hỏng nghiêm trọng.                                  │
│                                                                            │
│ Quick Architecture:                                                        │
│ [ ] No AI [x] Rule [ ] LLM [ ] Agent                                       │
│ [x] Computer Vision [x] Human-in-the-loop                                  │
└────────────────────────────────────────────────────────────────────────────┘
```

---

### QUICK PROBLEM CARD #02 – AI Demand Forecasting & Fleet Optimization

```text
┌────────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #02 – AI Demand Forecasting & Fleet Optimization        │
│                                                                            │
│ Bài toán (1 câu):                                                          │
│ Dự báo nhu cầu đặt xe theo khu vực và khung giờ nhằm hỗ trợ phân bổ phương │
│ tiện, giảm thời gian khách chờ và quãng đường di chuyển không có khách.    │
│                                                                            │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM                               │
│                     [ ] Vinhomes  [ ] Vinmec  [ ] Khác                     │
│                                                                            │
│ Ai đang đau (Actor):                                                       │
│ • Nhân viên điều phối.                                                     │
│ • Quản lý vận hành đội xe.                                                 │
│ • Tài xế và khách hàng.                                                    │
│                                                                            │
│ Workflow hiện tại (giả định):                                              │
│ 1. Thu thập số chuyến, vị trí xe và nhu cầu theo khu vực.                  │
│ 2. Ước lượng nhu cầu đặt xe ở các khung giờ tiếp theo.                     │
│ 3. Đề xuất phân bổ xe trống đến khu vực có nhu cầu.                        │
│ 4. Theo dõi kết quả và điều chỉnh phương án vận hành.                      │
│                                                                            │
│ Bước tốn thời gian/lỗi nhất:                                               │
│ • Bước 2–3: Ước lượng nhu cầu và tái phân bổ; 15 phút/chu kỳ.              │
│ • Rủi ro: Dự báo sai, thừa/thiếu xe cục bộ.                                │
│                                                                            │
│ AI hỗ trợ ở bước nào:                                                      │
│ • Bước 2: ML dự báo nhu cầu theo thời gian và khu vực.                     │
│ • Bước 3: Thuật toán tối ưu hóa đề xuất phân bổ xe.                        │
│ • Dữ liệu: GPS, lịch sử chuyến, thời tiết, sự kiện, SOC pin.               │
│                                                                            │
│ Metric mục tiêu (giả định lab):                                            │
│ • Giảm WAPE dự báo nhu cầu ≥15% so với baseline.                           │
│ • P90 thời gian khách chờ: 12 phút → ≤10 phút.                             │
│ • Tỷ lệ km chạy rỗng: 30% → ≤27%.                                          │
│ • Không giảm tỷ lệ nhận và hoàn thành chuyến.                              │
│                                                                            │
│ Quick Architecture:                                                        │
│ [ ] No AI [x] Rule [ ] LLM [ ] Agent                                       │
│ [x] Machine Learning [x] Optimization                                      │
└────────────────────────────────────────────────────────────────────────────┘
```

---

### QUICK PROBLEM CARD #03 – AI Complaint Resolution Agent

```text
┌────────────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #03 – AI Complaint Resolution Agent                     │
│                                                                            │
│ Bài toán (1 câu):                                                          │
│ Hỗ trợ tự động phân loại khiếu nại, truy xuất thông tin chuyến đi và đề    │
│ xuất phương án xử lý nhằm giảm thời gian giải quyết yêu cầu chăm sóc khách │
│ hàng.                                                                      │
│                                                                            │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM                               │
│                     [ ] Vinhomes  [ ] Vinmec  [ ] Khác                     │
│                                                                            │
│ Ai đang đau (Actor):                                                       │
│ • Nhân viên chăm sóc khách hàng.                                           │
│ • Trưởng nhóm CSKH.                                                        │
│ • Bộ phận xử lý khiếu nại.                                                 │
│                                                                            │
│ Workflow hiện tại (giả định):                                              │
│ 1. Tiếp nhận phản ánh từ khách hàng.                                       │
│ 2. Phân loại vấn đề và tra cứu thông tin chuyến đi.                        │
│ 3. Đối chiếu chính sách, xác minh và chọn phương án xử lý.                 │
│ 4. Soạn phản hồi, gửi khách hàng và cập nhật ticket.                       │
│                                                                            │
│ Bước tốn thời gian/lỗi nhất:                                               │
│ • Bước 2–3: Tra cứu và tổng hợp dữ liệu; 6 phút/ticket.                    │
│ • Tổng thời gian xử lý: 10 phút/ticket.                                    │
│ • Rủi ro: Tra cứu sai, bỏ sót chính sách, phản hồi không nhất quán.        │
│                                                                            │
│ AI hỗ trợ ở bước nào:                                                      │
│ • Bước 2: LLM phân loại khiếu nại.                                         │
│ • Bước 2–3: Function Calling truy xuất dữ liệu chuyến đi.                  │
│ • Bước 3: RAG tra cứu chính sách xử lý.                                    │
│ • Bước 4: Agent đề xuất phương án, soạn nháp để người duyệt.               │
│                                                                            │
│ Metric mục tiêu (giả định lab):                                            │
│ • Average Handling Time: 10 phút → ≤6 phút/ticket.                         │
│ • Độ chính xác phân loại ≥95%.                                             │
│ • Tỷ lệ đề xuất được nhân viên chấp nhận ≥85%.                             │
│ • Tỷ lệ ticket mở lại không tăng so với baseline.                          │
│ • Chi phí xử lý mỗi ticket thấp hơn hiện tại.                              │
│                                                                            │
│ Quick Architecture:                                                        │
│ [ ] No AI [x] Rule [x] LLM [x] Agent                                       │
│ [x] RAG [x] Human-in-the-loop                                              │
└────────────────────────────────────────────────────────────────────────────┘
```

---
