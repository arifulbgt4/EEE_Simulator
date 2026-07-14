# Counter

- **Family ID:** `fam-digital-logic-counter`
- **Category:** Digital logic
- **Lifecycle:** Planned
- **Basic component tag:** Not tagged basic
- **Release target:** Mixed variant targets: Realistic Electronics MVP and Post-MVP catalog (see variant table)
- **Source:** Source PDF, pp. 21-26

## Purpose and scope

Counter is the canonical family for the variants listed below. The family boundary is behavioral: package, color, marking, tolerance, and vendor model choices do not create a new electrical family. Vendor-specific parts bind to a variant and an importable model.

## Aliases

Search aliases are **Counter**, **Counter**, and `counter`. Variant names are also aliases. Aliases never replace stable IDs.

## Variants

| Stable variant ID | Display name | Model tiers | Release target | Compatible package profiles |
|---|---|---|---|---|
| `var-digital-logic-counter-ripple` | Ripple | F0, F2, F3 | Realistic Electronics MVP | `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric` |
| `var-digital-logic-counter-synchronous` | Synchronous | F0, F2, F3 | Realistic Electronics MVP | `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric` |
| `var-digital-logic-counter-up-down` | Up Down | F0, F2, F3 | Post-MVP catalog | `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric` |

A variant is a simulation preset, not a manufacturer SKU. All production variants are tagged with an explicit release target. A family carrying `basic-component` requires a scalable physical representation before any variant may become `Released`.

## Original symbol and physical views

- Symbol ID: `sym-digital-logic-counter`. The artwork is original project work aligned with familiar IEC/ANSI conventions; IEC 60617 artwork must not be copied.
- Schematic, physical, and package views share one instance identity, connectivity graph, parameter set, model binding, live simulation state, selection state, and undo history.
- Physical artwork must show the body, leads or contacts, polarity and pin-one cues, value/part markings, and material/color regions appropriate to the selected variant and package.
- Geometry is scalable and uses zoom-dependent detail levels. Shape, labels, and orientation cues must remain understandable without color.
- Physical appearance is illustrative unless a package record supplies verified dimensions. It must never imply unvalidated dimensional, thermal, or electrical accuracy.
- Package selection is independent of electrical function. Changing package cannot change the model unless the user explicitly chooses a package-parasitic profile.

## Pin contract

| Pin or group | Name | Electrical type | Domains |
|---|---|---|---|
| `1..N` | INPUTS | input | digital, power |
| `N+1..M` | OUTPUTS | output | digital, power |
| `VDD` | VDD | power | digital, power |
| `VSS` | VSS | power | digital, power |

Pin IDs are stable inside a variant. A package pin map must be explicit, bijective for all required logical pins, and validated before export or release. Unmapped no-connect package pins are declared, never inferred.

## Parameter contract

| Parameter | Meaning | Internal unit | Default | Limits |
|---|---|---:|---:|---|
| `width` | Counter width | bit | 8 | 1..4096 |
| `modulus` | Counter modulus | 1 | 256 | 2..2^width |
| `direction` | Initial direction | 1 | up | up or down |
| `initial_value` | Initial count | 1 | 0 | 0..modulus-1 |
| `clock_to_output` | Clock-to-output delay | s | 0 | >=0 |

All numerical values use SI base units internally. Display prefixes and localized formatting are presentation concerns. Variant-specific parameters may refine this table but may not weaken its validation rules.

## Fidelity and supported analyses

Supported fidelity tiers: **F0, F2, F3**. Supported analysis capabilities: **digital event, timing, truth table**.

- F0 validates connectivity and pin rules.
- F1 supplies ideal or equation-level behavior where applicable.
- F2 supplies behavioral, event, timing, or control behavior where applicable.
- F3 binds a compact, macro, HDL, S-parameter, or other validated external model.
- F4 adds tolerance, electrothermal, parasitic, aging, and failure behavior where applicable.
- F5 is restricted to declared research models and may not be represented as production-ready.

## Family-specific implementation reference

This section is the normative planning baseline for model tasks. A vendor or imported model may refine it only inside a declared validation envelope; it may not silently change pin order, units, polarity, state initialization, or unsupported behavior.

- **Governing relation or state rule:** A bounded state value advances, decrements, loads, or resets on declared events with modulus, carry/borrow, enable, and timing rules.
- **F0:** Connectivity-only: validate declared pins, domains, width/direction, hierarchy, and package mapping; do not claim numerical behavior. Family baseline: A bounded state value advances, decrements, loads, or resets on declared events with modulus, carry/borrow, enable, and timing rules.
- **F2:** Behavioral/timing tier: preserve the family baseline using deterministic integer-tick state/event rules and explicit initialization: A bounded state value advances, decrements, loads, or resets on declared events with modulus, carry/borrow, enable, and timing rules.
- **F3:** Compact/macro/external tier: bind a pinned model or executable relation that preserves ordered pins and the validated envelope; the governing family relation is: A bounded state value advances, decrements, loads, or resets on declared events with modulus, carry/borrow, enable, and timing rules.
- **Exact nominal vector:** pins `1..N:INPUTS`/input, `N+1..M:OUTPUTS`/output, `VDD:VDD`/power, `VSS:VSS`/power; parameters `width`=8 bit (1..4096); `modulus`=256 1 (2..2^width); `direction`=up 1 (up or down); `initial_value`=0 1 (0..modulus-1); `clock_to_output`=0 s (>=0).
- **Boundary vector:** every declared inclusive/exclusive parameter limit, supported pin/domain/width edge, and supported-analysis boundary is exercised independently; combinations outside the declared envelope are invalid, not extrapolated.
- **Failure vector:** `open-circuit`, `short-circuit`, `parameter-drift`, `overstress-or-saturation`, plus non-finite parameters, invalid pin maps, unsupported analysis, and unavailable fidelity.
- **Golden evidence:** `GOLD-DIG-COUNTER-NOMINAL`, `GOLD-DIG-COUNTER-BOUNDARY`, `GOLD-DIG-COUNTER-FAILURE`.

## Non-ideal, thermal, and failure behavior

- Non-ideal behavior is explicit: applicable leakage, series resistance, capacitance, inductance, finite bandwidth, delay, saturation, quantization, hysteresis, or mechanical limits are parameters rather than hidden effects.
- Thermal behavior declares reference temperature, coefficients, power-to-heat coupling, operating limits, and whether self-heating is supported. Unsupported thermal behavior is reported, not silently approximated.
- Minimum fault modes are open circuit, short circuit, parameter drift, and overstress/saturation. Inapplicable modes are marked `not-applicable` with rationale.
- Failure transitions are deterministic for identical project, configuration, seed, and engine versions.

## Import and export mappings

Verilog/SystemVerilog, VCD/FST, and HEX/ELF bindings are applicable. SPICE or IBIS mappings may be attached only when pin and domain semantics are complete.

Every imported model records format/version, content digest, source URL or artifact identity, license/SPDX expression, original pin order, normalized pin map, supported analyses, known limits, and review status.

## Provenance and licensing

The taxonomy entry is project-authored from the platform scope (Source PDF, pp. 21-26). Symbol artwork is original and intended for Apache-2.0 distribution. Imported model licenses remain model-specific and require an SPDX identifier plus redistribution review. IEC references guide terminology only; proprietary symbol artwork is not copied.

## Golden validation

- `GOLD-DIG-COUNTER-NOMINAL`: nominal positive-path behavior.
- `GOLD-DIG-COUNTER-BOUNDARY`: declared parameter and operating boundaries.
- `GOLD-DIG-COUNTER-FAILURE`: diagnostic and fault behavior.

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

