# PLC I/O Concept

This file is an I/O concept only. It is not yet a formal I/O list.

A formal I/O list must include PLC device number, signal name, normal state, NPN/PNP type, COM group, terminal number, cable number, drawing reference, and remarks.

## PLC Hardware

| Device | Model | Notes |
|---|---|---|
| PLC | FX5U-64MT/ES | 32 input / 32 NPN transistor output. |
| Input expansion | FX5-16EX/ES | Add 16 inputs. |
| Motion module | FX5-40SSC-S | Required if using MR-J4-B SSCNET motion architecture. |

## Inputs To Allocate

| Group | Signals |
|---|---|
| X traverse | Origin, left limit, right limit. |
| X lift | Origin, upper limit, lower limit. |
| Z rotation | Origin. |
| Z lift | Origin, upper limit, lower limit. |
| Barcode | Read OK, read NG or ready if hardwired. Ethernet data is handled separately. |
| Vacuum group 1 | Vacuum OK. |
| Vacuum group 2 | Vacuum OK. |
| Static eliminator | Alarm, check. |
| Pneumatic cylinders | Reed switch extend/retract signals. |
| Safety | EMO, door/interlock, reset confirmation. |
| Sensors | Box detection, mask detection. |

## Input Count Status

48 DI are available with FX5U-64MT/ES plus FX5-16EX/ES, but sufficiency is not proven yet. The following must be expanded before final confirmation:

- All cylinder reed switches.
- All origin and limit sensors.
- All box and mask detection sensors.
- Vacuum OK signals.
- Static eliminator alarm/check signals.
- Barcode hardwired status signals if used.
- Safety feedback signals.

## Outputs To Allocate

| Group | Signals | Relay Required |
|---|---|---|
| Servo power contactors | KM1-KM4 | Yes, because coils are AC220V. |
| Tower light | Red, orange, green, buzzer | No, if DC24V current is within PLC output limits. |
| Solenoid valves | MVSY-156 manifold outputs | No, if DC24V coils and surge protection are provided. |
| Vacuum group 1 | Vacuum ON, release/blow | No, confirm coil current. |
| Vacuum group 2 | Vacuum ON, release/blow | No, confirm coil current. |
| Barcode | Trigger | No. |
| Static eliminator | H.V OFF or air solenoid | No for H.V OFF input; relay optional for isolation. |

## Output Count Status

32 transistor outputs are likely enough when using FX5-40SSC-S / SSCNET motion, but this is not proven until all outputs are assigned. The following must be expanded before final confirmation:

- Servo power contactors.
- Valve manifold outputs.
- Vacuum generator vacuum/release outputs.
- Brake control outputs if separated.
- Static eliminator H.V OFF and/or air solenoid.
- Tower light and buzzer outputs.
- Barcode trigger and reset signals.
- Safety reset and non-safety control signals.

## Relay Minimum

| Use | Count |
|---|---:|
| AC220V contactor coils | 4 |
| Spare / isolation | 2 |
| Total recommended minimum | 6 |

The original BOM lists 17 relays. Six relays is only a working minimum for AC220V contactors plus spare isolation. Final relay reduction requires per-load current, inrush, surge suppression, and PLC COM group total current verification.
