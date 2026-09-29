# Exit ticket

Đọc `docs/10-svm360-reading-vi.md` trước khi trả lời câu 1–2. Các câu về zone, `why`, rework, parking và sampling
đã nằm trong file tương ứng nên không hỏi lại ở đây.

1. Một vật ở vùng seam giữa hai camera thật xuất hiện với hai box khác nhau: đó là lỗi `DUPLICATE` hay cần một quy
   tắc riêng? Vì sao? Cần một quy tắc riêng. Vì ở tầng camera đơn lẻ (2D perception), mỗi camera ghi nhận hình ảnh độc lập theo góc nhìn thấu kính đó; không tự ý gộp hai box hoặc gán trùng Track ID khi chưa có dữ liệu calibration 3D và policy ghép nối ở hệ thống BEV/SVM downstream.
2. Một vật đi qua nhiều frame trên cùng camera: khi nào giữ cùng track ID, khi nào thêm keyframe hoặc trạng thái
   Outside? Giữ cùng Track ID khi vật thể di chuyển liên tục và quan sát rõ. Thêm trạng thái Outside/Keyframe khi vật thể bị che khuất hoàn toàn hoặc đi ra khỏi vùng quan sát của camera trước khi quay lại. Cần có bằng chứng đồng bộ timestamp và chuyển giao vị trí không gian trước khi nối track qua hai camera khác nhau.
3. Nhìn lại cả buổi: một chỗ bạn tin nhãn mình đúng nhưng reference hoặc người soát nghĩ khác (dẫn frame/`object_ref`),
   bạn đã xử lý thế nào, và nếu làm lại slice này bạn sẽ đổi gì trong cách làm? Ở frame `adasind_199770.jpg` vật thể `R4` ở xa rìa kính, tôi cho là vật thể quá mờ nên không vẽ, nhưng reference vẫn gán nhãn `Car`. Tôi đã đối chiếu quy tắc độ phân giải tối thiểu và chấp nhận bổ sung box ở đợt Rework. Nếu làm lại, tôi sẽ soi kỹ vùng biên và tham chiếu trước bảng phân loại ca khó (`taxonomy`).
