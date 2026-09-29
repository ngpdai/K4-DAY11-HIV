# Đối chiếu chất lượng cục bộ — rectangle

Teaching reference, không phải gold set đã phê duyệt; không có điểm đạt tự động.
Nguồn: export r1_craft đã khóa SHA256 `36000e2133bd85b2d881daba3de5d517b64e2e86c85cfe8ebaa0aa4f91f7f49f`; slice `B3-edge`.
Ghép hình học greedy một-một theo IoU ≥ 0.50, rồi so class; H ≥ 40 px.
Box trái nằm chủ yếu trong ignore_region reference không tính. Polygon, polyline, track không được chấm.
Đây là phép tính offline của lab, không phải báo cáo hay kết quả tương đương CVAT Premium.

Frame được tính: adasind_123090.jpg, adasind_128310.jpg, adasind_199770.jpg. Frame thiếu trong export: không.
TP=9; FP=8; FN=8; số lần đối chiếu=23; mean IoU của TP=0.834.

| Chỉ số | Micro | Macro | Nhãn thấp nhất |
|---|---:|---:|---:|
| accuracy | 0.391 | 0.884 | 0.783 |
| precision | 0.529 | 0.556 | 0.000 |
| recall | 0.529 | 0.472 | 0.000 |
| jaccard | 0.360 | 0.331 | 0.000 |
| dice | 0.529 | 0.454 | 0.000 |

| Nhãn | TP | FP | FN | Accuracy | Precision | Recall | Jaccard | Dice |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Bike | 1 | 2 | 3 | 0.783 | 0.333 | 0.250 | 0.167 | 0.286 |
| Bus | 0 | 1 | 0 | 0.957 | 0.000 | 0.000 | 0.000 | 0.000 |
| Car | 3 | 3 | 0 | 0.870 | 0.500 | 1.000 | 0.500 | 0.667 |
| Pedestrian | 2 | 2 | 1 | 0.870 | 0.500 | 0.667 | 0.400 | 0.571 |
| ThreeWheeler | 2 | 0 | 1 | 0.957 | 1.000 | 0.667 | 0.667 | 0.800 |
| Truck | 1 | 0 | 3 | 0.870 | 1.000 | 0.250 | 0.250 | 0.400 |

| Frame | TP | FP | FN | Accuracy | Precision | Recall |
|---|---:|---:|---:|---:|---:|---:|
| adasind_123090.jpg | 2 | 2 | 1 | 0.500 | 0.500 | 0.667 |
| adasind_128310.jpg | 3 | 1 | 2 | 0.600 | 0.750 | 0.600 |
| adasind_199770.jpg | 4 | 5 | 5 | 0.286 | 0.444 | 0.444 |

Confusion matrix: hàng = teaching reference; cột = export đã khóa.
`<missing>` là thiếu box; `<extra>` là box thừa. Xem `local_quality_confusion.csv`.

| Reference \ Export | Bike | Bus | Car | Pedestrian | ThreeWheeler | Truck | <missing> |
|---|---:|---:|---:|---:|---:|---:|---:|
| Bike | 1 | 0 | 0 | 0 | 0 | 0 | 3 |
| Bus | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| Car | 0 | 0 | 3 | 0 | 0 | 0 | 0 |
| Pedestrian | 0 | 0 | 0 | 2 | 0 | 0 | 1 |
| ThreeWheeler | 0 | 0 | 0 | 0 | 2 | 0 | 1 |
| Truck | 0 | 1 | 1 | 0 | 0 | 1 | 1 |
| <extra> | 2 | 0 | 2 | 2 | 0 | 0 | 0 |

Chi tiết xung đột trong `local_quality_conflicts.csv`; dữ liệu máy đọc trong `local_quality.json`.
Mismatching label đóng góp một FP cho class vẽ và một FN cho class reference; attribute khác được báo riêng.
Micro accuracy đếm mỗi cặp ghép sai class là một lần đối chiếu; Jaccard đếm cả FP và FN.
Macro/worst bỏ nhãn không xuất hiện ở cả hai phía; chỉ số không có mẫu là N/A.
