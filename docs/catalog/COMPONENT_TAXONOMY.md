# Component Taxonomy

Status: **Frozen documentation baseline 1.0**  
Requirements: **REQ-022, REQ-023, REQ-037, REQ-038**
Machine-readable source: [component-registry.yaml](component-registry.yaml)  
Normative pin profiles: [variant-pin-profiles.yaml](variant-pin-profiles.yaml)
Package source: [package-registry.yaml](package-registry.yaml)

## Completeness claim

The built-in catalog tracks **162 canonical component families and 502 meaningful variants/presets**. Of these, 157 families and 494 variants form the production baseline; five families and eight variants remain explicitly Deferred/Research. The baseline covers electrical, digital, embedded, computer, RF, environmental, instrument, and physical-interface primitives requested by the source brief. [Source PDF, pp. 6-35]

`Complete` does not mean every manufacturer ordering code. A manufacturer part is a vendor model bound to a canonical variant, its explicit `PinProfile`, provenance record, and an independently selected package through `DevicePackageBinding`. Package templates and package revisions are a separate dimension and never alter the frozen 162/502 component counts.

## Release profiles

- **Realistic Electronics MVP:** 106 explicitly tagged production presets covering the core connectivity, sources, RLC, basic switches, diode/LED, BJT, MOSFET, op-amp, basic logic/memory, and instruments needed by the R2-R6 golden demonstrations.
- **Post-MVP complete catalog:** 388 production presets remain visible and planned for R7; they are not omitted or silently represented as MVP-ready.
- **Deferred/Research:** eight presets remain visible behind explicit F5/research gates.

The machine-readable `release_target` on each variant is authoritative. A family may have mixed targets because its shared electrical model can support a small MVP preset while advanced presets retain separate catalog, validation, and release obligations. Reclassifying a preset requires synchronized registry, family, task, test, traceability, and release-checklist updates.

## Taxonomic levels

1. **Category** groups related engineering purpose and simulation domain.
2. **Family** owns the stable pin-role vocabulary, parameters, symbol contract, supported analyses, fidelity envelope, and validation obligations; its compact pin list is a preview, not a variant topology.
3. **Variant** is a meaningful built-in behavior/profile preset, not a cosmetic color or package, and selects exactly one normative `PinProfile`.
4. **Generic device** binds an exact reusable model/interface revision without claiming a manufacturer ordering code.
5. **Vendor device or ordering-code variant** inherits one exact generic-device revision and adds only bounded evidence-backed parameter overrides, package/pin binding, metadata, provenance, license, trust, and validation state.
6. **Vendor model** is imported data with provenance, license, pin map, supported analyses, executable-mode classification, trust, validation, and limitations.

Scientific models are inventoried separately in [model-registry.yaml](model-registry.yaml) as `physics`, `primitive`, `composite`, `behavioral`, or `external_adapter`. Symbols, packages, pin profiles, device-package bindings, boards/modules, systems, projects, and validation artifacts are independent types; a package is never an IC, board, module, or system.
5. **Package** describes physical appearance and contact geometry independently of electrical function.
6. **Footprint** is optional manufacturing metadata; it is not inferred from a visual package.

## Variant pin topology

The 502 built-in variants have 502 stable profile IDs in [variant-pin-profiles.yaml](variant-pin-profiles.yaml). The profile is authoritative for ordered logical pins, scalar versus bus shape, direction, domain, required state, optional groups, and bounded cardinality. This resolves legitimate family variation such as SPST/SPDT/DPDT contacts, isolated versus bussed resistor arrays, transformer windings and taps, RGB LED electrodes, semiconductor terminal conventions, analog/digital converter buses, motor phases, displays, connector protocols, memory interfaces, and RF N-ports.

Family role vocabulary remains stable while profiles select a valid subset and topology. For example, the IGBT family exposes collector/gate/emitter roles and its profiles use `C`, `G`, `E`, plus an optional Kelvin emitter; they do not inherit MOSFET `D/G/S/B` terminals. A topology change never comes from package selection. The package contact map remains an explicit, separately validated `DevicePackageBinding`.

## Frozen category counts

| Category ID | Category | Families | Variants | Baseline |
|---|---|---:|---:|---|
| `cat-connectivity` | Connectivity and schematic primitives | 10 | 18 | Production |
| `cat-sources-loads` | Sources and loads | 13 | 26 | Production |
| `cat-passives` | Passives, magnetics and transmission | 15 | 40 | Production |
| `cat-switch-protection` | Switches, protection and isolation | 12 | 36 | Production |
| `cat-semiconductors` | Semiconductor and optoelectronics | 15 | 46 | Production |
| `cat-analog-mixed-signal` | Analog and mixed-signal abstractions | 13 | 38 | Production |
| `cat-power-electronics` | Power-electronics blocks | 8 | 24 | Production |
| `cat-sensors-environment` | Sensors and environment | 10 | 42 | Production |
| `cat-actuators-hmi` | Actuators, displays and HMI | 10 | 32 | Production |
| `cat-connectors-cables` | Connectors and cables | 3 | 24 | Production |
| `cat-instruments` | Measurement instruments | 8 | 22 | Production |
| `cat-digital-logic` | Digital logic | 16 | 54 | Production |
| `cat-memory-storage` | Memory and storage | 6 | 18 | Production |
| `cat-mcu-fpga` | MCU, FPGA and peripherals | 5 | 24 | Production |
| `cat-computer-gpu` | CPU, computer and GPU blocks | 6 | 28 | Production |
| `cat-rf-communications` | RF and communications | 7 | 22 | Production |
| `cat-deferred-research` | Explicitly deferred research families | 5 | 8 | Deferred/Research |
| **Production subtotal** |  | **157** | **494** |  |
| **Full tracked registry** |  | **162** | **502** |  |

