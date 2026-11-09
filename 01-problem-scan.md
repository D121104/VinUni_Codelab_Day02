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

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Nhân viên Vinmec phải kiểm tra, nhập liệu │
│ và đối chiếu thủ công hồ sơ bảo hiểm của bệnh nhân.         │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [x] Vinmec   [ ] Khác                   │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên tiếp nhận (quá tải),         │
│ bệnh nhân (chờ đợi làm thủ tục).                            │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Tiếp nhận CCCD, BHYT và giấy tờ bảo hiểm               │
│   ──> 2. Kiểm tra tính đầy đủ của giấy tờ                   │
│   ──> 3. Nhập thông tin vào hệ thống quản lý                │
│   ──> 4. Đối chiếu thông tin giữa các giấy tờ               │
│   ──> 5. Xác nhận hoặc yêu cầu bổ sung hồ sơ                │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3-4                   │
│ (⏱ Ước tính 5-7 phút/hồ sơ)                                │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-4              │
│ OCR trích xuất -> Đối chiếu -> Cảnh báo sai lệch            │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm thời gian xử lý từ 7 phút ──> dưới 2 phút/hồ sơ.       │
│ Độ chính xác trích xuất thông tin ≥98%.                     │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

---

# 🗳️ Quyết định lựa chọn đề xuất

**Chọn Card #2 — Vinmec: Tự động kiểm tra và đối chiếu hồ sơ bảo hiểm** để thực hiện Deep-Dive.

## Lý do lựa chọn và loại bỏ các thẻ khác

- **Card #1 (Tóm tắt hồ sơ xuất viện):** Có tiềm năng tiết kiệm nhiều thời gian cho bác sĩ, nhưng đòi hỏi kiểm soát độ chính xác thông tin y tế, bảo mật hồ sơ bệnh nhân và quy trình kiểm duyệt nghiêm ngặt. Chưa phù hợp bằng Card #2 cho MVP ngắn hạn.

- **Card #5 (Tối ưu thời gian chờ khám bệnh):** Có tác động trực tiếp đến trải nghiệm bệnh nhân, nhưng cần dữ liệu lịch khám, thời gian phục vụ và tình trạng nguồn lực theo thời gian thực. Việc tích hợp hệ thống phức tạp hơn.

- **Card #2 (Kiểm tra hồ sơ bảo hiểm):** Có quy trình rõ ràng, dễ mô phỏng bằng dữ liệu tổng hợp, có thể ứng dụng OCR kết hợp kiểm tra quy tắc và đánh giá bằng thời gian xử lý, độ chính xác trích xuất, tỷ lệ phát hiện sai lệch.
