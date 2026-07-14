# CMP-DIGITAL-LOGIC-BUS-TRANSCEIVER-SHARED-F3-IMPORT - Define import mapping for Bus transceiver

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-digital-logic-bus-transceiver` - Bus transceiver |
| Variant | `shared` |
| Fidelity | F3 |
| Concern | IMPORT |
| Release | R7 |
| Requirements | REQ-018, REQ-021, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Implement and validate only the declared external-model mappings for **Bus transceiver**.

## Exact prerequisites

- `CMP-DIGITAL-LOGIC-BUS-TRANSCEIVER-SHARED-F3-MODEL`
- `PLAT-IMP-003`
- `PLAT-IMP-008`
- `PLAT-IMP-009`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-digital-logic-bus-transceiver.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-digital-logic-bus-transceiver` (Bus transceiver); task scope: shared family scope across `var-digital-logic-bus-transceiver-bidirectional`, `var-digital-logic-bus-transceiver-open-drain`; fidelity `F3`; concern `IMPORT`.
- Exact pins: `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power).
- Exact parameters/defaults/limits: `width`=8 bit with limits 1..4096; `direction`=A-to-B 1 with limits A-to-B or B-to-A; `enable_polarity`=active-low 1 with limits active-high or active-low; `propagation_delay`=0 s with limits >=0; `logic_family`=cmos 1 with limits registered profile.
- Supported analyses: `digital-event`, `timing`, `truth-table`.
- Valid package mappings: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Golden references: `GOLD-DIG-BUS_TRANSCEIVER-NOMINAL`, `GOLD-DIG-BUS_TRANSCEIVER-BOUNDARY`, `GOLD-DIG-BUS_TRANSCEIVER-FAILURE`.
- Import mappings applicable to this family: `Verilog/SystemVerilog`, `VCD/FST`, `HEX/ELF`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 21-26; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Bus transceiver family-specific implementation reference](../../catalog/families/fam-digital-logic-bus-transceiver.md#family-specific-implementation-reference), registry row `fam-digital-logic-bus-transceiver`, and shared family scope across `var-digital-logic-bus-transceiver-bidirectional`, `var-digital-logic-bus-transceiver-open-drain`.
- Exact pin vector: `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power).
- Exact parameter vector: `width`=8 bit with limits 1..4096; `direction`=A-to-B 1 with limits A-to-B or B-to-A; `enable_polarity`=active-low 1 with limits active-high or active-low; `propagation_delay`=0 s with limits >=0; `logic_family`=cmos 1 with limits registered profile.
- Declared analyses: `digital-event`, `timing`, `truth-table`; declared package bindings: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Exact import targets are `Verilog/SystemVerilog`, `VCD/FST`, `HEX/ELF`. Imported equations remain authoritative only inside their declared analysis/envelope and after ordered-pin, unit, provenance, license, and digest validation.
- Exact reference vectors: `GOLD-DIG-BUS_TRANSCEIVER-NOMINAL`, `GOLD-DIG-BUS_TRANSCEIVER-BOUNDARY`, `GOLD-DIG-BUS_TRANSCEIVER-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-digital-logic-bus-transceiver-shared-f3-import.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-digital-logic-bus-transceiver.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One ordered-pin/parameter/unit mapping and `ModelProvenance` record for each applicable target `Verilog/SystemVerilog`, `VCD/FST`, `HEX/ELF`.
- Round-trip or explicit-loss evidence plus structured rejection for unsupported syntax, ambiguous pins, unknown license, digest mismatch, unsafe include, and unsupported analysis.
- Scope is limited to `CMP-DIGITAL-LOGIC-BUS-TRANSCEIVER-SHARED-F3-IMPORT`: shared family scope across `var-digital-logic-bus-transceiver-bidirectional`, `var-digital-logic-bus-transceiver-open-drain`, fidelity `F3`, concern `IMPORT`, and requirements REQ-018, REQ-021, REQ-022, REQ-023, REQ-037, REQ-038.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F3**, and concern **IMPORT** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power); reject any package map outside `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `width`=8 bit with limits 1..4096; `direction`=A-to-B 1 with limits A-to-B or B-to-A; `enable_polarity`=active-low 1 with limits active-high or active-low; `propagation_delay`=0 s with limits >=0; `logic_family`=cmos 1 with limits registered profile.
- Support only `digital-event`, `timing`, `truth-table`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Path traversal, recursive include, resource limit, unsupported construct, ambiguous ground/reference, unknown rights, or executable/network behavior is quarantined or rejected.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-DIGITAL-LOGIC-BUS-TRANSCEIVER-SHARED-F3-IMPORT-NOMINAL`
- `TEST-CMP-DIGITAL-LOGIC-BUS-TRANSCEIVER-SHARED-F3-IMPORT-BOUNDARY`
- `TEST-CMP-DIGITAL-LOGIC-BUS-TRANSCEIVER-SHARED-F3-IMPORT-FAILURE`

## Acceptance

1. The exact output for `CMP-DIGITAL-LOGIC-BUS-TRANSCEIVER-SHARED-F3-IMPORT` exists and is limited to shared family scope across `var-digital-logic-bus-transceiver-bidirectional`, `var-digital-logic-bus-transceiver-open-drain`, `F3`, and `IMPORT`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-digital-logic-bus-transceiver` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-018, REQ-021, REQ-022, REQ-023, REQ-037, REQ-038, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
