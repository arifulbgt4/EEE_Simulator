# CMP-ACTUATORS-HMI-STEPPER-MOTOR-SHARED-F4-FAILURE - Implement Stepper motor failure behavior

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-actuators-hmi-stepper-motor` - Stepper motor |
| Variant | `shared` |
| Fidelity | F4 |
| Concern | FAILURE |
| Release | R7 |
| Requirements | REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Implement only the declared F4 failure states and controlled failure injection for **Stepper motor**.

## Exact prerequisites

- `CMP-ACTUATORS-HMI-STEPPER-MOTOR-SHARED-F4-MODEL`
- `CMP-ACTUATORS-HMI-STEPPER-MOTOR-SHARED-F4-THERMAL`
- `PLAT-REAL-010`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-actuators-hmi-stepper-motor.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-actuators-hmi-stepper-motor` (Stepper motor); task scope: shared family scope across `var-actuators-hmi-stepper-motor-unipolar`, `var-actuators-hmi-stepper-motor-bipolar`, `var-actuators-hmi-stepper-motor-hybrid`; fidelity `F4`; concern `FAILURE`.
- Exact pins: `1:DRIVE+` (input; electrical/mechanical/optical/acoustic), `2:DRIVE-` (input; electrical/mechanical/optical/acoustic), `M:MECHANICAL_OR_DISPLAY` (physical; electrical/mechanical/optical/acoustic).
- Exact parameters/defaults/limits: `phase_resistance`=2 ohm with limits >0; `phase_inductance`=2e-3 H with limits >=0; `step_angle`=0.0314159 rad with limits >0; `holding_torque`=0.5 N*m with limits >=0; `rotor_inertia`=1e-4 kg*m^2 with limits >0; `detent_torque`=0 N*m with limits >=0.
- Supported analyses: `dc`, `transient`, `electromechanical`.
- Valid package mappings: `pkg-electromechanical`, `pkg-display-module`, `pkg-custom-parametric`.
- Golden references: `GOLD-ACT-STEPPER_MOTOR-NOMINAL`, `GOLD-ACT-STEPPER_MOTOR-BOUNDARY`, `GOLD-ACT-STEPPER_MOTOR-FAILURE`.
- Import mappings applicable to this family: `SPICE .model/.subckt`, `Verilog-A/AMS 2023`, `CSV/PWL`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 17-21; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Stepper motor family-specific implementation reference](../../catalog/families/fam-actuators-hmi-stepper-motor.md#family-specific-implementation-reference), registry row `fam-actuators-hmi-stepper-motor`, and shared family scope across `var-actuators-hmi-stepper-motor-unipolar`, `var-actuators-hmi-stepper-motor-bipolar`, `var-actuators-hmi-stepper-motor-hybrid`.
- Exact pin vector: `1:DRIVE+` (input; electrical/mechanical/optical/acoustic), `2:DRIVE-` (input; electrical/mechanical/optical/acoustic), `M:MECHANICAL_OR_DISPLAY` (physical; electrical/mechanical/optical/acoustic).
- Exact parameter vector: `phase_resistance`=2 ohm with limits >0; `phase_inductance`=2e-3 H with limits >=0; `step_angle`=0.0314159 rad with limits >0; `holding_torque`=0.5 N*m with limits >=0; `rotor_inertia`=1e-4 kg*m^2 with limits >0; `detent_torque`=0 N*m with limits >=0.
- Declared analyses: `dc`, `transient`, `electromechanical`; declared package bindings: `pkg-electromechanical`, `pkg-display-module`, `pkg-custom-parametric`.
- The deterministic failure state machine evaluates the declared limit/damage predicates, records the triggering value/time/seed, and applies only these family modes: `open-circuit`, `short-circuit`, `parameter-drift`, `overstress-or-saturation`.
- Exact reference vectors: `GOLD-ACT-STEPPER_MOTOR-NOMINAL`, `GOLD-ACT-STEPPER_MOTOR-BOUNDARY`, `GOLD-ACT-STEPPER_MOTOR-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-actuators-hmi-stepper-motor-shared-f4-failure.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-actuators-hmi-stepper-motor.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One versioned `FailureDefinition` set for `open-circuit`, `short-circuit`, `parameter-drift`, `overstress-or-saturation`, with trigger, transition, latched/reset behavior, and diagnostic payload.
- Deterministic threshold, simultaneous-trigger, invalid-threshold, and seeded intermittent evidence without changing the base `F4` model relation.
- Scope is limited to `CMP-ACTUATORS-HMI-STEPPER-MOTOR-SHARED-F4-FAILURE`: shared family scope across `var-actuators-hmi-stepper-motor-unipolar`, `var-actuators-hmi-stepper-motor-bipolar`, `var-actuators-hmi-stepper-motor-hybrid`, fidelity `F4`, concern `FAILURE`, and requirements REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, REQ-038.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F4**, and concern **FAILURE** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `1:DRIVE+` (input; electrical/mechanical/optical/acoustic), `2:DRIVE-` (input; electrical/mechanical/optical/acoustic), `M:MECHANICAL_OR_DISPLAY` (physical; electrical/mechanical/optical/acoustic); reject any package map outside `pkg-electromechanical`, `pkg-display-module`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `phase_resistance`=2 ohm with limits >0; `phase_inductance`=2e-3 H with limits >=0; `step_angle`=0.0314159 rad with limits >0; `holding_torque`=0.5 N*m with limits >=0; `rotor_inertia`=1e-4 kg*m^2 with limits >0; `detent_torque`=0 N*m with limits >=0.
- Support only `dc`, `transient`, `electromechanical`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Invalid threshold ordering, simultaneous triggers, reset of a latched fault, undefined intermittent seed, and failure/model state conflict produce deterministic named outcomes.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-ACTUATORS-HMI-STEPPER-MOTOR-SHARED-F4-FAILURE-NOMINAL`
- `TEST-CMP-ACTUATORS-HMI-STEPPER-MOTOR-SHARED-F4-FAILURE-BOUNDARY`
- `TEST-CMP-ACTUATORS-HMI-STEPPER-MOTOR-SHARED-F4-FAILURE-FAILURE`

## Acceptance

1. The exact output for `CMP-ACTUATORS-HMI-STEPPER-MOTOR-SHARED-F4-FAILURE` exists and is limited to shared family scope across `var-actuators-hmi-stepper-motor-unipolar`, `var-actuators-hmi-stepper-motor-bipolar`, `var-actuators-hmi-stepper-motor-hybrid`, `F4`, and `FAILURE`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-actuators-hmi-stepper-motor` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, REQ-038, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
