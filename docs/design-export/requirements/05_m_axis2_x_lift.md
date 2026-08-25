# 05_M軸2_X升降

> Exported from `docs/PTC_Mask_Transfer_4Axis_Design_Draft.xlsx`.

| 05_M軸2_X升降 |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- |
| 位址 | 中文名稱 | English | 分類 | 用途 | 備註 |
| M4300 | 軸2_X升降_狀態_速度控制中標誌 | Axis2 X lift speed control active | 軸2_X升降 | 軸卡狀態 |  |
| M4301 | 軸2_X升降_狀態_速度/位置切換鎖存 | Axis2 X lift speed/position latch | 軸2_X升降 | 軸卡狀態 |  |
| M4302 | 軸2_X升降_狀態_指令到位標誌 | Axis2 X lift command in position | 軸2_X升降 | 軸卡狀態 |  |
| M4303 | 軸2_X升降_狀態_原點回歸請求 | Axis2 X lift home return request state | 軸2_X升降 | 軸卡狀態 |  |
| M4304 | 軸2_X升降_狀態_原點回歸完成 | Axis2 X lift home return complete | 軸2_X升降 | 軸卡狀態 |  |
| M4309 | 軸2_X升降_狀態_軸報警檢測 | Axis2 X lift axis alarm detected | 軸2_X升降 | 軸卡狀態 |  |
| M4312 | 軸2_X升降_狀態_M代碼ON | Axis2 X lift M-code ON | 軸2_X升降 | 軸卡狀態 |  |
| M4313 | 軸2_X升降_狀態_錯誤檢測 | Axis2 X lift error detected | 軸2_X升降 | 軸卡狀態 |  |
| M4314 | 軸2_X升降_狀態_啟動完成 | Axis2 X lift start complete | 軸2_X升降 | 軸卡狀態 |  |
| M4315 | 軸2_X升降_狀態_定位完成 | Axis2 X lift positioning complete | 軸2_X升降 | 軸卡狀態 |  |
| M4316 | 軸2_X升降_初始化 | Axis2 X lift initialize | 軸2_X升降 | MAIN初始化觸發 |  |
| M4327 | 軸2_X升降_BUSY | Axis2 X lift BUSY | 軸2_X升降 | U1\G3150 bit狀態 |  |
| M4331 | 軸2_X升降_JOG- | Axis2 X lift JOG- | 軸2_X升降 | HMI手動 |  |
| M4332 | 軸2_X升降_JOG+ | Axis2 X lift JOG+ | 軸2_X升降 | HMI手動 |  |
| M4320 | 軸2_X升降_上位命令 | Axis2 X lift 上位 command | 軸2_X升降 | 定位命令 |  |
| M4321 | 軸2_X升降_儲存盒取光罩位命令 | Axis2 X lift 儲存盒取光罩位 command | 軸2_X升降 | 定位命令 |  |
| M4322 | 軸2_X升降_儲存盒放光罩位命令 | Axis2 X lift 儲存盒放光罩位 command | 軸2_X升降 | 定位命令 |  |
| M4323 | 軸2_X升降_檢查位取光罩位命令 | Axis2 X lift 檢查位取光罩位 command | 軸2_X升降 | 定位命令 |  |
| M4324 | 軸2_X升降_檢查位放光罩位命令 | Axis2 X lift 檢查位放光罩位 command | 軸2_X升降 | 定位命令 |  |
| M4325 | 軸2_X升降_上機盒取光罩位命令 | Axis2 X lift 上機盒取光罩位 command | 軸2_X升降 | 定位命令 |  |
| M4326 | 軸2_X升降_上機盒放光罩位命令 | Axis2 X lift 上機盒放光罩位 command | 軸2_X升降 | 定位命令 |  |
| M4327 | 軸2_X升降_真空確認位命令 | Axis2 X lift 真空確認位 command | 軸2_X升降 | 定位命令 |  |
| M4350 | 軸2_上位到位 | Axis2 upper position complete | 到位 | Busy OFF + InPosition + Error<=D4300。 |  |
| M4351 | 軸2_儲存盒取位到位 | Axis2 storage pick position complete | 到位 | 對D4412/D4434。 |  |
| M4352 | 軸2_儲存盒放位到位 | Axis2 storage place position complete | 到位 | 對D4414/D4436。 |  |
| M4353 | 軸2_檢查位取位到位 | Axis2 inspection pick position complete | 到位 | 對D4416/D4438。 |  |
| M4354 | 軸2_檢查位放位到位 | Axis2 inspection place position complete | 到位 | 對D4418/D4440。 |  |
| M4355 | 軸2_上機盒取位到位 | Axis2 load box pick position complete | 到位 | 對D4420/D4442。 |  |
| M4356 | 軸2_上機盒放位到位 | Axis2 load box place position complete | 到位 | 對D4422/D4444。 |  |
| M4357 | 軸2_真空確認位到位 | Axis2 vacuum check position complete | 到位 | 對D4424/D4446。 |  |
| M4330 | 軸2_X升降_共用真空確認位命令 | Axis2 common vacuum check position command | 定位命令 | 取片後上升約10mm真空確認。 | 不可作JOG。 |
| M1227 | X升降子流程Done旗標 | X lift sub-flow done | 軸2_X升降 | S200完成後SET | 主流程讀取後RST，和M1226 Busy/M1228 Alarm成一組 |
| M4333 | 軸2_X升降_儲存盒真空確認位命令_預留 | Axis2 storage vacuum check command spare | 軸2_X升降 | 預留 | 若儲存盒真空確認高度不同時啟用 |
| M4334 | 軸2_X升降_檢查位真空確認位命令_預留 | Axis2 inspection vacuum check command spare | 軸2_X升降 | 預留 | 若檢查位真空確認高度不同時啟用 |
| M4335 | 軸2_X升降_上機盒真空確認位命令_預留 | Axis2 tool-box vacuum check command spare | 軸2_X升降 | 預留 | 若上機盒真空確認高度不同時啟用 |
| M4317 | 軸2_X升降_Ready | Axis2 X lift ready | 狀態 | 安全OK + MC送電 + Servo ON + Brake release condition + Alarm OFF + 軸卡Ready。 | 垂直軸需含煞車互鎖。 |
| M4318 | 軸2_X升降_Alarm | Axis2 X lift alarm | 狀態 | 軸卡Alarm/伺服Alarm/Timeout/極限/煞車異常總成。 | Alarm Detail需顯示來源。 |
| M4340 | 軸2_X升降_JOG+ | Axis2 jog plus | 手動調機 | HMI M6014驅動，需M6200允許。 |  |
| M4341 | 軸2_X升降_JOG- | Axis2 jog minus | 手動調機 | HMI M6013驅動，需M6200允許。 |  |
