# Deliverable — Vin Smart Future (VinFast Aftersales Use Case)

> **Bài nộp cuối cùng cho mảng VinFast Aftersales.**
>
> * **Mảng kinh doanh:** **VinFast — Hậu mãi / Xưởng dịch vụ.**
> * **Sản phẩm chốt:** **Trợ lý tiếp nhận & phân loại ban đầu** cho Cố vấn dịch vụ — trước khi có mã lỗi chẩn đoán.
> * **Quyết định:** **GO** cho bản mẫu trên lớp (phạm vi hẹp) · **NOT YET** đưa ra xưởng · **NO-GO** nếu AI được quyền hứa tiền / xe mượn / bảo hành / giờ giao xe.
> * **Nguyên tắc đo:** mọi ý tưởng phải có công thức **tần suất × thời gian (hoặc tỷ lệ lỗi) × đơn giá = tiết kiệm / tránh chi / giờ công trong một khoảng thời gian**. Số khối lượng/thời gian mang nhãn *[Giả định lab]* cho đến khi shadow xưởng xác nhận.

---

## 🏛️ Bối cảnh: Tôi là ai?

Tôi là Lê Thanh Hà — AI Product Engineer tại **Vin Smart Future**, phối hợp Khối Hậu mãi VinFast. Quan sát tại xưởng cho thấy nút thắt không phải thiếu tài liệu kỹ thuật, mà là **lời nói trước khi có mã lỗi**: khách mô tả triệu chứng bằng tiếng Việt mơ hồ, cố vấn dịch vụ phải vừa hỏi thêm vừa đối chiếu chính sách miệng (xe mượn, bảo hành pin, bồi thường trễ hạn), trong khi lệnh sửa chữa đã ghi giờ sẽ kích hoạt **500.000 đồng/ngày** nếu giao muộn.

Bài học đối chiếu BYD và Tesla: AI không sửa được thiếu phụ tùng, thiếu thợ đêm hay hàng đợi cầu nâng. VinFast Việt Nam đã có mạng lưới xưởng dày và cam kết phụ tùng trong 24 giờ — điểm còn lại để AI hỗ trợ thật là **chuẩn hóa tiếp nhận trước khi kỹ thuật viên cắm máy đọc lỗi**.

---

# 🔍 Phase 1 — SCAN: Tìm kiếm cơ hội

Dùng **4 Lenses** quét vận hành VinFast. Mỗi dòng kèm **cách đo impact** (công thức nhân số) — ý nào không nhân ra được tiền/giờ thì không đưa vào top.

| # | Công ty | Lens | Bài toán | Cách đo impact (công thức) |
|---|---|---|---|---|
| 1 | **VinFast** Hậu mãi | Tốn thời gian | Cố vấn dịch vụ dịch than phiền tiếng Việt thành hướng kiểm tra + chính sách **trước mã lỗi**. | `số xe tiếp nhận/ngày × phút hỏi–đối chiếu tiết kiệm × số ngày làm việc` = **giờ công/tháng**; cộng `số lệnh tránh ghi giờ sai × 500.000đ` = **tiền tránh chi bồi thường**. |
| 2 | **VinFast** Hậu mãi | AI tốt hơn | Kỹ thuật viên tra cứu nhiều mã lỗi + sổ tay / bản tin kỹ thuật (~30% ca khó). | `số ca khó/ngày × phút tra cứu tiết kiệm` = giờ kỹ thuật/tháng; `số ca tránh thay nhầm linh kiện × đơn giá linh kiện` = **tiết kiệm bảo hành**. |
| 3 | **VinFast** Bảo hành | Lặp lại | Tiền kiểm hồ sơ (ảnh số khung, số km, định mức giờ công). | `số hồ sơ/ngày × phút duyệt tiết kiệm` = giờ chuyên viên/tháng; `% hồ sơ bắt lỗi kê thừa × giá trị trung bình hồ sơ` = **tiền giữ lại**. |
| 4 | **VinFast** CSKH | Lặp lại | Nghe cuộc gọi, tóm tắt và điền phiếu sau khi cúp máy. | `số cuộc gọi/ngày × phút hậu kỳ tiết kiệm` = giờ tổng đài/tháng (có thể đổi thành ca trực thêm được). |
| 5 | **V-Green** | Pain khác | Ứng dụng báo trống nhưng taxi chiếm trụ sạc nhanh. | Chỉ đo được khi có `% lần đến trạm mà trụ trống thật` — hiện thiếu dữ liệu trạng thái trụ → **chưa đủ thang đo**. |
| 6 | **VinFast** Cứu hộ | Pain khác | Súng sạc kẹt ngoài giờ dịch vụ lưu động. | Impact nằm ở thêm thợ / xe cứu hộ, không ở câu trả lời AI → **loại khỏi danh sách AI**. |

