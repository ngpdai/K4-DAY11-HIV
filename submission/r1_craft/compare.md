# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_123090.jpg
- L2 mid SPURIOUS
- L3+R2 edge WRONG_CLASS
## adasind_128310.jpg
- L3+R3 mid WRONG_CLASS
- R5 mid MISSING
## adasind_199770.jpg
- L10 edge IGNORE_SCOPE
- L11 mid IGNORE_SCOPE
- L3+R2 edge ATTRIBUTE
- L1 center SPURIOUS
- L4+R9 center BOX_GEOMETRY
- L5+R5 edge BOX_GEOMETRY
- L8 center SPURIOUS
- L9 mid SPURIOUS
- R3 mid MISSING
- R4 mid MISSING
- R6 edge MISSING

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 6 | 5 | 1 | 3 |
| mid | 6 | 2 | 4 | 3 |
| edge | 5 | 2 | 3 | 2 |
