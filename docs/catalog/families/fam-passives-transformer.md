# Transformer

- **Family ID:** `fam-passives-transformer`
- **Category:** Passives, magnetics and transmission
- **Lifecycle:** Planned
- **Basic component tag:** `basic-component`
- **Release target:** Mixed variant targets: Realistic Electronics MVP and Post-MVP catalog (see variant table)
- **Source:** Source PDF, pp. 8-13

## Purpose and scope

Transformer is the canonical family for the variants listed below. The family boundary is behavioral: package, color, marking, tolerance, and vendor model choices do not create a new electrical family. Vendor-specific parts bind to a variant and an importable model.

## Aliases

Search aliases are **Transformer**, **Transformer**, and `transformer`. Variant names are also aliases. Aliases never replace stable IDs.

## Variants

| Stable variant ID | Display name | Model tiers | Release target | Compatible package profiles |
|---|---|---|---|---|
| `var-passives-transformer-ideal` | Ideal | F0, F1, F2, F3, F4 | Realistic Electronics MVP | `pkg-radial-2`, `pkg-custom-parametric` |
| `var-passives-transformer-center-tapped` | Center Tapped | F0, F1, F2, F3, F4 | Post-MVP catalog | `pkg-radial-2`, `pkg-custom-parametric` |
| `var-passives-transformer-pulse` | Pulse | F0, F1, F2, F3, F4 | Post-MVP catalog | `pkg-radial-2`, `pkg-custom-parametric` |
| `var-passives-transformer-autotransformer` | Autotransformer | F0, F1, F2, F3, F4 | Post-MVP catalog | `pkg-radial-2`, `pkg-custom-parametric` |

A variant is a simulation preset, not a manufacturer SKU. All production variants are tagged with an explicit release target. A family carrying `basic-component` requires a scalable physical representation before any variant may become `Released`.

## Original symbol and physical views

- Symbol ID: `sym-passives-transformer`. The artwork is original project work aligned with familiar IEC/ANSI conventions; IEC 60617 artwork must not be copied.
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
| `primary_inductance` | Primary magnetizing inductance | H | 1 | >0 |
| `turns_ratio` | Primary-to-secondary turns ratio | 1 | 1 | >0 |
| `coupling_coefficient` | Winding coupling | 1 | 0.999 | -1..1 |
| `primary_resistance` | Primary winding resistance | ohm | 0 | >=0 |
| `secondary_resistance` | Secondary winding resistance | ohm | 0 | >=0 |
| `core_saturation_flux` | Core saturation flux linkage | Wb | 1 | >0 |

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

- **Governing relation or state rule:** The ideal ratio enforces v1/v2 = N1/N2 and i1/i2 = -N2/N1; higher fidelity adds magnetizing, leakage, winding-loss, and saturation branches.
- **F0:** Connectivity-only: validate declared pins, domains, width/direction, hierarchy, and package mapping; do not claim numerical behavior. Family baseline: The ideal ratio enforces v1/v2 = N1/N2 and i1/i2 = -N2/N1; higher fidelity adds magnetizing, leakage, winding-loss, and saturation branches.
- **F1:** Ideal/equation tier: implement exactly this family baseline and its declared parameter limits: The ideal ratio enforces v1/v2 = N1/N2 and i1/i2 = -N2/N1; higher fidelity adds magnetizing, leakage, winding-loss, and saturation branches.
- **F2:** Behavioral/timing tier: preserve the family baseline using deterministic integer-tick state/event rules and explicit initialization: The ideal ratio enforces v1/v2 = N1/N2 and i1/i2 = -N2/N1; higher fidelity adds magnetizing, leakage, winding-loss, and saturation branches.
- **F3:** Compact/macro/external tier: bind a pinned model or executable relation that preserves ordered pins and the validated envelope; the governing family relation is: The ideal ratio enforces v1/v2 = N1/N2 and i1/i2 = -N2/N1; higher fidelity adds magnetizing, leakage, winding-loss, and saturation branches.
- **F4:** Electrothermal/tolerance/failure tier: extend the lower-tier relation with declared sampling, power-to-heat state Cth*dT/dt = P-(T-Tamb)/Rth, derating, and deterministic failure transitions; base relation: The ideal ratio enforces v1/v2 = N1/N2 and i1/i2 = -N2/N1; higher fidelity adds magnetizing, leakage, winding-loss, and saturation branches.
- **Exact nominal vector:** pins `1:P`/passive, `2:N`/passive; parameters `primary_inductance`=1 H (>0); `turns_ratio`=1 1 (>0); `coupling_coefficient`=0.999 1 (-1..1); `primary_resistance`=0 ohm (>=0); `secondary_resistance`=0 ohm (>=0); `core_saturation_flux`=1 Wb (>0).
- **Boundary vector:** every declared inclusive/exclusive parameter limit, supported pin/domain/width edge, and supported-analysis boundary is exercised independently; combinations outside the declared envelope are invalid, not extrapolated.
- **Failure vector:** `open-circuit`, `short-circuit`, `parameter-drift`, `overstress-or-saturation`, plus non-finite parameters, invalid pin maps, unsupported analysis, and unavailable fidelity.
- **Golden evidence:** `GOLD-PAS-TRANSFORMER-NOMINAL`, `GOLD-PAS-TRANSFORMER-BOUNDARY`, `GOLD-PAS-TRANSFORMER-FAILURE`.

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

- `GOLD-PAS-TRANSFORMER-NOMINAL`: nominal positive-path behavior.
- `GOLD-PAS-TRANSFORMER-BOUNDARY`: declared parameter and operating boundaries.
- `GOLD-PAS-TRANSFORMER-FAILURE`: diagnostic and fault behavior.

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

