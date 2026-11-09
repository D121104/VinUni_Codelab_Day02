# Lab 02 — Phase 1 SCAN + Phase 2 Quick Cards

> **Bài nộp cá nhân (I1):** Scan ≥5 bài toán + 3 Quick Problem Cards.  
> **Mảng:** VinFast — Hậu mãi / Xưởng dịch vụ.  
> **Sản phẩm chốt:** Trợ lý tiếp nhận & phân loại ban đầu cho cố vấn dịch vụ.

---

## 🏛️ Bối cảnh: Tôi là ai?

Tôi là **Lê Thanh Hà**, AI Product Engineer tại **Vin Smart Future**, phối hợp Khối Hậu mãi VinFast. Quan sát tại xưởng cho thấy nút thắt không phải thiếu tài liệu kỹ thuật, mà là **lời nói trước khi có mã lỗi máy chẩn đoán**: khách kể triệu chứng bằng lời thường, cố vấn dịch vụ vừa hỏi thêm vừa đối chiếu chính sách miệng (xe mượn, bảo hành pin, bồi thường trễ hạn), trong khi lệnh sửa chữa đã ghi giờ sẽ kích hoạt **500.000 đồng/ngày** nếu giao muộn (Fact). Điểm AI hỗ trợ thật là chuẩn hóa tiếp nhận **trước khi** kỹ thuật viên cắm máy đọc lỗi.

---

# 🔍 Phase 1 — SCAN: Tìm kiếm cơ hội

Dùng **4 Lenses** quét vận hành VinFast. Mỗi dòng ưu tiên đổ về thang **A (giờ công)** / **B (tiền tránh chi)** khi có số từ nguồn Final.

| # | Mảng | Lens | Bài toán | A Giờ/tháng | B Tránh chi/tháng | Ghi chú |
|---|---|---|---|---|---|---|
| 1 | Hậu mãi / Xưởng | Tốn thời gian | Quầy tiếp nhận: khách kể triệu chứng bằng lời thường; cố vấn hỏi + đối chiếu chính sách miệng trước mã lỗi | ~560 giờ *[Giả định lab]* | ~20 triệu (Fact 500k/ngày × lệnh tránh sai giờ) *[Giả định khối lượng]* | **Chốt Card #1** — Impact gộp ≈ 87 triệu/tháng |
| 2 | Hậu mãi / Kỹ thuật | AI tốt hơn | Tra cứu đa mã lỗi + sổ tay kỹ thuật; giảm thay nhầm linh kiện | ~480 giờ *[Giả định lab]* | ~75 triệu (linh kiện) *[Giả định lab]* | Card #2 — roadmap; chưa đo baseline |
| 3 | Bảo hành | Lặp lại | Tiền kiểm hồ sơ bảo hành: duyệt, bắt kê thừa | ~1.200 giờ *[Giả định lab]* | ~72 triệu (giữ lại) *[Giả định lab]* | Card #3 — Rule trước, AI sau |
| 4 | CSKH / Tổng đài | Lặp lại | Điền phiếu sau cuộc gọi; chuyển đúng bộ phận | Có thể điền A khi khóa phút hậu kỳ | 0 (ít tiền trực tiếp) | Chỉ vào top khi khóa được A |
| 5 | V-Green / Trạm sạc | Pain từ người khác | App báo trống / taxi chiếm trụ; khách chờ lâu | ❌ thiếu dữ liệu trạng thái trụ | phí chiếm trụ chưa gắn AI | **Loại** — chưa đủ thang đo |
| 6 | Cứu hộ / Mobile Service | Pain từ người khác | Súng sạc kẹt ngoài giờ; thiếu thợ đêm | ❌ không phải bài AI | ❌ | **Loại** — thiếu capacity vận hành |

> **Thước chung:** Impact tháng ≈ A × đơn giá giờ + B (+ C nếu chứng minh được; − D chi phí AI). Ý không điền được A hoặc B → không vào top. Fact cứng duy nhất gắn tiền ngay: **500.000đ/ngày** khi trễ giờ cam kết trên lệnh sửa.

---

# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards

Top 3 đều có thang đo nhân số. Thẻ triển khai sâu (Phase 3): **Card #1**.

