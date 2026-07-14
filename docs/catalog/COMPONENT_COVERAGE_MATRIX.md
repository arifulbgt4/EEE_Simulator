# Component Coverage Matrix

Status: **Baseline 1.0 coverage contract**  
Registry: [component-registry.yaml](component-registry.yaml)  
Family specifications: [families](families)  
Physical packages: [package-registry.yaml](package-registry.yaml)

## Interpretation

`Specified` means the documentation contract exists; it does not claim executable implementation. `Required` means the artifact or validation must exist before release. `Deferred` means the work is visible but outside production gates. No empty cell is permitted in this matrix.

Release coverage is variant-scoped: 106 production presets are tagged for the Realistic Electronics MVP, 388 production presets are tagged for the R7 complete-catalog gate, and eight presets remain Deferred/Research. Mixed-target families may finish a gate-scoped core profile while optional import formats or later presets remain explicitly unavailable; no unfinished capability may be claimed by the earlier profile.

## Category totals

| Category | Families | Variants | Symbol contract | Physical/package contract | Model contract | Validation contract |
|---|---:|---:|---|---|---|---|
| Connectivity and schematic primitives | 10 | 18 | Specified | Specified | Specified | Required |
| Sources and loads | 13 | 26 | Specified | Specified | Specified | Required |
| Passives, magnetics and transmission | 15 | 40 | Specified | Specified | Specified | Required |
| Switches, protection and isolation | 12 | 36 | Specified | Specified | Specified | Required |
| Semiconductor and optoelectronics | 15 | 46 | Specified | Specified | Specified | Required |
| Analog and mixed-signal abstractions | 13 | 38 | Specified | Specified | Specified | Required |
| Power-electronics blocks | 8 | 24 | Specified | Specified | Specified | Required |
| Sensors and environment | 10 | 42 | Specified | Specified | Specified | Required |
| Actuators, displays and HMI | 10 | 32 | Specified | Specified | Specified | Required |
| Connectors and cables | 3 | 24 | Specified | Specified | Specified | Required |
| Measurement instruments | 8 | 22 | Specified | Specified | Specified | Required |
| Digital logic | 16 | 54 | Specified | Specified | Specified | Required |
| Memory and storage | 6 | 18 | Specified | Specified | Specified | Required |
| MCU, FPGA and peripherals | 5 | 24 | Specified | Specified | Specified | Required |
| CPU, computer and GPU blocks | 6 | 28 | Specified | Specified | Specified | Required |
| RF and communications | 7 | 22 | Specified | Specified | Specified | Required |
| Explicitly deferred research families | 5 | 8 | Specified | Research profile | Deferred | Research gate |
| **Total** | **162** | **502** | **Specified** | **Specified** | **Specified/Deferred** | **Required** |

## Family-level coverage

