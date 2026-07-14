# CMP-RF-COMMUNICATIONS-RF-SWITCH-AMPLIFIER-SHARED-F3-IMPORT - Define import mapping for RF switch and amplifier

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-rf-communications-rf-switch-amplifier` - RF switch and amplifier |
| Variant | `shared` |
| Fidelity | F3 |
| Concern | IMPORT |
| Release | R7 |
| Requirements | REQ-011, REQ-012, REQ-024, REQ-028, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Implement and validate only the declared external-model mappings for **RF switch and amplifier**.

## Exact prerequisites

- `CMP-RF-COMMUNICATIONS-RF-SWITCH-AMPLIFIER-SHARED-F3-MODEL`
- `PLAT-IMP-005`
- `PLAT-IMP-006`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-rf-communications-rf-switch-amplifier.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-rf-communications-rf-switch-amplifier` (RF switch and amplifier); task scope: shared family scope across `var-rf-communications-rf-switch-amplifier-rf-switch`, `var-rf-communications-rf-switch-amplifier-lna`, `var-rf-communications-rf-switch-amplifier-power-amplifier`; fidelity `F3`; concern `IMPORT`.
- Exact pins: `IN:RF_IN` (passive; rf/electrical/communications), `OUT:RF_OUT` (passive; rf/electrical/communications), `GND:GROUND` (reference; rf/electrical/communications).
- Exact parameters/defaults/limits: `port_count`=2 1 with limits 2..64; `gain`=10 1 with limits >=0; `noise_figure`=2 1 with limits >=1; `compression_power`=1 W with limits >0; `isolation`=1e-3 1 with limits 0..1; `center_frequency`=1e9 Hz with limits >0.
- Supported analyses: `ac`, `s-parameter`, `noise`, `modulation`.
- Valid package mappings: `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Golden references: `GOLD-RFC-RF_SWITCH_AMPLIFIER-NOMINAL`, `GOLD-RFC-RF_SWITCH_AMPLIFIER-BOUNDARY`, `GOLD-RFC-RF_SWITCH_AMPLIFIER-FAILURE`.
- Import mappings applicable to this family: `Touchstone 2.1`, `IBIS 8.0`, `CSV`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 28-35; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [RF switch and amplifier family-specific implementation reference](../../catalog/families/fam-rf-communications-rf-switch-amplifier.md#family-specific-implementation-reference), registry row `fam-rf-communications-rf-switch-amplifier`, and shared family scope across `var-rf-communications-rf-switch-amplifier-rf-switch`, `var-rf-communications-rf-switch-amplifier-lna`, `var-rf-communications-rf-switch-amplifier-power-amplifier`.
- Exact pin vector: `IN:RF_IN` (passive; rf/electrical/communications), `OUT:RF_OUT` (passive; rf/electrical/communications), `GND:GROUND` (reference; rf/electrical/communications).
- Exact parameter vector: `port_count`=2 1 with limits 2..64; `gain`=10 1 with limits >=0; `noise_figure`=2 1 with limits >=1; `compression_power`=1 W with limits >0; `isolation`=1e-3 1 with limits 0..1; `center_frequency`=1e9 Hz with limits >0.
- Declared analyses: `ac`, `s-parameter`, `noise`, `modulation`; declared package bindings: `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Exact import targets are `Touchstone 2.1`, `IBIS 8.0`, `CSV`. Imported equations remain authoritative only inside their declared analysis/envelope and after ordered-pin, unit, provenance, license, and digest validation.
- Exact reference vectors: `GOLD-RFC-RF_SWITCH_AMPLIFIER-NOMINAL`, `GOLD-RFC-RF_SWITCH_AMPLIFIER-BOUNDARY`, `GOLD-RFC-RF_SWITCH_AMPLIFIER-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-rf-communications-rf-switch-amplifier-shared-f3-import.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-rf-communications-rf-switch-amplifier.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One ordered-pin/parameter/unit mapping and `ModelProvenance` record for each applicable target `Touchstone 2.1`, `IBIS 8.0`, `CSV`.
- Round-trip or explicit-loss evidence plus structured rejection for unsupported syntax, ambiguous pins, unknown license, digest mismatch, unsafe include, and unsupported analysis.
- Scope is limited to `CMP-RF-COMMUNICATIONS-RF-SWITCH-AMPLIFIER-SHARED-F3-IMPORT`: shared family scope across `var-rf-communications-rf-switch-amplifier-rf-switch`, `var-rf-communications-rf-switch-amplifier-lna`, `var-rf-communications-rf-switch-amplifier-power-amplifier`, fidelity `F3`, concern `IMPORT`, and requirements REQ-011, REQ-012, REQ-024, REQ-028, REQ-022, REQ-023, REQ-037, REQ-038.

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

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `IN:RF_IN` (passive; rf/electrical/communications), `OUT:RF_OUT` (passive; rf/electrical/communications), `GND:GROUND` (reference; rf/electrical/communications); reject any package map outside `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `port_count`=2 1 with limits 2..64; `gain`=10 1 with limits >=0; `noise_figure`=2 1 with limits >=1; `compression_power`=1 W with limits >0; `isolation`=1e-3 1 with limits 0..1; `center_frequency`=1e9 Hz with limits >0.
- Support only `ac`, `s-parameter`, `noise`, `modulation`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Path traversal, recursive include, resource limit, unsupported construct, ambiguous ground/reference, unknown rights, or executable/network behavior is quarantined or rejected.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-RF-COMMUNICATIONS-RF-SWITCH-AMPLIFIER-SHARED-F3-IMPORT-NOMINAL`
- `TEST-CMP-RF-COMMUNICATIONS-RF-SWITCH-AMPLIFIER-SHARED-F3-IMPORT-BOUNDARY`
- `TEST-CMP-RF-COMMUNICATIONS-RF-SWITCH-AMPLIFIER-SHARED-F3-IMPORT-FAILURE`

## Acceptance

1. The exact output for `CMP-RF-COMMUNICATIONS-RF-SWITCH-AMPLIFIER-SHARED-F3-IMPORT` exists and is limited to shared family scope across `var-rf-communications-rf-switch-amplifier-rf-switch`, `var-rf-communications-rf-switch-amplifier-lna`, `var-rf-communications-rf-switch-amplifier-power-amplifier`, `F3`, and `IMPORT`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-rf-communications-rf-switch-amplifier` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-011, REQ-012, REQ-024, REQ-028, REQ-022, REQ-023, REQ-037, REQ-038, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
