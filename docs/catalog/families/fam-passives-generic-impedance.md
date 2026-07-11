# Generic impedance

- **Family ID:** `fam-passives-generic-impedance`
- **Category:** Passives, magnetics and transmission
- **Lifecycle:** Planned
- **Basic component tag:** `basic-component`
- **Release target:** Realistic Electronics MVP
- **Source:** Source PDF, pp. 8-13

## Purpose and scope

Generic impedance is the canonical family for the variants listed below. The family boundary is behavioral: package, color, marking, tolerance, and vendor model choices do not create a new electrical family. Vendor-specific parts bind to a variant and an importable model.

## Aliases

Search aliases are **Generic impedance**, **Generic Impedance**, and `generic-impedance`. Variant names are also aliases. Aliases never replace stable IDs.

## Variants

| Stable variant ID | Display name | Model tiers | Release target | Compatible package profiles |
|---|---|---|---|---|
| `var-passives-generic-impedance-series-rlc` | Series Rlc | F0, F1, F2, F3, F4 | Realistic Electronics MVP | `pkg-axial-2`, `pkg-smd-chip`, `pkg-radial-2` |
| `var-passives-generic-impedance-parallel-rlc` | Parallel Rlc | F0, F1, F2, F3, F4 | Realistic Electronics MVP | `pkg-axial-2`, `pkg-smd-chip`, `pkg-radial-2` |
| `var-passives-generic-impedance-laplace` | Laplace | F0, F1, F2, F3, F4 | Realistic Electronics MVP | `pkg-axial-2`, `pkg-smd-chip`, `pkg-radial-2` |
| `var-passives-generic-impedance-tabulated` | Tabulated | F0, F1, F2, F3, F4 | Realistic Electronics MVP | `pkg-axial-2`, `pkg-smd-chip`, `pkg-radial-2` |

A variant is a simulation preset, not a manufacturer SKU. All production variants are tagged with an explicit release target. A family carrying `basic-component` requires a scalable physical representation before any variant may become `Released`.

## Original symbol and physical views

- Symbol ID: `sym-passives-generic-impedance`. The artwork is original project work aligned with familiar IEC/ANSI conventions; IEC 60617 artwork must not be copied.
- Schematic, physical, and package views share one instance identity, connectivity graph, parameter set, model binding, live simulation state, selection state, and undo history.
- Physical artwork must show the body, leads or contacts, polarity and pin-one cues, value/part markings, and material/color regions appropriate to the selected variant and package.
- Geometry is scalable and uses zoom-dependent detail levels. Shape, labels, and orientation cues must remain understandable without color.
- Physical appearance is illustrative unless a package record supplies verified dimensions. It must never imply unvalidated dimensional, thermal, or electrical accuracy.
- Package selection is independent of electrical function. Changing package cannot change the model unless the user explicitly chooses a package-parasitic profile.

## Pin contract

| Pin or group | Electrical type | Meaning | Domains |
|---|---|---|---|
| `P` | passive | Positive or first terminal | electrical, thermal |
| `N` | passive | Negative or second terminal | electrical, thermal |

Pin IDs are stable inside a variant. A package pin map must be explicit, bijective for all required logical pins, and validated before export or release. Unmapped no-connect package pins are declared, never inferred.

## Parameter contract

| Parameter | Internal unit | Default | Limits |
|---|---:|---:|---|
| `nominal` | family-specific SI unit | 1 | finite and positive unless stated |
| `tolerance` | 1 | 0.05 | 0..1 |
| `temperature_coefficient` | 1/K | 0 | variant-defined |

All numerical values use SI base units internally. Display prefixes and localized formatting are presentation concerns. Variant-specific parameters may refine this table but may not weaken its validation rules.

## Fidelity and supported analyses

Supported fidelity tiers: **F0, F1, F2, F3, F4**. Supported analysis capabilities: **DC, AC, transient, noise, Monte Carlo**.

- F0 validates connectivity and pin rules.
- F1 supplies ideal or equation-level behavior where applicable.
- F2 supplies behavioral, event, timing, or control behavior where applicable.
- F3 binds a compact, macro, HDL, S-parameter, or other validated external model.
- F4 adds tolerance, electrothermal, parasitic, aging, and failure behavior where applicable.
- F5 is restricted to declared research models and may not be represented as production-ready.

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

- `GOLD-PAS-GENERIC_IMPEDANCE-NOMINAL`: nominal positive-path behavior.
- `GOLD-PAS-GENERIC_IMPEDANCE-BOUNDARY`: declared parameter and operating boundaries.
- `GOLD-PAS-GENERIC_IMPEDANCE-FAILURE`: diagnostic and fault behavior.

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

