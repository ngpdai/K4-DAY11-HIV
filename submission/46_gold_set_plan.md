# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide,
**không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có
normal và hard slice. “Gold set” ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference
ADASIND hoặc nhãn bạn vừa vẽ. Nếu cần, dùng `notebooks/day11-svm360-colab.ipynb` để thử tổng phân bổ; notebook
không làm thay phần lý do.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Đèn pha ngược sáng, xe cắt ngang | Méo rìa ống kính, lóa sáng đêm | 2D Bounding Box + Lens border ignore | Dual annotation + Lead Review |
| rear | Xe bám sát đuôi, che khuất một phần | Khoảng cách quá gần làm biến dạng góc nhìn | 2D Bounding Box + Ego body ignore | Cross-reviewer QA |
| left | Vạch kẻ ô đỗ khuất bóng râm, mép lề đường | Nhầm lẫn giữa vạch ô đỗ và lối đi | Parking line + Ignore region | Expert Arbitration |
| right | Vùng chồng lấp góc (seam zone) | Độ cong fisheye lớn, góc mù | 2D Bounding Box + Seam area tag | Dual annotation + Expert Review |

- Khi nào cần refresh gold set (đổi camera, calibration hoặc rule): Khi có sự thay đổi về phần cứng camera, góc lắp đặt (calibration), hoặc khi ban hành version quy tắc gán nhãn mới.
- Một ca seam/cross-camera cần policy và evidence trước khi ghép hai box: Cần có timestamps đồng bộ, thông số calibration chuẩn xác và logic phân định vùng đè lấp trước khi gộp 2 box thành 1 Track ID.
- Vì sao peer agreement hoặc quality report trên ảnh một camera chưa chứng minh gold set đúng cho cả bốn camera: Đánh giá trên 1 camera không phản ánh được các lỗi liên camera như lệch góc nhìn, sai khác độ sáng/màu sắc giữa các thấu kính và lỗi ở vùng chồng lấp (seams).
