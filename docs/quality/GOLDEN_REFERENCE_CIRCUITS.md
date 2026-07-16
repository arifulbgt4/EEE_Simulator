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
| GRC-001 | DC source and resistor | Ohm's law, branch current, resistor power | R2 |
| GRC-002 | Two-resistor divider | Node voltage, source power, load effect | R2 |
| GRC-003 | Current source and resistor | Compliance behavior and node voltage | R2 |
| GRC-004 | VCVS/VCCS/CCVS/CCCS set | Gain/transresistance/transconductance and control polarity | R2 |
| GRC-005 | Battery with internal resistance | Open-circuit voltage, loaded voltage, power split | R2 |
| GRC-006 | RC charge/discharge | Time constant and sampled waveform | R2 |
| GRC-007 | RL step | Current rise, inductor voltage, stored energy | R2 |
| GRC-008 | Series and parallel RLC | Resonance, damping, gain, phase | R2 |
| GRC-009 | Transformer | Turns ratio, polarity, reflected impedance | R3 |
| GRC-010 | Transmission-line termination | Delay and reflection coefficient | R7 |

## Semiconductor and analog fixtures

| ID | Fixture | Required assertions | Primary release |
|---|---|---|---|
| GRC-011 | Forward and reverse diode sweep | I-V curve, leakage, temperature trend | R3 |
| GRC-012 | Zener regulator | Breakdown voltage, dynamic resistance, power | R3 |
| GRC-013 | Half-wave and bridge rectifier | Conduction intervals, ripple, diode stress | R3 |
| GRC-014 | LED resistor circuit | Current, optical indicator state, thermal power | R3 |
| GRC-015 | BJT common-emitter stage | Bias point, gain, cutoff, saturation | R3 |
| GRC-016 | MOSFET low-side switch | Threshold region, on loss, switching transient | R3 |
| GRC-017 | CMOS inverter | Transfer curve, noise margins, delay, short-circuit power | R3 |
| GRC-018 | Op-amp buffer and inverting amplifier | Gain, clipping, slew rate, input/output limits | R3 |
| GRC-019 | Comparator with hysteresis | Thresholds, state memory, propagation delay | R3 |
| GRC-020 | 555 astable | Frequency, duty cycle, startup | R3 |

## Power, thermal, and failure fixtures

| ID | Fixture | Required assertions | Primary release |
|---|---|---|---|
| GRC-021 | Overrated resistor | Temperature rise, derating warning, open/short injection | R4 |
| GRC-022 | MOSFET thermal runaway | Rds(on), leakage, junction temperature feedback | R4 |
| GRC-023 | Buck converter | Regulation, ripple, switching loss, efficiency | R7 |
| GRC-024 | H-bridge motor drive | Dead time, shoot-through prevention, current and back-EMF | R7 |
| GRC-025 | Fuse and TVS surge protection | Trip/clamp behavior and post-failure state | R7 |
| GRC-026 | Monte Carlo divider | Distribution, deterministic seed, pass yield | R4 |

## Digital and mixed-signal fixtures

| ID | Fixture | Required assertions | Primary release |
|---|---|---|---|
| GRC-027 | Primitive gate truth tables | 0/1/X/Z, delay, drive strength | R5 |
| GRC-028 | NAND ring oscillator | Event order, oscillation, delay accumulation | R5 |
| GRC-029 | SR latch | Set/reset/hold and invalid state | R5 |
| GRC-030 | D flip-flop | Edge capture, setup/hold violation | R5 |
| GRC-031 | Counter and shift register | Sequential state and reset behavior | R5 |
| GRC-032 | Half and full adder | Exhaustive truth table and carry propagation | R5 |
| GRC-033 | ADC/DAC loop | Quantization, reference scaling, latency | R5 |
| GRC-034 | Analog/digital threshold adapter | Threshold band, hysteresis, loading, simultaneous event | R5 |
| GRC-035 | 6T SRAM cell | Read, write, hold, noise margin | R8 |

## Sensors, actuators, and communication fixtures

| ID | Fixture | Required assertions | Primary release |
|---|---|---|---|
| GRC-036 | Thermistor divider | Temperature-to-voltage transfer and self-heating | R7 |
| GRC-037 | Load-cell bridge and amplifier | Force transfer, offset, saturation | R7 |
| GRC-038 | DC motor startup | Inrush, acceleration, back-EMF, stall | R7 |
| GRC-039 | I2C sensor transaction | Electrical thresholds and protocol decode | R7 |
| GRC-040 | Touchstone two-port | S-parameter import and frequency response | R7 |

## Computer-system fixtures

