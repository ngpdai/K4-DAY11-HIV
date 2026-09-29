# Guideline patch

- **Rule mới đề xuất:** Đối với toàn bộ ảnh Fisheye, mọi chi tiết thuộc vỏ xe / mui xe gắn camera (`ego_body`) lộ diện ở mép dưới ảnh bắt buộc phải vẽ Polygon và gán thuộc tính `ignore_region` (`ego_body=true`).
- **Áp dụng cho:** Tất cả các slice thuộc camera fisheye (đặc biệt vùng rìa dưới ảnh).
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** Quy tắc hiện tại chưa quy định rõ ranh giới giữa phần vành kính đen `lens_border` và thân xe `ego_body`, dẫn đến việc người gán nhãn thường bỏ sót mui xe hoặc nhầm lẫn với khu vực nền.
- **`rules_version` mới:** v1.1.0
- **Hiệu lực từ:** Round P5 (Rework) và áp dụng cho các lô dữ liệu Fisheye tiếp theo.
