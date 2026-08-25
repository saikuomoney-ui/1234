# 12_流程_Z升降_Barcode_S300

> Exported from `docs/PTC_Mask_Transfer_4Axis_Design_Draft.xlsx`.

| Step | 名稱 | 進入條件 | 主要動作 | 完成條件 | 異常/Timeout | M/D/IO |
| --- | --- | --- | --- | --- | --- | --- |
| S300 | Z/Barcode入口 | M6101 ON + M6100 ON + X0000安全OK + X0001氣壓OK | SET M6102；RST M6103；確認X已離開檢查位干涉區。 | 進S301 | K171 | M6100/M6101/M6102 |
| S301 | 左右定位伸出 | S300 | Y0025 ON，左右定位氣缸伸出。 | X0044 ON | K180 | LR Extend Complete |
| S302 | 前後定位伸出 | X0044 ON | Y0026 ON，前後定位氣缸伸出。 | X0046 ON | K180 | FB Extend Complete |
| S303 | 光罩在席確認 | X0044 ON + X0046 ON | 確認檢查站光罩在席。 | X0026 ON | K230 | Inspection Mask Present |
| S304 | Z升到Platform位 | X0026 ON | SET M4521，Axis3到D4514。 | M4551 ON | K240 | D4514/M4551 |
| S305 | 定位氣缸縮回 | M4551 ON | Y0025 OFF、Y0026 OFF。 | X0045 ON + X0047 ON | K180 | LR/FB Retract Complete |
| S306 | Z到Barcode掃描位 | X0045/X0047 ON | SET M4522，Axis3到D4510。 | M4552 ON | K240 | D4510/M4552 |
| S307 | Barcode讀取 | M4552 ON | 若M6300 ON，SET M6302觸發SR-2000W；若OFF，SET M6306 Bypass。 | M6303 ON或M6306 ON | K181 | D6300/D6350/D6400/D6422 |
| S308 | Barcode比對 | M6303 ON | Mask Barcode與Storage Barcode比對。 | M6304 OK進S309；M6305 NG進S380 | K182 | D6402/D6412 |
| S309 | Visual人工確認 | M6304 ON | 若M6500 ON，SET M6501 HMI彈窗Hold；若OFF，SET M6504 Bypass。 | M6502 OK或M6504 ON；M6503 NG進S380 | K260 | D6500/D6502 |
| S310 | Z回Home/安全等待位 | Barcode/Visual OK | SET M4520，Axis3回D4512。 | M4550或M4553 ON | K240 | Z Safe For X |
| S311 | 通知X可回檢查位 | Z安全位完成 | SET M6103；RST M6102。 | RETSTL |  | X流程接續S131/S163 |
| S380 | NG Return判定 | Barcode NG或Visual NG | 依方向決定Return：正向回Storage、反向回Load。 | 交給X流程Return sequence | K182/K260 | 不得直接PASS。 |
| S389 | Z/Barcode異常 | 任一停機異常 | RST M6102；不SET M6103；寫D6004/D6006/D6008。 | HMI復歸後回初始化 |  |  |
