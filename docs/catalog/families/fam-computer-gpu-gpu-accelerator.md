# GPU and accelerator

- **Family ID:** `fam-computer-gpu-gpu-accelerator`
- **Category:** CPU, computer and GPU blocks
- **Lifecycle:** Planned
- **Basic component tag:** Not tagged basic
- **Release target:** Post-MVP catalog
- **Source:** Source PDF, pp. 27-35

## Purpose and scope

GPU and accelerator is the canonical family for the variants listed below. The family boundary is behavioral: package, color, marking, tolerance, and vendor model choices do not create a new electrical family. Vendor-specific parts bind to a variant and an importable model.

## Aliases

Search aliases are **GPU and accelerator**, **Gpu Accelerator**, and `gpu-accelerator`. Variant names are also aliases. Aliases never replace stable IDs.

## Variants

| Stable variant ID | Display name | Model tiers | Release target | Compatible package profiles |
|---|---|---|---|---|
| `var-computer-gpu-gpu-accelerator-simt` | Simt | F0, F2 | Post-MVP catalog | `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric` |
| `var-computer-gpu-gpu-accelerator-raster-pipeline` | Raster Pipeline | F0, F2 | Post-MVP catalog | `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric` |
| `var-computer-gpu-gpu-accelerator-compute` | Compute | F0, F2 | Post-MVP catalog | `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric` |
| `var-computer-gpu-gpu-accelerator-vector-accelerator` | Vector Accelerator | F0, F2 | Post-MVP catalog | `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric` |

A variant is a simulation preset, not a manufacturer SKU. All production variants are tagged with an explicit release target. A family carrying `basic-component` requires a scalable physical representation before any variant may become `Released`.

## Original symbol and physical views

- Symbol ID: `sym-computer-gpu-gpu-accelerator`. The artwork is original project work aligned with familiar IEC/ANSI conventions; IEC 60617 artwork must not be copied.
- Schematic, physical, and package views share one instance identity, connectivity graph, parameter set, model binding, live simulation state, selection state, and undo history.
- Physical artwork must show the body, leads or contacts, polarity and pin-one cues, value/part markings, and material/color regions appropriate to the selected variant and package.
- Geometry is scalable and uses zoom-dependent detail levels. Shape, labels, and orientation cues must remain understandable without color.
- Physical appearance is illustrative unless a package record supplies verified dimensions. It must never imply unvalidated dimensional, thermal, or electrical accuracy.
- Package selection is independent of electrical function. Changing package cannot change the model unless the user explicitly chooses a package-parasitic profile.

## Pin contract

| Pin or group | Name | Electrical type | Domains |
|---|---|---|---|
| `ADDR` | ADDRESS | bidirectional | digital, architecture, power |
| `DATA` | DATA | bidirectional | digital, architecture, power |
| `CTRL` | CONTROL | bidirectional | digital, architecture, power |
| `CLK` | CLOCK | input | digital, architecture, power |
| `PWR` | POWER | power | digital, architecture, power |

Pin IDs are stable inside a variant. A package pin map must be explicit, bijective for all required logical pins, and validated before export or release. Unmapped no-connect package pins are declared, never inferred.

## Parameter contract

| Parameter | Meaning | Internal unit | Default | Limits |
|---|---|---:|---:|---|
| `execution_profile` | GPU/accelerator profile | 1 | simt | raster, compute, simd, or simt |
| `lane_count` | SIMD lane count | 1 | 32 | 1..65536 |
| `warp_size` | SIMT warp size | 1 | 32 | 1..1024 |
| `clock_frequency` | Modeled clock | Hz | 1e9 | >0 |
| `memory_size` | Device-memory size | byte | 1073741824 | >0 |
| `engine_digest` | Pinned engine digest | 1 | unset | valid reviewed digest before Ready |

All numerical values use SI base units internally. Display prefixes and localized formatting are presentation concerns. Variant-specific parameters may refine this table but may not weaken its validation rules.

## Fidelity and supported analyses

Supported fidelity tiers: **F0, F2**. Supported analysis capabilities: **functional, cycle, ISA, architecture**.

