# 16_驗收_Release_Gate

> Exported from `docs/PTC_Mask_Transfer_4Axis_Design_Draft.xlsx`.

| 項目 |  |  |  |
| --- | --- | --- | --- |
| PLC/HMI設計文件 | PASS_TO_CODING | 已整合20260826來源設計最終封口建議，可作Coding依據。 | 依正式X/Y、M/D/T/S表Coding，不沿用舊衝突點位。 |
| 正式X/Y點位 | PASS | 02_XY點位表維持BOM/PLC已確認點位，未新增X0044~X0047/Y0025/Y0026。 | 新增需求只能先列待確認，不可直接佔用正式X/Y。 |
| 2軸流程 | PASS | X橫移/X升降正反向、初始化、真空確認、異常復歸已定義。 | 單機測試D441x/D443x、D4100/D4300。 |
| Z升降+Barcode | 可Coding/HOLD | S300含檢查站定位、Z平台抬高、定位縮回、Barcode位、比對、回安全位。 | Barcode Reader實際型號依BOM；通訊格式、字串長度、Byte order、Timeout需實測。 |
| Z旋轉 | PASS_TO_MANUAL | S400只限手動/調機；自動流程禁止使用D6412旋轉。 | 測0/90/180/270與回原點後移0位。 |
| Cycle Complete | HOLD | 已拆成儲存盒關蓋等效→儲存盒破真空→上機盒關蓋等效→上機盒破真空→兩盒取出。 | 需現場確認X0023/X0025 OFF是否等同關蓋。 |
| Ionizer | HOLD | Enable條件已修為停止輸出OFF、異常OFF、檢查訊號正常。 | 需確認DTY-ELK01 X0032檢查訊號正常/異常邏輯。 |
| Safety Stop策略 | 現場待定 | Safety OFF、Air OFF、真空保持/破真空、煞車落下策略需業主/機構確認。 | FAT前封口。 |
| 整機Release | HOLD | 文件可進程式設計與單機測試，但尚未實機測試，不可判定量產驗收通過。 | 完成FAT/SAT後再Release。 |
