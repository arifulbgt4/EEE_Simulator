# Resistor array

- **Family ID:** `fam-passives-resistor-array`
- **Category:** Passives, magnetics and transmission
- **Lifecycle:** Planned
- **Basic component tag:** `basic-component`
- **Release target:** Post-MVP catalog
- **Source:** Source PDF, pp. 8-13

## Purpose and scope

Resistor array is the canonical family for the variants listed below. The family boundary is behavioral: package, color, marking, tolerance, and vendor model choices do not create a new electrical family. Vendor-specific parts bind to a variant and an importable model.

## Aliases

Search aliases are **Resistor array**, **Resistor Array**, and `resistor-array`. Variant names are also aliases. Aliases never replace stable IDs.

## Variants

| Stable variant ID | Display name | Model tiers | Release target | Compatible package profiles |
|---|---|---|---|---|
| `var-passives-resistor-array-isolated` | Isolated | F0, F1, F2, F3, F4 | Post-MVP catalog | `pkg-axial-2`, `pkg-smd-chip`, `pkg-radial-2` |
| `var-passives-resistor-array-bussed` | Bussed | F0, F1, F2, F3, F4 | Post-MVP catalog | `pkg-axial-2`, `pkg-smd-chip`, `pkg-radial-2` |

A variant is a simulation preset, not a manufacturer SKU. All production variants are tagged with an explicit release target. A family carrying `basic-component` requires a scalable physical representation before any variant may become `Released`.

## Original symbol and physical views

- Symbol ID: `sym-passives-resistor-array`. The artwork is original project work aligned with familiar IEC/ANSI conventions; IEC 60617 artwork must not be copied.
- Schematic, physical, and package views share one instance identity, connectivity graph, parameter set, model binding, live simulation state, selection state, and undo history.
- Physical artwork must show the body, leads or contacts, polarity and pin-one cues, value/part markings, and material/color regions appropriate to the selected variant and package.
- Geometry is scalable and uses zoom-dependent detail levels. Shape, labels, and orientation cues must remain understandable without color.
- Physical appearance is illustrative unless a package record supplies verified dimensions. It must never imply unvalidated dimensional, thermal, or electrical accuracy.
- Package selection is independent of electrical function. Changing package cannot change the model unless the user explicitly chooses a package-parasitic profile.

## Pin contract

| Pin or group | Name | Electrical type | Domains |
|---|---|---|---|
| `1` | P | passive | electrical, thermal |
| `2` | N | passive | electrical, thermal |

Pin IDs are stable inside a variant. A package pin map must be explicit, bijective for all required logical pins, and validated before export or release. Unmapped no-connect package pins are declared, never inferred.

## Parameter contract

| Parameter | Meaning | Internal unit | Default | Limits |
|---|---|---:|---:|---|
| `element_count` | Resistor element count | 1 | 4 | 2..1024 |
| `element_resistance` | Element resistance | ohm | 10000 | >0 |
| `tolerance` | Element tolerance | 1 | 0.05 | 0..1 |
| `matching_tolerance` | Within-array matching | 1 | 0.01 | 0..1 |
| `topology` | Array topology | 1 | isolated | isolated or bussed |

All numerical values use SI base units internally. Display prefixes and localized formatting are presentation concerns. Variant-specific parameters may refine this table but may not weaken its validation rules.

## Fidelity and supported analyses

Supported fidelity tiers: **F0, F1, F2, F3, F4**. Supported analysis capabilities: **DC, AC, transient, noise, Monte Carlo**.

- F0 validates connectivity and pin rules.
- F1 supplies ideal or equation-level behavior where applicable.
- F2 supplies behavioral, event, timing, or control behavior where applicable.
- F3 binds a compact, macro, HDL, S-parameter, or other validated external model.
- F4 adds tolerance, electrothermal, parasitic, aging, and failure behavior where applicable.
- F5 is restricted to declared research models and may not be represented as production-ready.

## Family-specific implementation reference

This section is the normative planning baseline for model tasks. A vendor or imported model may refine it only inside a declared validation envelope; it may not silently change pin order, units, polarity, state initialization, or unsupported behavior.

