# CMP-SENSORS-ENVIRONMENT-OPTICAL-SENSOR-SHARED-F4-THERMAL - Implement Optical sensor electrothermal behavior

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-sensors-environment-optical-sensor` - Optical sensor |
| Variant | `shared` |
| Fidelity | F4 |
| Concern | THERMAL |
| Release | R7 |
| Requirements | REQ-014, REQ-015, REQ-018, REQ-020, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Implement only the F4 power, temperature and electrothermal feedback concern for **Optical sensor**.

## Exact prerequisites

- `CMP-SENSORS-ENVIRONMENT-OPTICAL-SENSOR-SHARED-F4-MODEL`
- `PLAT-REAL-007`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-sensors-environment-optical-sensor.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-sensors-environment-optical-sensor` (Optical sensor); task scope: shared family scope across `var-sensors-environment-optical-sensor-photodiode-module`, `var-sensors-environment-optical-sensor-ambient-light`, `var-sensors-environment-optical-sensor-color`, `var-sensors-environment-optical-sensor-infrared`; fidelity `F4`; concern `THERMAL`.
- Exact pins: `S:STIMULUS` (physical; electrical/physical/environmental), `O:OUTPUT` (output; electrical/physical/environmental), `VDD:VDD` (power; electrical/physical/environmental), `GND:GND` (power; electrical/physical/environmental).
- Exact parameters/defaults/limits: `minimum_illuminance`=0 lx with limits >=0; `maximum_illuminance`=100e3 lx with limits >minimum_illuminance; `responsivity`=0.5 A/W with limits >=0; `dark_offset`=0 A with limits >=0; `response_time`=0.01 s with limits >=0.
- Supported analyses: `dc`, `transient`, `monte-carlo`, `environmental`.
- Valid package mappings: `pkg-sensor-module`, `pkg-sot-23`, `pkg-qfn`, `pkg-custom-parametric`.
- Golden references: `GOLD-SEN-OPTICAL_SENSOR-NOMINAL`, `GOLD-SEN-OPTICAL_SENSOR-BOUNDARY`, `GOLD-SEN-OPTICAL_SENSOR-FAILURE`.
- Import mappings applicable to this family: `SPICE .model/.subckt`, `Verilog-A/AMS 2023`, `CSV/PWL`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 16-20; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Optical sensor family-specific implementation reference](../../catalog/families/fam-sensors-environment-optical-sensor.md#family-specific-implementation-reference), registry row `fam-sensors-environment-optical-sensor`, and shared family scope across `var-sensors-environment-optical-sensor-photodiode-module`, `var-sensors-environment-optical-sensor-ambient-light`, `var-sensors-environment-optical-sensor-color`, `var-sensors-environment-optical-sensor-infrared`.
- Exact pin vector: `S:STIMULUS` (physical; electrical/physical/environmental), `O:OUTPUT` (output; electrical/physical/environmental), `VDD:VDD` (power; electrical/physical/environmental), `GND:GND` (power; electrical/physical/environmental).
- Exact parameter vector: `minimum_illuminance`=0 lx with limits >=0; `maximum_illuminance`=100e3 lx with limits >minimum_illuminance; `responsivity`=0.5 A/W with limits >=0; `dark_offset`=0 A with limits >=0; `response_time`=0.01 s with limits >=0.
- Declared analyses: `dc`, `transient`, `monte-carlo`, `environmental`; declared package bindings: `pkg-sensor-module`, `pkg-sot-23`, `pkg-qfn`, `pkg-custom-parametric`.
- Exact F4 thermal coupling is Cth*dT/dt = P-(T-Tamb)/Rth, with P from the family relation, explicit SI parameters, declared initialization, and no invented default when reference data is absent.
- Exact reference vectors: `GOLD-SEN-OPTICAL_SENSOR-NOMINAL`, `GOLD-SEN-OPTICAL_SENSOR-BOUNDARY`, `GOLD-SEN-OPTICAL_SENSOR-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-sensors-environment-optical-sensor-shared-f4-thermal.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-sensors-environment-optical-sensor.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One F4 thermal-state contract for `fam-sensors-environment-optical-sensor` naming P, T, Tamb, Rth, Cth, initial state, valid range, update order, and unsupported coupling behavior.
- Deterministic steady/transient thermal and runaway/limit evidence tied to the exact family reference vectors.
- Scope is limited to `CMP-SENSORS-ENVIRONMENT-OPTICAL-SENSOR-SHARED-F4-THERMAL`: shared family scope across `var-sensors-environment-optical-sensor-photodiode-module`, `var-sensors-environment-optical-sensor-ambient-light`, `var-sensors-environment-optical-sensor-color`, `var-sensors-environment-optical-sensor-infrared`, fidelity `F4`, concern `THERMAL`, and requirements REQ-014, REQ-015, REQ-018, REQ-020, REQ-022, REQ-023, REQ-037, REQ-038.

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

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `S:STIMULUS` (physical; electrical/physical/environmental), `O:OUTPUT` (output; electrical/physical/environmental), `VDD:VDD` (power; electrical/physical/environmental), `GND:GND` (power; electrical/physical/environmental); reject any package map outside `pkg-sensor-module`, `pkg-sot-23`, `pkg-qfn`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `minimum_illuminance`=0 lx with limits >=0; `maximum_illuminance`=100e3 lx with limits >minimum_illuminance; `responsivity`=0.5 A/W with limits >=0; `dark_offset`=0 A with limits >=0; `response_time`=0.01 s with limits >=0.
- Support only `dc`, `transient`, `monte-carlo`, `environmental`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Non-positive Rth/Cth, temperature outside the declared range, runaway, non-finite power, unsupported coupling, and timestep underflow produce named diagnostics.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-SENSORS-ENVIRONMENT-OPTICAL-SENSOR-SHARED-F4-THERMAL-NOMINAL`
- `TEST-CMP-SENSORS-ENVIRONMENT-OPTICAL-SENSOR-SHARED-F4-THERMAL-BOUNDARY`
- `TEST-CMP-SENSORS-ENVIRONMENT-OPTICAL-SENSOR-SHARED-F4-THERMAL-FAILURE`

## Acceptance

1. The exact output for `CMP-SENSORS-ENVIRONMENT-OPTICAL-SENSOR-SHARED-F4-THERMAL` exists and is limited to shared family scope across `var-sensors-environment-optical-sensor-photodiode-module`, `var-sensors-environment-optical-sensor-ambient-light`, `var-sensors-environment-optical-sensor-color`, `var-sensors-environment-optical-sensor-infrared`, `F4`, and `THERMAL`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-sensors-environment-optical-sensor` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-014, REQ-015, REQ-018, REQ-020, REQ-022, REQ-023, REQ-037, REQ-038, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
