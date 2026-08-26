# 20_HMI權限與互鎖

> Exported from `docs/PTC_Mask_Transfer_4Axis_Design_Draft.xlsx`.

| 功能 | Operator | Engineer | Admin | 必須條件 | 禁止條件 | PLC點位/資料 |
| --- | --- | --- | --- | --- | --- | --- |
| 自動正向/反向啟動 | 允許 | 允許 | 允許 | X0000/X0001、M1125/M1225/M1325、M4117/M4317/M4517、M4553、Material一致 | Auto Busy、Alarm、Manual Mode | M6002/M6003 |
| Auto Stop | 允許 | 允許 | 允許 | Auto Busy |  | M6004 |
| Abort中止 | 限制 | 允許 | 允許 | Auto Busy |  | M6008 |
| Alarm Reset | 允許 | 允許 | 允許 | 異常條件解除 | Safety未復歸 | M6040 |
| Servo Reset | 禁止 | 允許 | 允許 | 軸停止、Safety OK | 軸Busy | M6041 |
| Safety Reset | 禁止 | 允許 | 允許 | EMO釋放、門鎖成立 | 安全條件未成立 | M6042/Y0000 |
| Manual/JOG | 禁止 | 允許 | 允許 | M6010、M6200、M6201低速、對應Move Permit | Auto Busy、Safety NG | M4131/M4132/M4340/M4341/M4531/M4532/M4731/M4732 |
| 氣缸/真空單動 | 禁止 | 允許 | 允許 | M6010、M6200、位置安全、二次確認、雙線圈互斥 | Auto Busy、Safety NG | HMI寫M6210~M6223，PLC互鎖後驅動Y0007~Y0022 |
| 位置Teach | 禁止 | 允許 | 允許 | 手動模式、軸停止、正確Safe Zone、確認視窗 | Auto Busy | D441x/D451x/D471x |
| Tolerance/Speed/Timeout | 禁止 | 允許 | 允許 | 工程權限、上下限檢查 | Auto Busy | D4100/D4300/D4504/D4704/D602x |
| 人工料態修正 | 禁止 | 允許 | 允許 | M6030 Apply、二次確認、Sensor一致檢查 | Auto Busy | D6101/M6030/M6031 |
| Service Unlock Request | 禁止 | 限制 | 允許 | 安全硬體/安全控制器授權、低速、門鎖條件符合 | 自動流程中、未授權 | M6104只作請求，不作Safety Bypass |
