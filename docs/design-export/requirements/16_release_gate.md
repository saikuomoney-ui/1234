# 16_驗收_Release_Gate

> Exported from `docs/PTC_Mask_Transfer_4Axis_Design_Draft.xlsx`.

| 項目 |  |  |  |
| --- | --- | --- | --- |
| PLC/HMI設計文件 | PASS_TO_CODING | 已整合20260826全量來源設計驗證P0項目，可作Coding依據。 | 依正式X/Y、M/D/T/S表Coding，不沿用舊衝突點位。 |
| 正式X/Y點位 | PASS | 02_XY點位表維持BOM/PLC已確認點位，未新增X0044~X0047/Y0025/Y0026。 | 新增需求只能先列待確認，不可直接佔用正式X/Y。 |
| Device唯一性 | PASS_TO_CODING | M4327只作Axis2 BUSY；M4330為真空確認位命令；M4340/M4341為Axis2 JOG；M6002/M6003為正反啟動。 | 正式PLC/HMI不得引用Deprecated點位作控制。 |
| 正反向主流程 | PASS_TO_CODING | 已補Inspection Place→X Clear→Z Request→Z Done→X回Inspection Pick→目的盒Place。 | Coding時需用S116/S166放檢查位，不能跳過。 |
| Manual/Teach | PASS_TO_CODING/HOLD | HMI不直寫Y；改M6210~M6223命令，PLC互鎖後驅動Y。 | Move Permit機構干涉條件需在GX Works3逐軸落實並實測。 |
| Z升降+Barcode | 可Coding/HOLD | S300含定位汽缸、光罩在席、Platform、Retract、Barcode、Visual、Home。 | Barcode Reader實際型號依BOM；通訊格式需實測。 |
| Z旋轉 | PASS_TO_MANUAL | S400只限手動/調機；自動流程禁止使用D6412旋轉。 | 測0/90/180/270與回原點後移0位。 |
| Alarm Master | PASS_TO_CODING | K3xx、K360、真空來源K200/K202/K203已列入正式Alarm Master。 | HMI Alarm Detail需顯示Step/Axis/Vacuum Source。 |
| I/O Master欄位 | HOLD | 正式X/Y點位已定，但COM/Terminal/Cable/Drawing Ref仍需電路圖封口。 | 不影響流程Coding，但影響配線與驗收文件。 |
| Cycle Complete | HOLD | 已拆成儲存盒/上機盒分別關蓋等效→破真空→兩盒取出。 | 需現場確認X0023/X0025 OFF是否等同關蓋。 |
| 整機Release | HOLD | 文件可進程式設計與單機測試，但尚未實機測試，不可判定量產驗收通過。 | 完成FAT/SAT後再Release。 |