## Card #1 — Trợ lý tiếp nhận & phân loại ban đầu *(CHỐT)*

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Quầy tiếp nhận — khách kể triệu chứng bằng lời   │
│ thường; cố vấn dịch vụ cần hỏi đúng + không hứa bừa         │
│ (xe mượn / tiền / giờ trả) TRƯỚC khi thợ đọc mã lỗi         │
│ máy chẩn đoán.                                              │
│ Công ty thành viên: [x] VinFast — Hậu mãi / Xưởng dịch vụ   │
│                                                             │
│ Ai đang đau? Cố vấn dịch vụ, chủ xe                         │
│                                                             │
│ Workflow thủ công hiện tại:                                 │
│   1. Đặt lịch (ứng dụng / tổng đài)                         │
│   → 2. Tới xưởng, chờ cố vấn dịch vụ                        │
│   → 3. Phỏng vấn + đối chiếu chính sách miệng               │
│   → 4. Kỹ thuật viên cắm máy → mã lỗi chẩn đoán             │
│   → 5. Ghi giờ giao trên lệnh sửa chữa                      │
│                                                             │
│ Bước nghẽn? Bước 3 (⏱ ~12 phút/xe) *[Giả định lab]*         │
│ AI nhảy vào? Soạn nháp câu hỏi cần hỏi thêm + gắn cờ        │
│ "chưa xác nhận — chờ mã lỗi" (cấm hứa tiền/xe mượn/giờ trả) │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Vận hành [Giả định lab]: 12 phút → ≤ 5 phút hỏi–đối chiếu │
│   / xe; pilot 40 xe/ngày × 5 xưởng = 200 xe/ngày            │
│   → tiết kiệm ~560 giờ/tháng × 120.000đ ≈ 67 triệu (A)      │
│   + tránh ~20 triệu bồi thường giờ giao sai (B, Fact 500k)  │
│   → Impact pilot ≈ 87 triệu đồng/tháng                      │
│   Lab: 24 câu vàng; ≥80% đủ câu hỏi; 0/24 dính tiền /       │
│   xe mượn / bảo hành / ngày-giờ; ≥3 câu đối kháng từ chối.  │
│                                                             │
│ Quick Architecture: [x] Tính năng mô hình ngôn ngữ          │
│                     + duyệt người (cố vấn) bắt buộc         │
└─────────────────────────────────────────────────────────────┘
```

## Card #2 — Trợ lý chẩn đoán kỹ thuật *(roadmap)*

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán: Kỹ thuật viên mất thời gian tra cứu đa mã lỗi    │
│ máy chẩn đoán + sổ tay kỹ thuật; dễ thay nhầm linh kiện.    │
│ Công ty thành viên: [x] VinFast — Hậu mãi / Kỹ thuật xưởng  │
│                                                             │
│ Ai đang đau? Kỹ thuật viên, cố vấn dịch vụ (lặp lệnh)       │
│                                                             │
│ Workflow thủ công hiện tại:                                 │
│   1. Nhận mã lỗi từ máy chẩn đoán                           │
│   → 2. Tra cứu sổ tay / bản tin kỹ thuật thủ công           │
│   → 3. Đoán hướng sửa / chọn linh kiện                      │
│   → 4. Thay thử → kiểm tra lại                              │
│                                                             │
│ Bước nghẽn? Bước 2–3 (⏱ giảm ~10 phút/ca khó) *[Giả định]*  │
│ AI nhảy vào? Gợi ý hướng tra cứu + cảnh báo linh kiện rủi ro│
│                                                             │
│ Đo thành công bằng gì (Metric có số)? *[Giả định lab]*      │
│   120 ca khó/ngày × 10 phút = ~480 giờ kỹ thuật/tháng       │
│   × 150.000đ/giờ ≈ 72 triệu (A)                             │
│   + giảm 5 ca thay nhầm linh kiện cao áp/tháng × 15 triệu   │
│   ≈ 75 triệu tránh chi (B) → Impact giấy ≈ 147 triệu        │
│                                                             │
│ Quick Architecture: [x] Tính năng mô hình ngôn ngữ          │
│                     (cần corpus sổ tay đo được)             │
│ Verdict: NOT YET — giữ roadmap; chưa khóa baseline phút     │
│          tra cứu và tỷ lệ sửa đúng lần đầu trên dữ liệu thật│
└─────────────────────────────────────────────────────────────┘
```

## Card #3 — Tiền kiểm hồ sơ bảo hành *(Rule-first)*

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán: Chuyên viên bảo hành mất thời gian tiền kiểm      │
│ hồ sơ (đủ giấy tờ, điều kiện đời xe / km, kê thừa chi phí). │
│ Công ty thành viên: [x] VinFast — Bảo hành                  │
│                                                             │
│ Ai đang đau? Chuyên viên bảo hành, xưởng (chờ duyệt tiền)   │
│                                                             │
│ Workflow thủ công hiện tại:                                 │
│   1. Nhận hồ sơ từ xưởng                                    │
│   → 2. Đối chiếu điều kiện bảo hành theo đời xe / km        │
│   → 3. Kiểm tra kê thừa linh kiện / công                    │
│   → 4. Duyệt hoặc trả lại                                   │
│                                                             │
│ Bước nghẽn? Bước 2–3 (⏱ giảm ~10 phút/hồ sơ) *[Giả định]*   │
│ AI nhảy vào? Chỉ sau khi quy tắc cứng / truy vấn dữ liệu    │
│ cover phần lớn kiểm tra; AI hỗ trợ đuôi dài / ảnh chứng từ  │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? *[Giả định lab]*      │
│   300 hồ sơ/ngày × 10 phút = ~1.200 giờ/tháng               │
│   × 100.000đ/giờ ≈ 120 triệu (A)                            │
│   + bắt 3% hồ sơ kê thừa × giá trị TB 8 triệu ≈ 72 triệu (B)│
│   → Impact giấy ≈ 192 triệu                                 │
│                                                             │
│ Quick Architecture: [x] Quy tắc / truy vấn dữ liệu trước    │
│                     [ ] Mô hình ngôn ngữ sau (đuôi dài)      │
│ Verdict: Rule-first — ~80% làm được bằng quy tắc; ảnh xưởng │
│          dễ báo sai → impact thật phụ thuộc báo động giả    │
└─────────────────────────────────────────────────────────────┘
```

---

# 🗳️ Quyết định lựa chọn của nhóm

Nhóm chốt **Card #1 — Trợ lý tiếp nhận & phân loại ban đầu**.

* **Có Fact tiền cứng ngay:** mỗi ngày trễ trên lệnh đã ghi giờ = **500.000 đồng** — AI chỉ đụng lớp *trước* khi đồng hồ đó bị mở sai bằng lời hứa miệng.
* **Đo được trong lab / pilot hẹp:** A + B điền được (dù khối lượng còn *[Giả định lab]*); ranh giới an toàn rõ (cấm tiền / xe mượn / giờ trả + duyệt người).
* **Card #2 / #3 chưa chốt:** #2 impact giấy lớn nhưng thiếu baseline; #3 phần lớn là quy tắc cứng → Rule trước. V-Green trụ đầy / súng kẹt đêm → **loại** (thiếu dữ liệu trụ / thiếu thợ, không nhân ra impact AI).
