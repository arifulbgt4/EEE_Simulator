# CMP-DIGITAL-LOGIC-LATCH-D-F0-CAT - Specify D catalog preset

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-digital-logic-latch` - Latch |
| Variant | `var-digital-logic-latch-d` - D |
| Fidelity | F0 |
| Concern | CAT |
| Release | R5 |
| Requirements | REQ-018, REQ-021, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Create the complete, immutable catalog definition for **D** without implementing a different fidelity or sibling preset.

## Exact prerequisites

- `PLAT-GOV-001`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-digital-logic-latch.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-digital-logic-latch` (Latch); task scope: variant `var-digital-logic-latch-d` (D); fidelity `F0`; concern `CAT`.
- Exact pins: `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power).
- Exact parameters/defaults/limits: `width`=1 bit with limits 1..4096; `initial_state`=X 1 with limits width-matched 0/1/X vector; `propagation_delay`=0 s with limits >=0; `setup_time`=0 s with limits >=0; `hold_time`=0 s with limits >=0.
- Supported analyses: `digital-event`, `timing`, `truth-table`.
- Valid package mappings: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Golden references: `GOLD-DIG-LATCH-NOMINAL`, `GOLD-DIG-LATCH-BOUNDARY`, `GOLD-DIG-LATCH-FAILURE`.
- Import mappings applicable to this family: `Verilog/SystemVerilog`, `VCD/FST`, `HEX/ELF`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 21-26; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.
- Selected variant tiers: `F0`, `F2`, `F3`; release target: Realistic Electronics MVP; package references: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Latch family-specific implementation reference](../../catalog/families/fam-digital-logic-latch.md#family-specific-implementation-reference), registry row `fam-digital-logic-latch`, and variant `var-digital-logic-latch-d` (D).
- Exact pin vector: `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power).
- Exact parameter vector: `width`=1 bit with limits 1..4096; `initial_state`=X 1 with limits width-matched 0/1/X vector; `propagation_delay`=0 s with limits >=0; `setup_time`=0 s with limits >=0; `hold_time`=0 s with limits >=0.
- Declared analyses: `digital-event`, `timing`, `truth-table`; declared package bindings: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- This catalog concern has no numerical equation. It freezes the selected variant's inherited/overridden fields against the governing family rule: The latch updates stored state while enable is active and holds it otherwise, with explicit illegal SR, delay, setup/hold, and metastability diagnostics.
- Exact reference vectors: `GOLD-DIG-LATCH-NOMINAL`, `GOLD-DIG-LATCH-BOUNDARY`, `GOLD-DIG-LATCH-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-digital-logic-latch-d-f0-cat.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-digital-logic-latch.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One normalized `ComponentVariant` record for variant `var-digital-logic-latch-d` (D), retaining stable ID, aliases, inherited pins/parameters, declared tier list, package candidates, release target, provenance, and limitations.
- A field-by-field registry/family consistency result and structured rejection evidence for duplicate ID, invalid override, missing package, or unsupported tier.
- Scope is limited to `CMP-DIGITAL-LOGIC-LATCH-D-F0-CAT`: variant `var-digital-logic-latch-d` (D), fidelity `F0`, concern `CAT`, and requirements REQ-018, REQ-021, REQ-022, REQ-023, REQ-037, REQ-038.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family and one variant, fidelity **F0**, and concern **CAT** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power); reject any package map outside `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `width`=1 bit with limits 1..4096; `initial_state`=X 1 with limits width-matched 0/1/X vector; `propagation_delay`=0 s with limits >=0; `setup_time`=0 s with limits >=0; `hold_time`=0 s with limits >=0.
- Support only `digital-event`, `timing`, `truth-table`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Duplicate stable IDs, incompatible inherited overrides, undeclared package/tier references, or absent provenance block publication of the variant record.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-DIGITAL-LOGIC-LATCH-D-F0-CAT-NOMINAL`
- `TEST-CMP-DIGITAL-LOGIC-LATCH-D-F0-CAT-BOUNDARY`
- `TEST-CMP-DIGITAL-LOGIC-LATCH-D-F0-CAT-FAILURE`

## Acceptance

1. The exact output for `CMP-DIGITAL-LOGIC-LATCH-D-F0-CAT` exists and is limited to variant `var-digital-logic-latch-d` (D), `F0`, and `CAT`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-digital-logic-latch` and its family specification.
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
