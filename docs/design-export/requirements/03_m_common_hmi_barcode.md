# 03_M共用_HMI_Barcode

> Exported from `docs/PTC_Mask_Transfer_4Axis_Design_Draft.xlsx`.

| 03_M共用_HMI_Barcode |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- |
| 位址 | 中文名稱 | English | 分類 | 用途 | 備註 |
| M1000 | 全機自動中 | Machine auto running | 共用流程 | 自動循環總旗標 |  |
| M1001 | 全機初始化請求 | Machine initialize request | 共用流程 | HMI 全部初始化 |  |
| M1002 | 全機初始化中 | Machine initializing | 共用流程 | 初始化總控 |  |
| M1003 | 全機初始化完成 | Machine initialization complete | 共用流程 | 各軸初始化完成後ON |  |
| M1100 | X橫移_STL啟用旗標 | X traverse STL enable | X橫移流程 | S100/S150流程入口 |  |
| M1101 | X橫移_手動旗標 | X traverse manual | X橫移流程 | HMI手動調機 |  |
| M1102 | X橫移_送片旗標 | X traverse forward transfer | X橫移流程 | 儲存盒到上機盒 |  |
| M1103 | X橫移_回片旗標 | X traverse reverse transfer | X橫移流程 | 上機盒到儲存盒 |  |
| M1120 | X橫移_MC送電旗標 | X traverse MC power request | X橫移流程 | 控制Y0003 |  |
| M1121 | X橫移_開機完成旗標 | X traverse power ready | X橫移流程 | 伺服送電完成 |  |
| M1122 | X橫移_未初始化旗標 | X traverse not initialized | X橫移流程 | 初始狀態 |  |
| M1123 | X橫移_初始化請求旗標 | X traverse initialize request | X橫移流程 | 進S190 |  |
| M1124 | X橫移_初始化中旗標 | X traverse initializing | X橫移流程 | 初始化執行中 |  |
| M1125 | X橫移_初始化完成旗標 | X traverse initialized | X橫移流程 | 原點後到檢查/等待位 |  |
| M1126 | X橫移_Busy旗標 | X traverse busy | X橫移流程 | 子流程運轉中 |  |
| M1160 | X橫移_MF Ready旗標 | X traverse MF ready | X橫移流程 | 可被主流程呼叫 |  |
| M1200 | X升降_STL啟用旗標 | X lift STL enable | X升降流程 | S200流程入口 |  |
| M1201 | X升降_手動旗標 | X lift manual | X升降流程 | HMI手動調機 |  |
| M1220 | X升降_MC送電旗標 | X lift MC power request | X升降流程 | 控制Y0004 |  |
| M1221 | X升降_開機完成旗標 | X lift power ready | X升降流程 | 伺服送電完成 |  |
| M1223 | X升降_初始化請求旗標 | X lift initialize request | X升降流程 | 進S290 |  |
| M1224 | X升降_初始化中旗標 | X lift initializing | X升降流程 | 初始化執行中 |  |
| M1225 | X升降_初始化完成旗標 | X lift initialized | X升降流程 | 原點後到上位 |  |
| M1226 | X升降子流程_Busy | X lift subflow busy | 軸2流程 | S2xx進入時SET，完成/異常時RST。 | 主流程等待子流程時使用。 |
| M1228 | X升降子流程_Alarm | X lift subflow alarm | 軸2流程 | Timeout/真空/定位異常時SET。 | 主流程遇ON轉S189。 |
| M1300 | Z升降_STL啟用旗標 | Z lift STL enable | Z流程 | S300流程入口 |  |
| M1400 | Z旋轉_STL啟用旗標 | Z rotation STL enable | Z旋轉手動 | S400只允許工程/手動 | 自動禁用 |
| M1500 | 四軸MC送電完成 | All servo MC power ON completed | 軸卡共用 | 4軸伺服送電條件成立 |  |
| M1510 | 軸卡FlashROM寫入請求 | SSC flash ROM write request | 軸卡共用 | HMI/工程請求 | 不要與M6020混用 |
| M1511 | 軸卡FlashROM寫入中 | SSC flash ROM writing | 軸卡共用 | 寫入狀態 |  |
| M1512 | 軸卡FlashROM寫入完成 | SSC flash ROM write complete | 軸卡共用 | 寫入完成 |  |
| M1513 | 軸卡FlashROM寫入異常 | SSC flash ROM write alarm | 軸卡共用 | 寫入失敗 |  |
| M6010 | 工程/手動模式 | Engineering/manual mode | HMI | 允許手動調機與S400 |  |
| M6004 | HMI Auto Stop | HMI auto stop | HMI自動 | 一般停止，跑到安全點停止。 | Abort/E-stop需分開。 |
| M6020 | X升降上位狀態 | X lift upper position state | HMI | HMI畫面狀態顯示 | 不可作FlashROM命令 |
| M6060 | FlashROM寫入請求 | Flash ROM write request | HMI/軸卡 | 取代舊M6019/M6020寫入用途 |  |
| M6061 | FlashROM寫入命令 | Flash ROM write command | HMI/軸卡 | 軸卡寫入用 |  |
| M6103 | Z/Barcode流程完成且Z升降在安全位 | Z barcode done and Z lift safe | X/Z交握 | Z/Barcode成功完成且Z升降回安全位後SET。 | 不可代表Z旋轉自動完成。 |
| M6104 | 工程門鎖Bypass | Engineering door bypass | 工程模式 | Barcode NG人工介入時，依權限允許門鎖Bypass。 | 不可作X/Z交握異常。 |
| M6200 | Manual允許總旗標 | Manual operation enable | 手動調機 | M6010 + Safety OK + Auto Busy OFF + Axis Stop。 | JOG與單動輸出必須串此條件。 |
| M6201 | JOG低速模式 | JOG low speed mode | 手動調機 | 手動JOG固定低速或限速。 | 維修模式速度需<50mm/s時在此互鎖。 |
| M6202 | Barcode OK | Barcode OK | Barcode | 讀取且比對OK |  |
| M6203 | Barcode NG | Barcode NG | Barcode | 讀取失敗/比對失敗 | 走NG人工介入 |
| M6400 | Z旋轉手動調機模式 | Z rotation manual setup mode | HMI | 允許S400手動角度測試 | 需M6010同時成立 |
| M6401 | Z旋轉回原點請求 | Z rotation home request | HMI | 手動回原點 | 回原點後必須移到0位 |
| M6402 | Z旋轉0度請求 | Z rotation 0 deg request | HMI | 手動定位 |  |
| M6403 | Z旋轉90度請求 | Z rotation 90 deg request | HMI | 手動定位 |  |
| M6404 | Z旋轉180度請求 | Z rotation 180 deg request | HMI | 手動定位 |  |
| M6405 | Z旋轉270度請求 | Z rotation 270 deg request | HMI | 手動定位 |  |
| M1004 | 全機Auto Busy | Machine auto busy | 共用流程 | 自動循環執行中 | HMI狀態顯示 |
| M1005 | 全機Auto Done | Machine auto done | 共用流程 | 自動流程完成 |  |
| M1227 | X升降子流程_Done | X lift subflow done | 軸2流程 | S2xx成功完成時SET，下一次進入前RST。 | 主流程成功銜接必要條件。 |
| M6001 | HMI正向啟動 | HMI forward start | HMI自動 | 儲存盒到上機盒啟動 | 觸發M1102 |
| M6002 | HMI正向啟動 | HMI forward start | HMI自動 | Momentary，啟動M1102。 | 依最新驗證表採M6002/M6003為正反啟動。 |
| M6003 | HMI反向啟動 | HMI reverse start | HMI自動 | Momentary，啟動M1103。 | Auto Busy中禁止。 |
| M6005 | HMI Auto Busy顯示 | HMI auto busy display | HMI自動 | 顯示M1004 |  |
| M6006 | Barcode生產前掃碼OK | Pre-production barcode OK | HMI/Barcode | 允許自動生產前置條件 | 由Barcode讀取/比對結果或人工確認產生 |
| M6030 | 人工料態套用請求 | Manual material state apply request | HMI | 工程權限按下套用，PLC確認條件後寫入D6100。 | Auto Busy時禁止。 |
| M6031 | 人工料態套用確認 | Manual material state apply confirmed | HMI | PLC完成D6100人工修正後SET一掃描或短保持。 | HMI顯示完成。 |
| M6040 | HMI異常復歸 | HMI alarm reset | HMI Reset | 只復歸可復歸警報。 | 不自動重新啟動。 |
| M6041 | HMI伺服復歸 | HMI servo reset | HMI Reset | 伺服/軸卡異常復歸。 | 需軸停止。 |
| M6042 | HMI安全復歸請求 | HMI safety reset request | HMI Reset | 條件成立後瞬時Y0000。 | 安全繼電器復歸。 |
| M6100 | X已離開檢查位且允許Z動作 | X clear for Z | X/Z交握 | 只能在X已移到安全/等待位置且到位確認後SET。 | 不得與X移動命令同時SET。 |
| M6101 | X要求Z/Barcode流程 | X request Z barcode flow | X/Z交握 | X主流程要求Z升降+Barcode開始。 | S120/S162後SET。 |
| M6102 | Z流程已接收/Busy | Z flow acknowledge busy | X/Z交握 | Z流程開始後SET，完成或異常RST。 | 主流程可用來確認Z有接手。 |
| M6105 | X/Z交握Timeout | X/Z handshake timeout | X/Z交握 | 等待ACK/Done逾時。 | Alarm K171。 |
| M6008 | HMI Abort中止 | HMI abort | HMI自動 | 中止目前流程，轉異常/安全停止出口。 | 不同於M6004 Normal Stop。 |
| M6300 | Barcode Enable | Barcode compare enable | 功能Enable | ON時Storage Barcode Valid必須成立才可Auto Start。 | OFF時Barcode結果記錄BYPASS。 |
| M6301 | Storage Barcode Valid | Storage barcode valid | Barcode | 工單/儲存盒條碼已輸入且有效。 | Auto Ready必要條件。 |
| M6302 | Mask Barcode Read Request | Mask barcode read request | Barcode | Z到Barcode高度後觸發讀碼。 |  |
| M6303 | Mask Barcode Read Done | Mask barcode read done | Barcode | 讀碼完成。 |  |
| M6304 | Barcode Compare OK | Barcode compare OK | Barcode | Mask Barcode等於Storage Barcode。 | OK才進Visual或放片。 |
| M6305 | Barcode Compare NG | Barcode compare NG | Barcode | 比對失敗。 | 正向Return Storage；反向Return Load。 |
| M6306 | Barcode Bypass | Barcode bypass | Barcode | Barcode Enable OFF時ON。 | HMI需明顯顯示。 |
| M6500 | Visual Enable | Visual inspection enable | 目視檢查 | ON時Barcode OK後HMI彈窗Hold。 | OFF時Visual結果記錄BYPASS。 |
| M6501 | Visual Request | Visual inspection request | 目視檢查 | PLC要求HMI跳出目視確認。 |  |
| M6502 | Visual OK | Visual OK | 目視檢查 | 人工判定OK。 |  |
| M6503 | Visual NG | Visual NG | 目視檢查 | 人工判定NG。 | 走Return Sequence。 |
| M6504 | Visual Bypass | Visual bypass | 目視檢查 | Visual Enable OFF時ON。 |  |
| M6600 | Cycle Complete Popup Request | Cycle complete popup request | 流程完成 | 流程完成後要求HMI顯示可開門/取盒。 |  |
| M6601 | Door Unlock Request | Door unlock request | 流程完成 | 完成流程後PLC送Y0027請求。 | 只送請求，不取代安全。 |
| M6602 | Storage Box Release Permit | Storage box release permit | 流程完成 | 儲存盒盒蓋關閉後允許破真空。 | X0052 ON。 |
| M6603 | Load Box Release Permit | Load box release permit | 流程完成 | 上機盒盒蓋關閉後允許破真空。 | X0053 ON。 |
| M6604 | Cycle Complete | Cycle complete | 流程完成 | Storage/Load Box Present皆OFF後完成。 | X0022/X0024 OFF。 |
