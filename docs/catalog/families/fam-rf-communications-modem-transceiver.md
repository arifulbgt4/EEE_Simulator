# Modem and transceiver

- **Family ID:** `fam-rf-communications-modem-transceiver`
- **Category:** RF and communications
- **Lifecycle:** Planned
- **Basic component tag:** Not tagged basic
- **Release target:** Post-MVP catalog
- **Source:** Source PDF, pp. 28-35

## Purpose and scope

Modem and transceiver is the canonical family for the variants listed below. The family boundary is behavioral: package, color, marking, tolerance, and vendor model choices do not create a new electrical family. Vendor-specific parts bind to a variant and an importable model.

## Aliases

Search aliases are **Modem and transceiver**, **Modem Transceiver**, and `modem-transceiver`. Variant names are also aliases. Aliases never replace stable IDs.

## Variants

| Stable variant ID | Display name | Model tiers | Release target | Compatible package profiles |
|---|---|---|---|---|
| `var-rf-communications-modem-transceiver-analog-modem` | Analog Modem | F1, F2, F3 | Post-MVP catalog | `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric` |
| `var-rf-communications-modem-transceiver-ook-fsk` | Ook Fsk | F1, F2, F3 | Post-MVP catalog | `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric` |
| `var-rf-communications-modem-transceiver-qam-ofdm` | Qam Ofdm | F1, F2, F3 | Post-MVP catalog | `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric` |

A variant is a simulation preset, not a manufacturer SKU. All production variants are tagged with an explicit release target. A family carrying `basic-component` requires a scalable physical representation before any variant may become `Released`.

## Original symbol and physical views

- Symbol ID: `sym-rf-communications-modem-transceiver`. The artwork is original project work aligned with familiar IEC/ANSI conventions; IEC 60617 artwork must not be copied.
- Schematic, physical, and package views share one instance identity, connectivity graph, parameter set, model binding, live simulation state, selection state, and undo history.
- Physical artwork must show the body, leads or contacts, polarity and pin-one cues, value/part markings, and material/color regions appropriate to the selected variant and package.
- Geometry is scalable and uses zoom-dependent detail levels. Shape, labels, and orientation cues must remain understandable without color.
- Physical appearance is illustrative unless a package record supplies verified dimensions. It must never imply unvalidated dimensional, thermal, or electrical accuracy.
- Package selection is independent of electrical function. Changing package cannot change the model unless the user explicitly chooses a package-parasitic profile.

## Pin contract

| Pin or group | Name | Electrical type | Domains |
|---|---|---|---|
| `IN` | RF_IN | passive | rf, electrical, communications |
| `OUT` | RF_OUT | passive | rf, electrical, communications |
| `GND` | GROUND | reference | rf, electrical, communications |

Pin IDs are stable inside a variant. A package pin map must be explicit, bijective for all required logical pins, and validated before export or release. Unmapped no-connect package pins are declared, never inferred.

## Parameter contract

| Parameter | Meaning | Internal unit | Default | Limits |
|---|---|---:|---:|---|
| `carrier_frequency` | Carrier frequency | Hz | 1e9 | >0 |
| `symbol_rate` | Symbol rate | 1/s | 1e6 | >0 |
| `modulation` | Modulation profile | 1 | qpsk | registered profile |
| `coding_rate` | Coding rate | 1 | 1 | 0..1 |
| `tx_power` | Transmit power | W | 0.1 | >=0 |
| `noise_figure` | Receiver noise factor | 1 | 2 | >=1 |

All numerical values use SI base units internally. Display prefixes and localized formatting are presentation concerns. Variant-specific parameters may refine this table but may not weaken its validation rules.

## Fidelity and supported analyses

Supported fidelity tiers: **F1, F2, F3**. Supported analysis capabilities: **AC, S-parameter, noise, modulation**.

- F0 validates connectivity and pin rules.
- F1 supplies ideal or equation-level behavior where applicable.
- F2 supplies behavioral, event, timing, or control behavior where applicable.
- F3 binds a compact, macro, HDL, S-parameter, or other validated external model.
- F4 adds tolerance, electrothermal, parasitic, aging, and failure behavior where applicable.
- F5 is restricted to declared research models and may not be represented as production-ready.

## Family-specific implementation reference

This section is the normative planning baseline for model tasks. A vendor or imported model may refine it only inside a declared validation envelope; it may not silently change pin order, units, polarity, state initialization, or unsupported behavior.