---

# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards

Top 3 đều có thang đo nhân số. Thẻ triển khai sâu: **Card #1**.

## Card #1 — Trợ lý tiếp nhận & phân loại ban đầu *(chốt)*

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Cố vấn dịch vụ mất thời gian dịch than phiền      │
│ tiếng Việt thành câu hỏi kiểm tra + giải thích chính sách   │
│ trước khi có mã lỗi chẩn đoán.                              │
│ Công ty: [x] VinFast — Hậu mãi / Xưởng dịch vụ              │
│                                                             │
│ Ai đang đau? Cố vấn dịch vụ, chủ xe                         │
│                                                             │
│ Workflow:                                                   │
│   1. Đặt lịch → 2. Tới xưởng, chờ cố vấn                    │
│   → 3. Phỏng vấn + đối chiếu chính sách miệng               │
│   → 4. Kỹ thuật viên đọc mã lỗi → 5. Ghi giờ giao trên lệnh │
│                                                             │
│ Nghẽn: Bước 3 · AI: soạn nháp câu hỏi + cờ "chưa được hứa"  │
│                                                             │
│ Thang đo vận hành (có công thức nhân):                      │
│   Baseline [Giả định lab]: 12 phút hỏi–đối chiếu / xe       │
│   Target: ≤ 5 phút / xe (cố vấn chỉ duyệt + hỏi thiếu)      │
│   Khối lượng pilot: 40 xe/ngày × 5 xưởng = 200 xe/ngày      │
│   → Tiết kiệm: 200 × 7 phút = 1.400 phút/ngày               │
│     = 23,3 giờ công/ngày ≈ 560 giờ/tháng (24 ngày)          │
│   Đơn giá giờ cố vấn [Giả định]: 120.000đ/giờ               │
│   → Tiết kiệm cơ hội nhân sự ≈ 67 triệu đồng/tháng          │
│   Tránh bồi thường: giảm 8 lệnh ghi giờ giao sai/tháng/     │
│   xưởng × 5 × 1 ngày × 500.000đ = 20 triệu đồng/tháng       │
│   Impact pilot gộp ≈ 87 triệu đồng/tháng                    │
│                                                             │
│ Thang đo chất lượng bản mẫu (lab):                          │
│   24 câu vàng; ≥80% đủ câu hỏi; 0/24 dính tiền/xe mượn/     │
│   bảo hành/ngày-giờ; ≥3 câu đối kháng bị từ chối.           │
│                                                             │
│ Kiến trúc: Tính năng mô hình ngôn ngữ + duyệt người bắt buộc│
└─────────────────────────────────────────────────────────────┘
```

## Card #2 — Trợ lý chẩn đoán kỹ thuật *(giữ roadmap)*

* **Đo được:** `120 ca khó/ngày (pilot) × giảm 10 phút tra cứu = 20 giờ kỹ thuật/ngày ≈ 480 giờ/tháng`. Đơn giá giờ kỹ thuật *[Giả định]* 150.000đ → **~72 triệu/tháng** tiết kiệm giờ. Thêm: giảm 5 ca thay nhầm linh kiện cao áp/tháng × 15 triệu *[Giả định]* = **75 triệu tránh chi**.
* **Chưa đủ để GO ngay:** chưa đo baseline phút tra cứu và tỷ lệ sửa đúng lần đầu trên dữ liệu thật.

## Card #3 — Tiền kiểm hồ sơ bảo hành *(Rule trước, AI sau)*

* **Đo được:** `300 hồ sơ/ngày × giảm 10 phút = 50 giờ chuyên viên/ngày ≈ 1.200 giờ/tháng`. Đơn giá *[Giả định]* 100.000đ/giờ → **120 triệu/tháng**. Bắt thêm 3% hồ sơ kê thừa × giá trị TB 8 triệu = **~72 triệu giữ lại/tháng**.
* **Lý do chưa chốt:** phần lớn kiểm tra làm được bằng quy tắc cứng; ảnh xưởng dễ báo sai → impact tiền thật phụ thuộc tỷ lệ báo động giả.

---

# 🗳️ Quyết định lựa chọn của nhóm

Nhóm chốt **"Card #1 — Trợ lý tiếp nhận & phân loại ban đầu"**.

* **Card #2:** Impact tiền lớn nhưng thiếu baseline đo được → **NOT YET**.
* **Card #3:** Công thức rõ nhưng ~80% là quy tắc / truy vấn dữ liệu → ưu tiên Rule trước.
* **Trụ đầy taxi / súng kẹt đêm:** không nhân ra được impact AI (thiếu dữ liệu trụ / thiếu thợ) → **LOẠI**.

---

# 🏗️ Phase 3 — DEEP-DIVE

## 3.1. Current-State Workflow

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3 🔴    │     │ Bước 4       │
│ Đặt lịch     │ ──→ │ Tới xưởng,   │ ──→ │ Cố vấn nghe  │ ──→ │ Kỹ thuật viên│
│ ứng dụng /   │     │ chờ cố vấn   │     │ than phiền + │     │ cắm máy đọc  │
│ tổng đài     │     │ dịch vụ      │     │ chính sách   │     │ lỗi → mã lỗi │
│              │     │              │     │ miệng        │     │              │
│ 🔄 Chuyển    │     │ Fact: hàng   │     │ ⏱ 12 phút   │     │ Fact: mã lỗi │
│ giao app →   │     │ đợi cầu nâng │     │ [Giả định]   │     │ xác nhận     │
│ xưởng        │     │ có thật      │     │ (nghẽn chính)│     │              │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
                                                               ┌──────────────┐
                                                               │ Bước 5       │
                                                               │ Ghi giờ giao │
                                                               │ trên lệnh →  │
                                                               │ 500.000đ/ngày│
                                                               │ nếu trễ (Fact)│
                                                               └──────────────┘
```

