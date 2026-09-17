# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202602142
- Ngày / CVAT local: 17/9/2026
- Công cụ đã dùng: Brush / Polygon

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: ảnh `medium_instance`, khu vực xe ở giữa phía dưới ảnh; object đầu tiên là một chiếc xe.
- Class và quy tắc tôi dùng để chọn biên: class là `car`; tôi dừng mask ở mép thân xe, không kéo sang vùng nền, và khi không chắc giữa `motorcycle` và `car`, tôi ưu tiên `car` nếu thân xe lớn hơn và hình dáng giống ô tô rõ hơn. Nếu không xác định được, tôi dùng quy tắc: người chân người, xe chân xe.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: không dùng; tôi vẫn kiểm lại class theo quy tắc: `person` chỉ vẽ người, `car` chỉ vẽ xe, không gộp nhầm giữa người và xe hay giữa `motorcycle` và `car`.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `medium_instance`, một vùng có nhiều vật gần nhau; lỗi là nhầm nhãn giữa `motorcycle` và `car`.
- Lỗi thuộc loại: sai lớp / thiếu-thừa vật / gộp-tách / biên / phủ vùng / khác: sai lớp.
- Bằng chứng tôi nhìn thấy: thân xe lớn, hình dạng giống ô tô hơn, trong khi `motorcycle` có kích thước nhỏ và mảnh hơn; một số vùng bị gán nhầm vì độ gần và bóng đổ.
- Quy tắc và hành động sửa: tôi dùng quy tắc `nguoi chan nguoi`, `xe chan xe`, tức người được gán theo thân người, xe theo thân xe, không gán theo chuyển động hay bóng. Tôi sửa lại mask cho đúng class, rồi Save và export lại.
- Sau sửa đã Save và export lại chưa? Đã Save và export lại.

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): … / chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| 1 | Vùng người phía trước có thể là `person` hoặc bị nhầm với nền/đồ vật | `nguoi chan nguoi`: chỉ vẽ phần thân người, mép áo và chân rõ ràng, không kéo nền. | Quyết định chọn `person` vì có hình thái cơ thể rõ; nếu không chắc thì hỏi coach. |
| 2 | Một vật xe có thể là `motorcycle` hoặc `car` | `xe chan xe`: xét tỷ lệ thân xe và kích thước, `motorcycle` nhỏ hơn, `car` lớn hơn và rộng hơn. | Quyết định chọn `car` khi hình dạng và kích thước phù hợp; nếu không chắc, cần coach kiểm tra. |
| 3 | Vùng gần nhau có thể bị gộp thành một instance hoặc tách thành nhiều vật | Dùng ranh giới vật rõ nhất, không cộng thêm vùng che khuất hoặc bóng. | Quyết định tách theo từng thân xe/người, giữ biên ở mép nhìn thấy, không đoán sau vật che. |
