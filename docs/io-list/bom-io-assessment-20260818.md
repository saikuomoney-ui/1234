# BOM I/O Assessment - 2026-08-18

Source reviewed: PTC mask transfer purchasing BOM workbook on the project NAS, sheet `BOM_20260812`.

The raw BOM workbook is not committed to Git. This file keeps only the sanitized I/O engineering assessment.

## PLC Capacity

| Hardware | Qty | Effective I/O |
|---|---:|---:|
| FX5U-64MT/ES | 1 | 32 DI / 32 transistor DO |
| FX5-16EX/ES | 1 | +16 DI |
| Total available |  | 48 DI / 32 DO |

Motion is assumed to use `FX5-40SSC-S + MR-J4-B` over SSCNET III/H. Servo positioning therefore does not consume PLC pulse outputs `Y000` to `Y007`.

## I/O Count Summary

| Group | DI | DO | Notes |
|---|---:|---:|---|
| Safety relay and contactor feedback | 5 | 1 | G9SE/G9SB status plus 4 contactor feedbacks; reset pulse from PLC output. |
| Door locks | 6 | 3 | 3 doors, door closed + lock confirmed inputs, unlock coil outputs. |
| E-stop individual monitor | 4 | 0 | Optional but recommended for HMI diagnosis. Safety contacts still go to safety relay. |
| Axis / mechanism sensors from current BOM | 1 | 0 | EE-SX674 currently only one listed. Add more if final mechanical design needs origin/limit sensors. |
| Cylinder reed switches | 12 | 0 | BOM row states not purchased, but they still consume PLC inputs if cylinders use them. |
| Box / mask photo sensors | 5 | 0 | Box detection x4, mask detection x1. |
| Pneumatic solenoid valves | 0 | 8 | MVSY-156-4E2 x4, double coil, 2 outputs each. |
| Vacuum generators | 2 | 4 | Two stations. Assumes Vacuum ON + release/blow outputs and vacuum OK input per station. |
| Tower light / buzzer | 0 | 4 | Red, orange, green, buzzer. |
| Static eliminator | 2 | 1 | Assumes CHECK and ALARM inputs, H.V OFF or enable output. |
| KEYENCE SR-1000W barcode reader | 0 | 0 | Preferred communication by Ethernet / MC Protocol. Hard trigger/status I/O optional. |
| Optional barcode hard I/O | 2 | 1 | Trigger, read OK, read NG if Ethernet handshake is not used. |
| Servo system hard I/O | 0 | 0 | Servo status and alarms should be read by SSCNET. Brake control handled by servo amplifier. |

Recommended base count with individual E-stop monitoring and Ethernet barcode:

| Type | Used | Available | Margin |
|---|---:|---:|---:|
| DI | 37 | 48 | 11 |
| DO | 21 | 32 | 11 |

Worst case if barcode hard I/O is added:

| Type | Used | Available | Margin |
|---|---:|---:|---:|
| DI | 39 | 48 | 9 |
| DO | 22 | 32 | 10 |

Conclusion: `FX5U-64MT/ES + FX5-16EX/ES` is enough for the current BOM concept. `FX5U-64MT/ES` alone is tight or insufficient if door lock diagnosis, contactor feedback, reed switches, and safety diagnosis are all retained.

## Recommended PLC Input Allocation