- **Governing relation or state rule:** Bits/symbols map through the selected modulation, coding, framing, timing, RF/baseband, synchronization, and error state machine.
- **F1:** Ideal/equation tier: implement exactly this family baseline and its declared parameter limits: Bits/symbols map through the selected modulation, coding, framing, timing, RF/baseband, synchronization, and error state machine.
- **F2:** Behavioral/timing tier: preserve the family baseline using deterministic integer-tick state/event rules and explicit initialization: Bits/symbols map through the selected modulation, coding, framing, timing, RF/baseband, synchronization, and error state machine.
- **F3:** Compact/macro/external tier: bind a pinned model or executable relation that preserves ordered pins and the validated envelope; the governing family relation is: Bits/symbols map through the selected modulation, coding, framing, timing, RF/baseband, synchronization, and error state machine.
- **Exact nominal vector:** pins `IN:RF_IN`/passive, `OUT:RF_OUT`/passive, `GND:GROUND`/reference; parameters `carrier_frequency`=1e9 Hz (>0); `symbol_rate`=1e6 1/s (>0); `modulation`=qpsk 1 (registered profile); `coding_rate`=1 1 (0..1); `tx_power`=0.1 W (>=0); `noise_figure`=2 1 (>=1).
- **Boundary vector:** every declared inclusive/exclusive parameter limit, supported pin/domain/width edge, and supported-analysis boundary is exercised independently; combinations outside the declared envelope are invalid, not extrapolated.
- **Failure vector:** `open-circuit`, `short-circuit`, `parameter-drift`, `overstress-or-saturation`, plus non-finite parameters, invalid pin maps, unsupported analysis, and unavailable fidelity.
- **Golden evidence:** `GOLD-RFC-MODEM_TRANSCEIVER-NOMINAL`, `GOLD-RFC-MODEM_TRANSCEIVER-BOUNDARY`, `GOLD-RFC-MODEM_TRANSCEIVER-FAILURE`.

## Non-ideal, thermal, and failure behavior

- Non-ideal behavior is explicit: applicable leakage, series resistance, capacitance, inductance, finite bandwidth, delay, saturation, quantization, hysteresis, or mechanical limits are parameters rather than hidden effects.
- Thermal behavior declares reference temperature, coefficients, power-to-heat coupling, operating limits, and whether self-heating is supported. Unsupported thermal behavior is reported, not silently approximated.
- Minimum fault modes are open circuit, short circuit, parameter drift, and overstress/saturation. Inapplicable modes are marked `not-applicable` with rationale.
- Failure transitions are deterministic for identical project, configuration, seed, and engine versions.

## Import and export mappings

Touchstone 2.1, IBIS 8.0, and CSV table mappings are applicable. Reference impedance and port order are mandatory.

Every imported model records format/version, content digest, source URL or artifact identity, license/SPDX expression, original pin order, normalized pin map, supported analyses, known limits, and review status.

## Provenance and licensing

The taxonomy entry is project-authored from the platform scope (Source PDF, pp. 28-35). Symbol artwork is original and intended for Apache-2.0 distribution. Imported model licenses remain model-specific and require an SPDX identifier plus redistribution review. IEC references guide terminology only; proprietary symbol artwork is not copied.

## Golden validation

- `GOLD-RFC-MODEM_TRANSCEIVER-NOMINAL`: nominal positive-path behavior.
- `GOLD-RFC-MODEM_TRANSCEIVER-BOUNDARY`: declared parameter and operating boundaries.
- `GOLD-RFC-MODEM_TRANSCEIVER-FAILURE`: diagnostic and fault behavior.

Each released variant must link concrete fixtures and reference results for every applicable test. Physical-view QA additionally checks pin count/order, orientation after rotation/mirroring, polarity/pin-one markings, LOD behavior, keyboard/non-color identification, and view-switch state preservation.

## Limitations

- Only the listed variants, analyses, fidelity tiers, validated parameter envelope, and explicit package maps may be claimed.
- A realistic illustration does not certify a footprint, enclosure, creepage, clearance, thermal resistance, or manufacturability.
- Manufacturer ordering codes are external library records, not built-in family variants.
- Deferred or unsupported behavior must remain visible in the editor and diagnostics.

## Release checklist

- [ ] Registry entry and this specification agree.
- [ ] Original schematic and physical artwork pass visual and accessibility review.
- [ ] Every package mapping is explicit and validated.
- [ ] Nominal, boundary, and failure golden tests have current evidence.
- [ ] Provenance and license metadata are complete.
- [ ] Coverage, traceability, and task records are synchronized.