- **Governing relation or state rule:** Each declared resistor branch obeys v_k = R_k*i_k; shared-terminal and matching/correlation rules come only from the selected array topology.
- **F0:** Connectivity-only: validate declared pins, domains, width/direction, hierarchy, and package mapping; do not claim numerical behavior. Family baseline: Each declared resistor branch obeys v_k = R_k*i_k; shared-terminal and matching/correlation rules come only from the selected array topology.
- **F1:** Ideal/equation tier: implement exactly this family baseline and its declared parameter limits: Each declared resistor branch obeys v_k = R_k*i_k; shared-terminal and matching/correlation rules come only from the selected array topology.
- **F2:** Behavioral/timing tier: preserve the family baseline using deterministic integer-tick state/event rules and explicit initialization: Each declared resistor branch obeys v_k = R_k*i_k; shared-terminal and matching/correlation rules come only from the selected array topology.
- **F3:** Compact/macro/external tier: bind a pinned model or executable relation that preserves ordered pins and the validated envelope; the governing family relation is: Each declared resistor branch obeys v_k = R_k*i_k; shared-terminal and matching/correlation rules come only from the selected array topology.
- **F4:** Electrothermal/tolerance/failure tier: extend the lower-tier relation with declared sampling, power-to-heat state Cth*dT/dt = P-(T-Tamb)/Rth, derating, and deterministic failure transitions; base relation: Each declared resistor branch obeys v_k = R_k*i_k; shared-terminal and matching/correlation rules come only from the selected array topology.
- **Exact nominal vector:** pins `1:P`/passive, `2:N`/passive; parameters `element_count`=4 1 (2..1024); `element_resistance`=10000 ohm (>0); `tolerance`=0.05 1 (0..1); `matching_tolerance`=0.01 1 (0..1); `topology`=isolated 1 (isolated or bussed).
- **Boundary vector:** every declared inclusive/exclusive parameter limit, supported pin/domain/width edge, and supported-analysis boundary is exercised independently; combinations outside the declared envelope are invalid, not extrapolated.
- **Failure vector:** `open-circuit`, `short-circuit`, `parameter-drift`, `overstress-or-saturation`, plus non-finite parameters, invalid pin maps, unsupported analysis, and unavailable fidelity.
- **Golden evidence:** `GOLD-PAS-RESISTOR_ARRAY-NOMINAL`, `GOLD-PAS-RESISTOR_ARRAY-BOUNDARY`, `GOLD-PAS-RESISTOR_ARRAY-FAILURE`.

## Non-ideal, thermal, and failure behavior

- Non-ideal behavior is explicit: applicable leakage, series resistance, capacitance, inductance, finite bandwidth, delay, saturation, quantization, hysteresis, or mechanical limits are parameters rather than hidden effects.
- Thermal behavior declares reference temperature, coefficients, power-to-heat coupling, operating limits, and whether self-heating is supported. Unsupported thermal behavior is reported, not silently approximated.
- Minimum fault modes are open circuit, short circuit, parameter drift, and overstress/saturation. Inapplicable modes are marked `not-applicable` with rationale.
- Failure transitions are deterministic for identical project, configuration, seed, and engine versions.

## Import and export mappings

SPICE `.model`/`.subckt`, Verilog-A/AMS 2023, and CSV/PWL mappings are applicable where the target format can preserve this family's pin and parameter semantics.

Every imported model records format/version, content digest, source URL or artifact identity, license/SPDX expression, original pin order, normalized pin map, supported analyses, known limits, and review status.

## Provenance and licensing

The taxonomy entry is project-authored from the platform scope (Source PDF, pp. 8-13). Symbol artwork is original and intended for Apache-2.0 distribution. Imported model licenses remain model-specific and require an SPDX identifier plus redistribution review. IEC references guide terminology only; proprietary symbol artwork is not copied.

## Golden validation

- `GOLD-PAS-RESISTOR_ARRAY-NOMINAL`: nominal positive-path behavior.
- `GOLD-PAS-RESISTOR_ARRAY-BOUNDARY`: declared parameter and operating boundaries.
- `GOLD-PAS-RESISTOR_ARRAY-FAILURE`: diagnostic and fault behavior.

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

