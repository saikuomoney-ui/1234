# 00_設計標準總覽

> Exported from `docs/PTC_Mask_Transfer_4Axis_Design_Draft.xlsx`.

| 00_設計標準總覽 |  |  |  |
| --- | --- | --- | --- |
| 類別 | 標準/分區 | 狀態 | 說明 |
| 文件目的 | PLC/HMI 設計標準版 V2 | PASS_TO_CODING | 整合目前定案內容，移除舊矛盾與過程文字 |
| 適用範圍 | X橫移、X升降、Z升降、Z旋轉、Barcode、HMI、安全/停止策略 | 設計文件 | 位址範圍限制 X/Y/M/D/T/S 0~6999 |
| 2軸流程 | X橫移 + X升降 | PASS | 可進入 PLC Coding 與單機測試 |
| Z升降+Barcode | 完整機構流程 + KEYENCE SR-2000W | 可 Coding / 未實測 | 含定位氣缸、光罩在席、Z抬高、氣缸縮回、Barcode掃描位；通訊格式需實機確認 |
| Z旋轉 | 僅手動/調機 0/90/180/270 | 自動禁用 | Barcode 建議角度只供HMI顯示與人工調機參考 |
| HMI | 自動、手動調機、初始化、Barcode NG、I/O、Alarm、Recipe | 可設計 / 待畫面實作 | 已補正向/反向啟動、Auto Stop、Auto Busy、初始化完成、Barcode生產前掃碼OK |
| 整機 Release | 現場驗收 | HOLD | SR-2000W通訊、Z高度、Tolerance、Safety OFF、真空/煞車/門鎖Bypass需實測 |
| 成熟度 | 約 88%~90% | 可進程式設計 | 比上一版更接近Coding版，但不是現場整機Release通過 |
