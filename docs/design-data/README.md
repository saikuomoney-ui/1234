# 力成光罩傳送機 4軸 PLC/HMI 新設計手稿

本資料由 `docs/PTC_Mask_Transfer_4Axis_Design_Draft.xlsx` 匯出，目的是讓 GitHub/ChatGPT 可直接讀取設計內容。

## 設計邊界

- Axis1：X橫移，自動與手動調機。
- Axis2：X升降，自動與手動調機，含夾爪、真空、破真空流程。
- Axis3：Z升降，自動流程含檢查站定位、Barcode、Visual Inspection。
- Axis4：Z旋轉，只允許工程/手動調機 0/90/180/270，不進自動流程。
- BOM/PDF/暫存檔/客戶機密原始資料不放入 Git，本 repo 只放設計手稿與可審查文字匯出。

## 匯出分頁

| Sheet | Markdown | CSV | Rows |
| --- | --- | --- | --- |
| 00_設計標準總覽 | [00_設計標準總覽.md](docs/design-data/requirements/00_設計標準總覽.md) | [00_設計標準總覽.csv](docs/design-data/requirements/00_設計標準總覽.csv) | 10 |
| 01_位址分區標準 | [01_位址分區標準.md](docs/design-data/requirements/01_位址分區標準.md) | [01_位址分區標準.csv](docs/design-data/requirements/01_位址分區標準.csv) | 28 |
| 02_XY點位表 | [02_XY點位表.md](docs/design-data/io-list/02_XY點位表.md) | [02_XY點位表.csv](docs/design-data/io-list/02_XY點位表.csv) | 75 |
| 03_M共用_HMI_Barcode | [03_M共用_HMI_Barcode.md](docs/design-data/requirements/03_M共用_HMI_Barcode.md) | [03_M共用_HMI_Barcode.csv](docs/design-data/requirements/03_M共用_HMI_Barcode.csv) | 86 |
| 04_M軸1_X橫移 | [04_M軸1_X橫移.md](docs/design-data/requirements/04_M軸1_X橫移.md) | [04_M軸1_X橫移.csv](docs/design-data/requirements/04_M軸1_X橫移.csv) | 24 |
| 05_M軸2_X升降 | [05_M軸2_X升降.md](docs/design-data/requirements/05_M軸2_X升降.md) | [05_M軸2_X升降.csv](docs/design-data/requirements/05_M軸2_X升降.csv) | 41 |
| 06_M軸3_Z升降 | [06_M軸3_Z升降.md](docs/design-data/requirements/06_M軸3_Z升降.md) | [06_M軸3_Z升降.csv](docs/design-data/requirements/06_M軸3_Z升降.csv) | 26 |
| 07_M軸4_Z旋轉 | [07_M軸4_Z旋轉.md](docs/design-data/requirements/07_M軸4_Z旋轉.md) | [07_M軸4_Z旋轉.csv](docs/design-data/requirements/07_M軸4_Z旋轉.csv) | 26 |
| 08_D資料參數 | [08_D資料參數.md](docs/design-data/requirements/08_D資料參數.md) | [08_D資料參數.csv](docs/design-data/requirements/08_D資料參數.csv) | 84 |
| 09_T_S流程分區 | [09_T_S流程分區.md](docs/design-data/sequence/09_T_S流程分區.md) | [09_T_S流程分區.csv](docs/design-data/sequence/09_T_S流程分區.csv) | 16 |
| 10_流程_X橫移_S100_S150 | [10_流程_X橫移_S100_S150.md](docs/design-data/sequence/10_流程_X橫移_S100_S150.md) | [10_流程_X橫移_S100_S150.csv](docs/design-data/sequence/10_流程_X橫移_S100_S150.csv) | 24 |
| 11_流程_X升降_S200 | [11_流程_X升降_S200.md](docs/design-data/sequence/11_流程_X升降_S200.md) | [11_流程_X升降_S200.csv](docs/design-data/sequence/11_流程_X升降_S200.csv) | 17 |
| 12_流程_Z升降_Barcode_S300 | [12_流程_Z升降_Barcode_S300.md](docs/design-data/sequence/12_流程_Z升降_Barcode_S300.md) | [12_流程_Z升降_Barcode_S300.csv](docs/design-data/sequence/12_流程_Z升降_Barcode_S300.csv) | 15 |
| 13_流程_Z旋轉手動_S400 | [13_流程_Z旋轉手動_S400.md](docs/design-data/sequence/13_流程_Z旋轉手動_S400.md) | [13_流程_Z旋轉手動_S400.csv](docs/design-data/sequence/13_流程_Z旋轉手動_S400.csv) | 8 |
| 14_HMI畫面標準 | [14_HMI畫面標準.md](docs/design-data/requirements/14_HMI畫面標準.md) | [14_HMI畫面標準.csv](docs/design-data/requirements/14_HMI畫面標準.csv) | 18 |
| 15_異常警報標準 | [15_異常警報標準.md](docs/design-data/requirements/15_異常警報標準.md) | [15_異常警報標準.csv](docs/design-data/requirements/15_異常警報標準.csv) | 18 |
| 16_驗收_Release_Gate | [16_驗收_Release_Gate.md](docs/design-data/requirements/16_驗收_Release_Gate.md) | [16_驗收_Release_Gate.csv](docs/design-data/requirements/16_驗收_Release_Gate.csv) | 9 |
| 99_來源與版本 | [99_來源與版本.md](docs/design-data/requirements/99_來源與版本.md) | [99_來源與版本.csv](docs/design-data/requirements/99_來源與版本.csv) | 7 |
| 00_總覽 | [00_總覽.md](docs/design-data/requirements/00_總覽.md) | [00_總覽.csv](docs/design-data/requirements/00_總覽.csv) | 8 |
| 17_CODEX審查封口 | [17_CODEX審查封口.md](docs/design-data/requirements/17_CODEX審查封口.md) | [17_CODEX審查封口.csv](docs/design-data/requirements/17_CODEX審查封口.csv) | 15 |
| 18_Fault_Output_Matrix | [18_Fault_Output_Matrix.md](docs/design-data/requirements/18_Fault_Output_Matrix.md) | [18_Fault_Output_Matrix.csv](docs/design-data/requirements/18_Fault_Output_Matrix.csv) | 12 |
| 19_Timeout_參數標準 | [19_Timeout_參數標準.md](docs/design-data/requirements/19_Timeout_參數標準.md) | [19_Timeout_參數標準.csv](docs/design-data/requirements/19_Timeout_參數標準.csv) | 8 |
| 20_HMI權限與互鎖 | [20_HMI權限與互鎖.md](docs/design-data/requirements/20_HMI權限與互鎖.md) | [20_HMI權限與互鎖.csv](docs/design-data/requirements/20_HMI權限與互鎖.csv) | 12 |
| 00_4軸新設計總覽 | [00_4軸新設計總覽.md](docs/design-data/requirements/00_4軸新設計總覽.md) | [00_4軸新設計總覽.csv](docs/design-data/requirements/00_4軸新設計總覽.csv) | 12 |
| 01_IO新增與配置 | [01_IO新增與配置.md](docs/design-data/io-list/01_IO新增與配置.md) | [01_IO新增與配置.csv](docs/design-data/io-list/01_IO新增與配置.csv) | 14 |
| 21_4軸Auto完整流程 | [21_4軸Auto完整流程.md](docs/design-data/sequence/21_4軸Auto完整流程.md) | [21_4軸Auto完整流程.csv](docs/design-data/sequence/21_4軸Auto完整流程.csv) | 16 |
| 22_功能Enable矩陣 | [22_功能Enable矩陣.md](docs/design-data/requirements/22_功能Enable矩陣.md) | [22_功能Enable矩陣.csv](docs/design-data/requirements/22_功能Enable矩陣.csv) | 7 |
| 23_Barcode_History設計 | [23_Barcode_History設計.md](docs/design-data/requirements/23_Barcode_History設計.md) | [23_Barcode_History設計.csv](docs/design-data/requirements/23_Barcode_History設計.csv) | 8 |
| 24_HMI_4軸畫面 | [24_HMI_4軸畫面.md](docs/design-data/requirements/24_HMI_4軸畫面.md) | [24_HMI_4軸畫面.csv](docs/design-data/requirements/24_HMI_4軸畫面.csv) | 15 |
| 25_4軸CODEX封口清單 | [25_4軸CODEX封口清單.md](docs/design-data/requirements/25_4軸CODEX封口清單.md) | [25_4軸CODEX封口清單.csv](docs/design-data/requirements/25_4軸CODEX封口清單.csv) | 12 |
