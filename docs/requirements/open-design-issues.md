# Open Design Issues

This file tracks design items that must be closed before electrical drawings and purchasing are treated as final.

## Critical

| Level | Issue | Required decision |
|---|---|---|
| Red | Safety circuit definition is incomplete. | Define the safety architecture before final electrical drawing: safety relay or safety controller, dual-channel E-stop, guard door / interlock method, reset circuit, servo STO wiring, and target safety level such as PL or SIL where applicable. |
| Red | Safety control parts are missing from BOM. | Add formal safety control components to BOM after architecture selection. Do not rely on standard PLC outputs for safety functions. |
| Red | 24 VDC fuse allocation is not finalized. | Recalculate 24 VDC branch current and split PLC, HMI, network, barcode, sensors, valves, brakes, and static eliminator into maintainable fuse groups. |
| Red | Fuse BOM quantity does not match the power plan. | Align fuse holder, fuse indicator, and fuse rating quantities with the final FU branch count. |

## Major

| Level | Issue | Required decision |
|---|---|---|
| Orange | I/O document is still a concept, not a formal I/O list. | Expand to X/Y device numbers, COM group, NPN/PNP type, normal state, terminal number, cable number, and drawing reference. |
| Orange | Input point count has not been proven. | Expand all reed switches, box sensors, mask sensors, axis origins/limits, vacuum OK, static alarm/check, barcode inputs, and safety feedback before confirming 48 DI is enough. |
| Orange | Output point count has not been proven. | Expand all contactors, valves, vacuum outputs, brake outputs, static outputs, tower light, buzzer, barcode trigger, and reset outputs before confirming 32 DO is enough. |
| Orange | Six-relay strategy is still an assumption. | Verify every direct-driven DC24V load: coil current, inrush, surge suppression, PLC per-point current, and COM group total current. |
| Orange | Servo breaker selection is not coordinated. | Finalize MR-J4-10B / MR-J4-20B branch breaker ratings based on Mitsubishi recommendation, input current, inrush, wire size, and protection coordination. |
| Orange | Servo cable `-HT` suffix must be closed. | Confirm with supplier whether `-HT` is an orderable equivalent to Mitsubishi high-flex `-H` cable. |
| Orange | Barcode register map is conceptual. | Define MC Protocol mapping, device addresses, string format, byte order, trigger handshake, timeout, retry, and OK/NG behavior. |
| Orange | Vacuum generator signals depend on final AZK configuration. | Confirm AZK-X-NE-D valve and electrical configuration before finalizing vacuum ON / release / vacuum OK wiring. |

## Minor

| Level | Issue | Required decision |
|---|---|---|
| Yellow | Main power system conditions are missing. | Define incoming voltage, phase, neutral availability, grounding system, short-circuit capacity, and panel supply assumptions. |

