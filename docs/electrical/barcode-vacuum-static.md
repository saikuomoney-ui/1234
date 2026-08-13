# Barcode, Vacuum, and Static Eliminator Wiring

## KEYENCE SR-1000W Barcode Reader

Recommended connection:

```text
SR-1000W
-> 24 VDC power
-> Ethernet switch EKI-2525-BE
-> FX5U Ethernet / MC Protocol
```

PLC output may be used for read trigger. Barcode result, center coordinate, and OK/NG should be transferred by Ethernet whenever possible.

Register concept:

| Device | Purpose |
|---|---|
| M100 | Read trigger command. |
| M101 | Read complete. |
| M102 | Read OK. |
| M103 | Read NG. |
| D5000-D5030 | Barcode string. |
| D5040 | Code center X. |
| D5041 | Code center Y. |
| D5050 | Computed target angle. |

## Vacuum Generators

Two vacuum groups are required:

| Group | Model | Signals |
|---|---|---|
| Vacuum 1 | AZK-X-NE-D | Vacuum ON, release, vacuum OK. |
| Vacuum 2 | AZK-X-NE-D | Vacuum ON, release, vacuum OK. |

Use NPN vacuum OK output to PLC input. Direct PLC transistor output can drive DC24V control valves if current is within output rating and surge protection is provided.

## Static Eliminator

Recommended parts:

| Item | Model |
|---|---|
| Static eliminator | DTY-ELK01 |
| Bar nozzle | DTY-NZK-300B |

Wiring concept:

| Pin / Signal | Connection |
|---|---|
| 24 VDC | Fused 24 VDC branch. |
| 0 VDC | DC common. |
| F.G. | Panel PE / ground bar. |
| H.V OFF | PLC output or contact to stop ionization. |
| ALARM | PLC input. |
| CHECK | PLC input. |

Air supply requires regulator, filter, tubing, and fittings. Add an air solenoid if ionized air must be PLC controlled separately from high-voltage enable.