| ID | Fixture | Required assertions | Primary release |
|---|---|---|---|
| GRC-041 | One-bit memory and register | Store, retain, read and reset | R6 |
| GRC-042 | Four-bit ALU | Arithmetic, flags, logic, exhaustive vectors | R8 |
| GRC-043 | Four-bit CPU | Fetch/decode/execute and branching | R8 |
| GRC-044 | Eight-bit computer | Program, bus, RAM/ROM, timer, UART and display | R9 |
| GRC-045 | RTL differential model | Gate/event model versus Verilated model | R9 |
| GRC-046 | Cache and DRAM timing | Hit/miss, row behavior, deterministic event counts | R12 |
| GRC-047 | Full-system boot | Functional ISA execution and checkpoint/restart | R12 |
| GRC-048 | GPU compute kernel | Functional output, cycle counters and bandwidth limits | R13 |

## Physical appearance and package fixtures

| ID | Fixture | Required assertions | Primary release |
|---|---|---|---|
| GRC-049 | Resistor package physical set | Axial and SMD recognizable geometry, lead/contact style, value/tolerance cues, exact PinProfile-to-contact binding, rotation and scale; candidate-only input is rejected | R1 |
| GRC-050 | Discrete, optoelectronic and power package physical set | Radial passive, diode, LED, SOT/TO/DPAK and power-module recognition; polarity/orientation, exact contact map and pin labels through a concrete binding | R1 |
| GRC-051 | Through-hole and perimeter-leaded IC package set | DIP/SIP/ZIP and SOIC/SSOP/TSSOP/PLCC pin-one cues, numbering, resolved dimensions, labels and exact PinProfile/package-contact equivalence through a concrete binding | R1 |
| GRC-052 | Quad, leadless and grid-array IC package set | QFP/QFN/DFN and LGA/BGA/CSP multi-side/grid numbering, thermal-pad/ball semantics, complete contact disposition, orientation and zoom behavior | R1 |
| GRC-053 | Custom package designer | Parameter constraints, immutable deterministic package revision, unbound-state handling and valid reviewed DevicePackageBinding creation without implicit pin inference | R1 |
| GRC-054 | Dual-view and interface-package project | Same component/model/binding identity, nets and results across views; virtual, module, connector and cable state/anchor preservation and binding-revision round trip | R1 |

## Physical benchmark and experimental-correlation fixtures

These fixtures compare an immutable simulation configuration with retained physical measurements. Each requires exact schematic, BOM and ordering codes, package, measured tolerances, specimen count, source and wiring, calibrated equipment, environment, procedure, raw-data digest, model/dependency revisions, processing method, uncertainty budget, category-specific acceptance envelope, limitations, and regression evidence. Agreement with another simulator alone is not physical correlation.

| ID | Fixture | Required assertions | Primary release |
|---|---|---|---|
| GRC-055 | Physical resistor divider | Measured loaded voltage, source/instrument loading, tolerance and uncertainty envelope | R4 |
| GRC-056 | Physical RC charging and discharging | Measured time constant, source/probe loading, parasitics, temperature and uncertainty | R4 |
| GRC-057 | Physical RL transient | Measured current rise, winding resistance, source limit, probe bandwidth and uncertainty | R4 |
| GRC-058 | Physical RLC resonance | Measured resonance, damping, ESR/ESL, source/instrument bandwidth and uncertainty | R4 |
| GRC-059 | Physical diode rectifier | Measured conduction, ripple, source impedance, junction temperature and model envelope | R4 |
| GRC-060 | Physical LED current and heating | Measured current, forward voltage, thermal rise, tolerance and bounded optical limitation | R4 |
| GRC-061 | Physical BJT switch | Measured cutoff/saturation, base drive, delay, heating and device variation | R4 |
| GRC-062 | Physical MOSFET switch | Measured gate transient, on loss, source/load parasitics, junction heating and variation | R4 |
| GRC-063 | Physical op-amp amplifier | Measured gain, offset, bandwidth, clipping, supply behavior and probe loading | R4 |
| GRC-064 | Physical regulator load response | Measured regulation, dropout, transient response, ripple, current limit and heating | R4 |
| GRC-065 | Physical oscillator | Measured startup, frequency, duty, amplitude, drift, loading and uncertainty | R4 |
| GRC-066 | Physical thermal overload circuit | Measured power-to-temperature feedback, derating threshold, runaway/failure state and uncertainty | R4 |

## Expansion rule

The 66 fixtures above are the minimum cross-platform suite. Every component family specification adds at least one family-specific fixture or explicitly links to an existing fixture with additional assertions. No family may use a generic fixture without naming the variant-specific expected result. GRC-055 through GRC-066 remain `Specified`, not measured or passing, until their validation cards retain real calibrated evidence.