These totals are acceptance invariants. Adding, removing, merging, or splitting a family or variant requires a versioned catalog decision and migration plan. Adding packages or vendor models does not change them.

## Family inventory

### Connectivity and schematic primitives

10 families and 18 variants; Source PDF, pp. 6-8.

- [`fam-connectivity-wire`](families/fam-connectivity-wire.md) - Wire and conductor; variant: Conductor.
- [`fam-connectivity-junction`](families/fam-connectivity-junction.md) - Electrical junction; variants: Junction.
- [`fam-connectivity-crossover`](families/fam-connectivity-crossover.md) - Non-connected crossover; variants: Bridge Crossover.
- [`fam-connectivity-bus`](families/fam-connectivity-bus.md) - Bus conductor; variants: Parameterized Bus.
- [`fam-connectivity-net-label`](families/fam-connectivity-net-label.md) - Net label; variant: Parameterized Local or Global Label.
- [`fam-connectivity-ground`](families/fam-connectivity-ground.md) - Ground reference; variants: Earth, Signal, Chassis, Analog, Digital, Power.
- [`fam-connectivity-power-rail`](families/fam-connectivity-power-rail.md) - Power rail; variants: Parameterized Rail.
- [`fam-connectivity-terminal-bridge`](families/fam-connectivity-terminal-bridge.md) - Terminal, net tie, jumper, and domain adapter; variants: Terminal, Net Tie, Jumper, Domain Adapter.
- [`fam-connectivity-hierarchical-port`](families/fam-connectivity-hierarchical-port.md) - Hierarchical port; variants: Directional Port.
- [`fam-connectivity-subcircuit`](families/fam-connectivity-subcircuit.md) - Hierarchical subcircuit; variants: Subcircuit Instance.

### Sources and loads

13 families and 26 variants; Source PDF, pp. 8-10.

- [`fam-sources-loads-independent-voltage`](families/fam-sources-loads-independent-voltage.md) - Independent voltage source; variants: Dc, Ac Small Signal, Sine, Pulse.
- [`fam-sources-loads-independent-current`](families/fam-sources-loads-independent-current.md) - Independent current source; variants: Dc, Ac Small Signal, Sine, Pulse.
- [`fam-sources-loads-waveform-source`](families/fam-sources-loads-waveform-source.md) - Deterministic waveform source; variants: Triangle, Sawtooth, Pwl, Chirp.
- [`fam-sources-loads-noise-source`](families/fam-sources-loads-noise-source.md) - Noise source; variants: White, Pink.
- [`fam-sources-loads-digital-pattern-source`](families/fam-sources-loads-digital-pattern-source.md) - Digital pattern source; variants: Pattern.
- [`fam-sources-loads-dependent-source`](families/fam-sources-loads-dependent-source.md) - Controlled source; variants: Vcvs, Vccs, Ccvs, Cccs.
- [`fam-sources-loads-behavioral-source`](families/fam-sources-loads-behavioral-source.md) - Behavioral source; variants: Expression.
- [`fam-sources-loads-battery-source`](families/fam-sources-loads-battery-source.md) - Battery source; variants: Battery Pack.
- [`fam-sources-loads-mains-source`](families/fam-sources-loads-mains-source.md) - Mains source; variants: Single Phase.
- [`fam-sources-loads-solar-source`](families/fam-sources-loads-solar-source.md) - Solar source; variants: Pv Array.
- [`fam-sources-loads-constant-load`](families/fam-sources-loads-constant-load.md) - Constant load; variants: Constant Power.
- [`fam-sources-loads-programmable-load`](families/fam-sources-loads-programmable-load.md) - Programmable load; variants: Profiled Load.
- [`fam-sources-loads-electronic-load`](families/fam-sources-loads-electronic-load.md) - Electronic load; variants: Cc Cv Cr Cp.

### Passives, magnetics and transmission

15 families and 40 variants; Source PDF, pp. 8-13.