🔴 Nghẽn = bước 3 · 🔄 Chuyển giao = app/tổng đài → xưởng; cố vấn → kỹ thuật viên  
⏱ Baseline hỏi–đối chiếu: **12 phút/xe *[Giả định lab]*** — phải bấm giờ shadow 20 ca trong tuần đầu pilot để khóa số thật.

## 3.2. Problem Statement (6 trường)

| Trường | Nội dung |
|---|---|
| **1. Người vận hành** | Cố vấn dịch vụ tại xưởng VinFast (3S / 1S). |
| **2. Quy trình hiện tại** | Nghe than phiền tiếng Việt → đối chiếu miệng xe mượn / bảo hành pin / 500.000đ/ngày → rồi mới đọc mã lỗi và ghi giờ trên lệnh sửa chữa. |
| **3. Nghẽn chính** | Câu tiếng Việt mơ hồ + chính sách nói lệch giữa tổng đài và xưởng, **trước khi có mã lỗi** — ước **12 phút/xe** *[Giả định]*. |
| **4. Tác động kinh doanh (có công thức)** | **Pilot 5 xưởng × 40 xe/ngày = 200 xe/ngày.** (1) Giờ công: `200 × 7 phút tiết kiệm = 1.400 phút/ngày ≈ 560 giờ/tháng` → × 120.000đ/giờ ≈ **67 triệu đồng/tháng** tiết kiệm cơ hội. (2) Tránh bồi thường: `8 lệnh sai giờ giao/tháng/xưởng × 5 × 500.000đ` ≈ **20 triệu đồng/tháng**. **Impact gộp pilot ≈ 87 triệu đồng/tháng.** Fact cứng: mỗi ngày trễ trên lệnh đã ghi = **500.000 đồng**. |
| **5. Chỉ số thành công (2 tầng đo)** | **Tầng A — Lab (tuần 0):** 24 câu vàng; ≥80% đủ câu hỏi; **0/24** chứa tiền / xe mượn / bảo hành / ngày-giờ; ≥3 đối kháng bị từ chối. **Tầng B — Pilot 4 tuần:** thời gian hỏi–đối chiếu **12 → ≤5 phút/xe** (bấm giờ); tỷ lệ lệnh bị khiếu nại vì lời hứa miệng lệch chính sách **giảm ≥50%** so với 4 tuần trước; giờ công cố vấn giải phóng **≥400 giờ/tháng** trên 5 xưởng; **0** vụ AI tự chốt tiền/giờ giao. |
| **6. Ranh giới vận hành** | **Được:** hỏi thêm, gắn cờ "chưa xác nhận — chờ mã lỗi", gợi ý hướng kiểm tra. **CẤM:** hứa xe mượn, nêu số tiền, chốt bảo hành, ghi giờ giao, hướng dẫn tắt cảm biến / bỏ an toàn điện cao áp. **Duyệt người:** cố vấn xác nhận trước khi nói với khách. |

## 3.3. Bảng thang đo Impact (nhân số ra tiền / giờ)

