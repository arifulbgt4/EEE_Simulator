# CMP-SWITCH-PROTECTION-FUSE-SHARED-F4-THERMAL - Implement Fuse and resettable protector electrothermal behavior

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-switch-protection-fuse` - Fuse and resettable protector |
| Variant | `shared` |
| Fidelity | F4 |
| Concern | THERMAL |
| Release | R7 |
| Requirements | REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Implement only the F4 power, temperature and electrothermal feedback concern for **Fuse and resettable protector**.

## Exact prerequisites

- `CMP-SWITCH-PROTECTION-FUSE-SHARED-F4-MODEL`
- `PLAT-REAL-007`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-switch-protection-fuse.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-switch-protection-fuse` (Fuse and resettable protector); task scope: shared family scope across `var-switch-protection-fuse-fast-blow`, `var-switch-protection-fuse-slow-blow`, `var-switch-protection-fuse-ptc-resettable`; fidelity `F4`; concern `THERMAL`.
- Exact pins: `1:P` (passive; electrical/control), `2:N` (passive; electrical/control).
- Exact parameters/defaults/limits: `rated_current`=1 A with limits >0; `i2t_limit`=1 A^2*s with limits >0; `cold_resistance`=0.05 ohm with limits >=0; `resettable`=false 1 with limits true or false; `ambient_temperature`=298.15 K with limits >0.
- Supported analyses: `dc`, `transient`, `electrothermal`, `fault`.
- Valid package mappings: `pkg-custom-parametric`.
- Golden references: `GOLD-SWP-FUSE-NOMINAL`, `GOLD-SWP-FUSE-BOUNDARY`, `GOLD-SWP-FUSE-FAILURE`.
- Import mappings applicable to this family: `SPICE .model/.subckt`, `Verilog-A/AMS 2023`, `CSV/PWL`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 10-14; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Fuse and resettable protector family-specific implementation reference](../../catalog/families/fam-switch-protection-fuse.md#family-specific-implementation-reference), registry row `fam-switch-protection-fuse`, and shared family scope across `var-switch-protection-fuse-fast-blow`, `var-switch-protection-fuse-slow-blow`, `var-switch-protection-fuse-ptc-resettable`.
- Exact pin vector: `1:P` (passive; electrical/control), `2:N` (passive; electrical/control).
- Exact parameter vector: `rated_current`=1 A with limits >0; `i2t_limit`=1 A^2*s with limits >0; `cold_resistance`=0.05 ohm with limits >=0; `resettable`=false 1 with limits true or false; `ambient_temperature`=298.15 K with limits >0.
- Declared analyses: `dc`, `transient`, `electrothermal`, `fault`; declared package bindings: `pkg-custom-parametric`.
- Exact F4 thermal coupling is Cth*dT/dt = P-(T-Tamb)/Rth, with P from the family relation, explicit SI parameters, declared initialization, and no invented default when reference data is absent.
- Exact reference vectors: `GOLD-SWP-FUSE-NOMINAL`, `GOLD-SWP-FUSE-BOUNDARY`, `GOLD-SWP-FUSE-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-switch-protection-fuse-shared-f4-thermal.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-switch-protection-fuse.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One F4 thermal-state contract for `fam-switch-protection-fuse` naming P, T, Tamb, Rth, Cth, initial state, valid range, update order, and unsupported coupling behavior.
- Deterministic steady/transient thermal and runaway/limit evidence tied to the exact family reference vectors.
- Scope is limited to `CMP-SWITCH-PROTECTION-FUSE-SHARED-F4-THERMAL`: shared family scope across `var-switch-protection-fuse-fast-blow`, `var-switch-protection-fuse-slow-blow`, `var-switch-protection-fuse-ptc-resettable`, fidelity `F4`, concern `THERMAL`, and requirements REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F4**, and concern **THERMAL** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `1:P` (passive; electrical/control), `2:N` (passive; electrical/control); reject any package map outside `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `rated_current`=1 A with limits >0; `i2t_limit`=1 A^2*s with limits >0; `cold_resistance`=0.05 ohm with limits >=0; `resettable`=false 1 with limits true or false; `ambient_temperature`=298.15 K with limits >0.
- Support only `dc`, `transient`, `electrothermal`, `fault`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Non-positive Rth/Cth, temperature outside the declared range, runaway, non-finite power, unsupported coupling, and timestep underflow produce named diagnostics.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-SWITCH-PROTECTION-FUSE-SHARED-F4-THERMAL-NOMINAL`
- `TEST-CMP-SWITCH-PROTECTION-FUSE-SHARED-F4-THERMAL-BOUNDARY`
- `TEST-CMP-SWITCH-PROTECTION-FUSE-SHARED-F4-THERMAL-FAILURE`

## Acceptance

1. The exact output for `CMP-SWITCH-PROTECTION-FUSE-SHARED-F4-THERMAL` exists and is limited to shared family scope across `var-switch-protection-fuse-fast-blow`, `var-switch-protection-fuse-slow-blow`, `var-switch-protection-fuse-ptc-resettable`, `F4`, and `THERMAL`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-switch-protection-fuse` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