- [`fam-passives-resistor`](families/fam-passives-resistor.md) - Resistor; variants: Carbon Film, Metal Film, Wirewound, Thick Film, Current Sense.
- [`fam-passives-potentiometer`](families/fam-passives-potentiometer.md) - Potentiometer; variants: Linear, Logarithmic.
- [`fam-passives-resistor-array`](families/fam-passives-resistor-array.md) - Resistor array; variants: Isolated, Bussed.
- [`fam-passives-thermistor`](families/fam-passives-thermistor.md) - Thermistor; variants: Ntc, Ptc.
- [`fam-passives-photoresistor`](families/fam-passives-photoresistor.md) - Photoresistor; variants: Ldr.
- [`fam-passives-capacitor`](families/fam-passives-capacitor.md) - Capacitor; variants: Ceramic, Film, Aluminum Electrolytic, Tantalum.
- [`fam-passives-variable-capacitor`](families/fam-passives-variable-capacitor.md) - Variable capacitor; variants: Variable, Trimmer.
- [`fam-passives-inductor`](families/fam-passives-inductor.md) - Inductor; variants: Air Core, Iron Core, Ferrite Core.
- [`fam-passives-choke`](families/fam-passives-choke.md) - Choke; variants: Common Mode, Differential Mode.
- [`fam-passives-ferrite`](families/fam-passives-ferrite.md) - Ferrite suppressor; variants: Bead.
- [`fam-passives-coupled-inductor`](families/fam-passives-coupled-inductor.md) - Coupled inductor; variants: Two Winding, Multi Winding.
- [`fam-passives-transformer`](families/fam-passives-transformer.md) - Transformer; variants: Ideal, Center Tapped, Pulse, Autotransformer.
- [`fam-passives-crystal-resonator`](families/fam-passives-crystal-resonator.md) - Crystal and resonator; variants: Quartz Crystal, Ceramic Resonator, Saw Resonator.
- [`fam-passives-transmission-line`](families/fam-passives-transmission-line.md) - Transmission line; variants: Lossless, Lossy, Time Delay.
- [`fam-passives-generic-impedance`](families/fam-passives-generic-impedance.md) - Generic impedance; variants: Series Rlc, Parallel Rlc, Laplace, Tabulated.

### Switches, protection and isolation

12 families and 36 variants; Source PDF, pp. 10-14.

- [`fam-switch-protection-mechanical-switch`](families/fam-switch-protection-mechanical-switch.md) - Mechanical switch; variants: Spst, Spdt, Dpst, Dpdt, Momentary.
- [`fam-switch-protection-controlled-switch`](families/fam-switch-protection-controlled-switch.md) - Controlled switch; variants: Voltage Controlled, Current Controlled, Ideal Controlled.
- [`fam-switch-protection-analog-switch`](families/fam-switch-protection-analog-switch.md) - Analog switch; variants: Spst, Spdt, Multiplexer.
- [`fam-switch-protection-transmission-gate`](families/fam-switch-protection-transmission-gate.md) - Transmission gate; variants: Cmos, Bidirectional.
- [`fam-switch-protection-relay`](families/fam-switch-protection-relay.md) - Relay; variants: Spst, Spdt, Dpst, Latching.
- [`fam-switch-protection-fuse`](families/fam-switch-protection-fuse.md) - Fuse and resettable protector; variants: Fast Blow, Slow Blow, Ptc Resettable.
- [`fam-switch-protection-circuit-breaker`](families/fam-switch-protection-circuit-breaker.md) - Circuit breaker; variants: Thermal, Magnetic, Thermal Magnetic.
- [`fam-switch-protection-surge-suppressor`](families/fam-switch-protection-surge-suppressor.md) - Surge and ESD suppressor; variants: Mov, Tvs, Gdt, Esd Clamp.
- [`fam-switch-protection-crowbar`](families/fam-switch-protection-crowbar.md) - Crowbar protector; variants: Scr, Triac.
- [`fam-switch-protection-snubber`](families/fam-switch-protection-snubber.md) - Snubber network; variants: Rc, Rcd.
- [`fam-switch-protection-isolation-device`](families/fam-switch-protection-isolation-device.md) - Isolation device; variants: Optocoupler, Digital Isolator, Isolation Amplifier.
- [`fam-switch-protection-thermal-protection`](families/fam-switch-protection-thermal-protection.md) - Thermal protection; variants: Thermal Fuse, Thermostat.

### Semiconductor and optoelectronics

15 families and 46 variants; Source PDF, pp. 10-15.

