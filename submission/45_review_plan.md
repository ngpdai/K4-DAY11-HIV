# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| `adasind_019560.jpg` (C0) | 6 ca (3 SPURIOUS, 1 IGNORE_SCOPE, 1 WRONG_CLASS) | Frame hiệu chuẩn C0 có nhiều lỗi nhầm lớp và vành kính | `findings.csv` (dòng 0-5), `submission/screenshots/terminal_check.png` |
| `adasind_199770.jpg` (B3-edge) | 12 ca (6 MISSING, 4 SPURIOUS, 2 BOX_GEOMETRY) | Frame ở vùng biên (edge) bị méo fisheye nặng gây sót box | `findings.csv` (dòng 10-20), `submission/screenshots/cvat_rework.png` |

Giới hạn của kết luận từ ba frame ADASIND: Số lượng 3 frame chưa đại diện đủ cho biến động ánh sáng, điều kiện thời tiết và toàn bộ 360 độ quanh xe (mới chỉ kiểm tra trên 1 góc nhìn camera).

## Chuyển sang kế hoạch bốn camera giả lập

Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv` (kể cả tránh đếm nhiều frame liền nhau trong cùng cảnh
như nhiều ca độc lập), và vì sao kế hoạch đó chỉ giúp tìm ca cần soi, chưa đo được tỷ lệ lỗi: Lấy mẫu phân tầng (Stratified Sampling) giãn cách time-step giữa các frame để tránh trùng lặp bối cảnh. Kế hoạch lấy mẫu giúp phát hiện các tình huống biên (edge cases) nhưng chưa đo được tỷ lệ lỗi tổng thể vì số lượng mẫu tập trung cố ý vào các ca khó (`hard` cases).
