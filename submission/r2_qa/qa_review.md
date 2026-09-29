# Peer QA Review Report (P3)

## 1. Tổng quan Đánh giá
* **Người thực hiện Review:** QA Reviewer
* **Trạng thái chung:** Cần Rework
* **Mức độ hoàn thiện:** Chưa đạt yêu cầu bắt buộc về vùng ignore (`ego_body`).

---

## 2. Các Lỗi Nhận xét & Phát hiện Chi tiết

### Lỗi Nghiêm trọng (Critical / Blocker)
* **Thiếu gán nhãn Mui xe (`ego_body`):** 
  * Phát hiện cả **3/3 frame** trong slice đều **quên chưa vẽ phần mui xe / vỏ xe** (vùng ego vehicle).
  * Đối tượng đã vẽ: Đã gán nhãn đầy đủ các đối tượng di động như `Car`, `Bike`, `Pedestrian`... và có sẵn vành kính `lens_border`.
  * Tuy nhiên, hoàn toàn **chưa có bất kỳ đa giác (Polygon)** nào được tạo cho vùng `ego_body`.

---

## 3. Hướng dẫn & Hành động Cần Rework cho Cặp tác giả

1. **Gán bổ sung `ego_body` trên CVAT:**
   * Mở lại 3 bức ảnh thuộc Slice trên CVAT.
   * Quan sát vùng mép dưới ảnh (nơi xuất hiện phần mui/vỏ xe gắn camera).
   * Dùng công cụ **Polygon** khoanh trọn vùng vỏ xe đó.
   * Chọn nhãn / thuộc tính: **`ignore_region`** với lý do/attribute là **`ego_body`**.

2. **Đối chiếu chi tiết Bounding Box với Đáp án Chuẩn (P4):**
   * Để kiểm tra kích thước các khung xe (`Car`, `Bike`, `Pedestrian`...) đã vẽ có bị hẹp/rộng hay sai nhãn hay không, hãy chạy 2 lệnh sau tại Terminal:
     ```bash
     python lab11.py reference r1_craft
     python lab11.py compare r1_craft
     ```
   * Sau khi chạy lệnh 2, hệ thống sẽ tự động so sánh từng pixel với reference và xuất danh sách lỗi chi tiết vào file `submission/findings.csv`. 
   * Mở file `submission/findings.csv` để rà soát toàn bộ các box cần chỉnh sửa.