- [`fam-semiconductors-diode`](families/fam-semiconductors-diode.md) - Diode; variants: Signal, Rectifier, Schottky, Zener, Tvs, Varactor, Pin, Tunnel.
- [`fam-semiconductors-led`](families/fam-semiconductors-led.md) - Light-emitting diode; variants: Visible, Rgb, Infrared, Ultraviolet, High Power.
- [`fam-semiconductors-photodetector`](families/fam-semiconductors-photodetector.md) - Photodetector; variants: Photodiode, Phototransistor, Avalanche Photodiode.
- [`fam-semiconductors-photovoltaic`](families/fam-semiconductors-photovoltaic.md) - Photovoltaic device; variants: Cell, Module.
- [`fam-semiconductors-bjt`](families/fam-semiconductors-bjt.md) - Bipolar junction transistor; variants: Npn, Pnp, Darlington Npn, Darlington Pnp.
- [`fam-semiconductors-jfet`](families/fam-semiconductors-jfet.md) - Junction field-effect transistor; variants: N Channel, P Channel.
- [`fam-semiconductors-mosfet`](families/fam-semiconductors-mosfet.md) - MOSFET; variants: N Enhancement, P Enhancement, N Depletion, P Depletion, Gan Power, Sic Power.
- [`fam-semiconductors-igbt`](families/fam-semiconductors-igbt.md) - Insulated-gate bipolar transistor; variants: N Channel, P Channel.
- [`fam-semiconductors-thyristor`](families/fam-semiconductors-thyristor.md) - Thyristor family; variants: Scr, Triac, Diac, Gto.
- [`fam-semiconductors-ujt`](families/fam-semiconductors-ujt.md) - Unijunction transistor; variants: N Type, P Type.
- [`fam-semiconductors-mesfet`](families/fam-semiconductors-mesfet.md) - MESFET; variants: N Channel, P Channel.
- [`fam-semiconductors-hemt`](families/fam-semiconductors-hemt.md) - High-electron-mobility transistor; variants: Gaas, Gan.
- [`fam-semiconductors-opto-isolator`](families/fam-semiconductors-opto-isolator.md) - Optically isolated semiconductor; variants: Phototransistor Output, Triac Output.
- [`fam-semiconductors-laser-diode`](families/fam-semiconductors-laser-diode.md) - Laser diode; variants: Edge Emitting.
- [`fam-semiconductors-semiconductor-generic`](families/fam-semiconductors-semiconductor-generic.md) - Generic semiconductor black box; variants: Equation Model.

### Analog and mixed-signal abstractions

13 families and 38 variants; Source PDF, pp. 13-17.

- [`fam-analog-mixed-signal-operational-amplifier`](families/fam-analog-mixed-signal-operational-amplifier.md) - Operational amplifier; variants: Ideal, Bipolar General Purpose, Cmos, Rail To Rail.
- [`fam-analog-mixed-signal-comparator`](families/fam-analog-mixed-signal-comparator.md) - Comparator; variants: Ideal, Open Collector, Window.
- [`fam-analog-mixed-signal-schmitt-trigger`](families/fam-analog-mixed-signal-schmitt-trigger.md) - Schmitt trigger; variants: Inverting, Non Inverting.
- [`fam-analog-mixed-signal-instrumentation-amplifier`](families/fam-analog-mixed-signal-instrumentation-amplifier.md) - Instrumentation amplifier; variants: Three Op Amp, Integrated.
- [`fam-analog-mixed-signal-transimpedance-amplifier`](families/fam-analog-mixed-signal-transimpedance-amplifier.md) - Transimpedance amplifier; variants: Ideal, Band Limited.
- [`fam-analog-mixed-signal-ota`](families/fam-analog-mixed-signal-ota.md) - Operational transconductance amplifier; variants: Single Ended, Differential.
- [`fam-analog-mixed-signal-current-mirror`](families/fam-analog-mixed-signal-current-mirror.md) - Current mirror; variants: Simple, Wilson.
- [`fam-analog-mixed-signal-analog-math`](families/fam-analog-mixed-signal-analog-math.md) - Analog math block; variants: Sum Difference, Multiplier Divider, Integrator Differentiator.
- [`fam-analog-mixed-signal-analog-mux`](families/fam-analog-mixed-signal-analog-mux.md) - Analog multiplexer; variants: Mux, Demux, Crosspoint.
- [`fam-analog-mixed-signal-sample-hold`](families/fam-analog-mixed-signal-sample-hold.md) - Sample and hold; variants: Track And Hold, Sample And Hold.
- [`fam-analog-mixed-signal-data-converter`](families/fam-analog-mixed-signal-data-converter.md) - Data converter; variants: Sar Adc, Delta Sigma Adc, R2r Dac, Current Steering Dac.
- [`fam-analog-mixed-signal-regulator-reference`](families/fam-analog-mixed-signal-regulator-reference.md) - Linear regulator and reference; variants: Ldo, Shunt Reference, Series Reference.
- [`fam-analog-mixed-signal-timing-filter-conversion`](families/fam-analog-mixed-signal-timing-filter-conversion.md) - Timing, filter, and converter abstraction; variants: Timer 555, Vco, Pll, Active Filter, Level Converter, Frequency Converter.

### Power-electronics blocks

8 families and 24 variants; Source PDF, pp. 14-18.

