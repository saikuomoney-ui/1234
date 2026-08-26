# 20_HMI權限與互鎖

> Generated from PTC_Mask_Transfer_4Axis_Design_Draft.xlsx. Source workbook is the controlled Excel design draft.

| 功能 | Operator | Engineer | Admin | 必須條件 | 禁止條件 | PLC點位/資料 |
| --- | --- | --- | --- | --- | --- | --- |
| 自動正向/反向啟動 | 允許 | 允許 | 允許 | Safety OK、Air OK、Init OK、Ready、Z Safe、Material一致 | Auto Busy、Alarm、Manual Mode | M6002/M6003 |
| Auto Stop | 允許 | 允許 | 允許 | Auto Busy |  | M6004 |
| Abort中止 | 限制 | 允許 | 允許 | Auto Busy |  | M6008 |
| Alarm Reset | 允許 | 允許 | 允許 | 異常條件解除 | Safety未復歸 | M6040 |
| Servo Reset | 禁止 | 允許 | 允許 | 軸停止、Safety OK | 軸Busy | M6041 |
| Safety Reset | 禁止 | 允許 | 允許 | EMO釋放、門鎖成立 | 安全條件未成立 | M6042/Y0000 |
| Manual/JOG | 禁止 | 允許 | 允許 | M6010、M6200、低速、軸停止 | Auto Busy、Safety NG | M6011~M6018/M6200 |
| 氣缸/真空單動 | 禁止 | 允許 | 允許 | 手動模式、位置安全、二次確認 | Auto Busy、Safety NG | Y0007~Y0022 |
| 位置Teach | 禁止 | 允許 | 允許 | 手動模式、軸停止、確認視窗 | Auto Busy | D441x/D451x/D471x |
| Tolerance/Speed/Timeout | 禁止 | 允許 | 允許 | 工程權限、上下限檢查 | Auto Busy | D4100/D4300/D602x |
| 人工料態修正 | 禁止 | 允許 | 允許 | M6030 Apply、二次確認、Sensor一致檢查 | Auto Busy | D6101/M6030/M6031 |
