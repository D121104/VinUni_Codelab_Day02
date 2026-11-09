# 📝 Phase 6 — REFLECTION

**Bài toán nhóm lựa chọn:** Card #05 — Vinhomes: Phân loại và điều phối lead từ website, quảng cáo và sự kiện đến nhân viên Sales phù hợp.

## 1. Nhóm đã sử dụng AI vào những công việc gì?

Trong buổi lab, nhóm sử dụng AI như một công cụ hỗ trợ phân tích và phản biện, không coi nội dung do AI tạo ra là bằng chứng về hoạt động nội bộ doanh nghiệp.

| Giai đoạn | AI đã hỗ trợ | Phần tôi/nhóm cần tự quyết định |
|---|---|---|
| **Phase 1 — SCAN** | Gợi ý các điểm nghẽn vận hành và diễn đạt bài toán theo 4 góc nhìn: lặp lại, tốn thời gian, AI có thể làm tốt hơn, pain từ người khác. | Chọn và chỉnh sửa các pain point phù hợp, tránh khẳng định giả thuyết là sự thật. |
| **Phase 2 — QUICK-ASSESS** | Chuẩn hóa các thẻ bài toán về actor, workflow, bottleneck, metric và hướng công nghệ; đưa ra câu hỏi phản biện. | Cùng nhóm lựa chọn **Card #05 — Vinhomes điều phối lead** để phân tích sâu. |
| **Phase 3 — DEEP-DIVE** | Hỗ trợ phác thảo luồng hiện tại/tương lai, xác định điểm chuyển giao, đề xuất Rule Engine kết hợp mô hình ngôn ngữ và cơ chế nhân viên duyệt. | Xác định ranh giới hệ thống và xem xét khả năng thu thập dữ liệu, đo hiệu quả thực tế. |
| **Phase 5 — EVALUATE** | Hỗ trợ quy đổi giả định giờ công thành đồng/tháng, xây dựng checklist và tiêu chí GO/NOT YET/NO-GO. | Không chấp nhận các con số mô phỏng như ROI thực tế; giữ kết luận **NOT YET** đối với tích hợp vận hành. |

## 2. AI giúp ích nhiều nhất ở đâu?

AI giúp tôi chuyển một ý tưởng ban đầu khá rộng — “điều phối lead hiệu quả hơn” — thành một bài toán có đầu vào, đầu ra và giới hạn rõ ràng: đọc thông tin khách hàng từ nhiều kênh, nhận diện nhu cầu, phát hiện hồ sơ cần rà soát và **đề xuất** nhóm Sales phù hợp. AI cũng giúp tôi nhìn thấy sự khác nhau giữa bước cần hiểu ngôn ngữ tự nhiên và bước chỉ cần áp dụng quy tắc phân công.

Điểm hữu ích nhất là quá trình **challenge**: đặt câu hỏi liệu một hệ thống quản lý quan hệ khách hàng (CRM) kết hợp quy tắc có thể xử lý tốt hơn mô hình ngôn ngữ hay không. Nhờ đó, đề xuất cuối không mặc định phải dùng Agent tự trị; giải pháp phù hợp hơn là **Rule Engine + LLM Feature + nhân viên phê duyệt**, với phương án quay về xử lý thủ công khi thiếu dữ liệu hoặc mô hình không chắc chắn.

## 3. AI có hạn chế hoặc dễ khiến tôi hiểu sai ở đâu?

- **Dễ tạo số liệu có vẻ thuyết phục nhưng chưa được đo:** Ví dụ 100 lead/ngày, 10 phút thao tác/lead, tiết kiệm 5 phút/lead và 3 triệu đồng/tháng chi phí AI đều là **[Giả định lab]**, không phải số liệu Vinhomes xác nhận.
- **Dễ đề xuất kiến trúc quá phức tạp:** Không phải mọi bước phân tuyến đều cần mô hình ngôn ngữ hoặc AI Agent. Các điều kiện về khu vực, dự án, quyền nhận lead và tải công việc nên được thực thi bằng quy tắc rõ ràng.
- **Không thể xác minh quy trình nội bộ chỉ bằng suy luận:** AI chưa chứng minh rằng quy trình phân loại lead hiện tại ở Vinhomes chủ yếu làm thủ công, hoặc rằng các nguồn lead đang bị thất lạc. Phải khảo sát người vận hành và đối chiếu nhật ký hệ thống.
- **Không bảo đảm tính chính xác khi tự động hóa:** Mô hình có thể suy đoán ngân sách, ưu đãi hoặc thông tin khách hàng không có trong đầu vào. Cần giới hạn quyền và yêu cầu duyệt ở các bước nhạy cảm.

## 4. Nhóm đã kiểm soát và phản biện đầu ra AI như thế nào?

Nhóm sử dụng ba nguyên tắc khi hoàn thiện bài toán:

1. **Fact khác giả định:** Mọi giá trị chưa đo được gắn nhãn **[Giả định lab]**, không gọi là tổn thất hay hiệu quả thực tế của doanh nghiệp.
2. **So sánh với giải pháp không dùng AI:** Phải có baseline từ form chuẩn hóa, quy tắc phân tuyến và kiểm tra trùng trước khi kết luận mô hình ngôn ngữ tạo thêm giá trị.
3. **Giữ người chịu trách nhiệm ở bước quyết định:** AI được phân tích nội dung và đề xuất; không được tự hứa giá/ưu đãi, bịa thông tin khách hàng, tự phân quyền hoặc thực hiện hành động ngoài quyền truy cập.

Trong phần phân tích kinh tế, kịch bản lab giả định **100 lead/ngày × 5 phút tiết kiệm × 26 ngày ÷ 60 = 216,67 giờ/tháng**. Với **120.000đ/giờ**, công suất nhân sự quy đổi khoảng **26 triệu đồng/tháng**; trừ **3 triệu đồng/tháng** chi phí AI giả định, được **23 triệu đồng/tháng**. Đây là **giá trị công suất mô phỏng sau chi phí AI**, không phải khoản tiết kiệm tiền mặt đã xác minh. Không cộng doanh thu tăng thêm khi chưa có bằng chứng cải thiện tỷ lệ chuyển đổi.

## 5. Kết luận

AI là **người hỗ trợ brainstorm, cấu trúc hóa và phản biện**, không thay thế việc khảo sát thực tế hay quyết định của nhóm. Nhóm chọn tiếp tục nghiên cứu **Card #05 — Vinhomes điều phối lead**, nhưng đánh giá trạng thái hiện tại là **NOT YET cho tích hợp thực tế** vì chưa đủ dữ liệu xác minh baseline và lợi ích tăng thêm so với rule-based. Hướng phù hợp là thử nghiệm prototype offline với dữ liệu giả lập/đã ẩn danh trước, rồi mới cân nhắc pilot có kiểm soát.

