# Escalation ticket

## Ticket 1

- **Frame:** `adasind_199770.jpg`
- **Ảnh chụp:** `submission/screenshots/cvat_rework.png`
- **Expected impact:** Tránh tình trạng gán nhãn sai lệch (False Positive / False Negative) ở các vật thể nằm trên đường ranh giới chồng lấp (seam) giữa hai camera.
- **Owner:** `data_ops` / `ai_team`
- **Recommendation:** Thống nhất quy định gán nhãn độc lập trên từng camera đơn lẻ trước khi thực hiện ghép nối (stitching/tracking) ở tầng policy downstream.