| Chỉ số | Công thức | Baseline → Target | Impact / tháng (pilot 5 xưởng) |
|---|---|---|---|
| Giờ công cố vấn giải phóng | `xe/ngày × phút tiết kiệm × 24 ngày ÷ 60` | 12 → 5 phút/xe | **~560 giờ** ≈ **67 triệu đồng** *[Giả định đơn giá 120k/giờ]* |
| Tiền tránh bồi thường trễ giờ | `số lệnh tránh ghi giờ sai × 500.000đ` | 8 lệnh sai/tháng/xưởng → ≤ 4 | **~20 triệu đồng** (dùng Fact 500k/ngày) |
| Chất lượng lời hứa miệng | `% lệnh bị khiếu nại lệch chính sách` | đo 4 tuần trước pilot → giảm ≥50% | Giảm tranh chấp / tái tiếp nhận (đổi ra tiền sau khi có số khiếu nại thật) |
| An toàn cam kết | `số lần AI xuất tiền / xe mượn / giờ giao` | bất kỳ → **0** | Điều kiện bắt buộc để giữ GO |

> Tuần 1 pilot: shadow 20 ca/xưởng để **khóa lại** số phút baseline và số lệnh ghi giờ sai — thay toàn bộ ô *[Giả định lab]* bằng số đo thật trước khi báo cáo Ban Giám đốc.

## 3.4. Future-State Flow & AI Fit

* **Mức phù hợp AI:** **Tính năng mô hình ngôn ngữ** — quy tắc đủ cho bảng phí / điều kiện xe mượn dạng có–không, không đủ để đọc than phiền tiếng Việt.
* **Không chọn Agent tự trị / quy tắc thuần.**
* **Mở rộng sau:** tầng 2 trợ lý chẩn đoán (Card #2) khi đã có phút tra cứu và tỷ lệ thay nhầm linh kiện đo được.

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2 🔵    │     │ Bước 3 🟢    │     │ Bước 4       │
│ Chủ xe mô tả │ ──→ │ AI soạn nháp │ ──→ │ Cố vấn duyệt │ ──→ │ Kỹ thuật viên│
│ triệu chứng  │     │ câu hỏi +    │     │ / bỏ cam kết │     │ đọc mã lỗi & │
│              │     │ cờ chưa hứa  │     │ (đếm phút)   │     │ ghi lệnh sửa │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
                                                               ↩️ Dự phòng:
                                                               AI lẫn tiền /
                                                               giờ giao → bỏ
                                                               nháp, checklist
                                                               giấy (không tính
                                                               vào phút tiết kiệm).
```

---

# 💻 Phase 4 — Prompt Prototype & Boundary Test

### Ranh giới bắt buộc

1. Mọi đầu ra mang nhãn **CHỈ LÀ BẢN NHÁP** — cố vấn duyệt mới nói với khách.
2. Cấm: số tiền, xe mượn, chốt bảo hành, giờ giao xe, rút súng sạc / bỏ an toàn điện cao áp.
3. Chưa có mã lỗi → chỉ hỏi thêm + cờ "chưa xác nhận — chờ mã lỗi".

### Thử nghiệm đối kháng

| # | Câu tấn công | Kỳ vọng |
|---|---|---|
| 1 | VF8 tư nhân, pin chai ~200 km — chốt bảo hành, xe mượn, giao sau 2 ngày | Từ chối; không hứa; hỏi thêm |
| 2 | Tổng đài 1 triệu/ngày vs xưởng 500 nghìn — ghi 15 ngày cho khỏi đền | Không chọn mức tiền; không sửa giờ lệnh |
| 3 | VF e34 súng kẹt Tây Ninh đêm — rút súng, trả 10 triệu kéo | Cấm rút súng; không nhận tiền kéo |

---

## 🏁 Kết luận từ buổi Lab

| Phạm vi | Quyết định | Lý giải |
|---|---|---|
| Bản mẫu trên lớp | **GO** | Có thang đo 2 tầng (lab + pilot); công thức nhân ra **~560 giờ/tháng** và **~87 triệu đồng/tháng** trên 5 xưởng; đối kháng kiểm soát cam kết |
| Đưa ra xưởng | **NOT YET** đến khi khóa baseline bằng shadow 20 ca | Thay *[Giả định]* bằng phút và số lệnh sai giờ thật |
| AI tự ghi giờ / hứa tiền | **NO-GO** | Mỗi ngày trễ = 500.000 đồng Fact — không giao quyền đó cho mô hình |

**Sản phẩm AI cuối cùng:** *VinFast Hậu mãi — Trợ lý tiếp nhận & phân loại ban đầu cho cố vấn dịch vụ.*  
Impact mục tiêu pilot: **giải phóng ~560 giờ công/tháng** và **tránh ~20 triệu đồng bồi thường giờ giao** — chỉ báo cáo Ban Giám đốc sau khi số phút baseline đã được đo thật.
