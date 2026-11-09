# 03 — AI Reflection Log (Lab 02 / gate I3)

**Tác giả:** Lê Thanh Hà  
**Lab:** AI Product Scoping — VinFast Aftersales  
**Công cụ:** Cursor agents + 2 file research dump + merge vào `VinFast-AI-Product-Final.md`

---

## 1. Bối cảnh buổi lab & tool AI đã dùng

Lab 02 yêu cầu chọn **một** bài toán AI hẹp cho VinFast Hậu mãi / xưởng dịch vụ, có thang đo và ranh giới an toàn — không làm slide “AI sẽ cứu cả chuỗi”.

Tôi dùng Cursor agents theo 3 vòng (file nằm cùng workspace):

1. **`Argon Research.md`** — dump rộng: 8 bài toán × 4 lenses, top card là Diagnostic Co-pilot (RAG Shop Manual / DTC), kèm warranty pre-audit và CSKH ticket. Giọng “Senior AI PE”, impact to, kiến trúc nặng (Multimodal RAG, FTFR, citation groundedness).
2. **`Curso-research.md`** — dump đối chiếu BYD/Tesla + stress-test kiểu CFO/Head of Aftersales. Thu hẹp mạnh: chỉ triage lời nói trước mã lỗi; **KILL** trụ đầy taxi và súng kẹt đêm; tách Fact (500k/ngày, 24h phụ tùng, 350 xưởng) khỏi giai thoại Ocean Park / trụ đầy.
3. **`VinFast-AI-Product-Final.md`** — merge: Card #1 = tiếp nhận trước DTC; thước A/B/C/D chung mọi mảng; gói debate 5 phút; Fact vs *[Giả định lab]*; kill criteria viết sẵn.

AI không “làm hộ bài” một phát. Nó cho hai cực: tham vọng và dao cắt. Việc của tôi là chọn cực nào được mang vào nộp — và viết lại bằng tiếng teammate hiểu.

---

## 2. AI giúp gì (có ví dụ cụ thể)