- F0 validates connectivity and pin rules.
- F1 supplies ideal or equation-level behavior where applicable.
- F2 supplies behavioral, event, timing, or control behavior where applicable.
- F3 binds a compact, macro, HDL, S-parameter, or other validated external model.
- F4 adds tolerance, electrothermal, parasitic, aging, and failure behavior where applicable.
- F5 is restricted to declared research models and may not be represented as production-ready.

## Family-specific implementation reference

This section is the normative planning baseline for model tasks. A vendor or imported model may refine it only inside a declared validation envelope; it may not silently change pin order, units, polarity, state initialization, or unsupported behavior.

- **Governing relation or state rule:** The selected raster/compute/SIMD/SIMT abstraction advances command, lane/warp, memory, synchronization, and result state under a versioned execution profile.
- **F0:** Connectivity-only: validate declared pins, domains, width/direction, hierarchy, and package mapping; do not claim numerical behavior. Family baseline: The selected raster/compute/SIMD/SIMT abstraction advances command, lane/warp, memory, synchronization, and result state under a versioned execution profile.
- **F2:** Behavioral/timing tier: preserve the family baseline using deterministic integer-tick state/event rules and explicit initialization: The selected raster/compute/SIMD/SIMT abstraction advances command, lane/warp, memory, synchronization, and result state under a versioned execution profile.
- **Exact nominal vector:** pins `ADDR:ADDRESS`/bidirectional, `DATA:DATA`/bidirectional, `CTRL:CONTROL`/bidirectional, `CLK:CLOCK`/input, `PWR:POWER`/power; parameters `execution_profile`=simt 1 (raster, compute, simd, or simt); `lane_count`=32 1 (1..65536); `warp_size`=32 1 (1..1024); `clock_frequency`=1e9 Hz (>0); `memory_size`=1073741824 byte (>0); `engine_digest`=unset 1 (valid reviewed digest before Ready).
- **Boundary vector:** every declared inclusive/exclusive parameter limit, supported pin/domain/width edge, and supported-analysis boundary is exercised independently; combinations outside the declared envelope are invalid, not extrapolated.
- **Failure vector:** `open-circuit`, `short-circuit`, `parameter-drift`, `overstress-or-saturation`, plus non-finite parameters, invalid pin maps, unsupported analysis, and unavailable fidelity.
- **Golden evidence:** `GOLD-CPU-GPU_ACCELERATOR-NOMINAL`, `GOLD-CPU-GPU_ACCELERATOR-BOUNDARY`, `GOLD-CPU-GPU_ACCELERATOR-FAILURE`.

## Non-ideal, thermal, and failure behavior

- Non-ideal behavior is explicit: applicable leakage, series resistance, capacitance, inductance, finite bandwidth, delay, saturation, quantization, hysteresis, or mechanical limits are parameters rather than hidden effects.
- Thermal behavior declares reference temperature, coefficients, power-to-heat coupling, operating limits, and whether self-heating is supported. Unsupported thermal behavior is reported, not silently approximated.
- Minimum fault modes are open circuit, short circuit, parameter drift, and overstress/saturation. Inapplicable modes are marked `not-applicable` with rationale.
- Failure transitions are deterministic for identical project, configuration, seed, and engine versions.

## Import and export mappings

SPICE `.model`/`.subckt`, Verilog-A/AMS 2023, and CSV/PWL mappings are applicable where the target format can preserve this family's pin and parameter semantics.

Every imported model records format/version, content digest, source URL or artifact identity, license/SPDX expression, original pin order, normalized pin map, supported analyses, known limits, and review status.

## Provenance and licensing

The taxonomy entry is project-authored from the platform scope (Source PDF, pp. 27-35). Symbol artwork is original and intended for Apache-2.0 distribution. Imported model licenses remain model-specific and require an SPDX identifier plus redistribution review. IEC references guide terminology only; proprietary symbol artwork is not copied.

## Golden validation

- `GOLD-CPU-GPU_ACCELERATOR-NOMINAL`: nominal positive-path behavior.
- `GOLD-CPU-GPU_ACCELERATOR-BOUNDARY`: declared parameter and operating boundaries.
- `GOLD-CPU-GPU_ACCELERATOR-FAILURE`: diagnostic and fault behavior.

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

