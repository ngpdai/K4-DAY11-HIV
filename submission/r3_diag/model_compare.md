# L / R / M

L/R/M là thứ tự box in-scope theo XML của từng frame.

## adasind_123090.jpg
- L1+R1+M1: LRM (center)
- L4+R3+M4: LRM (mid)
- L2: L_only (mid)
- L3: L_only (edge)
- R2+M2: RM_noL (edge)
- M3: M_only (mid)
- M6: M_only (mid)
## adasind_128310.jpg
- L1+R4+M6: LRM (center)
- L2+R2+M1: LRM (edge)
- L4+R1+M2: LRM (center)
- L3: L_only (mid)
- R3+M3: RM_noL (mid)
- R5: R_only (mid)
- M4: M_only (center)
## adasind_199770.jpg
- L7+R1+M1: LRM (center)
- L6+R7: LR_noM (mid)
- L3+R2: LR_noM (edge)
- L2+R8: LR_noM (center)
- L1: L_only (center)
- L4+M3: LM_noR (center)
- L5+M5: LM_noR (edge)
- L8: L_only (center)
- L9+M9: LM_noR (mid)
- R3+M10: RM_noL (mid)
- R4: R_only (mid)
- R5: R_only (edge)
- R6: R_only (edge)
- R9: R_only (center)
- M4: M_only (edge)
- M6: M_only (mid)
- M8: M_only (edge)
- M11: M_only (center)
- M12: M_only (center)
- M13: M_only (center)

## Zone × cell
| zone | LRM | LR_noM | LM_noR | L_only | RM_noL | R_only | M_only |
|---|---|---|---|---|---|---|---|
| center | 4 | 1 | 1 | 2 | 0 | 1 | 4 |
| mid | 1 | 1 | 1 | 2 | 2 | 2 | 3 |
| edge | 1 | 1 | 1 | 1 | 1 | 2 | 2 |
