# CMP-POWER-ELECTRONICS-DC-CONVERTER-SHARED-F2-MODEL - Implement DC converter F2 model

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-power-electronics-dc-converter` - DC converter |
| Variant | `shared` |
| Fidelity | F2 |
| Concern | MODEL |
| Release | R7 |
| Requirements | REQ-009, REQ-010, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Implement one model tier, **F2**, for **DC converter** using the family equations/behavior and no higher-fidelity claims.

## Exact prerequisites

- `CMP-POWER-ELECTRONICS-DC-CONVERTER-BUCK-F0-CAT`
- `CMP-POWER-ELECTRONICS-DC-CONVERTER-BOOST-F0-CAT`
- `CMP-POWER-ELECTRONICS-DC-CONVERTER-BUCK-BOOST-F0-CAT`
- `CMP-POWER-ELECTRONICS-DC-CONVERTER-FLYBACK-F0-CAT`
- `CMP-POWER-ELECTRONICS-DC-CONVERTER-FORWARD-F0-CAT`
- `CMP-POWER-ELECTRONICS-DC-CONVERTER-CHARGE-PUMP-F0-CAT`
- `CMP-POWER-ELECTRONICS-DC-CONVERTER-SHARED-F1-MODEL`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-power-electronics-dc-converter.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-power-electronics-dc-converter` (DC converter); task scope: shared family scope across `var-power-electronics-dc-converter-buck`, `var-power-electronics-dc-converter-boost`, `var-power-electronics-dc-converter-buck-boost`, `var-power-electronics-dc-converter-flyback`, `var-power-electronics-dc-converter-forward`, `var-power-electronics-dc-converter-charge-pump`; fidelity `F2`; concern `MODEL`.
- Exact pins: `IN+:INPUT+` (power; electrical/control/thermal), `IN-:INPUT-` (power; electrical/control/thermal), `OUT+:OUTPUT+` (power; electrical/control/thermal), `OUT-:OUTPUT-` (power; electrical/control/thermal), `CTRL:CONTROL` (input; electrical/control/thermal).
- Exact parameters/defaults/limits: `input_voltage`=12 V with limits >0; `output_voltage`=5 V with limits >0; `switching_frequency`=100e3 Hz with limits >0; `inductance`=100e-6 H with limits >0; `capacitance`=100e-6 F with limits >0; `efficiency`=0.9 1 with limits 0..1.
- Supported analyses: `dc`, `transient`, `harmonic`, `electrothermal`.
- Valid package mappings: `pkg-to-220`, `pkg-to-247`, `pkg-power-module`, `pkg-custom-parametric`.
- Golden references: `GOLD-PWR-DC_CONVERTER-NOMINAL`, `GOLD-PWR-DC_CONVERTER-BOUNDARY`, `GOLD-PWR-DC_CONVERTER-FAILURE`.
- Import mappings applicable to this family: `SPICE .model/.subckt`, `Verilog-A/AMS 2023`, `CSV/PWL`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 14-18; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [DC converter family-specific implementation reference](../../catalog/families/fam-power-electronics-dc-converter.md#family-specific-implementation-reference), registry row `fam-power-electronics-dc-converter`, and shared family scope across `var-power-electronics-dc-converter-buck`, `var-power-electronics-dc-converter-boost`, `var-power-electronics-dc-converter-buck-boost`, `var-power-electronics-dc-converter-flyback`, `var-power-electronics-dc-converter-forward`, `var-power-electronics-dc-converter-charge-pump`.
- Exact pin vector: `IN+:INPUT+` (power; electrical/control/thermal), `IN-:INPUT-` (power; electrical/control/thermal), `OUT+:OUTPUT+` (power; electrical/control/thermal), `OUT-:OUTPUT-` (power; electrical/control/thermal), `CTRL:CONTROL` (input; electrical/control/thermal).
- Exact parameter vector: `input_voltage`=12 V with limits >0; `output_voltage`=5 V with limits >0; `switching_frequency`=100e3 Hz with limits >0; `inductance`=100e-6 H with limits >0; `capacitance`=100e-6 F with limits >0; `efficiency`=0.9 1 with limits 0..1.
- Declared analyses: `dc`, `transient`, `harmonic`, `electrothermal`; declared package bindings: `pkg-to-220`, `pkg-to-247`, `pkg-power-module`, `pkg-custom-parametric`.
- Exact F2 execution rule: Behavioral/timing tier: preserve the family baseline using deterministic integer-tick state/event rules and explicit initialization: The selected buck/boost/buck-boost/flyback/forward/charge-pump profile uses either an explicit switching topology or declared averaged state-space equations.
- Exact reference vectors: `GOLD-PWR-DC_CONVERTER-NOMINAL`, `GOLD-PWR-DC_CONVERTER-BOUNDARY`, `GOLD-PWR-DC_CONVERTER-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-power-electronics-dc-converter-shared-f2-model.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-power-electronics-dc-converter.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One `ModelBinding` for `fam-power-electronics-dc-converter` at `F2` implementing the exact tier rule above, its initialization/state/stamp/event behavior, power reporting, and structured diagnostics.
- One `AnalysisCapability` result for each of `dc`, `transient`, `harmonic`, `electrothermal`, with every unlisted analysis rejected rather than approximated.
- Scope is limited to `CMP-POWER-ELECTRONICS-DC-CONVERTER-SHARED-F2-MODEL`: shared family scope across `var-power-electronics-dc-converter-buck`, `var-power-electronics-dc-converter-boost`, `var-power-electronics-dc-converter-buck-boost`, `var-power-electronics-dc-converter-flyback`, `var-power-electronics-dc-converter-forward`, `var-power-electronics-dc-converter-charge-pump`, fidelity `F2`, concern `MODEL`, and requirements REQ-009, REQ-010, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, REQ-038.

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

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `IN+:INPUT+` (power; electrical/control/thermal), `IN-:INPUT-` (power; electrical/control/thermal), `OUT+:OUTPUT+` (power; electrical/control/thermal), `OUT-:OUTPUT-` (power; electrical/control/thermal), `CTRL:CONTROL` (input; electrical/control/thermal); reject any package map outside `pkg-to-220`, `pkg-to-247`, `pkg-power-module`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `input_voltage`=12 V with limits >0; `output_voltage`=5 V with limits >0; `switching_frequency`=100e3 Hz with limits >0; `inductance`=100e-6 H with limits >0; `capacitance`=100e-6 F with limits >0; `efficiency`=0.9 1 with limits 0..1.
- Support only `dc`, `transient`, `harmonic`, `electrothermal`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Initialization, limiting, discontinuity, convergence/event ordering, cancellation, overflow/NaN, and out-of-envelope behavior must follow the `F2` rule without silent fallback.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-POWER-ELECTRONICS-DC-CONVERTER-SHARED-F2-MODEL-NOMINAL`
- `TEST-CMP-POWER-ELECTRONICS-DC-CONVERTER-SHARED-F2-MODEL-BOUNDARY`
- `TEST-CMP-POWER-ELECTRONICS-DC-CONVERTER-SHARED-F2-MODEL-FAILURE`

## Acceptance

1. The exact output for `CMP-POWER-ELECTRONICS-DC-CONVERTER-SHARED-F2-MODEL` exists and is limited to shared family scope across `var-power-electronics-dc-converter-buck`, `var-power-electronics-dc-converter-boost`, `var-power-electronics-dc-converter-buck-boost`, `var-power-electronics-dc-converter-flyback`, `var-power-electronics-dc-converter-forward`, `var-power-electronics-dc-converter-charge-pump`, `F2`, and `MODEL`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-power-electronics-dc-converter` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-009, REQ-010, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, REQ-038, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