- **Hai research dump song song:** Argon mở không gian (chẩn đoán RAG, bảo hành Vision, CSKH ASR); Curso ép phải trả lời “CFO sẽ hỏi gì” — nhờ đó tôi có cả longlist lẫn lý do giết card (trụ taxi, súng kẹt đêm).
- **Chốt Card #1 đúng chỗ đồng hồ tiền:** AI (vòng Curso + final) đẩy pain từ “KTV thiếu sổ tay” sang **lời nói trước mã lỗi** — vì lệnh đã ghi giờ = Fact **500.000đ/ngày** nếu trễ. Đó là insight tôi giữ thay vì RAG toàn Shop Manual.
- **Thang A/B/C/D thống nhất:** final doc quy mọi mảng về giờ công / tránh chi / mở khóa / chi phí AI. So Card #1 (~87tr) / #2 (~147tr giả định) / #3 (~192tr giả định) không còn kiểu “FTFR vs ACW vs tỷ lệ bắt lỗi” lệch đơn vị.
- **Debate kit & wording presentation:** pitch 30 giây, bảng đáp teammate (“#3 gần 200 triệu sao không làm?” → Rule-first), kill criteria, output mẫu 1 ca VF8 tụt pin — agent soạn khung; tôi giữ giọng tranh luận thật.
- **Làm rõ chính sách xe mượn:** Curso/final nhấn xe mượn **không luôn có** — gắn chủ yếu lỗi pin/e-motor; không phải pin/máy thì thường không; pin loan / taxi voucher / 500k/ngày là lớp chính sách riêng, AI **không được** gộp thành “có xe mượn”.
- **Đơn giản hóa jargon:** “than phiền tiếng Việt” / “triage no_promise” trong slide dễ làm teammate ngơ → đổi thành **“khách kể triệu chứng bằng lời thường”** + cờ **“chưa xác nhận — chờ mã lỗi”**. Cùng ý, người ngoài lab hiểu được.
- **HITL + adversarial sẵn:** 3 câu tấn công (chai pin + xe mượn + ETA; tổng đài 1tr vs xưởng 500k; rút súng Tây Ninh) — AI draft kỳ vọng từ chối; tôi dùng làm gate lab thay vì tin “model sẽ biết đúng”.

---

## 3. AI sai / hallucination / thiên lệch ở đâu

- **Vanity metrics kiểu Argon:** 25 → 7 phút tra cứu, FTFR 78% → 92%, Citation ≥98% — số đẹp, không có baseline đo. Curso cũng từng có “20 → 8 phút” rồi tự gạch vì assumption. Nếu copy nguyên Argon vào nộp là bị trừ điểm ngay.
- **Over-claim xe mượn:** dump sớm dễ viết như xe mượn luôn sẵn khi khách than. Fact/stress-test: hết xe là chuyện thường; ca Tây Ninh (không pin/máy) = không xe mượn. AI “hứa xe mượn” = phá boundary và mở rủi ro tiền — lẫn với pin loan / taxi voucher / 500k/ngày.
- **Inflate impact qua ô C:** nếu cộng “công suất xe thêm / ngày” khi chưa đo throughput thật → Impact tháng phình ảo. Final phải ghi **C = 0** công khai; chỉ claim A (phút hỏi) + B (lời hứa sai → 500k).
- **Jargon / viết tắt dày:** DTC, RO, ACW, Multimodal RAG, Structured Diagnostic Synthesis… nghe “đúng nghề” nhưng teammate không vận hành xưởng sẽ không tranh luận được nội dung — chỉ tranh luận từ. Thiên lệch của model: ưu tiên formal product language hơn tiếng người dùng.
- **So sánh hãng lệch ngữ cảnh:** kiểu “VinFast giống BYD Hàn / Tesla đô thị → LLM kéo thời gian nằm xưởng” — Curso đã gọi thẳng là câu bị trừ điểm. BYD chết đồng sơn/phụ tùng; Tesla chết lịch/pin HV; VinFast VN đã dày xưởng + 24h phụ tùng. AI hay ghép narrative cho “đẹp slide”.

---

## 4. Tôi đã sửa prompt / scope / ranh giới thế nào

- **Thu hẹp scope:** từ Diagnostic RAG + nhiều card → **pre-code intake** thôi: soạn nháp câu hỏi + cờ chưa được hứa. Card #2/#3 giữ roadmap / Rule-first, không GO cùng lúc.
- **Prompt boundary cứng:** mọi output = **CHỈ LÀ BẢN NHÁP**; cấm số tiền, xe mượn, chốt bảo hành, giờ giao, hướng dẫn rút súng / bỏ an toàn HV. HITL: cố vấn duyệt trước khi nói với khách.
- **Fact vs [Giả định lab]:** 500k/ngày = Fact; 12 phút hỏi, 40 xe/ngày, 120kđ/giờ = giả định — tuần 1 shadow 20 ca mới khóa.
- **C = 0 until proven:** không bán story “rút tiếp nhận → thêm xe/ngày” khi chưa có số; hàng đợi cầu nâng AI không sửa — Curso đã chỉ rõ.
- **Kill criteria viết trước debate:** A chết nếu hỏi sẵn < 5 phút; B yếu nếu gần như không có khiếu nại lệch lời hứa; >0/24 câu lọt tiền/xe mượn → NO-GO shape production; cố vấn từ chối vì gõ thêm >30s/ca → dừng.
- **Problem statement plain-language:** bỏ “Diagnostic Co-pilot / FTFR”; nói thẳng cố vấn mất thời gian dịch lời thường + chính sách miệng trước khi KTV cắm máy.
- **Sửa cách hỏi agent:** từ “viết product card impact cao” → “stress-test như CFO, giết metric ảo, chỉ giữ LLM-fit + Fact tiền cứng”. Prompt khác → dump khác.

---

## 5. Bài học cho lần scoping sau

1. **Hai dump tốt hơn một dump “hoàn hảo”.** Một agent tham vọng (Argon) + một agent CFO-harsh (Curso) nhanh hơn tự chỉnh một file dài; merge có chủ đích mới là sản phẩm — không phải chọn dump nào “nghe hay hơn”.
2. **Số không gắn Fact thì gắn nhãn giả định — hoặc giết metric.** Vanity (25→7 phút, FTFR, % hài lòng) làm pitch đẹp và làm pilot chết khi CFO hỏi “đo ở đâu?”.
3. **Ranh giới tiền / giờ / xe mượn viết trước demo.** Nếu AI được hứa những thứ đó, bài toán không còn là prototype — là nợ vận hành (mỗi ngày trễ trên lệnh = 500k Fact).

Ghi nhớ nhanh khi mở agent lần sau: hỏi *“metric nào là Fact, card nào Rule đủ, AI sai một lần ai trả tiền?”* trước khi hỏi *“impact bao nhiêu triệu?”*.

---

## 6. Trạng thái quyết định hiện tại

| Phạm vi | Quyết định |
|---|---|
| Prototype trên lớp (24 câu vàng, ≥80% đủ câu hỏi, 0/24 dính tiền–xe mượn–BH–giờ) | **GO** |
| Đưa ra xưởng thật | **NOT YET** — chờ shadow 20 ca khóa A/B, thay *[Giả định lab]* |
| AI được quyền hứa tiền / giờ giao / xe mượn / bảo hành | **NO-GO** |

**Sản phẩm chốt:** Trợ lý tiếp nhận & phân loại ban đầu cho cố vấn dịch vụ — trước mã lỗi chẩn đoán.  
Impact pilot trên giấy ≈ 560 giờ + 20 triệu tránh bồi thường ≈ 87 triệu/tháng − D — **chỉ báo cáo CFO sau khi phút baseline đo thật**.

AI đã giúp tôi **mở rộng rồi cắt**; phần tôi không ủy thác là quyết định GO hẹp và chấp nhận C = 0.

*— Hết log Lab 02 / gate I3.*