- [`fam-power-electronics-rectifier-block`](families/fam-power-electronics-rectifier-block.md) - Rectifier block; variants: Half Wave, Full Wave, Three Phase.
- [`fam-power-electronics-gate-driver`](families/fam-power-electronics-gate-driver.md) - Gate driver; variants: Low Side, High Side, Isolated.
- [`fam-power-electronics-dc-converter`](families/fam-power-electronics-dc-converter.md) - DC converter; variants: Buck, Boost, Buck Boost, Flyback, Forward, Charge Pump.
- [`fam-power-electronics-bridge-inverter`](families/fam-power-electronics-bridge-inverter.md) - Bridge and inverter; variants: Half Bridge, Full Bridge, Three Phase Inverter.
- [`fam-power-electronics-pwm-controller`](families/fam-power-electronics-pwm-controller.md) - PWM controller; variants: Configurable Pwm.
- [`fam-power-electronics-motor-driver`](families/fam-power-electronics-motor-driver.md) - Motor driver; variants: Brushed Dc, Bldc, Stepper.
- [`fam-power-electronics-charger-bms`](families/fam-power-electronics-charger-bms.md) - Charger and battery management; variants: Battery Charger, Bms.
- [`fam-power-electronics-power-control`](families/fam-power-electronics-power-control.md) - Power control; variants: Dimmer, Soft Starter, Pfc.

### Sensors and environment

10 families and 42 variants; Source PDF, pp. 16-20.

- [`fam-sensors-environment-temperature-sensor`](families/fam-sensors-environment-temperature-sensor.md) - Temperature sensor; variants: Thermocouple, Rtd, Thermistor Probe, Integrated Temperature.
- [`fam-sensors-environment-optical-sensor`](families/fam-sensors-environment-optical-sensor.md) - Optical sensor; variants: Photodiode Module, Ambient Light, Color, Infrared.
- [`fam-sensors-environment-magnetic-motion-sensor`](families/fam-sensors-environment-magnetic-motion-sensor.md) - Magnetic and motion sensor; variants: Hall, Reed, Accelerometer, Gyroscope, Magnetometer.
- [`fam-sensors-environment-force-pressure-sensor`](families/fam-sensors-environment-force-pressure-sensor.md) - Force and pressure sensor; variants: Strain Gauge, Load Cell, Absolute Pressure, Differential Pressure.
- [`fam-sensors-environment-sound-distance-sensor`](families/fam-sensors-environment-sound-distance-sensor.md) - Sound and distance sensor; variants: Microphone, Ultrasonic, Infrared Distance, Lidar.
- [`fam-sensors-environment-climate-gas-sensor`](families/fam-sensors-environment-climate-gas-sensor.md) - Climate and gas sensor; variants: Humidity, Barometric, Carbon Dioxide, Voc, Generic Gas.
- [`fam-sensors-environment-safety-agriculture-sensor`](families/fam-sensors-environment-safety-agriculture-sensor.md) - Safety and agriculture sensor; variants: Smoke, Flame, Soil Moisture, Rain, Water Level.
- [`fam-sensors-environment-water-quality-sensor`](families/fam-sensors-environment-water-quality-sensor.md) - Water quality sensor; variants: Ph, Conductivity, Turbidity, Dissolved Oxygen, Salinity, Orp.
- [`fam-sensors-environment-electrical-sensor`](families/fam-sensors-environment-electrical-sensor.md) - Electrical sensor; variants: Current, Voltage, Power Energy.
- [`fam-sensors-environment-environment-stimulus`](families/fam-sensors-environment-environment-stimulus.md) - Environmental stimulus; variants: Constant Stimulus, Time Profile.

### Actuators, displays and HMI

10 families and 32 variants; Source PDF, pp. 17-21.

- [`fam-actuators-hmi-lamp-heater`](families/fam-actuators-hmi-lamp-heater.md) - Lamp and heater; variants: Indicator Lamp, Incandescent Lamp, Resistive Heater.
- [`fam-actuators-hmi-audio-output`](families/fam-actuators-hmi-audio-output.md) - Audio output; variants: Speaker, Buzzer, Piezo Sounder, Siren.
- [`fam-actuators-hmi-dc-motor`](families/fam-actuators-hmi-dc-motor.md) - DC motor; variants: Brushed, Geared, Vibration.
- [`fam-actuators-hmi-bldc-motor`](families/fam-actuators-hmi-bldc-motor.md) - Brushless DC motor; variants: Sensored, Sensorless.
- [`fam-actuators-hmi-stepper-motor`](families/fam-actuators-hmi-stepper-motor.md) - Stepper motor; variants: Unipolar, Bipolar, Hybrid.
- [`fam-actuators-hmi-servo`](families/fam-actuators-hmi-servo.md) - Servo; variants: Positional, Continuous Rotation.
- [`fam-actuators-hmi-solenoid-valve`](families/fam-actuators-hmi-solenoid-valve.md) - Solenoid and valve; variants: Solenoid, Pneumatic Valve, Liquid Valve.
- [`fam-actuators-hmi-fan-pump`](families/fam-actuators-hmi-fan-pump.md) - Fan and pump; variants: Fan, Blower, Pump, Compressor.
- [`fam-actuators-hmi-display`](families/fam-actuators-hmi-display.md) - Display; variants: Seven Segment, Dot Matrix, Lcd, Oled, E Paper.
- [`fam-actuators-hmi-hmi-input`](families/fam-actuators-hmi-hmi-input.md) - Human-machine input; variants: Pushbutton Panel, Keypad, Rotary Encoder.

