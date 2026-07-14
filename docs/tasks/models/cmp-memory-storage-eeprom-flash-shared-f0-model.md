# CMP-MEMORY-STORAGE-EEPROM-FLASH-SHARED-F0-MODEL - Implement EEPROM and Flash F0 model

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-memory-storage-eeprom-flash` - EEPROM and Flash |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | MODEL |
| Release | R8 |
| Requirements | REQ-018, REQ-021, REQ-025, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Implement one model tier, **F0**, for **EEPROM and Flash** using the family equations/behavior and no higher-fidelity claims.

## Exact prerequisites

- `CMP-MEMORY-STORAGE-EEPROM-FLASH-EEPROM-F0-CAT`
- `CMP-MEMORY-STORAGE-EEPROM-FLASH-NOR-FLASH-F0-CAT`
- `CMP-MEMORY-STORAGE-EEPROM-FLASH-NAND-FLASH-F0-CAT`
- `PLAT-NET-008`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-memory-storage-eeprom-flash.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-memory-storage-eeprom-flash` (EEPROM and Flash); task scope: shared family scope across `var-memory-storage-eeprom-flash-eeprom`, `var-memory-storage-eeprom-flash-nor-flash`, `var-memory-storage-eeprom-flash-nand-flash`; fidelity `F0`; concern `MODEL`.
- Exact pins: `A:ADDRESS` (input; digital/storage/power), `D:DATA` (bidirectional; digital/storage/power), `C:CONTROL` (input; digital/storage/power), `VDD:VDD` (power; digital/storage/power), `VSS:VSS` (power; digital/storage/power).
- Exact parameters/defaults/limits: `address_width`=16 bit with limits 1..64; `data_width`=8 bit with limits 1..4096; `erase_block_size`=4096 byte with limits >0; `program_time`=1e-3 s with limits >=0; `erase_time`=0.1 s with limits >=0; `initial_contents`=all-ones 1 with limits size-matched image.
- Supported analyses: `digital-event`, `timing`, `firmware`.
- Valid package mappings: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Golden references: `GOLD-MEM-EEPROM_FLASH-NOMINAL`, `GOLD-MEM-EEPROM_FLASH-BOUNDARY`, `GOLD-MEM-EEPROM_FLASH-FAILURE`.
- Import mappings applicable to this family: `Verilog/SystemVerilog`, `VCD/FST`, `HEX/ELF`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 24-28; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [EEPROM and Flash family-specific implementation reference](../../catalog/families/fam-memory-storage-eeprom-flash.md#family-specific-implementation-reference), registry row `fam-memory-storage-eeprom-flash`, and shared family scope across `var-memory-storage-eeprom-flash-eeprom`, `var-memory-storage-eeprom-flash-nor-flash`, `var-memory-storage-eeprom-flash-nand-flash`.
- Exact pin vector: `A:ADDRESS` (input; digital/storage/power), `D:DATA` (bidirectional; digital/storage/power), `C:CONTROL` (input; digital/storage/power), `VDD:VDD` (power; digital/storage/power), `VSS:VSS` (power; digital/storage/power).
- Exact parameter vector: `address_width`=16 bit with limits 1..64; `data_width`=8 bit with limits 1..4096; `erase_block_size`=4096 byte with limits >0; `program_time`=1e-3 s with limits >=0; `erase_time`=0.1 s with limits >=0; `initial_contents`=all-ones 1 with limits size-matched image.
- Declared analyses: `digital-event`, `timing`, `firmware`; declared package bindings: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Exact F0 execution rule: Connectivity-only: validate declared pins, domains, width/direction, hierarchy, and package mapping; do not claim numerical behavior. Family baseline: A persistent word array follows declared read/program/erase commands, timing, granularity, initialization, endurance metadata, and invalid-command behavior.
- Exact reference vectors: `GOLD-MEM-EEPROM_FLASH-NOMINAL`, `GOLD-MEM-EEPROM_FLASH-BOUNDARY`, `GOLD-MEM-EEPROM_FLASH-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-memory-storage-eeprom-flash-shared-f0-model.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-memory-storage-eeprom-flash.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One `ModelBinding` for `fam-memory-storage-eeprom-flash` at `F0` implementing the exact tier rule above, its initialization/state/stamp/event behavior, power reporting, and structured diagnostics.
- One `AnalysisCapability` result for each of `digital-event`, `timing`, `firmware`, with every unlisted analysis rejected rather than approximated.
- Scope is limited to `CMP-MEMORY-STORAGE-EEPROM-FLASH-SHARED-F0-MODEL`: shared family scope across `var-memory-storage-eeprom-flash-eeprom`, `var-memory-storage-eeprom-flash-nor-flash`, `var-memory-storage-eeprom-flash-nand-flash`, fidelity `F0`, concern `MODEL`, and requirements REQ-018, REQ-021, REQ-025, REQ-022, REQ-023, REQ-037, REQ-038.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F0**, and concern **MODEL** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `A:ADDRESS` (input; digital/storage/power), `D:DATA` (bidirectional; digital/storage/power), `C:CONTROL` (input; digital/storage/power), `VDD:VDD` (power; digital/storage/power), `VSS:VSS` (power; digital/storage/power); reject any package map outside `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `address_width`=16 bit with limits 1..64; `data_width`=8 bit with limits 1..4096; `erase_block_size`=4096 byte with limits >0; `program_time`=1e-3 s with limits >=0; `erase_time`=0.1 s with limits >=0; `initial_contents`=all-ones 1 with limits size-matched image.
- Support only `digital-event`, `timing`, `firmware`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Initialization, limiting, discontinuity, convergence/event ordering, cancellation, overflow/NaN, and out-of-envelope behavior must follow the `F0` rule without silent fallback.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-MEMORY-STORAGE-EEPROM-FLASH-SHARED-F0-MODEL-NOMINAL`
- `TEST-CMP-MEMORY-STORAGE-EEPROM-FLASH-SHARED-F0-MODEL-BOUNDARY`
- `TEST-CMP-MEMORY-STORAGE-EEPROM-FLASH-SHARED-F0-MODEL-FAILURE`

## Acceptance

1. The exact output for `CMP-MEMORY-STORAGE-EEPROM-FLASH-SHARED-F0-MODEL` exists and is limited to shared family scope across `var-memory-storage-eeprom-flash-eeprom`, `var-memory-storage-eeprom-flash-nor-flash`, `var-memory-storage-eeprom-flash-nand-flash`, `F0`, and `MODEL`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-memory-storage-eeprom-flash` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-018, REQ-021, REQ-025, REQ-022, REQ-023, REQ-037, REQ-038, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
