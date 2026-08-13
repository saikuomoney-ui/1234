# Control BOM Summary

This is a sanitized engineering BOM summary for source control. It intentionally excludes supplier pricing, quotations, raw purchasing spreadsheets, manuals, PDFs, CAD files, and customer confidential documents.

## Control Core

| Item | Brand | Model | Qty | Notes |
|---|---|---:|---:|---|
| PLC | Mitsubishi | FX5U-64MT/ES | 1 | AC power, 32 inputs / 32 transistor outputs. BOM text must not describe this as relay output. |
| Input expansion | Mitsubishi | FX5-16EX/ES | 1 | 16-point input expansion. |
| HMI | Pro-face | PFXET6400WAD | 1 | ET6000, 7 inch, 800 x 480, 24 VDC. |
| Ethernet switch | Advantech | EKI-2525-BE | 1 | 5-port industrial Ethernet switch. |
| 24 VDC power supply | MEAN WELL | NDR-240-24 | 1 | 24 VDC, 10 A. |

## Servo System

| Axis | Amplifier | Motor | Brake | Qty | Notes |
|---|---|---|---|---:|---|
| X traverse | MR-J4-20B | HG-KR23 | No | 1 | 200 W. |
| X lift | MR-J4-10B | HG-KR13B | Yes | 1 | 100 W. |
| Z rotation | MR-J4-10B | HG-KR13K | No | 1 | 100 W, keyway shaft. |
| Z lift | MR-J4-20B | HG-KR23B | Yes | 1 | 200 W. |

| Cable | Model | Qty | Notes |
|---|---|---:|---|
| SSCNET cable | MR-J3BUS015M | 3 | Servo network short links. |
| SSCNET cable | MR-J3BUS2M | 1 | Servo network long link. |
| Motor power cable, 1 m | MR-PWS1CBL1M-A2-HT | 1 | Confirm `-HT` with supplier; Mitsubishi standard suffix is commonly `-H`. |
| Encoder cable, 1 m | MR-J3ENCBL1M-A2-HT | 1 | Confirm `-HT` with supplier. |
| Brake cable, 1 m | MR-BKS1CBL1M-A2-HT | 1 | For brake motor. |
| Motor power cable, 2 m | MR-PWS1CBL2M-A2-HT | 2 | Confirm final length on layout. |
| Encoder cable, 2 m | MR-J3ENCBL2M-A2-HT | 2 | Confirm final length on layout. |
| Motor power cable, 3 m | MR-PWS1CBL3M-A2-HT | 1 | From BOM part reference. |
| Encoder cable, 3 m | MR-J3ENCBL3M-A2-HT | 1 | From BOM part reference. |
| Brake cable, 3 m | MR-BKS1CBL3M-A2-HT | 1 | From BOM part reference. |

## Power Protection

| Item | Brand | Model | Qty | Notes |
|---|---|---:|---:|---|
| Main earth leakage breaker | Shihlin | NV30-SN 3P30A delayed switching type | 1 | Main protection. |
| Servo branch breaker | Shihlin | BHA33C5 | 4 | BOM currently lists 4 pcs. Check whether 100 W axes can use 4 A instead of 5 A. |
| 24 V power branch breaker | Shihlin | BHA32C4 | 1 | Recommended for 24 VDC power supply input. |
| Auxiliary branch breaker | Shihlin | BHA32C10 | 1 | Confirm actual load assignment. |
| Contactor | Shihlin | S-P09S AC220V 1a | 4 | For servo main power contactor branches. Requires relay or isolated contact control. |
| External breaker handle | Shihlin | EH100N 3P/4P | 1 | Confirm mechanical panel fit. |
| Fuse holder | TEND | TFBR-101 | 4 | 24 VDC branch fusing. |
| Fuse indicator cover | TEND | TFB-101N DC | 4 | 24 VDC branch fusing. |
| Fuse | TEND | TFU-30-3A | 4 | Confirm branch allocation. |

## Relay Strategy

| Item | Brand | Model | BOM Qty | Recommended Qty | Notes |
|---|---|---:|---:|---:|---|
| Slim relay | IDEC | RJ2S-CLD-D24 | 17 | 6 if reducing relay usage | Keep relays for AC220V contactor control and spare isolation. |
| Relay socket | IDEC | SJ2S-07L | 17 | 6 if reducing relay usage | Match relay quantity. |

Relay reduction rule:

- Keep relay for AC220V contactor coils.
- Direct PLC transistor output is acceptable for small DC24V loads when current is within PLC output limits and surge protection is provided.
- Do not route servo pulse signals through mechanical relays.

## Barcode / Sensing

| Item | Brand | Model | Qty | Notes |
|---|---|---:|---:|---|
| Automatic focus code reader | KEYENCE | SR-1000W | 1 | Test with real 200 mm x 200 mm mask and barcode location. |
| Barcode reader power cable | TBD | TBD | 1 | Confirm KEYENCE cable model. |
| Barcode reader bracket | TBD | TBD | 1 | Confirm mounting height and field of view. |
| USB barcode reader | FILUX | FS-1600 | 1 | Optional / manual read. |
| Box detection photo sensor | TBD | TBD | 4 | Confirm with sensor vendor. |
| Mask detection photo sensor | TBD | TBD | 1 | Confirm with sensor vendor. |
| Cylinder reed switch | TBD | TBD | 12 | Model pending mechanical cylinder selection. |

## Pneumatic / Vacuum

| Item | Brand | Model | Qty | Notes |
|---|---|---:|---:|---|
| Solenoid valve manifold | Mindman | MVSY-156-5B4 | 1 | Four-station manifold. Confirm DC24V coil model. |
| Vacuum generator | AIRBEST | AZK-X-NE-D | 2 | High-vacuum type, NPN switch, DIN rail mounting. |
| Suction cup / holder | TBD | TBD | TBD | Confirm cup diameter, material, and quantity by box weight and surface. |
| Regulator / filter | TBD | TBD | TBD | Required for pneumatic supply. |

## Static Elimination

| Item | Brand | Model | Qty | Notes |
|---|---|---:|---:|---|
| Static eliminator controller | KOGANEI | DTY-ELK01 | 1 | Add to BOM if final. |
| Static eliminator nozzle | KOGANEI | DTY-NZK-300B | 1 | Recommended for 200 mm mask width margin. |
| Air solenoid / regulator / tubing | TBD | TBD | TBD | Required if ionized air is PLC controlled. |

## Items To Confirm Before Purchase

- Final PLC motion method: FX5-40SSC-S + MR-J4-B, or FX5U pulse output + MR-J4-A.
- Servo cable suffix `-HT` versus official Mitsubishi `-H` equivalent.
- KEYENCE SR-1000W cable and bracket part numbers.
- Final sensor models for box, mask, origin, and limits.
- Whether relay quantity will stay at 17 or reduce to 6.
- Static eliminator final nozzle length and air circuit.
- Vacuum cup sizes and holding force margin.