### Connectors and cables

3 families and 24 variants; Source PDF, pp. 18-21.

- [`fam-connectors-cables-connector`](families/fam-connectors-cables-connector.md) - Connector; variants: Pin Header, Terminal Block, Usb A, Usb C, Rj45, Bnc, D Sub, Jst Style, Molex Style, Barrel, Banana, Edge Card.
- [`fam-connectors-cables-socket-board`](families/fam-connectors-cables-socket-board.md) - Socket and prototyping board; variants: Ic Socket, Breadboard, Card Socket, Screw Terminal, Spring Terminal, Pogo Array.
- [`fam-connectors-cables-cable`](families/fam-connectors-cables-cable.md) - Cable; variants: Coaxial, Ribbon, Twisted Pair, Shielded Multicore, Usb, Wire Harness.

### Measurement instruments

8 families and 22 variants; Source PDF, pp. 20-23.

- [`fam-instruments-probe`](families/fam-instruments-probe.md) - Probe; variants: Voltage, Current, Differential, Digital.
- [`fam-instruments-multimeter`](families/fam-instruments-multimeter.md) - Multimeter; variants: Handheld, Bench, Clamp.
- [`fam-instruments-oscilloscope`](families/fam-instruments-oscilloscope.md) - Oscilloscope; variants: Two Channel, Four Channel, Mixed Signal.
- [`fam-instruments-logic-analyzer`](families/fam-instruments-logic-analyzer.md) - Logic analyzer; variants: Eight Channel, Sixteen Channel.
- [`fam-instruments-signal-generator`](families/fam-instruments-signal-generator.md) - Signal generator; variants: Function, Arbitrary Waveform, Clock Pattern.
- [`fam-instruments-bench-supply`](families/fam-instruments-bench-supply.md) - Bench supply; variants: Single Output, Triple Output.
- [`fam-instruments-impedance-rf-instrument`](families/fam-instruments-impedance-rf-instrument.md) - Impedance and RF instrument; variants: Lcr Meter, Spectrum Analyzer, Network Analyzer.
- [`fam-instruments-specialized-instrument`](families/fam-instruments-specialized-instrument.md) - Specialized instrument; variants: Curve Tracer, Protocol Analyzer.

### Digital logic

16 families and 54 variants; Source PDF, pp. 21-26.

- [`fam-digital-logic-logic-constant`](families/fam-digital-logic-logic-constant.md) - Logic constant; variants: Low, High, Unknown, High Impedance.
- [`fam-digital-logic-logic-gate`](families/fam-digital-logic-logic-gate.md) - Logic gate; variants: Buffer, Inverter, And, Nand, Or, Nor, Xor, Xnor.
- [`fam-digital-logic-tri-state`](families/fam-digital-logic-tri-state.md) - Tri-state logic; variants: Buffer, Inverter.
- [`fam-digital-logic-arithmetic-logic`](families/fam-digital-logic-arithmetic-logic.md) - Arithmetic logic; variants: Half Adder, Full Adder, Subtractor, Alu, Multiplier.
- [`fam-digital-logic-digital-comparator`](families/fam-digital-logic-digital-comparator.md) - Digital comparator; variants: Magnitude, Parity.
- [`fam-digital-logic-mux-codec`](families/fam-digital-logic-mux-codec.md) - Multiplexer and code converter; variants: Multiplexer, Demultiplexer, Encoder, Decoder.
- [`fam-digital-logic-latch`](families/fam-digital-logic-latch.md) - Latch; variants: Sr, D, Gated.
- [`fam-digital-logic-flip-flop`](families/fam-digital-logic-flip-flop.md) - Flip-flop; variants: D, Jk, T, Sr.
- [`fam-digital-logic-register`](families/fam-digital-logic-register.md) - Register; variants: Shift, Parallel, Serial Converter.
- [`fam-digital-logic-counter`](families/fam-digital-logic-counter.md) - Counter; variants: Ripple, Synchronous, Up Down.
- [`fam-digital-logic-clock-timing`](families/fam-digital-logic-clock-timing.md) - Clock and timing; variants: Clock, Divider, Delay, One Shot.
- [`fam-digital-logic-bus-transceiver`](families/fam-digital-logic-bus-transceiver.md) - Bus transceiver; variants: Bidirectional, Open Drain.
- [`fam-digital-logic-logic-family`](families/fam-digital-logic-logic-family.md) - Logic family; variants: Ttl, Cmos, Lvc, Ecl.
- [`fam-digital-logic-digital-port`](families/fam-digital-logic-digital-port.md) - Digital port; variants: Input, Output.
- [`fam-digital-logic-digital-memory-primitive`](families/fam-digital-logic-digital-memory-primitive.md) - Digital memory primitive; variants: Bit Cell, Truth Table Rom.
- [`fam-digital-logic-state-machine`](families/fam-digital-logic-state-machine.md) - State machine; variants: Moore, Mealy.