| Device | Function | Suggested point | Source |
|---|---|---|---|
| Safety relay auxiliary output | Safety OK | X000 | G9SE X1 or equivalent status contact. |
| Contactor K1 auxiliary | X traverse servo power feedback | X001 | Use contactor auxiliary contact. |
| Contactor K2 auxiliary | X lift servo power feedback | X002 | Use contactor auxiliary contact. |
| Contactor K3 auxiliary | Z rotation servo power feedback | X003 | Use contactor auxiliary contact. |
| Contactor K4 auxiliary | Z lift servo power feedback | X004 | Use contactor auxiliary contact. |
| EMO1 auxiliary | E-stop 1 monitor | X005 | Diagnosis only, not safety control. |
| EMO2 auxiliary | E-stop 2 monitor | X006 | Diagnosis only, not safety control. |
| EMO3 auxiliary | E-stop 3 monitor | X007 | Diagnosis only, not safety control. |
| EMO4 auxiliary | E-stop 4 monitor | X010 | Diagnosis only, not safety control. |
| Door lock 1 | Door closed | X011 | Auxiliary contact. |
| Door lock 1 | Door locked | X012 | Auxiliary contact. |
| Door lock 2 | Door closed | X013 | Auxiliary contact. |
| Door lock 2 | Door locked | X014 | Auxiliary contact. |
| Door lock 3 | Door closed | X015 | Auxiliary contact. |
| Door lock 3 | Door locked | X016 | Auxiliary contact. |
| EE-SX674 | Origin / position sensor | X017 | Function to be named by mechanical layout. |
| Reed switch 1 | Cylinder position | X020 | Final cylinder name pending. |
| Reed switch 2 | Cylinder position | X021 | Final cylinder name pending. |
| Reed switch 3 | Cylinder position | X022 | Final cylinder name pending. |
| Reed switch 4 | Cylinder position | X023 | Final cylinder name pending. |
| Reed switch 5 | Cylinder position | X024 | Final cylinder name pending. |
| Reed switch 6 | Cylinder position | X025 | Final cylinder name pending. |
| Reed switch 7 | Cylinder position | X026 | Final cylinder name pending. |
| Reed switch 8 | Cylinder position | X027 | Final cylinder name pending. |
| Reed switch 9 | Cylinder position | X030 | Final cylinder name pending. |
| Reed switch 10 | Cylinder position | X031 | Final cylinder name pending. |
| Reed switch 11 | Cylinder position | X032 | Final cylinder name pending. |
| Reed switch 12 | Cylinder position | X033 | Final cylinder name pending. |
| Box sensor 1 | Box detection | X034 | Model pending. |
| Box sensor 2 | Box detection | X035 | Model pending. |
| Box sensor 3 | Box detection | X036 | Model pending. |
| Box sensor 4 | Box detection | X037 | Model pending. |
| Mask sensor | Mask detection | X040 | Model pending. |
| Vacuum generator 1 | Vacuum OK | X041 | AZK-X-NE-D NPN vacuum switch. |
| Vacuum generator 2 | Vacuum OK | X042 | AZK-X-NE-D NPN vacuum switch. |
| Static eliminator | CHECK | X043 | DTY-ELK01 output. |
| Static eliminator | ALARM | X044 | DTY-ELK01 output. |
| Spare | Spare input | X045-X057 | 11 points. |

## Recommended PLC Output Allocation

| Device | Function | Suggested point | Source |
|---|---|---|---|
| Safety reset relay | G9SE/G9SB manual reset pulse | Y000 | 0.3 to 0.5 s pulse from PLC after HMI Reset and permissive checks. |
| Door lock 1 | Unlock solenoid | Y001 | Mechanical lock / power-to-unlock. |
| Door lock 2 | Unlock solenoid | Y002 | Mechanical lock / power-to-unlock. |
| Door lock 3 | Unlock solenoid | Y003 | Mechanical lock / power-to-unlock. |
| Solenoid valve 1A | Cylinder valve coil A | Y004 | MVSY-156-4E2. |
| Solenoid valve 1B | Cylinder valve coil B | Y005 | MVSY-156-4E2. |
| Solenoid valve 2A | Cylinder valve coil A | Y006 | MVSY-156-4E2. |
| Solenoid valve 2B | Cylinder valve coil B | Y007 | MVSY-156-4E2. |
| Solenoid valve 3A | Cylinder valve coil A | Y010 | MVSY-156-4E2. |
| Solenoid valve 3B | Cylinder valve coil B | Y011 | MVSY-156-4E2. |
| Solenoid valve 4A | Cylinder valve coil A | Y012 | MVSY-156-4E2. |
| Solenoid valve 4B | Cylinder valve coil B | Y013 | MVSY-156-4E2. |
| Vacuum 1 | Vacuum ON | Y014 | AZK station 1. |
| Vacuum 1 | Release / blow | Y015 | AZK station 1. |
| Vacuum 2 | Vacuum ON | Y016 | AZK station 2. |
| Vacuum 2 | Release / blow | Y017 | AZK station 2. |
| Tower light | Red | Y020 | TPFQB5-L73ROG. |
| Tower light | Orange | Y021 | TPFQB5-L73ROG. |
| Tower light | Green | Y022 | TPFQB5-L73ROG. |
| Tower light | Buzzer | Y023 | TPFQB5-L73ROG. |
| Static eliminator | H.V OFF / enable | Y024 | DTY-ELK01. |
| Spare | Spare output | Y025-Y037 | 11 points. |

