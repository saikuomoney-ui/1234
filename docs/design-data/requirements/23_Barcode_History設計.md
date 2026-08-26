# 23_Barcode_History設計

> Generated from PTC_Mask_Transfer_4Axis_Design_Draft.xlsx. Source workbook is the controlled Excel design draft.

| 項目 | 需求 | 建議設計 | PLC資料 | HMI資料 | 備註 |
| --- | --- | --- | --- | --- | --- |
| Storage Barcode輸入 | 生產前輸入儲存盒條碼。 | HMI輸入後寫D6300起始區並SET M6301。 | D6300~D6349/M6301 | 輸入欄+Valid燈 | Barcode Enable ON時必須有效。 |
| Mask Barcode讀取 | Z到Barcode位後讀取光罩條碼。 | PLC觸發SR-2000W，結果寫D6350起始區。 | D6350~D6399/M6302/M6303 | 即時顯示讀取值 | 通訊格式需實測。 |
| Compare | Mask Barcode等於Storage Barcode才PASS。 | PLC或HMI比對皆可，但建議PLC保留結果位。 | M6304/M6305/D6402 | OK/NG/BYPASS | NG不可直接放目的地。 |
| History 1000筆 | 保留1000筆。 | 建議由HMI Data Logging/Ring Buffer做 newest-first；PLC只提供本次結果。 | D6400/D6402/D6500/D6004 | 歷史表格1000列 | 避免PLC每Cycle搬移大量字串。 |
| History欄位 | 需可追溯。 | 時間、方向、Storage Barcode、Mask Barcode、Barcode結果、Visual結果、Final結果、Alarm。 | D資料+HMI時間 | CSV/內部紀錄 | 可供FAT查證。 |
| Barcode OFF | 允許功能Bypass時。 | History Barcode Result記BYPASS。 | M6306/D6400 | 顯示BYPASS | 需工程權限。 |
| Barcode NG | 比對失敗。 | HMI Popup顯示差異，流程走Return。 | M6305/D6402 | NG彈窗 | 不得給PASS機會，除非工程權限另行定義。 |
