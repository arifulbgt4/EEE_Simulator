# CMP-SENSORS-ENVIRONMENT-CLIMATE-GAS-SENSOR-SHARED-F2-MODEL - Implement Climate and gas sensor F2 model

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-sensors-environment-climate-gas-sensor` - Climate and gas sensor |
| Variant | `shared` |
| Fidelity | F2 |
| Concern | MODEL |
| Release | R7 |
| Requirements | REQ-014, REQ-015, REQ-018, REQ-020, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Implement one model tier, **F2**, for **Climate and gas sensor** using the family equations/behavior and no higher-fidelity claims.

## Exact prerequisites

- `CMP-SENSORS-ENVIRONMENT-CLIMATE-GAS-SENSOR-HUMIDITY-F0-CAT`
- `CMP-SENSORS-ENVIRONMENT-CLIMATE-GAS-SENSOR-BAROMETRIC-F0-CAT`
- `CMP-SENSORS-ENVIRONMENT-CLIMATE-GAS-SENSOR-CARBON-DIOXIDE-F0-CAT`
- `CMP-SENSORS-ENVIRONMENT-CLIMATE-GAS-SENSOR-VOC-F0-CAT`
- `CMP-SENSORS-ENVIRONMENT-CLIMATE-GAS-SENSOR-GENERIC-GAS-F0-CAT`
- `CMP-SENSORS-ENVIRONMENT-CLIMATE-GAS-SENSOR-SHARED-F1-MODEL`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-sensors-environment-climate-gas-sensor.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-sensors-environment-climate-gas-sensor` (Climate and gas sensor); task scope: shared family scope across `var-sensors-environment-climate-gas-sensor-humidity`, `var-sensors-environment-climate-gas-sensor-barometric`, `var-sensors-environment-climate-gas-sensor-carbon-dioxide`, `var-sensors-environment-climate-gas-sensor-voc`, `var-sensors-environment-climate-gas-sensor-generic-gas`; fidelity `F2`; concern `MODEL`.
- Exact pins: `S:STIMULUS` (physical; electrical/physical/environmental), `O:OUTPUT` (output; electrical/physical/environmental), `VDD:VDD` (power; electrical/physical/environmental), `GND:GND` (power; electrical/physical/environmental).
- Exact parameters/defaults/limits: `relative_humidity_full_scale`=1 1 with limits >0; `pressure_full_scale`=120e3 Pa with limits >0; `concentration_full_scale`=0.01 mol/mol with limits >0; `warmup_time`=0 s with limits >=0; `response_time`=1 s with limits >=0.
- Supported analyses: `dc`, `transient`, `monte-carlo`, `environmental`.
- Valid package mappings: `pkg-sensor-module`, `pkg-sot-23`, `pkg-qfn`, `pkg-custom-parametric`.
- Golden references: `GOLD-SEN-CLIMATE_GAS_SENSOR-NOMINAL`, `GOLD-SEN-CLIMATE_GAS_SENSOR-BOUNDARY`, `GOLD-SEN-CLIMATE_GAS_SENSOR-FAILURE`.
- Import mappings applicable to this family: `SPICE .model/.subckt`, `Verilog-A/AMS 2023`, `CSV/PWL`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 16-20; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Climate and gas sensor family-specific implementation reference](../../catalog/families/fam-sensors-environment-climate-gas-sensor.md#family-specific-implementation-reference), registry row `fam-sensors-environment-climate-gas-sensor`, and shared family scope across `var-sensors-environment-climate-gas-sensor-humidity`, `var-sensors-environment-climate-gas-sensor-barometric`, `var-sensors-environment-climate-gas-sensor-carbon-dioxide`, `var-sensors-environment-climate-gas-sensor-voc`, `var-sensors-environment-climate-gas-sensor-generic-gas`.
- Exact pin vector: `S:STIMULUS` (physical; electrical/physical/environmental), `O:OUTPUT` (output; electrical/physical/environmental), `VDD:VDD` (power; electrical/physical/environmental), `GND:GND` (power; electrical/physical/environmental).
- Exact parameter vector: `relative_humidity_full_scale`=1 1 with limits >0; `pressure_full_scale`=120e3 Pa with limits >0; `concentration_full_scale`=0.01 mol/mol with limits >0; `warmup_time`=0 s with limits >=0; `response_time`=1 s with limits >=0.
- Declared analyses: `dc`, `transient`, `monte-carlo`, `environmental`; declared package bindings: `pkg-sensor-module`, `pkg-sot-23`, `pkg-qfn`, `pkg-custom-parametric`.
- Exact F2 execution rule: Behavioral/timing tier: preserve the family baseline using deterministic integer-tick state/event rules and explicit initialization: Output follows the declared humidity/gas concentration transfer with warm-up, cross-sensitivity, saturation, response/recovery, and environmental terms.
- Exact reference vectors: `GOLD-SEN-CLIMATE_GAS_SENSOR-NOMINAL`, `GOLD-SEN-CLIMATE_GAS_SENSOR-BOUNDARY`, `GOLD-SEN-CLIMATE_GAS_SENSOR-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-sensors-environment-climate-gas-sensor-shared-f2-model.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-sensors-environment-climate-gas-sensor.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One `ModelBinding` for `fam-sensors-environment-climate-gas-sensor` at `F2` implementing the exact tier rule above, its initialization/state/stamp/event behavior, power reporting, and structured diagnostics.
- One `AnalysisCapability` result for each of `dc`, `transient`, `monte-carlo`, `environmental`, with every unlisted analysis rejected rather than approximated.
- Scope is limited to `CMP-SENSORS-ENVIRONMENT-CLIMATE-GAS-SENSOR-SHARED-F2-MODEL`: shared family scope across `var-sensors-environment-climate-gas-sensor-humidity`, `var-sensors-environment-climate-gas-sensor-barometric`, `var-sensors-environment-climate-gas-sensor-carbon-dioxide`, `var-sensors-environment-climate-gas-sensor-voc`, `var-sensors-environment-climate-gas-sensor-generic-gas`, fidelity `F2`, concern `MODEL`, and requirements REQ-014, REQ-015, REQ-018, REQ-020, REQ-022, REQ-023, REQ-037, REQ-038.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F2**, and concern **MODEL** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `S:STIMULUS` (physical; electrical/physical/environmental), `O:OUTPUT` (output; electrical/physical/environmental), `VDD:VDD` (power; electrical/physical/environmental), `GND:GND` (power; electrical/physical/environmental); reject any package map outside `pkg-sensor-module`, `pkg-sot-23`, `pkg-qfn`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `relative_humidity_full_scale`=1 1 with limits >0; `pressure_full_scale`=120e3 Pa with limits >0; `concentration_full_scale`=0.01 mol/mol with limits >0; `warmup_time`=0 s with limits >=0; `response_time`=1 s with limits >=0.
- Support only `dc`, `transient`, `monte-carlo`, `environmental`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Initialization, limiting, discontinuity, convergence/event ordering, cancellation, overflow/NaN, and out-of-envelope behavior must follow the `F2` rule without silent fallback.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-SENSORS-ENVIRONMENT-CLIMATE-GAS-SENSOR-SHARED-F2-MODEL-NOMINAL`
- `TEST-CMP-SENSORS-ENVIRONMENT-CLIMATE-GAS-SENSOR-SHARED-F2-MODEL-BOUNDARY`
- `TEST-CMP-SENSORS-ENVIRONMENT-CLIMATE-GAS-SENSOR-SHARED-F2-MODEL-FAILURE`

## Acceptance

1. The exact output for `CMP-SENSORS-ENVIRONMENT-CLIMATE-GAS-SENSOR-SHARED-F2-MODEL` exists and is limited to shared family scope across `var-sensors-environment-climate-gas-sensor-humidity`, `var-sensors-environment-climate-gas-sensor-barometric`, `var-sensors-environment-climate-gas-sensor-carbon-dioxide`, `var-sensors-environment-climate-gas-sensor-voc`, `var-sensors-environment-climate-gas-sensor-generic-gas`, `F2`, and `MODEL`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-sensors-environment-climate-gas-sensor` and its family specification.
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
