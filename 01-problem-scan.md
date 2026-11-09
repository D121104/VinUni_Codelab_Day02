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

## Card #1 -Vinmec : Tóm tắt hồ sơ xuất viện
** 
```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Bác sĩ Vinmec mất nhiều thời gian đọc,    │
│ tổng hợp và viết tóm tắt hồ sơ xuất viện cho bệnh nhân.     │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [x] Vinmec   [ ] Khác                   │
│                                                             │
│ Ai đang đau (Actor)? Bác sĩ điều trị (quá tải công việc),   │
│ bệnh nhân (có thể phải chờ hoàn tất hồ sơ xuất viện).       │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Truy cập hồ sơ bệnh án của bệnh nhân                    │
│   ──> 2. Đọc lịch sử điều trị, xét nghiệm và đơn thuốc      │
│   ──> 3. Tổng hợp chẩn đoán, diễn biến và kết quả điều trị   │
│   ──> 4. Viết bản tóm tắt hồ sơ xuất viện                    │
│   ──> 5. Kiểm tra, chỉnh sửa và xác nhận hồ sơ              │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2-4                   │
│ (⏱ Ước tính 20-30 phút/bệnh nhân)                           │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-4              │
│ Trích xuất thông tin -> Tóm tắt -> Tạo bản nháp xuất viện   │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Mục tiêu giảm thời gian từ 30 -> dưới 10 phút/hồ sơ.        │
│ 100% bản tóm tắt phải được bác sĩ kiểm tra trước khi duyệt. │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```
## Card #2 — Vinmec: Kiểm tra hồ sơ bảo hiểm

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
## Card #3 — Vinmec: Tối ưu thời gian chờ khám bệnh
```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Bệnh nhân Vinmec phải chờ đợi giữa các    │
│ bước khám, xét nghiệm và nhận kết quả do việc điều phối     │
│ lịch hẹn và nguồn lực chưa tối ưu.                          │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [x] Vinmec   [ ] Khác                   │
│                                                             │
│ Ai đang đau (Actor)? Bệnh nhân (chờ đợi lâu), nhân viên     │
│ điều phối (khó phân bổ lịch khám và nguồn lực).             │
│                                                             │
│ Workflow thủ công hiện tại (5 bước):                        │
│   1. Bệnh nhân đăng ký và nhận lịch khám                    │
│   ──> 2. Nhân viên tiếp nhận và phân luồng bệnh nhân        │
│   ──> 3. Bệnh nhân chờ đến lượt khám                         │
│   ──> 4. Chờ thực hiện xét nghiệm hoặc chẩn đoán hình ảnh   │
│   ──> 5. Chờ kết quả và quay lại gặp bác sĩ                 │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3-5                   │
│ (⏱ Giả định 30-60 phút chờ giữa các công đoạn)             │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2-4              │
│ Dự đoán thời gian chờ -> Đề xuất điều phối lịch và nguồn lực│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Mục tiêu giảm thời gian chờ trung bình ít nhất 30%.         │
│ Giảm sai số dự đoán thời gian chờ xuống dưới 10 phút.       │
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
