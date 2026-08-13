# PLC I/O Plan

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

## Relay Minimum

| Use | Count |
|---|---:|
| AC220V contactor coils | 4 |
| Spare / isolation | 2 |
| Total recommended minimum | 6 |

The original BOM lists 17 relays. Use 17 if following relay-isolation style for all outputs. Use 6 if reducing relays and directly driving DC24V loads.

