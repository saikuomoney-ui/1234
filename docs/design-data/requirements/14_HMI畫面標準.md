# 14_HMI畫面標準

> Generated from PTC_Mask_Transfer_4Axis_Design_Draft.xlsx. Source workbook is the controlled Excel design draft.

| 畫面/功能 |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- |
| 自動畫面 | 正向啟動 | M6001 -> M1102 | 安全OK、氣壓OK、初始化完成、Barcode生產前資料OK | Auto Busy、Alarm、Manual Mode | 儲存盒到上機盒。 |
| 自動畫面 | 反向啟動 | M6002 -> M1103 | 同上 | 同上 | 上機盒到儲存盒。 |
| 自動畫面 | Auto Stop | M6004 | 自動中 |  | 一般停止/暫停，不等同EMO。 |
| 狀態總覽 | Auto Busy/Ready | M1126/M1226/M6102/M1125/M1225 | 常時顯示 |  | 顯示機台可啟動條件與目前Step。 |
| 初始化 | 全部初始化 | M1001 -> M13 | 安全OK、氣壓OK | Auto Busy | 依MAIN先升降再橫移，避免干涉。 |
| 初始化 | X橫移初始化 | M1123 | 手動/工程 | Auto Busy | 走S190~S198。 |
| 手動調機 | X橫移JOG-/JOG+ | M6011/M6012 -> M4131/M4132 | M6010工程/手動 | Auto Busy、安全NG | 速度使用手動速度D。 |
| 手動調機 | X升降JOG-/JOG+ | M6013/M6014 -> M4341/M4340 | M6010工程/手動 | Auto Busy、安全NG | 不可寫到M4330。 |
| 手動調機 | Z升降JOG-/JOG+ | M6015/M6016 -> M4531/M4532 | M6010工程/手動 | Auto Busy、安全NG | 需避開X/Z干涉。 |
| 手動調機 | Z旋轉0/90/180/270 | M6400 + S400 | M6010工程/手動 + Z安全 | Auto Busy | D6412只作建議角度參考。 |
| 夾爪/真空 | 夾爪開關/真空ON/破真空 | Y0007~Y0022 + X0014~X0031 | 手動模式、單動允許 | Auto Busy或安全NG | 每個手動輸出需顯示回授。 |
| Barcode | 生產前掃碼/重掃/NG確認 | D6300/D6350/D6400/D6402/D6420 | 安全OK或工程Bypass流程 | 門未關且非Bypass | Barcode NG需彈窗、重掃一次、確認失敗退回來源。 |
| Reset | 異常復歸 | M6040 | 異常條件解除 | Safety未復歸 | 只清軟體警報。 |
| Reset | 伺服復歸 | M6041 | 安全OK、Servo可復歸 | 軸仍動作中 | 對應伺服/軸卡錯誤復歸。 |
| Reset | 安全復歸 | M6042 -> Y0000瞬時 | EMO釋放、門鎖成立 | 任一安全條件未成立 | 安全繼電器復歸獨立於Alarm Reset。 |
| I/O監看 | X/Y即時狀態 | 所有X/Y | 常時 |  | 給調機與查修使用。 |
| 參數/Recipe | 位置/速度/Tolerance | D4100/D4300/D441x/D443x/D451x | 工程權限 | Auto Busy | Teach/Save需確認，不直接寫Flash ROM高頻操作。 |
