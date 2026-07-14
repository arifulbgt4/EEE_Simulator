# CMP-CONNECTIVITY-WIRE-SHARED-F0-VALIDATION - Validate Wire and conductor F0

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-connectivity-wire` - Wire and conductor |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | VALIDATION |
| Release | R2 |
| Requirements | REQ-004, REQ-005, REQ-008, REQ-022, REQ-023, REQ-037 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Produce independent validation evidence for **Wire and conductor** at **F0** without modifying the model under test.

## Exact prerequisites

- `CMP-CONNECTIVITY-WIRE-SHARED-F0-MODEL`
- `PLAT-QA-001`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-connectivity-wire.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-connectivity-wire` (Wire and conductor); task scope: shared family scope across `var-connectivity-wire-conductor`; fidelity `F0`; concern `VALIDATION`.
- Exact pins: `1:P` (passive; electrical/schematic), `2:N` (passive; electrical/schematic).
- Exact parameters/defaults/limits: `length`=0.01 m with limits >0; `series_resistance`=0 ohm with limits >=0; `series_inductance`=0 H with limits >=0; `shunt_capacitance`=0 F with limits >=0.
- Supported analyses: `connectivity`, `erc`.
- Valid package mappings: `pkg-virtual`.
- Golden references: `GOLD-CON-WIRE-NOMINAL`, `GOLD-CON-WIRE-BOUNDARY`, `GOLD-CON-WIRE-FAILURE`.
- Import mappings applicable to this family: `SPICE .model/.subckt`, `Verilog-A/AMS 2023`, `CSV/PWL`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 6-8; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Wire and conductor family-specific implementation reference](../../catalog/families/fam-connectivity-wire.md#family-specific-implementation-reference), registry row `fam-connectivity-wire`, and shared family scope across `var-connectivity-wire-conductor`.
- Exact pin vector: `1:P` (passive; electrical/schematic), `2:N` (passive; electrical/schematic).
- Exact parameter vector: `length`=0.01 m with limits >0; `series_resistance`=0 ohm with limits >=0; `series_inductance`=0 H with limits >=0; `shunt_capacitance`=0 F with limits >=0.
- Declared analyses: `connectivity`, `erc`; declared package bindings: `pkg-virtual`.
- Candidate and independent reference must evaluate the same F0 rule: Connectivity-only: validate declared pins, domains, width/direction, hierarchy, and package mapping; do not claim numerical behavior. Family baseline: Ideal connectivity enforces v(P) - v(N) = 0; any F1 non-ideal profile replaces the ideal branch with an explicitly parameterized series impedance.
- Exact reference vectors: `GOLD-CON-WIRE-NOMINAL`, `GOLD-CON-WIRE-BOUNDARY`, `GOLD-CON-WIRE-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-connectivity-wire-shared-f0-validation.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-connectivity-wire.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One immutable candidate/reference evidence bundle for `GOLD-CON-WIRE-NOMINAL`, `GOLD-CON-WIRE-BOUNDARY`, `GOLD-CON-WIRE-FAILURE` at `F0`, containing exact inputs, expected outputs, tolerance, versions, seed, and raw-result digests.
- Nominal, every declared boundary class, and every applicable failure/diagnostic vector linked to this task's three stable acceptance-test IDs.
- Scope is limited to `CMP-CONNECTIVITY-WIRE-SHARED-F0-VALIDATION`: shared family scope across `var-connectivity-wire-conductor`, fidelity `F0`, concern `VALIDATION`, and requirements REQ-004, REQ-005, REQ-008, REQ-022, REQ-023, REQ-037.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F0**, and concern **VALIDATION** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `1:P` (passive; electrical/schematic), `2:N` (passive; electrical/schematic); reject any package map outside `pkg-virtual`.
- Reject non-finite values and any value outside this exact parameter contract: `length`=0.01 m with limits >0; `series_resistance`=0 ohm with limits >=0; `series_inductance`=0 H with limits >=0; `shunt_capacitance`=0 F with limits >=0.
- Support only `connectivity`, `erc`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Missing independent reference, wrong seed/version, tolerance breach, nondeterminism, absent raw data, or a silent diagnostic mismatch fails the evidence bundle.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-CONNECTIVITY-WIRE-SHARED-F0-VALIDATION-NOMINAL`
- `TEST-CMP-CONNECTIVITY-WIRE-SHARED-F0-VALIDATION-BOUNDARY`
- `TEST-CMP-CONNECTIVITY-WIRE-SHARED-F0-VALIDATION-FAILURE`

## Acceptance

1. The exact output for `CMP-CONNECTIVITY-WIRE-SHARED-F0-VALIDATION` exists and is limited to shared family scope across `var-connectivity-wire-conductor`, `F0`, and `VALIDATION`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-connectivity-wire` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-004, REQ-005, REQ-008, REQ-022, REQ-023, REQ-037, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
