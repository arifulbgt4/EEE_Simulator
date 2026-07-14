# CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-SHARED-F0-DOCS - Document RF mixer and oscillator

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-rf-communications-rf-mixer-oscillator` - RF mixer and oscillator |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | DOCS |
| Release | R7 |
| Requirements | REQ-011, REQ-012, REQ-024, REQ-028, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Publish user and contributor documentation for **RF mixer and oscillator** without changing its model, symbol, package, or validation behavior.

## Exact prerequisites

- `CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-MIXER-F1-CAT`
- `CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-LOCAL-OSCILLATOR-F1-CAT`
- `CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-RF-VCO-F1-CAT`
- `CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-SHARED-F0-SYM`
- `CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-SHARED-F1-MODEL`
- `CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-SHARED-F1-VALIDATION`
- `CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-SHARED-F2-MODEL`
- `CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-SHARED-F2-VALIDATION`
- `CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-SHARED-F3-MODEL`
- `CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-SHARED-F3-VALIDATION`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-rf-communications-rf-mixer-oscillator.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-rf-communications-rf-mixer-oscillator` (RF mixer and oscillator); task scope: shared family scope across `var-rf-communications-rf-mixer-oscillator-mixer`, `var-rf-communications-rf-mixer-oscillator-local-oscillator`, `var-rf-communications-rf-mixer-oscillator-rf-vco`; fidelity `F0`; concern `DOCS`.
- Exact pins: `IN:RF_IN` (passive; rf/electrical/communications), `OUT:RF_OUT` (passive; rf/electrical/communications), `GND:GROUND` (reference; rf/electrical/communications).
- Exact parameters/defaults/limits: `rf_frequency`=1e9 Hz with limits >0; `lo_frequency`=900e6 Hz with limits >0; `if_frequency`=100e6 Hz with limits >=0; `conversion_gain`=1 1 with limits >=0; `phase_noise`=0 1/Hz with limits >=0.
- Supported analyses: `ac`, `s-parameter`, `noise`, `modulation`.
- Valid package mappings: `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Golden references: `GOLD-RFC-RF_MIXER_OSCILLATOR-NOMINAL`, `GOLD-RFC-RF_MIXER_OSCILLATOR-BOUNDARY`, `GOLD-RFC-RF_MIXER_OSCILLATOR-FAILURE`.
- Import mappings applicable to this family: `Touchstone 2.1`, `IBIS 8.0`, `CSV`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 28-35; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [RF mixer and oscillator family-specific implementation reference](../../catalog/families/fam-rf-communications-rf-mixer-oscillator.md#family-specific-implementation-reference), registry row `fam-rf-communications-rf-mixer-oscillator`, and shared family scope across `var-rf-communications-rf-mixer-oscillator-mixer`, `var-rf-communications-rf-mixer-oscillator-local-oscillator`, `var-rf-communications-rf-mixer-oscillator-rf-vco`.
- Exact pin vector: `IN:RF_IN` (passive; rf/electrical/communications), `OUT:RF_OUT` (passive; rf/electrical/communications), `GND:GROUND` (reference; rf/electrical/communications).
- Exact parameter vector: `rf_frequency`=1e9 Hz with limits >0; `lo_frequency`=900e6 Hz with limits >0; `if_frequency`=100e6 Hz with limits >=0; `conversion_gain`=1 1 with limits >=0; `phase_noise`=0 1/Hz with limits >=0.
- Declared analyses: `ac`, `s-parameter`, `noise`, `modulation`; declared package bindings: `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- This documentation concern introduces no equation. It publishes the core behavior supported by completed catalog, symbol, model, validation, thermal, and failure evidence for `fam-rf-communications-rf-mixer-oscillator`. Import mappings are planned extensions and remain explicitly unavailable/unclaimable until the separate IMPORT card is `Done`.
- Exact reference vectors: `GOLD-RFC-RF_MIXER_OSCILLATOR-NOMINAL`, `GOLD-RFC-RF_MIXER_OSCILLATOR-BOUNDARY`, `GOLD-RFC-RF_MIXER_OSCILLATOR-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-rf-communications-rf-mixer-oscillator-shared-f0-docs.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-rf-communications-rf-mixer-oscillator.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One evidence-backed final capability section in `families/fam-rf-communications-rf-mixer-oscillator.md` for `fam-rf-communications-rf-mixer-oscillator`, listing exact variants, tiers, analyses, packages, provenance, limitations, and task/test links.
- Synchronized registry, coverage, traceability, task-index, risk, and release-checklist records with no claim beyond completed evidence; each unfinished optional import mapping is labelled planned and unsupported rather than blocking the core documentation release.
- Scope is limited to `CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-SHARED-F0-DOCS`: shared family scope across `var-rf-communications-rf-mixer-oscillator-mixer`, `var-rf-communications-rf-mixer-oscillator-local-oscillator`, `var-rf-communications-rf-mixer-oscillator-rf-vco`, fidelity `F0`, concern `DOCS`, and requirements REQ-011, REQ-012, REQ-024, REQ-028, REQ-022, REQ-023, REQ-037, REQ-038.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F0**, and concern **DOCS** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `IN:RF_IN` (passive; rf/electrical/communications), `OUT:RF_OUT` (passive; rf/electrical/communications), `GND:GROUND` (reference; rf/electrical/communications); reject any package map outside `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `rf_frequency`=1e9 Hz with limits >0; `lo_frequency`=900e6 Hz with limits >0; `if_frequency`=100e6 Hz with limits >=0; `conversion_gain`=1 1 with limits >=0; `phase_noise`=0 1/Hz with limits >=0.
- Support only `ac`, `s-parameter`, `noise`, `modulation`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- A missing required concern/test/result/provenance/limitation link, contradictory capability claim, orphan ID, or premature `Released` state blocks documentation completion. An unfinished optional IMPORT card does not block the core release, but claiming its format does.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-SHARED-F0-DOCS-NOMINAL`
- `TEST-CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-SHARED-F0-DOCS-BOUNDARY`
- `TEST-CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-SHARED-F0-DOCS-FAILURE`

## Acceptance

1. The exact output for `CMP-RF-COMMUNICATIONS-RF-MIXER-OSCILLATOR-SHARED-F0-DOCS` exists and is limited to shared family scope across `var-rf-communications-rf-mixer-oscillator-mixer`, `var-rf-communications-rf-mixer-oscillator-local-oscillator`, `var-rf-communications-rf-mixer-oscillator-rf-vco`, `F0`, and `DOCS`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-rf-communications-rf-mixer-oscillator` and its family specification.
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
