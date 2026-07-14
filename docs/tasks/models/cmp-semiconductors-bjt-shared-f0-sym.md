# CMP-SEMICONDUCTORS-BJT-SHARED-F0-SYM - Create symbol and physical representation for Bipolar junction transistor

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-semiconductors-bjt` - Bipolar junction transistor |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | SYM |
| Release | R3 |
| Requirements | REQ-009, REQ-010, REQ-011, REQ-012, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Create original, electrically unambiguous schematic and recognizable physical representations for **Bipolar junction transistor**, including accessible orientation/polarity cues and reusable package mapping.

## Exact prerequisites

- `CMP-SEMICONDUCTORS-BJT-NPN-F0-CAT`
- `CMP-SEMICONDUCTORS-BJT-PNP-F0-CAT`
- `CMP-SEMICONDUCTORS-BJT-DARLINGTON-NPN-F0-CAT`
- `CMP-SEMICONDUCTORS-BJT-DARLINGTON-PNP-F0-CAT`
- `PLAT-SYM-007`
- `CMP-PACKAGE-SOT-23-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-TO-92-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-TO-220-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-QFN-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-CUSTOM-PARAMETRIC-TEMPLATE-F0-VALIDATION`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-semiconductors-bjt.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-semiconductors-bjt` (Bipolar junction transistor); task scope: shared family scope across `var-semiconductors-bjt-npn`, `var-semiconductors-bjt-pnp`, `var-semiconductors-bjt-darlington-npn`, `var-semiconductors-bjt-darlington-pnp`; fidelity `F0`; concern `SYM`.
- Exact pins: `1:C` (passive; electrical/optical/thermal), `2:B` (input; electrical/optical/thermal), `3:E` (passive; electrical/optical/thermal).
- Exact parameters/defaults/limits: `saturation_current`=1e-15 A with limits >0; `forward_beta`=100 1 with limits >0; `reverse_beta`=1 1 with limits >0; `early_voltage`=100 V with limits >0; `area_multiplier`=1 1 with limits >0; `temperature`=300.15 K with limits >0.
- Supported analyses: `dc`, `ac`, `transient`, `noise`, `electrothermal`.
- Valid package mappings: `pkg-sot-23`, `pkg-to-92`, `pkg-to-220`, `pkg-qfn`, `pkg-custom-parametric`.
- Golden references: `GOLD-SEM-BJT-NOMINAL`, `GOLD-SEM-BJT-BOUNDARY`, `GOLD-SEM-BJT-FAILURE`.
- Import mappings applicable to this family: `SPICE .model/.subckt`, `Verilog-A/AMS 2023`, `CSV/PWL`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 10-15; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Bipolar junction transistor family-specific implementation reference](../../catalog/families/fam-semiconductors-bjt.md#family-specific-implementation-reference), registry row `fam-semiconductors-bjt`, and shared family scope across `var-semiconductors-bjt-npn`, `var-semiconductors-bjt-pnp`, `var-semiconductors-bjt-darlington-npn`, `var-semiconductors-bjt-darlington-pnp`.
- Exact pin vector: `1:C` (passive; electrical/optical/thermal), `2:B` (input; electrical/optical/thermal), `3:E` (passive; electrical/optical/thermal).
- Exact parameter vector: `saturation_current`=1e-15 A with limits >0; `forward_beta`=100 1 with limits >0; `reverse_beta`=1 1 with limits >0; `early_voltage`=100 V with limits >0; `area_multiplier`=1 1 with limits >0; `temperature`=300.15 K with limits >0.
- Declared analyses: `dc`, `ac`, `transient`, `noise`, `electrothermal`; declared package bindings: `pkg-sot-23`, `pkg-to-92`, `pkg-to-220`, `pkg-qfn`, `pkg-custom-parametric`.
- This symbol/appearance concern has no electrical equation. It preserves the exact pin vector and family rule while implementing original scalable geometry and explicit package maps.
- Exact reference vectors: `GOLD-SEM-BJT-NOMINAL`, `GOLD-SEM-BJT-BOUNDARY`, `GOLD-SEM-BJT-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-semiconductors-bjt-shared-f0-sym.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-semiconductors-bjt.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One original `sym-semiconductors-bjt` schematic definition with anchors for `1:C` (passive; electrical/optical/thermal), `2:B` (input; electrical/optical/thermal), `3:E` (passive; electrical/optical/thermal).
- One scalable physical-view binding for every declared package `pkg-sot-23`, `pkg-to-92`, `pkg-to-220`, `pkg-qfn`, `pkg-custom-parametric`, including non-color orientation/polarity/pin-one cues, accessible text, and logical-to-package pin-equivalence evidence.
- Scope is limited to `CMP-SEMICONDUCTORS-BJT-SHARED-F0-SYM`: shared family scope across `var-semiconductors-bjt-npn`, `var-semiconductors-bjt-pnp`, `var-semiconductors-bjt-darlington-npn`, `var-semiconductors-bjt-darlington-pnp`, fidelity `F0`, concern `SYM`, and requirements REQ-009, REQ-010, REQ-011, REQ-012, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, REQ-038.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F0**, and concern **SYM** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `1:C` (passive; electrical/optical/thermal), `2:B` (input; electrical/optical/thermal), `3:E` (passive; electrical/optical/thermal); reject any package map outside `pkg-sot-23`, `pkg-to-92`, `pkg-to-220`, `pkg-qfn`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `saturation_current`=1e-15 A with limits >0; `forward_beta`=100 1 with limits >0; `reverse_beta`=1 1 with limits >0; `early_voltage`=100 V with limits >0; `area_multiplier`=1 1 with limits >0; `temperature`=300.15 K with limits >0.
- Support only `dc`, `ac`, `transient`, `noise`, `electrothermal`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Rotation, mirroring, LOD, high contrast, and view switching must preserve pin identity and selection; invisible orientation/polarity or color-only meaning fails validation.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-SEMICONDUCTORS-BJT-SHARED-F0-SYM-NOMINAL`
- `TEST-CMP-SEMICONDUCTORS-BJT-SHARED-F0-SYM-BOUNDARY`
- `TEST-CMP-SEMICONDUCTORS-BJT-SHARED-F0-SYM-FAILURE`

## Acceptance

1. The exact output for `CMP-SEMICONDUCTORS-BJT-SHARED-F0-SYM` exists and is limited to shared family scope across `var-semiconductors-bjt-npn`, `var-semiconductors-bjt-pnp`, `var-semiconductors-bjt-darlington-npn`, `var-semiconductors-bjt-darlington-pnp`, `F0`, and `SYM`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-semiconductors-bjt` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-009, REQ-010, REQ-011, REQ-012, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, REQ-038, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