### Memory and storage

6 families and 18 variants; Source PDF, pp. 24-28.

- [`fam-memory-storage-rom-prom`](families/fam-memory-storage-rom-prom.md) - ROM and PROM; variants: Mask Rom, Prom, Eprom.
- [`fam-memory-storage-eeprom-flash`](families/fam-memory-storage-eeprom-flash.md) - EEPROM and Flash; variants: Eeprom, Nor Flash, Nand Flash.
- [`fam-memory-storage-sram`](families/fam-memory-storage-sram.md) - Static RAM; variants: Asynchronous, Synchronous, Dual Port.
- [`fam-memory-storage-dram`](families/fam-memory-storage-dram.md) - Dynamic RAM; variants: Sdram, Ddr, Mobile Dram.
- [`fam-memory-storage-buffer-associative-memory`](families/fam-memory-storage-buffer-associative-memory.md) - Buffer and associative memory; variants: Fifo, Cam, Cache.
- [`fam-memory-storage-functional-storage`](families/fam-memory-storage-functional-storage.md) - Functional storage; variants: Block Device, File Image, Removable Media.

### MCU, FPGA and peripherals

5 families and 24 variants; Source PDF, pp. 25-30.

- [`fam-mcu-fpga-microcontroller`](families/fam-mcu-fpga-microcontroller.md) - Microcontroller; variants: Generic 8 Bit, Generic 32 Bit, Avr Profile, Arm Profile, Risc V Profile, Pic Profile.
- [`fam-mcu-fpga-mcu-peripheral`](families/fam-mcu-fpga-mcu-peripheral.md) - MCU peripheral; variants: Gpio, Timer, Pwm, Watchdog, Interrupt Controller, Dma.
- [`fam-mcu-fpga-serial-peripheral`](families/fam-mcu-fpga-serial-peripheral.md) - Serial peripheral; variants: Uart, I2c, Spi, Can, Usb.
- [`fam-mcu-fpga-firmware-runtime`](families/fam-mcu-fpga-firmware-runtime.md) - Firmware runtime; variants: Hex Image, Elf Image.
- [`fam-mcu-fpga-fpga-hdl`](families/fam-mcu-fpga-fpga-hdl.md) - FPGA and HDL block; variants: Lut, Block Ram, Dsp Slice, Pll, Hdl Wrapper.

### CPU, computer and GPU blocks

6 families and 28 variants; Source PDF, pp. 27-35.

- [`fam-computer-gpu-cpu-building-block`](families/fam-computer-gpu-cpu-building-block.md) - CPU building block; variants: Alu, Register File, Control Unit, Datapath, Pipeline, Cache, Mmu.
- [`fam-computer-gpu-educational-cpu`](families/fam-computer-gpu-educational-cpu.md) - Educational CPU; variants: One Bit, Four Bit, Eight Bit, Sixteen Bit, Small Risc V.
- [`fam-computer-gpu-computer-system`](families/fam-computer-gpu-computer-system.md) - Computer system; variants: Minimal Computer, Eight Bit Computer, Sixteen Bit Computer, Full Educational Computer.
- [`fam-computer-gpu-system-bus-peripheral`](families/fam-computer-gpu-system-bus-peripheral.md) - System bus and peripheral; variants: Address Bus, Data Bus, Control Bus, Interrupt Bus, Dma Controller.
- [`fam-computer-gpu-architecture-model`](families/fam-computer-gpu-architecture-model.md) - Architecture model; variants: Functional, Timing, Isa Execution.
- [`fam-computer-gpu-gpu-accelerator`](families/fam-computer-gpu-gpu-accelerator.md) - GPU and accelerator; variants: Simt, Raster Pipeline, Compute, Vector Accelerator.

### RF and communications

7 families and 22 variants; Source PDF, pp. 28-35.

- [`fam-rf-communications-rf-port-network`](families/fam-rf-communications-rf-port-network.md) - RF port and network model; variants: Rf Port, Termination, S Parameter Black Box.
- [`fam-rf-communications-antenna`](families/fam-rf-communications-antenna.md) - Antenna; variants: Dipole, Monopole, Patch, Array.
- [`fam-rf-communications-rf-passive`](families/fam-rf-communications-rf-passive.md) - RF passive; variants: Attenuator, Balun, Coupler, Splitter Combiner.
- [`fam-rf-communications-rf-switch-amplifier`](families/fam-rf-communications-rf-switch-amplifier.md) - RF switch and amplifier; variants: Rf Switch, Lna, Power Amplifier.
- [`fam-rf-communications-rf-mixer-oscillator`](families/fam-rf-communications-rf-mixer-oscillator.md) - RF mixer and oscillator; variants: Mixer, Local Oscillator, Rf Vco.
- [`fam-rf-communications-modem-transceiver`](families/fam-rf-communications-modem-transceiver.md) - Modem and transceiver; variants: Analog Modem, Ook Fsk, Qam Ofdm.
- [`fam-rf-communications-channel-model`](families/fam-rf-communications-channel-model.md) - Communications channel; variants: Awgn, Multipath Fading.

