# 21_4軸Auto完整流程

> Exported from `docs/PTC_Mask_Transfer_4Axis_Design_Draft.xlsx`.

| No | 流程段 | 主要動作 | 使用軸/輸出 | 完成條件 | 異常處理 | 備註 |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Auto Ready | 確認Safety/Air/FFU/初始化/Barcode條件 | X0000/X0001/X0036/X0037/M1125/M1225/M1425 | Ready成立 | 不成立禁止啟動 | Barcode Enable ON時需Storage Barcode Valid |
| 2 | X取來源盒 | X橫移到來源位，X升降到取片位，夾爪關，真空ON | Axis1/Axis2/Y0010/Y0015 | X0015+X0027 | 真空NG->S189/S299 | 正向來源=儲存盒；反向來源=上機盒 |
| 3 | X真空確認上升 | 上升約10mm到真空確認位，再確認真空OK | Axis2/M4330 | X0027保持ON | 真空掉落停機 | 確認後升到上位 |
| 4 | X移到檢查位 | X升降上位後，X橫移到檢查位 | Axis1 | M4151 ON | Axis Alarm停機 | 到位後才下降 |
| 5 | X放到檢查站 | X升降到檢查放位，破真空，夾爪開 | Axis2/Y0016/Y0007 | X0014+X0026 | 光罩未在席->Alarm | 放完X回上位再離開干涉區 |
| 6 | X離開檢查位 | X升降回上位，X橫移離開檢查區 | Axis1/Axis2 | X已Clear | 未Clear禁止Z | 避免Z軸動作干涉 |
| 7 | Z左右定位伸出 | 左右雙線圈閥伸出 | Y0011 ON/Y0012 OFF | X0016 ON | K310 | 2支磁簧串聯 |
| 8 | Z前後定位伸出 | 前後雙線圈閥伸出 | Y0013 ON/Y0014 OFF | X0020 ON | K311 | 2支磁簧串聯 |
| 9 | Z升平台位 | 確認X0026後Z升到平台位 | Axis3/M4521/D4514 | M4551 ON | K320 | 啟動前需X0016+X0020+X0026 |
| 10 | Z定位縮回 | 左右/前後雙線圈閥縮回 | Y0012 ON/Y0014 ON | X0017 AND X0021 | K321 | 縮回後才可去Barcode |
| 11 | Z到Barcode位 | Z升降到掃碼高度 | Axis3/M4522/D4510 | M4552 ON | K322 | 高度現場Teach |
| 12 | Barcode/Visual | 掃碼、比對、目視檢查選配 | M630x/M650x | OK/BYPASS | NG->回來源盒 | Axis4不參與Auto |
| 13 | Z回Home | Z升降回Home | Axis3/M4520/D4512 | M4550 ON | K350 | 固定Home Complete |
| 14 | X回檢查位取片 | X回檢查位，下降取片，真空確認，上升 | Axis1/Axis2/Y0010/Y0015 | X0027 ON | 真空NG停機 | 準備送目的盒 |
| 15 | X送目的盒 | PASS送目的盒；NG回來源盒 | Axis1/Axis2/Y0016/Y0007 | 放片完成 | 未到位/真空異常停機 | 正反向依D6100/M6002/M6003 |
| 16 | Cycle Complete | 允許開門/移除盒，等待兩盒移除 | M6600/Y0020/Y0022/X0022/X0024 | X0022 OFF AND X0024 OFF | 逾時警告 | 不新增門鎖X/Y，門鎖若需PLC監看另走擴充點位 |
