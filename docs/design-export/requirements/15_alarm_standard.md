# 15_異常警報標準

> Exported from `docs/PTC_Mask_Transfer_4Axis_Design_Draft.xlsx`.

| 代碼 |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- |
| K101 | Safety Relay NG | Common/停機 | X0000 OFF | Stop / Safety hardware | M6042 Safety Reset |
| K102 | Air Pressure NG | Common/停機 | X0001 OFF | Stop; preserve mask holding strategy | M6040 after air OK |
| K150 | Axis1 Move Timeout/Error | Axis1/停機 | Move timeout / error>D4100 | S189 | Init required |
| K160 | Axis2 Move Timeout/Error | Axis2/停機 | Move timeout / error>D4300 | M1228→S189 | Init required |
| K171 | X/Z Handshake Timeout | Common/停機 | Wait M6102/M6103 timeout | Stop X/Z; clear stale handshake |  |
| K180 | Cylinder/Gripper Timeout | Pneumatic/停機 | Grip/locator feedback timeout | Stop next motion | Check valve/reed |
| K200 | Arm Vacuum Build Fail | Vacuum-Arm/停機 | X手臂取片時X0027未ON | Do not lift/move | 不得混用X0030/X0031。 |
| K201 | Arm Vacuum Release Fail | Vacuum-Arm/停機/警告 | 放片破真空後X0027未OFF | Hold step | 檢查Y0016/管路。 |
| K202 | Storage Box Vacuum Fail | Vacuum-Storage/停機/警告 | 儲存盒真空建立/保持/釋放與X0030不一致 | Hold storage box step | 盒體固定用，不能當手臂Pick真空。 |
| K203 | Load Box Vacuum Fail | Vacuum-Load/停機/警告 | 上機盒真空建立/保持/釋放與X0031不一致 | Hold load box step | 盒體固定用，不能當手臂Pick真空。 |
| K210 | Ionizer Check | Process/警告 | X0032依實機定義為Check異常/維護 | Warn only unless owner requires stop | 需確認極性。 |
| K211 | Ionizer Alarm | Process/停機 | X0033 ON | Stop Auto |  |
| K230 | FFU Alarm | Process/警告/停機待定 | X0037 ON / X0036 OFF | No start or safe stop | Owner criteria |
| K240 | Axis3 Z lift fault | Axis3/停機 | Servo/position/timeout | Block X entry | Init required |
| K250 | Axis4 manual fault | Axis4/警告/停機 | Manual rotation fault | Stop Axis4 | Engineer reset |
| K270 | 儲存盒關蓋等效條件未成立 | End cycle/警告 | 等待X0023 OFF逾時 | 禁止Y0020 | 確認X0023 OFF是否等同關蓋。 |
| K271 | 儲存盒破真空未完成 | End cycle/警告/停機 | Y0020 ON後X0030未OFF且逾時 | 禁止Cycle End |  |
| K272 | 上機盒破真空未完成 | End cycle/警告/停機 | Y0022 ON後X0031未OFF且逾時 | 禁止Cycle End |  |
| K273 | 兩盒未取出 | End cycle/警告 | 等待X0022 OFF AND X0024 OFF逾時 | 保持完成提示，不進下一循環 |  |
| K274 | 上機盒關蓋等效條件未成立 | End cycle/警告 | 等待X0025 OFF逾時 | 禁止Y0022 | 確認X0025 OFF是否等同關蓋。 |
| K310 | LR locator extend timeout | Z station/停機 | X0016 not ON | Stop S300 |  |
| K311 | FB locator extend timeout | Z station/停機 | X0020 not ON | Stop S300 |  |
| K312 | Inspection Mask absent | Z station/停機 | X0026 OFF before Z rise | Stop S300 |  |
| K320 | Z Platform move fault | Axis3/停機 | M4551 timeout/error | Stop S300 |  |
| K321 | Locator retract timeout | Z station/停機 | X0017 AND X0021 not complete | Block Barcode move |  |
| K322 | Z Barcode move fault | Axis3/停機 | M4552 timeout/error | Stop S300 |  |
| K330 | Barcode read timeout | Barcode/停機或人工 | No ReadDone within D6422 | Fault/operator handling | Different from compare NG |
| K331 | Barcode compare NG | Process Reject | M6305 ON | RETURN route | 不是設備故障，除非業主要求停機。 |
| K340 | Visual timeout/invalid response | Visual/人工 | Visual Request unanswered / invalid | Hold/Alarm | Visual NG itself=RETURN |
| K350 | Z Home return fault | Axis3/停機 | M4550 timeout/error | Block X entry |  |
| K360 | Dual-coil interlock fault | Pneumatic/停機 | Y0011&Y0012 or Y0013&Y0014 simultaneous | Force same-group outputs OFF + Alarm | Program/HMI fault |
