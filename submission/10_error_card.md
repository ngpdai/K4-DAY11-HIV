# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B3 | BOX_GEOMETRY | 1 |
| center | B3 | MISSING | 2 |
| center | B3 | SPURIOUS | 9 |
| center | C0 | SPURIOUS | 3 |
| edge | B3 | ATTRIBUTE | 1 |
| edge | B3 | BOX_GEOMETRY | 1 |
| edge | B3 | IGNORE_SCOPE | 1 |
| edge | B3 | MISSING | 5 |
| edge | B3 | SPURIOUS | 4 |
| edge | B3 | WRONG_CLASS | 1 |
| edge | C0 | IGNORE_SCOPE | 1 |
| edge | C0 | SPURIOUS | 1 |
| edge | C0 | WRONG_CLASS | 1 |
| mid | B3 | IGNORE_SCOPE | 1 |
| mid | B3 | MISSING | 8 |
| mid | B3 | SPURIOUS | 8 |
| mid | B3 | WRONG_CLASS | 1 |

## Top defects
- SPURIOUS: 25 (ví dụ frame adasind_019560.jpg)
- MISSING: 15 (ví dụ frame adasind_128310.jpg)
- IGNORE_SCOPE: 3 (ví dụ frame adasind_019560.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: Tỷ lệ lỗi SPURIOUS (25 ca) và MISSING (15 ca) tập trung nhiều ở vùng `edge` và `mid` do hiệu ứng độ cong của thấu kính fisheye làm méo tỷ lệ vật thể ở góc nhìn biên. Đối với các lỗi `IGNORE_SCOPE` (3 ca ở frame adasind_019560.jpg), nguyên nhân là do gán nhãn trùng vào vùng vành kính `lens_border` hoặc bỏ sót phần mui xe `ego_body`.
- Cách sửa và ai nhận việc (`owner`): 
  - `human` (Annotator): Thực hiện rework gán bổ sung các box bị thiếu (`MISSING`) và xóa các box thừa (`SPURIOUS`) ở khu vực biên.
  - `guideline` / `data_ops`: Bổ sung hướng dẫn cắt viền gán nhãn sát vạch phân phân ranh giới vành kính.
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): Frame `adasind_019560.jpg` dòng 0-3 trong `findings.csv`, tuân thủ quy tắcignore region tại `docs/02-rules-vi.md`.
