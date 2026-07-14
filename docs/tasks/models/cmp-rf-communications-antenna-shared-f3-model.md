# CMP-RF-COMMUNICATIONS-ANTENNA-SHARED-F3-MODEL - Implement Antenna F3 model

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-rf-communications-antenna` - Antenna |
| Variant | `shared` |
| Fidelity | F3 |
| Concern | MODEL |
| Release | R7 |
| Requirements | REQ-011, REQ-012, REQ-024, REQ-028, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Implement one model tier, **F3**, for **Antenna** using the family equations/behavior and no higher-fidelity claims.

## Exact prerequisites

- `CMP-RF-COMMUNICATIONS-ANTENNA-DIPOLE-F1-CAT`
- `CMP-RF-COMMUNICATIONS-ANTENNA-MONOPOLE-F1-CAT`
- `CMP-RF-COMMUNICATIONS-ANTENNA-PATCH-F1-CAT`
- `CMP-RF-COMMUNICATIONS-ANTENNA-ARRAY-F1-CAT`
- `CMP-RF-COMMUNICATIONS-ANTENNA-SHARED-F2-MODEL`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-rf-communications-antenna.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-rf-communications-antenna` (Antenna); task scope: shared family scope across `var-rf-communications-antenna-dipole`, `var-rf-communications-antenna-monopole`, `var-rf-communications-antenna-patch`, `var-rf-communications-antenna-array`; fidelity `F3`; concern `MODEL`.
- Exact pins: `IN:RF_IN` (passive; rf/electrical/communications), `OUT:RF_OUT` (passive; rf/electrical/communications), `GND:GROUND` (reference; rf/electrical/communications).
- Exact parameters/defaults/limits: `reference_impedance`=50 ohm with limits >0; `center_frequency`=1e9 Hz with limits >0; `bandwidth`=100e6 Hz with limits >0; `peak_gain`=1 1 with limits >=0; `radiation_efficiency`=0.8 1 with limits 0..1.
- Supported analyses: `ac`, `s-parameter`, `noise`, `modulation`.
- Valid package mappings: `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Golden references: `GOLD-RFC-ANTENNA-NOMINAL`, `GOLD-RFC-ANTENNA-BOUNDARY`, `GOLD-RFC-ANTENNA-FAILURE`.
- Import mappings applicable to this family: `Touchstone 2.1`, `IBIS 8.0`, `CSV`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 28-35; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Antenna family-specific implementation reference](../../catalog/families/fam-rf-communications-antenna.md#family-specific-implementation-reference), registry row `fam-rf-communications-antenna`, and shared family scope across `var-rf-communications-antenna-dipole`, `var-rf-communications-antenna-monopole`, `var-rf-communications-antenna-patch`, `var-rf-communications-antenna-array`.
- Exact pin vector: `IN:RF_IN` (passive; rf/electrical/communications), `OUT:RF_OUT` (passive; rf/electrical/communications), `GND:GROUND` (reference; rf/electrical/communications).
- Exact parameter vector: `reference_impedance`=50 ohm with limits >0; `center_frequency`=1e9 Hz with limits >0; `bandwidth`=100e6 Hz with limits >0; `peak_gain`=1 1 with limits >=0; `radiation_efficiency`=0.8 1 with limits 0..1.
- Declared analyses: `ac`, `s-parameter`, `noise`, `modulation`; declared package bindings: `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Exact F3 execution rule: Compact/macro/external tier: bind a pinned model or executable relation that preserves ordered pins and the validated envelope; the governing family relation is: The antenna uses a declared port impedance/S-parameter plus radiation gain/pattern/polarization/efficiency profile over its validated frequency envelope.
- Exact reference vectors: `GOLD-RFC-ANTENNA-NOMINAL`, `GOLD-RFC-ANTENNA-BOUNDARY`, `GOLD-RFC-ANTENNA-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-rf-communications-antenna-shared-f3-model.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-rf-communications-antenna.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One `ModelBinding` for `fam-rf-communications-antenna` at `F3` implementing the exact tier rule above, its initialization/state/stamp/event behavior, power reporting, and structured diagnostics.
- One `AnalysisCapability` result for each of `ac`, `s-parameter`, `noise`, `modulation`, with every unlisted analysis rejected rather than approximated.
- Scope is limited to `CMP-RF-COMMUNICATIONS-ANTENNA-SHARED-F3-MODEL`: shared family scope across `var-rf-communications-antenna-dipole`, `var-rf-communications-antenna-monopole`, `var-rf-communications-antenna-patch`, `var-rf-communications-antenna-array`, fidelity `F3`, concern `MODEL`, and requirements REQ-011, REQ-012, REQ-024, REQ-028, REQ-022, REQ-023, REQ-037, REQ-038.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F3**, and concern **MODEL** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `IN:RF_IN` (passive; rf/electrical/communications), `OUT:RF_OUT` (passive; rf/electrical/communications), `GND:GROUND` (reference; rf/electrical/communications); reject any package map outside `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `reference_impedance`=50 ohm with limits >0; `center_frequency`=1e9 Hz with limits >0; `bandwidth`=100e6 Hz with limits >0; `peak_gain`=1 1 with limits >=0; `radiation_efficiency`=0.8 1 with limits 0..1.
- Support only `ac`, `s-parameter`, `noise`, `modulation`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Initialization, limiting, discontinuity, convergence/event ordering, cancellation, overflow/NaN, and out-of-envelope behavior must follow the `F3` rule without silent fallback.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-RF-COMMUNICATIONS-ANTENNA-SHARED-F3-MODEL-NOMINAL`
- `TEST-CMP-RF-COMMUNICATIONS-ANTENNA-SHARED-F3-MODEL-BOUNDARY`
- `TEST-CMP-RF-COMMUNICATIONS-ANTENNA-SHARED-F3-MODEL-FAILURE`

## Acceptance

1. The exact output for `CMP-RF-COMMUNICATIONS-ANTENNA-SHARED-F3-MODEL` exists and is limited to shared family scope across `var-rf-communications-antenna-dipole`, `var-rf-communications-antenna-monopole`, `var-rf-communications-antenna-patch`, `var-rf-communications-antenna-array`, `F3`, and `MODEL`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-rf-communications-antenna` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-011, REQ-012, REQ-024, REQ-028, REQ-022, REQ-023, REQ-037, REQ-038, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
