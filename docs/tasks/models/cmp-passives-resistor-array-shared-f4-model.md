# CMP-PASSIVES-RESISTOR-ARRAY-SHARED-F4-MODEL - Implement Resistor array F4 model

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-passives-resistor-array` - Resistor array |
| Variant | `shared` |
| Fidelity | F4 |
| Concern | MODEL |
| Release | R2 |
| Requirements | REQ-009, REQ-010, REQ-011, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Implement one model tier, **F4**, for **Resistor array** using the family equations/behavior and no higher-fidelity claims.

## Exact prerequisites

- `CMP-PASSIVES-RESISTOR-ARRAY-ISOLATED-F0-CAT`
- `CMP-PASSIVES-RESISTOR-ARRAY-BUSSED-F0-CAT`
- `CMP-PASSIVES-RESISTOR-ARRAY-SHARED-F3-MODEL`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-passives-resistor-array.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-passives-resistor-array` (Resistor array); task scope: shared family scope across `var-passives-resistor-array-isolated`, `var-passives-resistor-array-bussed`; fidelity `F4`; concern `MODEL`.
- Exact pins: `1:P` (passive; electrical/thermal), `2:N` (passive; electrical/thermal).
- Exact parameters/defaults/limits: `element_count`=4 1 with limits 2..1024; `element_resistance`=10000 ohm with limits >0; `tolerance`=0.05 1 with limits 0..1; `matching_tolerance`=0.01 1 with limits 0..1; `topology`=isolated 1 with limits isolated or bussed.
- Supported analyses: `dc`, `ac`, `transient`, `noise`, `monte-carlo`.
- Valid package mappings: `pkg-axial-2`, `pkg-smd-chip`, `pkg-radial-2`.
- Golden references: `GOLD-PAS-RESISTOR_ARRAY-NOMINAL`, `GOLD-PAS-RESISTOR_ARRAY-BOUNDARY`, `GOLD-PAS-RESISTOR_ARRAY-FAILURE`.
- Import mappings applicable to this family: `SPICE .model/.subckt`, `Verilog-A/AMS 2023`, `CSV/PWL`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 8-13; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Resistor array family-specific implementation reference](../../catalog/families/fam-passives-resistor-array.md#family-specific-implementation-reference), registry row `fam-passives-resistor-array`, and shared family scope across `var-passives-resistor-array-isolated`, `var-passives-resistor-array-bussed`.
- Exact pin vector: `1:P` (passive; electrical/thermal), `2:N` (passive; electrical/thermal).
- Exact parameter vector: `element_count`=4 1 with limits 2..1024; `element_resistance`=10000 ohm with limits >0; `tolerance`=0.05 1 with limits 0..1; `matching_tolerance`=0.01 1 with limits 0..1; `topology`=isolated 1 with limits isolated or bussed.
- Declared analyses: `dc`, `ac`, `transient`, `noise`, `monte-carlo`; declared package bindings: `pkg-axial-2`, `pkg-smd-chip`, `pkg-radial-2`.
- Exact F4 execution rule: Electrothermal/tolerance/failure tier: extend the lower-tier relation with declared sampling, power-to-heat state Cth*dT/dt = P-(T-Tamb)/Rth, derating, and deterministic failure transitions; base relation: Each declared resistor branch obeys v_k = R_k*i_k; shared-terminal and matching/correlation rules come only from the selected array topology.
- Exact reference vectors: `GOLD-PAS-RESISTOR_ARRAY-NOMINAL`, `GOLD-PAS-RESISTOR_ARRAY-BOUNDARY`, `GOLD-PAS-RESISTOR_ARRAY-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-passives-resistor-array-shared-f4-model.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-passives-resistor-array.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One `ModelBinding` for `fam-passives-resistor-array` at `F4` implementing the exact tier rule above, its initialization/state/stamp/event behavior, power reporting, and structured diagnostics.
- One `AnalysisCapability` result for each of `dc`, `ac`, `transient`, `noise`, `monte-carlo`, with every unlisted analysis rejected rather than approximated.
- Scope is limited to `CMP-PASSIVES-RESISTOR-ARRAY-SHARED-F4-MODEL`: shared family scope across `var-passives-resistor-array-isolated`, `var-passives-resistor-array-bussed`, fidelity `F4`, concern `MODEL`, and requirements REQ-009, REQ-010, REQ-011, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F4**, and concern **MODEL** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `1:P` (passive; electrical/thermal), `2:N` (passive; electrical/thermal); reject any package map outside `pkg-axial-2`, `pkg-smd-chip`, `pkg-radial-2`.
- Reject non-finite values and any value outside this exact parameter contract: `element_count`=4 1 with limits 2..1024; `element_resistance`=10000 ohm with limits >0; `tolerance`=0.05 1 with limits 0..1; `matching_tolerance`=0.01 1 with limits 0..1; `topology`=isolated 1 with limits isolated or bussed.
- Support only `dc`, `ac`, `transient`, `noise`, `monte-carlo`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Initialization, limiting, discontinuity, convergence/event ordering, cancellation, overflow/NaN, and out-of-envelope behavior must follow the `F4` rule without silent fallback.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-PASSIVES-RESISTOR-ARRAY-SHARED-F4-MODEL-NOMINAL`
- `TEST-CMP-PASSIVES-RESISTOR-ARRAY-SHARED-F4-MODEL-BOUNDARY`
- `TEST-CMP-PASSIVES-RESISTOR-ARRAY-SHARED-F4-MODEL-FAILURE`

## Acceptance

1. The exact output for `CMP-PASSIVES-RESISTOR-ARRAY-SHARED-F4-MODEL` exists and is limited to shared family scope across `var-passives-resistor-array-isolated`, `var-passives-resistor-array-bussed`, `F4`, and `MODEL`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-passives-resistor-array` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-009, REQ-010, REQ-011, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
