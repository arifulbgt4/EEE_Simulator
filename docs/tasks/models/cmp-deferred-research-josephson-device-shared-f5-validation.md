# CMP-DEFERRED-RESEARCH-JOSEPHSON-DEVICE-SHARED-F5-VALIDATION - Validate Josephson junction device F5

## Metadata

| Field | Value |
|---|---|
| Status | Deferred |
| Family | `fam-deferred-research-josephson-device` - Josephson junction device |
| Variant | `shared` |
| Fidelity | F5 |
| Concern | VALIDATION |
| Release | R13 |
| Requirements | REQ-001, REQ-002, REQ-022, REQ-023, REQ-028, REQ-034, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Produce independent validation evidence for **Josephson junction device** at **F5** without modifying the model under test.

## Exact prerequisites

- `CMP-DEFERRED-RESEARCH-JOSEPHSON-DEVICE-SHARED-F5-MODEL`
- `PLAT-QA-001`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-deferred-research-josephson-device.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-deferred-research-josephson-device` (Josephson junction device); task scope: shared family scope across `var-deferred-research-josephson-device-josephson-junction`; fidelity `F5`; concern `VALIDATION`.
- Exact pins: `1..N:TERMINALS` (multiphysics; research/multiphysics).
- Exact parameters/defaults/limits: `research_model_id`=unassigned 1 with limits registered identifier before Ready; `engine_digest`=unset 1 with limits valid reviewed digest before Ready; `configuration_digest`=unset 1 with limits valid digest before Ready; `resource_limit`=60 s with limits >0.
- Supported analyses: `research-only`.
- Valid package mappings: `pkg-custom-parametric`.
- Golden references: `GOLD-RSH-JOSEPHSON_DEVICE-NOMINAL`, `GOLD-RSH-JOSEPHSON_DEVICE-BOUNDARY`, `GOLD-RSH-JOSEPHSON_DEVICE-FAILURE`.
- Import mappings applicable to this family: `SPICE .model/.subckt`, `Verilog-A/AMS 2023`, `CSV/PWL`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 34-41; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Josephson junction device family-specific implementation reference](../../catalog/families/fam-deferred-research-josephson-device.md#family-specific-implementation-reference), registry row `fam-deferred-research-josephson-device`, and shared family scope across `var-deferred-research-josephson-device-josephson-junction`.
- Exact pin vector: `1..N:TERMINALS` (multiphysics; research/multiphysics).
- Exact parameter vector: `research_model_id`=unassigned 1 with limits registered identifier before Ready; `engine_digest`=unset 1 with limits valid reviewed digest before Ready; `configuration_digest`=unset 1 with limits valid digest before Ready; `resource_limit`=60 s with limits >0.
- Declared analyses: `research-only`; declared package bindings: `pkg-custom-parametric`.
- Candidate and independent reference must evaluate the same F5 rule: Research tier: execute only through the declared isolated, pinned research adapter and retain its full configuration/provenance; baseline: F5 behavior uses a pinned Josephson phase/current/voltage relation and external research solver with units, initialization, limits, and provenance.
- Exact reference vectors: `GOLD-RSH-JOSEPHSON_DEVICE-NOMINAL`, `GOLD-RSH-JOSEPHSON_DEVICE-BOUNDARY`, `GOLD-RSH-JOSEPHSON_DEVICE-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-deferred-research-josephson-device-shared-f5-validation.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-deferred-research-josephson-device.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One immutable candidate/reference evidence bundle for `GOLD-RSH-JOSEPHSON_DEVICE-NOMINAL`, `GOLD-RSH-JOSEPHSON_DEVICE-BOUNDARY`, `GOLD-RSH-JOSEPHSON_DEVICE-FAILURE` at `F5`, containing exact inputs, expected outputs, tolerance, versions, seed, and raw-result digests.
- Nominal, every declared boundary class, and every applicable failure/diagnostic vector linked to this task's three stable acceptance-test IDs.
- Scope is limited to `CMP-DEFERRED-RESEARCH-JOSEPHSON-DEVICE-SHARED-F5-VALIDATION`: shared family scope across `var-deferred-research-josephson-device-josephson-junction`, fidelity `F5`, concern `VALIDATION`, and requirements REQ-001, REQ-002, REQ-022, REQ-023, REQ-028, REQ-034, REQ-037, REQ-038.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F5**, and concern **VALIDATION** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `1..N:TERMINALS` (multiphysics; research/multiphysics); reject any package map outside `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `research_model_id`=unassigned 1 with limits registered identifier before Ready; `engine_digest`=unset 1 with limits valid reviewed digest before Ready; `configuration_digest`=unset 1 with limits valid digest before Ready; `resource_limit`=60 s with limits >0.
- Support only `research-only`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Missing independent reference, wrong seed/version, tolerance breach, nondeterminism, absent raw data, or a silent diagnostic mismatch fails the evidence bundle.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-DEFERRED-RESEARCH-JOSEPHSON-DEVICE-SHARED-F5-VALIDATION-NOMINAL`
- `TEST-CMP-DEFERRED-RESEARCH-JOSEPHSON-DEVICE-SHARED-F5-VALIDATION-BOUNDARY`
- `TEST-CMP-DEFERRED-RESEARCH-JOSEPHSON-DEVICE-SHARED-F5-VALIDATION-FAILURE`

## Acceptance

1. The exact output for `CMP-DEFERRED-RESEARCH-JOSEPHSON-DEVICE-SHARED-F5-VALIDATION` exists and is limited to shared family scope across `var-deferred-research-josephson-device-josephson-junction`, `F5`, and `VALIDATION`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-deferred-research-josephson-device` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-001, REQ-002, REQ-022, REQ-023, REQ-028, REQ-034, REQ-037, REQ-038, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
