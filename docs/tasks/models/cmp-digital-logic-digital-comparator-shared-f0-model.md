# CMP-DIGITAL-LOGIC-DIGITAL-COMPARATOR-SHARED-F0-MODEL - Implement Digital comparator F0 model

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-digital-logic-digital-comparator` - Digital comparator |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | MODEL |
| Release | R5 |
| Requirements | REQ-018, REQ-021, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Implement one model tier, **F0**, for **Digital comparator** using the family equations/behavior and no higher-fidelity claims.

## Exact prerequisites

- `CMP-DIGITAL-LOGIC-DIGITAL-COMPARATOR-MAGNITUDE-F0-CAT`
- `CMP-DIGITAL-LOGIC-DIGITAL-COMPARATOR-PARITY-F0-CAT`
- `PLAT-NET-008`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-digital-logic-digital-comparator.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-digital-logic-digital-comparator` (Digital comparator); task scope: shared family scope across `var-digital-logic-digital-comparator-magnitude`, `var-digital-logic-digital-comparator-parity`; fidelity `F0`; concern `MODEL`.
- Exact pins: `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power).
- Exact parameters/defaults/limits: `width`=1 bit with limits 1..4096; `signed_mode`=false 1 with limits true or false; `comparison`=magnitude 1 with limits magnitude, equality, or parity; `propagation_delay`=0 s with limits >=0.
- Supported analyses: `digital-event`, `timing`, `truth-table`.
- Valid package mappings: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Golden references: `GOLD-DIG-DIGITAL_COMPARATOR-NOMINAL`, `GOLD-DIG-DIGITAL_COMPARATOR-BOUNDARY`, `GOLD-DIG-DIGITAL_COMPARATOR-FAILURE`.
- Import mappings applicable to this family: `Verilog/SystemVerilog`, `VCD/FST`, `HEX/ELF`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 21-26; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Digital comparator family-specific implementation reference](../../catalog/families/fam-digital-logic-digital-comparator.md#family-specific-implementation-reference), registry row `fam-digital-logic-digital-comparator`, and shared family scope across `var-digital-logic-digital-comparator-magnitude`, `var-digital-logic-digital-comparator-parity`.
- Exact pin vector: `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power).
- Exact parameter vector: `width`=1 bit with limits 1..4096; `signed_mode`=false 1 with limits true or false; `comparison`=magnitude 1 with limits magnitude, equality, or parity; `propagation_delay`=0 s with limits >=0.
- Declared analyses: `digital-event`, `timing`, `truth-table`; declared package bindings: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Exact F0 execution rule: Connectivity-only: validate declared pins, domains, width/direction, hierarchy, and package mapping; do not claim numerical behavior. Family baseline: The selected signed/unsigned equality or magnitude relation maps fixed-width inputs to exact comparison outputs with X propagation.
- Exact reference vectors: `GOLD-DIG-DIGITAL_COMPARATOR-NOMINAL`, `GOLD-DIG-DIGITAL_COMPARATOR-BOUNDARY`, `GOLD-DIG-DIGITAL_COMPARATOR-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-digital-logic-digital-comparator-shared-f0-model.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-digital-logic-digital-comparator.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One `ModelBinding` for `fam-digital-logic-digital-comparator` at `F0` implementing the exact tier rule above, its initialization/state/stamp/event behavior, power reporting, and structured diagnostics.
- One `AnalysisCapability` result for each of `digital-event`, `timing`, `truth-table`, with every unlisted analysis rejected rather than approximated.
- Scope is limited to `CMP-DIGITAL-LOGIC-DIGITAL-COMPARATOR-SHARED-F0-MODEL`: shared family scope across `var-digital-logic-digital-comparator-magnitude`, `var-digital-logic-digital-comparator-parity`, fidelity `F0`, concern `MODEL`, and requirements REQ-018, REQ-021, REQ-022, REQ-023, REQ-037, REQ-038.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F0**, and concern **MODEL** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power); reject any package map outside `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `width`=1 bit with limits 1..4096; `signed_mode`=false 1 with limits true or false; `comparison`=magnitude 1 with limits magnitude, equality, or parity; `propagation_delay`=0 s with limits >=0.
- Support only `digital-event`, `timing`, `truth-table`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Initialization, limiting, discontinuity, convergence/event ordering, cancellation, overflow/NaN, and out-of-envelope behavior must follow the `F0` rule without silent fallback.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-DIGITAL-LOGIC-DIGITAL-COMPARATOR-SHARED-F0-MODEL-NOMINAL`
- `TEST-CMP-DIGITAL-LOGIC-DIGITAL-COMPARATOR-SHARED-F0-MODEL-BOUNDARY`
- `TEST-CMP-DIGITAL-LOGIC-DIGITAL-COMPARATOR-SHARED-F0-MODEL-FAILURE`

## Acceptance

1. The exact output for `CMP-DIGITAL-LOGIC-DIGITAL-COMPARATOR-SHARED-F0-MODEL` exists and is limited to shared family scope across `var-digital-logic-digital-comparator-magnitude`, `var-digital-logic-digital-comparator-parity`, `F0`, and `MODEL`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-digital-logic-digital-comparator` and its family specification.
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
