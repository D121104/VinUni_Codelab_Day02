# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | **Vinmec** | Pain từ người khác | Bác sĩ mất quá nhiều thời gian viết tóm tắt hồ sơ xuất viện (mất 20-30 phút/bệnh nhân, bác sĩ phàn nàn vì quá tải). || | |
| 2 | **Vinmec** | Lặp lại|Nhân viên tiếp nhận phải kiểm tra, nhập và đối chiếu thông tin CCCD, BHYT và giấy tờ bảo hiểm cho từng bệnh nhân, dễ phát sinh sai sót nhập liệu. || | |
| 3 | **Vinmec** | Tốn thời gian| Bác sĩ phải đọc lại lịch sử khám, kết quả xét nghiệm và đơn thuốc từ nhiều lần khám để tổng hợp thông tin trước khi tiếp nhận bệnh nhân.|| | |
| 4 | **Vinmec** | AI-upgrade| Hệ thống CSKH có thể chưa giải đáp hiệu quả những câu hỏi phức tạp về quy trình khám, chi phí và quyền lợi bảo hiểm, khiến nhân viên phải xử lý lại. || | |
| 5 | **Vinmec** | Pain từ người khác | Bệnh nhân phải chờ đợi giữa các bước khám, xét nghiệm và nhận kết quả do lịch hẹn và nguồn lực chưa được điều phối tối ưu. || | |
---
# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards (Cá nhân)

Chọn top 3 từ danh sách SCAN: **#1 (Vinmec – Tóm tắt hồ sơ xuất viện), #2 (Vinmec – Kiểm tra hồ sơ bảo hiểm), #5 (Vinmec – Tối ưu thời gian chờ khám bệnh).**

## Card #5 — Vinmec: Tối ưu thời gian chờ khám bệnh

**Bài toán:** Bệnh nhân có thể phải chờ lâu giữa các bước khám, xét nghiệm và nhận kết quả khi lịch hẹn và nguồn lực chưa được phân bổ tối ưu.

**Công ty thành viên:** Vinmec

**Ai đang đau?** Bệnh nhân (chờ đợi), nhân viên điều phối (khó cân bằng lịch khám).

**Workflow thủ công hiện tại (5 bước giả định):**
1. Bệnh nhân đăng ký và nhận lịch khám.
2. Nhân viên kiểm tra lịch bác sĩ và phòng khám.
3. Điều phối bệnh nhân đến khu vực khám hoặc xét nghiệm.
4. Theo dõi tiến độ và điều chỉnh thứ tự khi phát sinh chậm trễ.
5. Thông báo thời gian chờ dự kiến cho bệnh nhân.

**Bước nào tốn nhất?** Bước 3–4, đặc biệt khi có nhiều bệnh nhân và lịch khám thay đổi.

**AI có thể hỗ trợ bước nào?** Bước 2–5: Dự đoán thời gian chờ, đề xuất phân bổ lịch và cập nhật thời gian dự kiến.

**Metric:** Mục tiêu giảm thời gian chờ trung bình 20–30% so với baseline đo được, không làm tăng tỷ lệ trễ ở các ca ưu tiên.

**Quick Architecture:** [x] Predictive ML + Scheduling Optimization.

---

# 🗳️ Quyết định lựa chọn đề xuất

**Chọn Card #2 — Vinmec: Tự động kiểm tra và đối chiếu hồ sơ bảo hiểm** để thực hiện Deep-Dive.

## Lý do lựa chọn và loại bỏ các thẻ khác

- **Card #1 (Tóm tắt hồ sơ xuất viện):** Có tiềm năng tiết kiệm nhiều thời gian cho bác sĩ, nhưng đòi hỏi kiểm soát độ chính xác thông tin y tế, bảo mật hồ sơ bệnh nhân và quy trình kiểm duyệt nghiêm ngặt. Chưa phù hợp bằng Card #2 cho MVP ngắn hạn.

- **Card #5 (Tối ưu thời gian chờ khám bệnh):** Có tác động trực tiếp đến trải nghiệm bệnh nhân, nhưng cần dữ liệu lịch khám, thời gian phục vụ và tình trạng nguồn lực theo thời gian thực. Việc tích hợp hệ thống phức tạp hơn.

- **Card #2 (Kiểm tra hồ sơ bảo hiểm):** Có quy trình rõ ràng, dễ mô phỏng bằng dữ liệu tổng hợp, có thể ứng dụng OCR kết hợp kiểm tra quy tắc và đánh giá bằng thời gian xử lý, độ chính xác trích xuất, tỷ lệ phát hiện sai lệch.
