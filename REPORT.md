# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên VLearn. Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202602092
- Ngày / CVAT local: 17/09/2026
- Công cụ đã dùng: CVAT

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh VLearn đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | chưa có |0… / 1 | 3 |
| cp5_occlusion | chưa có | 0 / 1 | 3 |
| cp3_thin | chưa có | 0 / 1 | 3 |
| cp4_curb | chưa có | 0 / 1 | 3 |
| cp6_coverage | chưa có | 0 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: 000000181542.jpg, PERSON 20, 
- Class và quy tắc tôi dùng để chọn biên: class PERSON, tôi đã chọn biên bằng Mask/Brush. Cụ thể là brush 
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình. Không dùng; Quyết định gán nhãn vì guideline không yêu cầu gán Stuff, mà trong class list chỉ có danh sách các things, nên tôi quyết định gán things là PERSON đầu tiên vì object đếm được to nhất trên ảnh.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: Task medium/Ảnh 000000181542.jpg/MOTORCYCLE 11
- Lỗi thuộc loại: sai lớp / thiếu-thừa vật / gộp-tách / biên / phủ vùng / khác: Một vật hai mask
- Bằng chứng tôi nhìn thấy: Trong mask của MOTORCYCLE 11 lại có mask của MOTORCYCLE 1 đè lên
- Quy tắc và hành động sửa: Gộp mask của MOTORCYCLE 1 vào MOTORCYCLE 11
- Sau sửa đã Save và export lại chưa? …

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): … / chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| 1/000000181542.jpg/TRUCK 5 | Truck đang bị occluded bởi PERSON 28, vùng còn hiển thị hơi mơ hồ, không rõ ràng | Quy tắc vật thể chia đôi | Tiếp tục tô các vùng hiển thị mơ hồ, nối với cả mask chính. |
| 2/000000181542.jpg/BUS 30 | Bên trong BUS có người ngồi bên trong, rõ vùng hiển thị | Quy tắc khoét lỗ vật thể | Liệu khi nhìn rõ cả vật thể nằm bên trong vật thể thì mình có đánh mask khác cho vật thể nằm bên trong không? |
| 3/000000181542.jpg/MOTORCYCLE 13 | Chiếc xe máy bị occlude bởi 1 chiếc xe máy khác, có thể nhìn thấy đuôi xe và xác định được, nhưng bị che quá 80% |  Quy tắc  | Tiếp tục mask cho phần còn nhìn thấy của xe vì xác định được đó là xe máy do người ngồi trên và thuộc tính của xe. |
