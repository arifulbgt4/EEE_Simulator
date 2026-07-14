# CMP-MCU-FPGA-MICROCONTROLLER-AVR-PROFILE-F0-CAT - Specify Avr Profile catalog preset

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-mcu-fpga-microcontroller` - Microcontroller |
| Variant | `var-mcu-fpga-microcontroller-avr-profile` - Avr Profile |
| Fidelity | F0 |
| Concern | CAT |
| Release | R7 |
| Requirements | REQ-020, REQ-021, REQ-024, REQ-025, REQ-026, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Create the complete, immutable catalog definition for **Avr Profile** without implementing a different fidelity or sibling preset.

## Exact prerequisites

- `PLAT-GOV-001`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-mcu-fpga-microcontroller.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-mcu-fpga-microcontroller` (Microcontroller); task scope: variant `var-mcu-fpga-microcontroller-avr-profile` (Avr Profile); fidelity `F0`; concern `CAT`.
- Exact pins: `IO:GPIO` (bidirectional; digital/firmware/power), `RST:RESET` (input; digital/firmware/power), `CLK:CLOCK` (input; digital/firmware/power), `VDD:VDD` (power; digital/firmware/power), `VSS:VSS` (power; digital/firmware/power).
- Exact parameters/defaults/limits: `word_width`=8 bit with limits 1..64; `clock_frequency`=1e6 Hz with limits >0; `gpio_count`=16 1 with limits 0..4096; `flash_size`=32768 byte with limits >=0; `ram_size`=2048 byte with limits >=0; `profile_id`=generic-8-bit 1 with limits registered profile.
- Supported analyses: `digital-event`, `firmware`, `rtl`, `timing`.
- Valid package mappings: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Golden references: `GOLD-MCU-MICROCONTROLLER-NOMINAL`, `GOLD-MCU-MICROCONTROLLER-BOUNDARY`, `GOLD-MCU-MICROCONTROLLER-FAILURE`.
- Import mappings applicable to this family: `Verilog/SystemVerilog`, `VCD/FST`, `HEX/ELF`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 25-30; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.
- Selected variant tiers: `F0`, `F2`, `F3`; release target: Post-MVP catalog; package references: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Microcontroller family-specific implementation reference](../../catalog/families/fam-mcu-fpga-microcontroller.md#family-specific-implementation-reference), registry row `fam-mcu-fpga-microcontroller`, and variant `var-mcu-fpga-microcontroller-avr-profile` (Avr Profile).
- Exact pin vector: `IO:GPIO` (bidirectional; digital/firmware/power), `RST:RESET` (input; digital/firmware/power), `CLK:CLOCK` (input; digital/firmware/power), `VDD:VDD` (power; digital/firmware/power), `VSS:VSS` (power; digital/firmware/power).
- Exact parameter vector: `word_width`=8 bit with limits 1..64; `clock_frequency`=1e6 Hz with limits >0; `gpio_count`=16 1 with limits 0..4096; `flash_size`=32768 byte with limits >=0; `ram_size`=2048 byte with limits >=0; `profile_id`=generic-8-bit 1 with limits registered profile.
- Declared analyses: `digital-event`, `firmware`, `rtl`, `timing`; declared package bindings: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- This catalog concern has no numerical equation. It freezes the selected variant's inherited/overridden fields against the governing family rule: The selected MCU profile advances architectural/firmware state on deterministic ticks and exposes only the declared GPIO, interrupt, peripheral, memory, clock, and reset semantics.
- Exact reference vectors: `GOLD-MCU-MICROCONTROLLER-NOMINAL`, `GOLD-MCU-MICROCONTROLLER-BOUNDARY`, `GOLD-MCU-MICROCONTROLLER-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-mcu-fpga-microcontroller-avr-profile-f0-cat.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-mcu-fpga-microcontroller.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One normalized `ComponentVariant` record for variant `var-mcu-fpga-microcontroller-avr-profile` (Avr Profile), retaining stable ID, aliases, inherited pins/parameters, declared tier list, package candidates, release target, provenance, and limitations.
- A field-by-field registry/family consistency result and structured rejection evidence for duplicate ID, invalid override, missing package, or unsupported tier.
- Scope is limited to `CMP-MCU-FPGA-MICROCONTROLLER-AVR-PROFILE-F0-CAT`: variant `var-mcu-fpga-microcontroller-avr-profile` (Avr Profile), fidelity `F0`, concern `CAT`, and requirements REQ-020, REQ-021, REQ-024, REQ-025, REQ-026, REQ-022, REQ-023, REQ-037, REQ-038.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family and one variant, fidelity **F0**, and concern **CAT** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `IO:GPIO` (bidirectional; digital/firmware/power), `RST:RESET` (input; digital/firmware/power), `CLK:CLOCK` (input; digital/firmware/power), `VDD:VDD` (power; digital/firmware/power), `VSS:VSS` (power; digital/firmware/power); reject any package map outside `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `word_width`=8 bit with limits 1..64; `clock_frequency`=1e6 Hz with limits >0; `gpio_count`=16 1 with limits 0..4096; `flash_size`=32768 byte with limits >=0; `ram_size`=2048 byte with limits >=0; `profile_id`=generic-8-bit 1 with limits registered profile.
- Support only `digital-event`, `firmware`, `rtl`, `timing`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Duplicate stable IDs, incompatible inherited overrides, undeclared package/tier references, or absent provenance block publication of the variant record.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-MCU-FPGA-MICROCONTROLLER-AVR-PROFILE-F0-CAT-NOMINAL`
- `TEST-CMP-MCU-FPGA-MICROCONTROLLER-AVR-PROFILE-F0-CAT-BOUNDARY`
- `TEST-CMP-MCU-FPGA-MICROCONTROLLER-AVR-PROFILE-F0-CAT-FAILURE`

## Acceptance

1. The exact output for `CMP-MCU-FPGA-MICROCONTROLLER-AVR-PROFILE-F0-CAT` exists and is limited to variant `var-mcu-fpga-microcontroller-avr-profile` (Avr Profile), `F0`, and `CAT`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-mcu-fpga-microcontroller` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-020, REQ-021, REQ-024, REQ-025, REQ-026, REQ-022, REQ-023, REQ-037, REQ-038, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
