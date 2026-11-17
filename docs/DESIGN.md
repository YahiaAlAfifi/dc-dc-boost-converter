# Design notes

## Topology

The circuit uses a conventional asynchronous boost-converter topology:

```text
Vin -> L1 -> switching node -> D1 -> Vout
                 |                 |
                M1                C1 + R1
                 |                 |
                GND               GND
```

## Component choices

- **L1: 470 uH** - energy-storage element.
- **M1: BSZ0905NS** - PWM-controlled switching MOSFET.
- **D1: MBRS140** - Schottky rectifier selected for its low forward voltage.
- **C1: 22 uF** - output smoothing capacitor.
- **R1: 24 ohm** - resistive load.

## Simulation conditions

The LTspice source uses a 5 V DC input and a `PULSE(0 12 0 0 0 6u 10u)` gate drive. The included transient command runs for 6 ms. The reported average output voltage is 13.973 V.

## Interpretation

The transient plot shows the output rising above the 5 V input and settling near the target voltage. Deviations from an ideal boost-converter equation are expected because the model includes practical component behaviour and load current.
