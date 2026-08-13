# Power Wiring Plan

## Main Power

```text
AC input
-> NV30-SN 3P30A delayed earth leakage breaker
-> branch breakers
-> servo contactors / 24 VDC power supply / auxiliary loads
```

## Branch Breakers

| Branch | Proposed Breaker | Load |
|---|---|---|
| QF1 | NV30-SN 3P30A | Main incoming power. |
| QF2 | BHA32C4 | NDR-240-24 input. |
| QF3 | BHA32C10 | Auxiliary AC branch, confirm final use. |
| QF4-QF7 | BHA33C5 | Four servo amplifier branches. |

## Servo Main Power Contactors

| Contactor | Load |
|---|---|
| KM1 | MR-J4-20B, X traverse. |
| KM2 | MR-J4-10B, X lift. |
| KM3 | MR-J4-10B, Z rotation. |
| KM4 | MR-J4-20B, Z lift. |

`S-P09S AC220V` coils must not be driven directly by FX5U transistor outputs. Use an interposing relay or isolated contact.

## 24 VDC Fuse Branches

| Fuse | Proposed Rating | Load |
|---|---:|---|
| FU1 | 1 A | PLC, HMI, Ethernet switch, barcode communication. |
| FU2 | 2 A | Sensors and input devices. |
| FU3 | 3 A | Solenoid valves and vacuum generator coils. |
| FU4 | 3 A | Servo motor brake power. |
| FU5 | 2 A | Static eliminator and spare service branch. |

If BOM keeps only 4 fuse holders, combine FU5 into FU3 or add one more fuse holder. Five branches are preferred for maintenance.

