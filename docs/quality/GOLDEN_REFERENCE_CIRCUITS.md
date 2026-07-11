# Golden Reference Circuits

## Purpose

Golden reference circuits are small, reviewable fixtures used to prove that each simulation capability produces the expected electrical, logical, thermal, or architectural behavior. They are specifications, not implementation examples.

## Fixture rules

- Every fixture has a stable `GRC-*` ID, a single primary purpose, declared fidelity, supported analyses, exact parameters, probes, expected values, and tolerance.
- Analytical references are preferred. When no closed form is practical, the record must identify a pinned independent engine or published/manufacturer dataset.
- Golden circuits must not use the same model implementation as both system under test and reference.
- A fixture may support several tasks, but each task must name the exact assertion it owns.

## Analog and source fixtures

| ID | Fixture | Required assertions | Primary release |
|---|---|---|---|
| GRC-001 | DC source and resistor | Ohm's law, branch current, resistor power | R1 |
| GRC-002 | Two-resistor divider | Node voltage, source power, load effect | R1 |
| GRC-003 | Current source and resistor | Compliance behavior and node voltage | R1 |
| GRC-004 | VCVS/VCCS/CCVS/CCCS set | Gain/transresistance/transconductance and control polarity | R2 |
| GRC-005 | Battery with internal resistance | Open-circuit voltage, loaded voltage, power split | R2 |
| GRC-006 | RC charge/discharge | Time constant and sampled waveform | R1 |
| GRC-007 | RL step | Current rise, inductor voltage, stored energy | R1 |
| GRC-008 | Series and parallel RLC | Resonance, damping, gain, phase | R3 |
| GRC-009 | Transformer | Turns ratio, polarity, reflected impedance | R3 |
| GRC-010 | Transmission-line termination | Delay and reflection coefficient | R7 |

## Semiconductor and analog fixtures

| ID | Fixture | Required assertions | Primary release |
|---|---|---|---|
| GRC-011 | Forward and reverse diode sweep | I-V curve, leakage, temperature trend | R2 |
| GRC-012 | Zener regulator | Breakdown voltage, dynamic resistance, power | R2 |
| GRC-013 | Half-wave and bridge rectifier | Conduction intervals, ripple, diode stress | R2 |
| GRC-014 | LED resistor circuit | Current, optical indicator state, thermal power | MVP |
| GRC-015 | BJT common-emitter stage | Bias point, gain, cutoff, saturation | R2 |
| GRC-016 | MOSFET low-side switch | Threshold region, on loss, switching transient | R2 |
| GRC-017 | CMOS inverter | Transfer curve, noise margins, delay, short-circuit power | MVP |
| GRC-018 | Op-amp buffer and inverting amplifier | Gain, clipping, slew rate, input/output limits | R2 |
| GRC-019 | Comparator with hysteresis | Thresholds, state memory, propagation delay | R3 |
| GRC-020 | 555 astable | Frequency, duty cycle, startup | R7 |

## Power, thermal, and failure fixtures

| ID | Fixture | Required assertions | Primary release |
|---|---|---|---|
| GRC-021 | Overrated resistor | Temperature rise, derating warning, open/short injection | MVP |
| GRC-022 | MOSFET thermal runaway | Rds(on), leakage, junction temperature feedback | R3 |
| GRC-023 | Buck converter | Regulation, ripple, switching loss, efficiency | R7 |
| GRC-024 | H-bridge motor drive | Dead time, shoot-through prevention, current and back-EMF | R7 |
| GRC-025 | Fuse and TVS surge protection | Trip/clamp behavior and post-failure state | R7 |
| GRC-026 | Monte Carlo divider | Distribution, deterministic seed, pass yield | R3 |

## Digital and mixed-signal fixtures

| ID | Fixture | Required assertions | Primary release |
|---|---|---|---|
| GRC-027 | Primitive gate truth tables | 0/1/X/Z, delay, drive strength | R4 |
| GRC-028 | NAND ring oscillator | Event order, oscillation, delay accumulation | MVP |
| GRC-029 | SR latch | Set/reset/hold and invalid state | MVP |
| GRC-030 | D flip-flop | Edge capture, setup/hold violation | R4 |
| GRC-031 | Counter and shift register | Sequential state and reset behavior | R4 |
| GRC-032 | Half and full adder | Exhaustive truth table and carry propagation | MVP |
| GRC-033 | ADC/DAC loop | Quantization, reference scaling, latency | R5 |
| GRC-034 | Analog/digital threshold adapter | Threshold band, hysteresis, loading, simultaneous event | R5 |
| GRC-035 | 6T SRAM cell | Read, write, hold, noise margin | R6 |

## Sensors, actuators, and communication fixtures

| ID | Fixture | Required assertions | Primary release |
|---|---|---|---|
| GRC-036 | Thermistor divider | Temperature-to-voltage transfer and self-heating | R7 |
| GRC-037 | Load-cell bridge and amplifier | Force transfer, offset, saturation | R7 |
| GRC-038 | DC motor startup | Inrush, acceleration, back-EMF, stall | R7 |
| GRC-039 | I2C sensor transaction | Electrical thresholds and protocol decode | R7 |
| GRC-040 | Touchstone two-port | S-parameter import and frequency response | R11 |

## Computer-system fixtures

| ID | Fixture | Required assertions | Primary release |
|---|---|---|---|
| GRC-041 | One-bit memory and register | Store, retain, read and reset | MVP |
| GRC-042 | Four-bit ALU | Arithmetic, flags, logic, exhaustive vectors | R8 |
| GRC-043 | Four-bit CPU | Fetch/decode/execute and branching | R8 |
| GRC-044 | Eight-bit computer | Program, bus, RAM/ROM, timer, UART and display | R9 |
| GRC-045 | RTL differential model | Gate/event model versus Verilated model | R9 |
| GRC-046 | Cache and DRAM timing | Hit/miss, row behavior, deterministic event counts | R12 |
| GRC-047 | Full-system boot | Functional ISA execution and checkpoint/restart | R12 |
| GRC-048 | GPU compute kernel | Functional output, cycle counters and bandwidth limits | R13 |

## Expansion rule

The 48 fixtures above are the minimum cross-platform suite. Every component family specification adds at least one family-specific fixture or explicitly links to an existing fixture with additional assertions. No family may use a generic fixture without naming the variant-specific expected result.

