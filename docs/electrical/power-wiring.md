# Power Wiring Plan

## Main Power

```text
AC input
-> NV30-SN 3P30A delayed earth leakage breaker
-> branch breakers
-> servo contactors / 24 VDC power supply / auxiliary loads
```

Incoming power conditions are not final. Confirm voltage, phase, neutral availability, grounding system, and available short-circuit capacity before final breaker and wire sizing.

## Branch Breakers

| Branch | Proposed Breaker | Load |
|---|---|---|
| QF1 | NV30-SN 3P30A | Main incoming power. |
| QF2 | BHA32C4 | NDR-240-24 input. |
| QF3 | BHA32C10 | Auxiliary AC branch, confirm final use. |
| QF4-QF7 | BHA33C5 | Provisional four servo amplifier branches. Final rating requires servo input current, inrush, wire size, and manufacturer recommendation check. |

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
| FU1 | TBD | PLC CPU and expansion. |
| FU2 | TBD | HMI, Ethernet switch, and communication devices. |
| FU3 | TBD | Barcode reader and related I/O. |
| FU4 | TBD | Sensors and input devices. |
| FU5 | TBD | Solenoid valves and vacuum generator coils. |
| FU6 | TBD | Servo motor brake power. |
| FU7 | TBD | Static eliminator and spare service branch. |

Fuse ratings must be calculated from actual load current plus maintenance requirements. The current BOM quantity of 4 fuse holders does not match this provisional branch plan.

## Safety Power Interruption

Safety architecture is not final. The electrical design must define:

- Dual-channel E-stop loop.
- Safety relay or safety controller.
- Contactor interruption method.
- Servo STO wiring.
- Manual reset circuit.
- Safety feedback / EDM if required.
- Door or guard interlock requirements.
