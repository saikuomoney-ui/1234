# Servo Wiring Plan

## Architecture

Preferred architecture for four axes:

```text
FX5U-64MT/ES
-> FX5-40SSC-S
-> SSCNET III/H
-> MR-J4-B servo amplifiers
-> HG-KR servo motors
```

Using MR-J4-B means PLC transistor outputs are not consumed by pulse/direction positioning.

## Axis Assignment

| Axis | Amplifier | Motor | Brake | Purpose |
|---|---|---|---|---|
| Axis 1 | MR-J4-20B | HG-KR23 | No | X traverse. |
| Axis 2 | MR-J4-10B | HG-KR13B | Yes | X lift. |
| Axis 3 | MR-J4-10B | HG-KR13K | No | Z rotation. |
| Axis 4 | MR-J4-20B | HG-KR23B | Yes | Z lift. |

## MR-J4-B Connector Functions

| Connector | Function |
|---|---|
| CNP1 | Main power input. |
| CNP2 | Regenerative / control power terminals. |
| CNP3 | Motor power U/V/W/E. |
| CN1A/CN1B | SSCNET optical network in/out. |
| CN2 | Motor encoder cable. |
| CN3 | PC / parameter communication. |
| CN8 | STO safety input. |

## Required Drawing Details

- Show each amplifier with main power and control power.
- Show PE grounding to panel ground bar.
- Show motor power cable, encoder cable, and brake cable.
- Show SSCNET order and cable lengths.
- Show STO wiring strategy.
- Show brake power branch and fuse.

