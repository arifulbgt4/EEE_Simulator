# CMP-DIGITAL-LOGIC-COUNTER-SHARED-F3-VALIDATION - Validate Counter F3

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-digital-logic-counter` - Counter |
| Variant | `shared` |
| Fidelity | F3 |
| Concern | VALIDATION |
| Release | R5 |
| Requirements | REQ-018, REQ-021, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Produce independent validation evidence for **Counter** at **F3** without modifying the model under test.

## Exact prerequisites

- `CMP-DIGITAL-LOGIC-COUNTER-SHARED-F3-MODEL`
- `PLAT-QA-001`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-digital-logic-counter.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-digital-logic-counter` (Counter); task scope: shared family scope across `var-digital-logic-counter-ripple`, `var-digital-logic-counter-synchronous`, `var-digital-logic-counter-up-down`; fidelity `F3`; concern `VALIDATION`.
- Exact pins: `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power).
- Exact parameters/defaults/limits: `width`=8 bit with limits 1..4096; `modulus`=256 1 with limits 2..2^width; `direction`=up 1 with limits up or down; `initial_value`=0 1 with limits 0..modulus-1; `clock_to_output`=0 s with limits >=0.
- Supported analyses: `digital-event`, `timing`, `truth-table`.
- Valid package mappings: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Golden references: `GOLD-DIG-COUNTER-NOMINAL`, `GOLD-DIG-COUNTER-BOUNDARY`, `GOLD-DIG-COUNTER-FAILURE`.
- Import mappings applicable to this family: `Verilog/SystemVerilog`, `VCD/FST`, `HEX/ELF`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 21-26; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Counter family-specific implementation reference](../../catalog/families/fam-digital-logic-counter.md#family-specific-implementation-reference), registry row `fam-digital-logic-counter`, and shared family scope across `var-digital-logic-counter-ripple`, `var-digital-logic-counter-synchronous`, `var-digital-logic-counter-up-down`.
- Exact pin vector: `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power).
- Exact parameter vector: `width`=8 bit with limits 1..4096; `modulus`=256 1 with limits 2..2^width; `direction`=up 1 with limits up or down; `initial_value`=0 1 with limits 0..modulus-1; `clock_to_output`=0 s with limits >=0.
- Declared analyses: `digital-event`, `timing`, `truth-table`; declared package bindings: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Candidate and independent reference must evaluate the same F3 rule: Compact/macro/external tier: bind a pinned model or executable relation that preserves ordered pins and the validated envelope; the governing family relation is: A bounded state value advances, decrements, loads, or resets on declared events with modulus, carry/borrow, enable, and timing rules.
- Exact reference vectors: `GOLD-DIG-COUNTER-NOMINAL`, `GOLD-DIG-COUNTER-BOUNDARY`, `GOLD-DIG-COUNTER-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-digital-logic-counter-shared-f3-validation.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-digital-logic-counter.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One immutable candidate/reference evidence bundle for `GOLD-DIG-COUNTER-NOMINAL`, `GOLD-DIG-COUNTER-BOUNDARY`, `GOLD-DIG-COUNTER-FAILURE` at `F3`, containing exact inputs, expected outputs, tolerance, versions, seed, and raw-result digests.
- Nominal, every declared boundary class, and every applicable failure/diagnostic vector linked to this task's three stable acceptance-test IDs.
- Scope is limited to `CMP-DIGITAL-LOGIC-COUNTER-SHARED-F3-VALIDATION`: shared family scope across `var-digital-logic-counter-ripple`, `var-digital-logic-counter-synchronous`, `var-digital-logic-counter-up-down`, fidelity `F3`, concern `VALIDATION`, and requirements REQ-018, REQ-021, REQ-022, REQ-023, REQ-037, REQ-038.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F3**, and concern **VALIDATION** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power); reject any package map outside `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `width`=8 bit with limits 1..4096; `modulus`=256 1 with limits 2..2^width; `direction`=up 1 with limits up or down; `initial_value`=0 1 with limits 0..modulus-1; `clock_to_output`=0 s with limits >=0.
- Support only `digital-event`, `timing`, `truth-table`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Missing independent reference, wrong seed/version, tolerance breach, nondeterminism, absent raw data, or a silent diagnostic mismatch fails the evidence bundle.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-DIGITAL-LOGIC-COUNTER-SHARED-F3-VALIDATION-NOMINAL`
- `TEST-CMP-DIGITAL-LOGIC-COUNTER-SHARED-F3-VALIDATION-BOUNDARY`
- `TEST-CMP-DIGITAL-LOGIC-COUNTER-SHARED-F3-VALIDATION-FAILURE`

## Acceptance

1. The exact output for `CMP-DIGITAL-LOGIC-COUNTER-SHARED-F3-VALIDATION` exists and is limited to shared family scope across `var-digital-logic-counter-ripple`, `var-digital-logic-counter-synchronous`, `var-digital-logic-counter-up-down`, `F3`, and `VALIDATION`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-digital-logic-counter` and its family specification.
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
