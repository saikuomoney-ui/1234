# 12_流程_Z升降_Barcode_S300

> Exported from `docs/PTC_Mask_Transfer_4Axis_Design_Draft.xlsx`.

| Step | 動作 | 執行輸出/命令 | 完成條件 | 異常/Timeout | 互鎖/安全 | 備註 |
| --- | --- | --- | --- | --- | --- | --- |
| S300 | Z/Barcode流程入口 | SET M6102；RST M6103 | X0000安全OK、X0001氣壓OK、X0036 FFU Run、X0037 OFF | NG->S389 | Axis4 Auto禁止 | Auto只允許Axis1/2/3 |
| S301 | 檢查站左右定位伸出 | Y0011 ON；Y0012 OFF | X0016 ON | K310 | Y0011/Y0012互斥 | 左右2支伸出磁簧串聯後才完成 |
| S302 | 檢查站前後定位伸出 | Y0013 ON；Y0014 OFF | X0020 ON | K311 | Y0013/Y0014互斥 | 前後2支伸出磁簧串聯後才完成 |
| S303 | 確認光罩在檢查站 | 無 | X0026 ON | K312 | 若X0026 OFF禁止Z上升 | Z升降前必要條件 |
| S304 | Z升降到平台位，將光罩抬高 | SET M4521；目標D4514 | M4551 ON + M4527 Busy OFF + M4518 Alarm OFF + 誤差<=D4504 | K320 | 啟動前再確認X0016+X0020+X0026+M4517 | 平台位高度現場Teach |
| S305 | 檢查站左右/前後定位縮回 | Y0011 OFF；Y0012 ON；Y0013 OFF；Y0014 ON | X0017 AND X0021 | K321 | Y0011/Y0012不可同時ON；Y0013/Y0014不可同時ON | 未全部縮回不可進Barcode位 |
| S306 | Z升降到Barcode掃描位 | SET M4522；目標D4510 | M4552 ON + M4527 Busy OFF + M4518 Alarm OFF + 誤差<=D4504 | K322 | 定位縮回完成才允許 | Barcode高度現場Teach |
| S307 | Barcode讀取 | M6300 ON時SET M6302；M6300 OFF則SET M6306 | M6303 ON 或 M6306 ON | K330 | 通訊Timeout需停在S389 | Barcode型號依BOM/採購版統一；若目前BOM為Barcode Reader(依BOM實際採購型號)，文件先以Barcode Reader(依BOM實際採購型號) |
| S308 | Barcode比對 | 比較Storage Barcode與Mask Barcode | M6304 OK->S309；M6305 NG->S380 | K331 | NG不得直接PASS | Barcode OFF記錄BYPASS |
| S309 | 人工目視檢查選配 | M6500 ON時SET M6501；OFF則SET M6504 | M6502 OK/M6504->S310；M6503 NG->S380 | K340 | Popup Hold | NG返回來源盒 |
| S310 | Z升降回Home | SET M4520；目標D4512 | M4550 Home Complete + M4527 Busy OFF + M4518 Alarm OFF | K350 | 固定回Home，不用M4553替代 | 需求若改安全等待位再另定 |
| S311 | Z/Barcode完成交握 | SET M6103；RST M6102 | 主流程收到M6103 | - | X軸才可回Inspection | M6103=Z/Barcode流程完成且Z升降在安全位 |
| S380 | NG返回來源盒 | 依方向回儲存盒或上機盒 | X軸回放完成 | 必要時HMI確認 | Axis4不動作 | Barcode/Visual NG共同回收 |
| S389 | Z/Barcode異常監控 | SET Alarm Code；RST M6102 | HMI排除後回初始化/安全位 | - | 所有定位閥不可同時ON | 停機或警告依Alarm表 |