### Explicitly deferred research families

5 families and 8 variants; Source PDF, pp. 34-41.

- [`fam-deferred-research-vacuum-tube`](families/fam-deferred-research-vacuum-tube.md) - Vacuum tube; variants: Triode, Pentode.
- [`fam-deferred-research-memristive-device`](families/fam-deferred-research-memristive-device.md) - Memristive device; variants: Memristor.
- [`fam-deferred-research-josephson-device`](families/fam-deferred-research-josephson-device.md) - Josephson junction device; variants: Josephson Junction.
- [`fam-deferred-research-tcad-physics`](families/fam-deferred-research-tcad-physics.md) - TCAD physical device model; variants: Semiconductor Device, Photonic Device.
- [`fam-deferred-research-em-mems`](families/fam-deferred-research-em-mems.md) - Detailed EM and MEMS model; variants: Full Wave Em, Multiphysics Mems.

## Stable identifiers

- Category: `cat-<category>`.
- Family: `fam-<category>-<family>`.
- Variant: `var-<category>-<family>-<variant>`.
- Symbol: `sym-<category>-<family>`.
- Package: `pkg-<package>`.
- Device/package binding: `dpb-<variant-slug>-<package-slug>`.
- Golden validation: `GOLD-<CATEGORY_CODE>-<FAMILY>-<CONCERN>`.

Published IDs are immutable. Names and aliases may be clarified, but aliases cannot be reused for another object. A deprecated record remains resolvable and points to its successor or migration rule.

## Basic component and release-target tags

A family is tagged `basic-component` when users reasonably expect a recognizable standalone physical body, leads/contacts, polarity or orientation cues, and value/part markings. In baseline 1.0 this includes connectivity hardware, sources/loads with physical counterparts, passives, switches/protection, semiconductors/optoelectronics, sensors, actuators/HMI, and connectors/cables.

Every production variant declares a release target. The first target is `Realistic Electronics MVP`; later entries use `Post-MVP catalog` or an explicitly named stage. Deferred families use `Research`. A `basic-component` variant cannot become `Released` without an original scalable physical representation and at least one published concrete `DevicePackageBinding` when its physical view uses a reusable package. Candidate `package_refs` and family compatibility lists have no release authority. This is the catalog enforcement point for REQ-037; the exact distinction is normative in [DEVICE_PACKAGE_BINDING_CONTRACT.md](DEVICE_PACKAGE_BINDING_CONTRACT.md).

## Symbol, physical, package, and footprint separation

- The **schematic symbol** communicates function and connectivity.
- The **physical view** communicates recognizable appearance and orientation.
- The **package** supplies reusable body/contact geometry, dimensions, markings, materials, and pin numbering.
- The optional **footprint** supplies sourced manufacturing land-pattern metadata.
- The **electrical model** supplies simulation behavior.

Package compatibility metadata answers which definitions may be offered by a chooser. It never supplies a pinout. Only a `DevicePackageBinding` pins an exact logical-pin contract, package revision, resolved dimensions/contacts, appearance revision, explicit contact map, provenance, and evidence.

Switching views preserves instance identity, connectivity, parameters, model binding, live state, selection, and undo history. A package change cannot silently change electrical behavior. See [PACKAGE_AND_PHYSICAL_APPEARANCE.md](PACKAGE_AND_PHYSICAL_APPEARANCE.md).

## Lifecycle

`Planned -> Symbol Ready -> Connectivity Ready -> Model Ready -> Validated -> Released`

A state transition requires evidence in the registry, family specification, applicable golden tests, coverage matrix, traceability matrix, and release checklist. A physical view may be ready before its model, but neither state implies the other.

## Deferred and unsupported scope

Vacuum tubes, memristive devices, Josephson junctions, TCAD device physics, and detailed EM/MEMS models remain visible as Deferred/Research. They must not be silently substituted by ideal production behavior. Modern CPU/GPU systems use functional, RTL, cycle, architecture, or ISA abstractions rather than an infeasible full-transistor browser promise. [Source PDF, pp. 34-41]

## Governance checklist

- Registry totals remain exactly 162 families and 502 variants.
- Every family has one specification file and no specification is orphaned.
- Every variant has a stable ID, release target, model tiers, package compatibility, supported analyses, provenance, limitations, and golden-test obligations.
- Every released package map is a concrete `DevicePackageBinding`; candidate references are never counted as bindings.
- No IEC artwork, protected vendor mark, or unreviewed redistributable model is embedded.
- A completeness statement always distinguishes built-ins, vendor imports, packages, and research scope.
