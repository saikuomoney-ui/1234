# 22_功能Enable矩陣

> Generated from PTC_Mask_Transfer_4Axis_Design_Draft.xlsx. Source workbook is the controlled Excel design draft.

| 功能 | 必要性 | HMI設定 | Auto Ready條件 | OFF時流程行為 | 異常/顯示 | 備註 |
| --- | --- | --- | --- | --- | --- | --- |
| Safety Relay | 必須 | 不可Bypass | X0000 ON | OFF禁止Auto且安全硬體處理 | K101 | 不能由PLC旁路。 |
| Air Pressure | 必須 | 不可Bypass | X0001 ON | OFF禁止Auto | K102 | 掉片策略見Fault Matrix。 |
| FFU | 必須/依業主 | 不可Bypass或工程限定 | Run ON + Alarm OFF | 不成立禁止Auto Start或停在安全點 | K230 | 依潔淨需求決定停機等級。 |
| Ionizer | 可選 | Ionizer Enable | ON時需無Alarm | OFF只Bypass靜電消除判斷 | K210/K211 | HMI需顯示Bypass。 |
| Barcode Compare | 可選但建議必用 | Barcode Enable | ON時M6301 Storage Barcode Valid必須ON | OFF記錄BYPASS，不做比對 | K181/K182 | 若業主要求條碼追溯，建議不可Bypass。 |
| Visual Inspection | 可選 | Visual Enable | ON時Barcode OK後要求人工判定 | OFF記錄BYPASS | K260 | 人工確認流程。 |
