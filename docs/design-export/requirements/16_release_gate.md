# 16_驗收_Release_Gate

> Exported from `docs/PTC_Mask_Transfer_4Axis_Design_Draft.xlsx`.

| 項目 |  |  |  |
| --- | --- | --- | --- |
| PLC/HMI設計文件 | PASS_TO_CODING | 已整合審查P0/P1主要問題，可作Coding依據。 | 依本表Coding，不再沿用舊衝突點位。 |
| 2軸流程 | PASS | X橫移/X升降正反向、初始化、異常復歸已定義。 | 單機測試D441x/D443x。 |
| Z升降+Barcode | 可Coding | 流程完整但SR-2000W通訊未實測。 | 確認字串長度、Byte order、Timeout、重掃流程。 |
| Z旋轉 | PASS | 只限手動/調機；自動流程禁止使用。 | 測0/90/180/270與回原點後移0位。 |
| HMI完整操作 | 可Coding | 自動、手動、Alarm、Barcode、Reset、I/O監看已列。 | 實機驗證按鈕安全互鎖。 |
| Tolerance | 現場待定 | D4100/D4300/D4504/D4704需依pulse/mm與機構精度實測。 | 填入預設值、上下限、權限。 |
| Safety Stop策略 | 現場待定 | Safety OFF、Air OFF、真空保持/破真空、煞車落下策略需業主/機構確認。 | FAT前封口。 |
| 整機Release | HOLD | 尚未實機測試，不可判定量產驗收通過。 | 完成FAT/SAT後再Release。 |