| Family ID | Variants | Basic tag | Symbol | Physical view | Package map | Model tiers | Golden tests | Lifecycle |
|---|---:|---|---|---|---|---|---|---|
| [`fam-connectivity-wire`](families/fam-connectivity-wire.md) | 1 | Yes | Specified | Required | Explicit | F0-F1 | Nominal/boundary/failure | Planned |
| [`fam-connectivity-junction`](families/fam-connectivity-junction.md) | 1 | Yes | Specified | Required | Explicit | F0-F1 | Nominal/boundary/failure | Planned |
| [`fam-connectivity-crossover`](families/fam-connectivity-crossover.md) | 1 | Yes | Specified | Required | Explicit | F0-F1 | Nominal/boundary/failure | Planned |
| [`fam-connectivity-bus`](families/fam-connectivity-bus.md) | 1 | Yes | Specified | Required | Explicit | F0-F1 | Nominal/boundary/failure | Planned |
| [`fam-connectivity-net-label`](families/fam-connectivity-net-label.md) | 1 | Yes | Specified | Required | Explicit | F0-F1 | Nominal/boundary/failure | Planned |
| [`fam-connectivity-ground`](families/fam-connectivity-ground.md) | 6 | Yes | Specified | Required | Explicit | F0-F1 | Nominal/boundary/failure | Planned |
| [`fam-connectivity-power-rail`](families/fam-connectivity-power-rail.md) | 1 | Yes | Specified | Required | Explicit | F0-F1 | Nominal/boundary/failure | Planned |
| [`fam-connectivity-terminal-bridge`](families/fam-connectivity-terminal-bridge.md) | 4 | Yes | Specified | Required | Explicit | F0-F1 | Nominal/boundary/failure | Planned |
| [`fam-connectivity-hierarchical-port`](families/fam-connectivity-hierarchical-port.md) | 1 | Yes | Specified | Required | Explicit | F0-F1 | Nominal/boundary/failure | Planned |
| [`fam-connectivity-subcircuit`](families/fam-connectivity-subcircuit.md) | 1 | Yes | Specified | Required | Explicit | F0-F1 | Nominal/boundary/failure | Planned |
| [`fam-sources-loads-independent-voltage`](families/fam-sources-loads-independent-voltage.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sources-loads-independent-current`](families/fam-sources-loads-independent-current.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sources-loads-waveform-source`](families/fam-sources-loads-waveform-source.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sources-loads-noise-source`](families/fam-sources-loads-noise-source.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sources-loads-digital-pattern-source`](families/fam-sources-loads-digital-pattern-source.md) | 1 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sources-loads-dependent-source`](families/fam-sources-loads-dependent-source.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sources-loads-behavioral-source`](families/fam-sources-loads-behavioral-source.md) | 1 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sources-loads-battery-source`](families/fam-sources-loads-battery-source.md) | 1 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sources-loads-mains-source`](families/fam-sources-loads-mains-source.md) | 1 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sources-loads-solar-source`](families/fam-sources-loads-solar-source.md) | 1 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sources-loads-constant-load`](families/fam-sources-loads-constant-load.md) | 1 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sources-loads-programmable-load`](families/fam-sources-loads-programmable-load.md) | 1 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sources-loads-electronic-load`](families/fam-sources-loads-electronic-load.md) | 1 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-resistor`](families/fam-passives-resistor.md) | 5 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-potentiometer`](families/fam-passives-potentiometer.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-resistor-array`](families/fam-passives-resistor-array.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-thermistor`](families/fam-passives-thermistor.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-photoresistor`](families/fam-passives-photoresistor.md) | 1 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-capacitor`](families/fam-passives-capacitor.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-variable-capacitor`](families/fam-passives-variable-capacitor.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-inductor`](families/fam-passives-inductor.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-choke`](families/fam-passives-choke.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-ferrite`](families/fam-passives-ferrite.md) | 1 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-coupled-inductor`](families/fam-passives-coupled-inductor.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-transformer`](families/fam-passives-transformer.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-crystal-resonator`](families/fam-passives-crystal-resonator.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-transmission-line`](families/fam-passives-transmission-line.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-passives-generic-impedance`](families/fam-passives-generic-impedance.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-switch-protection-mechanical-switch`](families/fam-switch-protection-mechanical-switch.md) | 5 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-switch-protection-controlled-switch`](families/fam-switch-protection-controlled-switch.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-switch-protection-analog-switch`](families/fam-switch-protection-analog-switch.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-switch-protection-transmission-gate`](families/fam-switch-protection-transmission-gate.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-switch-protection-relay`](families/fam-switch-protection-relay.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-switch-protection-fuse`](families/fam-switch-protection-fuse.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-switch-protection-circuit-breaker`](families/fam-switch-protection-circuit-breaker.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-switch-protection-surge-suppressor`](families/fam-switch-protection-surge-suppressor.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-switch-protection-crowbar`](families/fam-switch-protection-crowbar.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-switch-protection-snubber`](families/fam-switch-protection-snubber.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-switch-protection-isolation-device`](families/fam-switch-protection-isolation-device.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-switch-protection-thermal-protection`](families/fam-switch-protection-thermal-protection.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-diode`](families/fam-semiconductors-diode.md) | 8 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-led`](families/fam-semiconductors-led.md) | 5 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-photodetector`](families/fam-semiconductors-photodetector.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-photovoltaic`](families/fam-semiconductors-photovoltaic.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-bjt`](families/fam-semiconductors-bjt.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-jfet`](families/fam-semiconductors-jfet.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-mosfet`](families/fam-semiconductors-mosfet.md) | 6 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-igbt`](families/fam-semiconductors-igbt.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-thyristor`](families/fam-semiconductors-thyristor.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-ujt`](families/fam-semiconductors-ujt.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-mesfet`](families/fam-semiconductors-mesfet.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-hemt`](families/fam-semiconductors-hemt.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-opto-isolator`](families/fam-semiconductors-opto-isolator.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-laser-diode`](families/fam-semiconductors-laser-diode.md) | 1 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-semiconductors-semiconductor-generic`](families/fam-semiconductors-semiconductor-generic.md) | 1 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-analog-mixed-signal-operational-amplifier`](families/fam-analog-mixed-signal-operational-amplifier.md) | 4 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-analog-mixed-signal-comparator`](families/fam-analog-mixed-signal-comparator.md) | 3 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-analog-mixed-signal-schmitt-trigger`](families/fam-analog-mixed-signal-schmitt-trigger.md) | 2 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-analog-mixed-signal-instrumentation-amplifier`](families/fam-analog-mixed-signal-instrumentation-amplifier.md) | 2 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-analog-mixed-signal-transimpedance-amplifier`](families/fam-analog-mixed-signal-transimpedance-amplifier.md) | 2 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-analog-mixed-signal-ota`](families/fam-analog-mixed-signal-ota.md) | 2 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-analog-mixed-signal-current-mirror`](families/fam-analog-mixed-signal-current-mirror.md) | 2 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-analog-mixed-signal-analog-math`](families/fam-analog-mixed-signal-analog-math.md) | 3 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-analog-mixed-signal-analog-mux`](families/fam-analog-mixed-signal-analog-mux.md) | 3 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-analog-mixed-signal-sample-hold`](families/fam-analog-mixed-signal-sample-hold.md) | 2 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-analog-mixed-signal-data-converter`](families/fam-analog-mixed-signal-data-converter.md) | 4 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-analog-mixed-signal-regulator-reference`](families/fam-analog-mixed-signal-regulator-reference.md) | 3 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-analog-mixed-signal-timing-filter-conversion`](families/fam-analog-mixed-signal-timing-filter-conversion.md) | 6 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-power-electronics-rectifier-block`](families/fam-power-electronics-rectifier-block.md) | 3 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-power-electronics-gate-driver`](families/fam-power-electronics-gate-driver.md) | 3 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-power-electronics-dc-converter`](families/fam-power-electronics-dc-converter.md) | 6 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-power-electronics-bridge-inverter`](families/fam-power-electronics-bridge-inverter.md) | 3 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-power-electronics-pwm-controller`](families/fam-power-electronics-pwm-controller.md) | 1 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-power-electronics-motor-driver`](families/fam-power-electronics-motor-driver.md) | 3 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-power-electronics-charger-bms`](families/fam-power-electronics-charger-bms.md) | 2 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-power-electronics-power-control`](families/fam-power-electronics-power-control.md) | 3 | No | Specified | Specified or virtual | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sensors-environment-temperature-sensor`](families/fam-sensors-environment-temperature-sensor.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sensors-environment-optical-sensor`](families/fam-sensors-environment-optical-sensor.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sensors-environment-magnetic-motion-sensor`](families/fam-sensors-environment-magnetic-motion-sensor.md) | 5 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sensors-environment-force-pressure-sensor`](families/fam-sensors-environment-force-pressure-sensor.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sensors-environment-sound-distance-sensor`](families/fam-sensors-environment-sound-distance-sensor.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sensors-environment-climate-gas-sensor`](families/fam-sensors-environment-climate-gas-sensor.md) | 5 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sensors-environment-safety-agriculture-sensor`](families/fam-sensors-environment-safety-agriculture-sensor.md) | 5 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sensors-environment-water-quality-sensor`](families/fam-sensors-environment-water-quality-sensor.md) | 6 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sensors-environment-electrical-sensor`](families/fam-sensors-environment-electrical-sensor.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-sensors-environment-environment-stimulus`](families/fam-sensors-environment-environment-stimulus.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-actuators-hmi-lamp-heater`](families/fam-actuators-hmi-lamp-heater.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-actuators-hmi-audio-output`](families/fam-actuators-hmi-audio-output.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-actuators-hmi-dc-motor`](families/fam-actuators-hmi-dc-motor.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-actuators-hmi-bldc-motor`](families/fam-actuators-hmi-bldc-motor.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-actuators-hmi-stepper-motor`](families/fam-actuators-hmi-stepper-motor.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-actuators-hmi-servo`](families/fam-actuators-hmi-servo.md) | 2 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-actuators-hmi-solenoid-valve`](families/fam-actuators-hmi-solenoid-valve.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-actuators-hmi-fan-pump`](families/fam-actuators-hmi-fan-pump.md) | 4 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-actuators-hmi-display`](families/fam-actuators-hmi-display.md) | 5 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-actuators-hmi-hmi-input`](families/fam-actuators-hmi-hmi-input.md) | 3 | Yes | Specified | Required | Explicit | F0-F4 | Nominal/boundary/failure | Planned |
| [`fam-connectors-cables-connector`](families/fam-connectors-cables-connector.md) | 12 | Yes | Specified | Required | Explicit | F0/F1/F3 | Nominal/boundary/failure | Planned |
| [`fam-connectors-cables-socket-board`](families/fam-connectors-cables-socket-board.md) | 6 | Yes | Specified | Required | Explicit | F0/F1/F3 | Nominal/boundary/failure | Planned |
| [`fam-connectors-cables-cable`](families/fam-connectors-cables-cable.md) | 6 | Yes | Specified | Required | Explicit | F0/F1/F3 | Nominal/boundary/failure | Planned |
| [`fam-instruments-probe`](families/fam-instruments-probe.md) | 4 | No | Specified | Specified or virtual | Explicit | F0-F2 | Nominal/boundary/failure | Planned |
| [`fam-instruments-multimeter`](families/fam-instruments-multimeter.md) | 3 | No | Specified | Specified or virtual | Explicit | F0-F2 | Nominal/boundary/failure | Planned |
| [`fam-instruments-oscilloscope`](families/fam-instruments-oscilloscope.md) | 3 | No | Specified | Specified or virtual | Explicit | F0-F2 | Nominal/boundary/failure | Planned |
| [`fam-instruments-logic-analyzer`](families/fam-instruments-logic-analyzer.md) | 2 | No | Specified | Specified or virtual | Explicit | F0-F2 | Nominal/boundary/failure | Planned |
| [`fam-instruments-signal-generator`](families/fam-instruments-signal-generator.md) | 3 | No | Specified | Specified or virtual | Explicit | F0-F2 | Nominal/boundary/failure | Planned |
| [`fam-instruments-bench-supply`](families/fam-instruments-bench-supply.md) | 2 | No | Specified | Specified or virtual | Explicit | F0-F2 | Nominal/boundary/failure | Planned |
| [`fam-instruments-impedance-rf-instrument`](families/fam-instruments-impedance-rf-instrument.md) | 3 | No | Specified | Specified or virtual | Explicit | F0-F2 | Nominal/boundary/failure | Planned |
| [`fam-instruments-specialized-instrument`](families/fam-instruments-specialized-instrument.md) | 2 | No | Specified | Specified or virtual | Explicit | F0-F2 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-logic-constant`](families/fam-digital-logic-logic-constant.md) | 4 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-logic-gate`](families/fam-digital-logic-logic-gate.md) | 8 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-tri-state`](families/fam-digital-logic-tri-state.md) | 2 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-arithmetic-logic`](families/fam-digital-logic-arithmetic-logic.md) | 5 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-digital-comparator`](families/fam-digital-logic-digital-comparator.md) | 2 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-mux-codec`](families/fam-digital-logic-mux-codec.md) | 4 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-latch`](families/fam-digital-logic-latch.md) | 3 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-flip-flop`](families/fam-digital-logic-flip-flop.md) | 4 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-register`](families/fam-digital-logic-register.md) | 3 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-counter`](families/fam-digital-logic-counter.md) | 3 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-clock-timing`](families/fam-digital-logic-clock-timing.md) | 4 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-bus-transceiver`](families/fam-digital-logic-bus-transceiver.md) | 2 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-logic-family`](families/fam-digital-logic-logic-family.md) | 4 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-digital-port`](families/fam-digital-logic-digital-port.md) | 2 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-digital-memory-primitive`](families/fam-digital-logic-digital-memory-primitive.md) | 2 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-digital-logic-state-machine`](families/fam-digital-logic-state-machine.md) | 2 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-memory-storage-rom-prom`](families/fam-memory-storage-rom-prom.md) | 3 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-memory-storage-eeprom-flash`](families/fam-memory-storage-eeprom-flash.md) | 3 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-memory-storage-sram`](families/fam-memory-storage-sram.md) | 3 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-memory-storage-dram`](families/fam-memory-storage-dram.md) | 3 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-memory-storage-buffer-associative-memory`](families/fam-memory-storage-buffer-associative-memory.md) | 3 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-memory-storage-functional-storage`](families/fam-memory-storage-functional-storage.md) | 3 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-mcu-fpga-microcontroller`](families/fam-mcu-fpga-microcontroller.md) | 6 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-mcu-fpga-mcu-peripheral`](families/fam-mcu-fpga-mcu-peripheral.md) | 6 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-mcu-fpga-serial-peripheral`](families/fam-mcu-fpga-serial-peripheral.md) | 5 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-mcu-fpga-firmware-runtime`](families/fam-mcu-fpga-firmware-runtime.md) | 2 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-mcu-fpga-fpga-hdl`](families/fam-mcu-fpga-fpga-hdl.md) | 5 | No | Specified | Specified or virtual | Explicit | F0/F2/F3 | Nominal/boundary/failure | Planned |
| [`fam-computer-gpu-cpu-building-block`](families/fam-computer-gpu-cpu-building-block.md) | 7 | No | Specified | Specified or virtual | Explicit | F0/F2 | Nominal/boundary/failure | Planned |
| [`fam-computer-gpu-educational-cpu`](families/fam-computer-gpu-educational-cpu.md) | 5 | No | Specified | Specified or virtual | Explicit | F0/F2 | Nominal/boundary/failure | Planned |
| [`fam-computer-gpu-computer-system`](families/fam-computer-gpu-computer-system.md) | 4 | No | Specified | Specified or virtual | Explicit | F0/F2 | Nominal/boundary/failure | Planned |
| [`fam-computer-gpu-system-bus-peripheral`](families/fam-computer-gpu-system-bus-peripheral.md) | 5 | No | Specified | Specified or virtual | Explicit | F0/F2 | Nominal/boundary/failure | Planned |
| [`fam-computer-gpu-architecture-model`](families/fam-computer-gpu-architecture-model.md) | 3 | No | Specified | Specified or virtual | Explicit | F0/F2 | Nominal/boundary/failure | Planned |
| [`fam-computer-gpu-gpu-accelerator`](families/fam-computer-gpu-gpu-accelerator.md) | 4 | No | Specified | Specified or virtual | Explicit | F0/F2 | Nominal/boundary/failure | Planned |
| [`fam-rf-communications-rf-port-network`](families/fam-rf-communications-rf-port-network.md) | 3 | No | Specified | Specified or virtual | Explicit | F1-F3 | Nominal/boundary/failure | Planned |
| [`fam-rf-communications-antenna`](families/fam-rf-communications-antenna.md) | 4 | No | Specified | Specified or virtual | Explicit | F1-F3 | Nominal/boundary/failure | Planned |
| [`fam-rf-communications-rf-passive`](families/fam-rf-communications-rf-passive.md) | 4 | No | Specified | Specified or virtual | Explicit | F1-F3 | Nominal/boundary/failure | Planned |
| [`fam-rf-communications-rf-switch-amplifier`](families/fam-rf-communications-rf-switch-amplifier.md) | 3 | No | Specified | Specified or virtual | Explicit | F1-F3 | Nominal/boundary/failure | Planned |
| [`fam-rf-communications-rf-mixer-oscillator`](families/fam-rf-communications-rf-mixer-oscillator.md) | 3 | No | Specified | Specified or virtual | Explicit | F1-F3 | Nominal/boundary/failure | Planned |
| [`fam-rf-communications-modem-transceiver`](families/fam-rf-communications-modem-transceiver.md) | 3 | No | Specified | Specified or virtual | Explicit | F1-F3 | Nominal/boundary/failure | Planned |
| [`fam-rf-communications-channel-model`](families/fam-rf-communications-channel-model.md) | 2 | No | Specified | Specified or virtual | Explicit | F1-F3 | Nominal/boundary/failure | Planned |
| [`fam-deferred-research-vacuum-tube`](families/fam-deferred-research-vacuum-tube.md) | 2 | No | Specified | Specified or virtual | Explicit | F5 | Nominal/boundary/failure | Deferred/Research |
| [`fam-deferred-research-memristive-device`](families/fam-deferred-research-memristive-device.md) | 1 | No | Specified | Specified or virtual | Explicit | F5 | Nominal/boundary/failure | Deferred/Research |
| [`fam-deferred-research-josephson-device`](families/fam-deferred-research-josephson-device.md) | 1 | No | Specified | Specified or virtual | Explicit | F5 | Nominal/boundary/failure | Deferred/Research |
| [`fam-deferred-research-tcad-physics`](families/fam-deferred-research-tcad-physics.md) | 2 | No | Specified | Specified or virtual | Explicit | F5 | Nominal/boundary/failure | Deferred/Research |
| [`fam-deferred-research-em-mems`](families/fam-deferred-research-em-mems.md) | 2 | No | Specified | Specified or virtual | Explicit | F5 | Nominal/boundary/failure | Deferred/Research |

## Coverage invariants

- The category table totals are mechanically checked against the registry.
- Every family row links to exactly one family specification.
- Every one of the 502 variants appears exactly once under one family.
- `basic-component` rows require physical appearance, polarity/pin-one cues where applicable, non-color identification, LOD behavior, and view-switch preservation before release.
- All package bindings require an explicit logical-to-physical pin map; no pin order is inferred from a package name.
- Golden validation must cover nominal, boundary, and failure behavior. `not-applicable` requires rationale; a blank is invalid.
- A component release row covers the exact gate-scoped core profile defined by the model contract. Optional import/capability extensions are tracked separately, remain unavailable until their own validation is `Done`, and cannot substitute for any gate-required tier, package, appearance, analysis, or failure evidence.
- Deferred families remain counted and visible but cannot satisfy a production release gate.

## Release evidence columns to add during implementation

Implementation tasks may append evidence links without changing stable IDs: symbol asset revision, physical asset revision, package-map validation report, model fixture, numerical reference, test run, license review, and release gate. Until evidence is current, lifecycle remains `Planned`.
