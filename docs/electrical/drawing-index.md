# Electrical Drawing Index

This document defines the electrical drawings required for the PTC mask transfer system. It is a sanitized drawing plan, not a raw DWG export.

## Drawing Set

| Sheet | Drawing | Purpose |
|---|---|---|
| E01 | Main power distribution | Main breaker, branch breakers, contactors, 24 VDC power supply, PE grounding. |
| E02 | 24 VDC distribution | Fuse branches for PLC/HMI/network/sensors/valves/brakes/barcode/static eliminator. |
| E03 | PLC base and expansion | FX5U-64MT/ES, FX5-16EX/ES, common wiring, 24 VDC input/output commons. |
| E04 | PLC input list | Origin, limits, photo sensors, reed switches, vacuum OK, alarm/check inputs. |
| E05 | PLC output list | Contactors, valves, vacuum, tower light, buzzer, barcode trigger, static eliminator control. |
| E06 | Servo network | FX5-40SSC-S to MR-J4-B axes by SSCNET cable. |
| E07 | Servo amplifier power | MR-J4-10B / MR-J4-20B main power, control power, brake, STO, regenerative terminals. |
| E08 | Servo motor wiring | HG-KR13K / HG-KR13B / HG-KR23 / HG-KR23B motor power, encoder, brake cables. |
| E09 | HMI and Ethernet | PFXET6400WAD, FX5U Ethernet, SR-1000W, EKI-2525-BE, service port. |
| E10 | Barcode reader | SR-1000W power, Ethernet, trigger, OK/NG, communication register notes. |
| E11 | Pneumatic control | MVSY-156-5B4 valve manifold, cylinders, reed switches, air supply. |
| E12 | Vacuum control | Two AZK-X-NE-D groups, vacuum ON, release, vacuum OK, suction pad groups. |
| E13 | Static eliminator | DTY-ELK01, DTY-NZK-300B, 24 VDC, FG, H.V OFF, alarm/check, air supply. |
| E14 | Safety / emergency stop | EMO loop, contactor interruption, servo STO concept, reset logic. |
| E15 | Terminal and cable schedule | Terminal block numbers, cable numbers, wire colors, field connector assignment. |

## Excluded From Git

- Raw DWG/DXF files.
- Customer-supplied drawings.
- Quotation drawings.
- Vendor manuals.
- Full BOM spreadsheet.
- Password files.

