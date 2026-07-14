# CMP-INSTRUMENTS-BENCH-SUPPLY-SHARED-F1-VALIDATION - Validate Bench supply F1

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-instruments-bench-supply` - Bench supply |
| Variant | `shared` |
| Fidelity | F1 |
| Concern | VALIDATION |
| Release | R2 |
| Requirements | REQ-007, REQ-021, REQ-022, REQ-023, REQ-034, REQ-037 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Produce independent validation evidence for **Bench supply** at **F1** without modifying the model under test.

## Exact prerequisites

- `CMP-INSTRUMENTS-BENCH-SUPPLY-SHARED-F1-MODEL`
- `PLAT-QA-001`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-instruments-bench-supply.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-instruments-bench-supply` (Bench supply); task scope: shared family scope across `var-instruments-bench-supply-single-output`, `var-instruments-bench-supply-triple-output`; fidelity `F1`; concern `VALIDATION`.
- Exact pins: `CH+:CHANNEL+` (input; measurement/electrical), `CH-:CHANNEL-` (input; measurement/electrical), `COM:COMMON` (reference; measurement/electrical).
- Exact parameters/defaults/limits: `channel_count`=1 1 with limits 1..16; `voltage_setpoint`=5 V with limits >=0; `current_limit`=1 A with limits >=0; `output_resistance`=0.01 ohm with limits >=0; `ramp_time`=0 s with limits >=0.
- Supported analyses: `measurement`, `dc`, `ac`, `transient`, `digital`.
- Valid package mappings: `pkg-virtual`.
- Golden references: `GOLD-INS-BENCH_SUPPLY-NOMINAL`, `GOLD-INS-BENCH_SUPPLY-BOUNDARY`, `GOLD-INS-BENCH_SUPPLY-FAILURE`.
- Import mappings applicable to this family: `SPICE .model/.subckt`, `Verilog-A/AMS 2023`, `CSV/PWL`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 20-23; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Bench supply family-specific implementation reference](../../catalog/families/fam-instruments-bench-supply.md#family-specific-implementation-reference), registry row `fam-instruments-bench-supply`, and shared family scope across `var-instruments-bench-supply-single-output`, `var-instruments-bench-supply-triple-output`.
- Exact pin vector: `CH+:CHANNEL+` (input; measurement/electrical), `CH-:CHANNEL-` (input; measurement/electrical), `COM:COMMON` (reference; measurement/electrical).
- Exact parameter vector: `channel_count`=1 1 with limits 1..16; `voltage_setpoint`=5 V with limits >=0; `current_limit`=1 A with limits >=0; `output_resistance`=0.01 ohm with limits >=0; `ramp_time`=0 s with limits >=0.
- Declared analyses: `measurement`, `dc`, `ac`, `transient`, `digital`; declared package bindings: `pkg-virtual`.
- Candidate and independent reference must evaluate the same F1 rule: Ideal/equation tier: implement exactly this family baseline and its declared parameter limits: The output follows CV/CC setpoints and transitions with declared source impedance, current limit, ramp, protection, and channel coupling.
- Exact reference vectors: `GOLD-INS-BENCH_SUPPLY-NOMINAL`, `GOLD-INS-BENCH_SUPPLY-BOUNDARY`, `GOLD-INS-BENCH_SUPPLY-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-instruments-bench-supply-shared-f1-validation.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-instruments-bench-supply.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One immutable candidate/reference evidence bundle for `GOLD-INS-BENCH_SUPPLY-NOMINAL`, `GOLD-INS-BENCH_SUPPLY-BOUNDARY`, `GOLD-INS-BENCH_SUPPLY-FAILURE` at `F1`, containing exact inputs, expected outputs, tolerance, versions, seed, and raw-result digests.
- Nominal, every declared boundary class, and every applicable failure/diagnostic vector linked to this task's three stable acceptance-test IDs.
- Scope is limited to `CMP-INSTRUMENTS-BENCH-SUPPLY-SHARED-F1-VALIDATION`: shared family scope across `var-instruments-bench-supply-single-output`, `var-instruments-bench-supply-triple-output`, fidelity `F1`, concern `VALIDATION`, and requirements REQ-007, REQ-021, REQ-022, REQ-023, REQ-034, REQ-037.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F1**, and concern **VALIDATION** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `CH+:CHANNEL+` (input; measurement/electrical), `CH-:CHANNEL-` (input; measurement/electrical), `COM:COMMON` (reference; measurement/electrical); reject any package map outside `pkg-virtual`.
- Reject non-finite values and any value outside this exact parameter contract: `channel_count`=1 1 with limits 1..16; `voltage_setpoint`=5 V with limits >=0; `current_limit`=1 A with limits >=0; `output_resistance`=0.01 ohm with limits >=0; `ramp_time`=0 s with limits >=0.
- Support only `measurement`, `dc`, `ac`, `transient`, `digital`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Missing independent reference, wrong seed/version, tolerance breach, nondeterminism, absent raw data, or a silent diagnostic mismatch fails the evidence bundle.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-INSTRUMENTS-BENCH-SUPPLY-SHARED-F1-VALIDATION-NOMINAL`
- `TEST-CMP-INSTRUMENTS-BENCH-SUPPLY-SHARED-F1-VALIDATION-BOUNDARY`
- `TEST-CMP-INSTRUMENTS-BENCH-SUPPLY-SHARED-F1-VALIDATION-FAILURE`

## Acceptance

1. The exact output for `CMP-INSTRUMENTS-BENCH-SUPPLY-SHARED-F1-VALIDATION` exists and is limited to shared family scope across `var-instruments-bench-supply-single-output`, `var-instruments-bench-supply-triple-output`, `F1`, and `VALIDATION`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-instruments-bench-supply` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-007, REQ-021, REQ-022, REQ-023, REQ-034, REQ-037, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