Optional if hardwired barcode I/O is used instead of only Ethernet:

| Device | Function | Suggested point |
|---|---|---|
| SR-1000W | Trigger | Y025 |
| SR-1000W | Read OK | X045 |
| SR-1000W | Read NG / Error | X046 |

## BOM Rows That Consume PLC I/O

| BOM item | Model | Qty | DI | DO | Notes |
|---:|---|---:|---:|---:|---|
| 20 | EE-SX674 | 1 | 1 | 0 | Photo sensor input. |
| 23 | Cylinder reed switches | 12 | 12 | 0 | Not purchased in BOM, but point count must include them if used. |
| 32 | TPFQB5-L73ROG | 1 | 0 | 4 | 3-color light plus buzzer. |
| 34 | SR-1000W | 1 | 0 | 0 | Ethernet / MC Protocol preferred. |
| 37 | Box photo sensors | 4 | 4 | 0 | Model pending. |
| 38 | Mask photo sensor | 1 | 1 | 0 | Model pending. |
| 39 | MVSY-156-4E2-DC24-LJ1 | 4 | 0 | 8 | Double coil valves. |
| 44 | AZK-X-NE-D | 2 | 2 | 4 | Assumes vacuum ON, release, vacuum OK per unit. |
| 48 | DTY-ELK01 | 1 | 2 | 1 | CHECK, ALARM, H.V OFF / enable. |
| 53 | TN2IK7R-L1AB | 4 | 4 | 0 | Individual PLC monitor only if auxiliary contact is available. Safety requires dual NC contacts. |
| 82 | D4NL-2DFA-B | 3 | 6 | 3 | Door closed, locked, unlock coil. Safety contacts go to safety relay. |
| 84 | G9SB-201-D / G9SE-201 | 1 | 1 | 1 | Safety OK input and manual reset pulse output. Model must be corrected before purchase. |

## BOM Rows That Do Not Consume PLC I/O

| BOM item range | Items |
|---|---|
| 1-19 | HMI, PLC, SSCNET module/cables, servo amplifiers, servo motors, servo cables. |
| 21 | EE-1006 sensor cable only. |
| 25-31 | Power supply, grounding, contactors, breakers, leakage breaker. Contactors use safety relay output, not PLC output. |
| 33 | Ethernet switch. |
| 35-36 | Barcode power cable and bracket. |
| 40-43 | Valve cables, manifold, silencer, regulator. |
| 45-47 | Terminal covers and 60 A terminal blocks. |
| 49-52 | Static nozzle and fuse parts. |
| 54-81 | E-stop guards, relays/sockets, wiring accessories, DIN rail, CCTV, IPC, terminals, ducting, screws. Relays are interface parts; they do not add extra PLC functions by themselves. |
| 83 | D4DS-K1 operation keys. |

## Design Warnings

- `G9SB-201-D` is not a confirmed standard OMRON model in previous checks. Confirm whether the intended part is `G9SE-201 DC24` or `G9SB-200-D AC/DC24` before purchase.
- `TN2IK7R-L1AB` is listed as `1a1b`. A dual-channel safety E-stop normally needs two NC contacts for the safety relay. If individual PLC diagnosis is also required, select an E-stop contact block combination with `2NC + auxiliary contact`.
- If `S-P09S AC220V 1a` only has one NO auxiliary contact, it is useful for PLC feedback but not ideal for a safety relay EDM/feedback loop that requires NC feedback contacts. Confirm auxiliary contact configuration.
- Door lock safety contacts must go to the safety relay. PLC inputs are only for HMI diagnosis and sequence permissive logic.
- PLC output current and COM group current must still be checked before deciding which DC24 loads can be driven directly without intermediate relays.
