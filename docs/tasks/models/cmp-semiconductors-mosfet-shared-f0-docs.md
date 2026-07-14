# CMP-SEMICONDUCTORS-MOSFET-SHARED-F0-DOCS - Document MOSFET

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-semiconductors-mosfet` - MOSFET |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | DOCS |
| Release | R4 |
| Requirements | REQ-009, REQ-010, REQ-011, REQ-012, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Publish user and contributor documentation for **MOSFET** without changing its model, symbol, package, or validation behavior.

## Exact prerequisites

- `CMP-SEMICONDUCTORS-MOSFET-N-ENHANCEMENT-F0-CAT`
- `CMP-SEMICONDUCTORS-MOSFET-P-ENHANCEMENT-F0-CAT`
- `CMP-SEMICONDUCTORS-MOSFET-N-DEPLETION-F0-CAT`
- `CMP-SEMICONDUCTORS-MOSFET-P-DEPLETION-F0-CAT`
- `CMP-SEMICONDUCTORS-MOSFET-GAN-POWER-F0-CAT`
- `CMP-SEMICONDUCTORS-MOSFET-SIC-POWER-F0-CAT`
- `CMP-SEMICONDUCTORS-MOSFET-SHARED-F0-SYM`
- `CMP-SEMICONDUCTORS-MOSFET-SHARED-F0-MODEL`
- `CMP-SEMICONDUCTORS-MOSFET-SHARED-F0-VALIDATION`
- `CMP-SEMICONDUCTORS-MOSFET-SHARED-F1-MODEL`
- `CMP-SEMICONDUCTORS-MOSFET-SHARED-F1-VALIDATION`
- `CMP-SEMICONDUCTORS-MOSFET-SHARED-F2-MODEL`
- `CMP-SEMICONDUCTORS-MOSFET-SHARED-F2-VALIDATION`
- `CMP-SEMICONDUCTORS-MOSFET-SHARED-F3-MODEL`
- `CMP-SEMICONDUCTORS-MOSFET-SHARED-F3-VALIDATION`
- `CMP-SEMICONDUCTORS-MOSFET-SHARED-F4-MODEL`
- `CMP-SEMICONDUCTORS-MOSFET-SHARED-F4-VALIDATION`
- `CMP-SEMICONDUCTORS-MOSFET-SHARED-F4-THERMAL`
- `CMP-SEMICONDUCTORS-MOSFET-SHARED-F4-FAILURE`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-semiconductors-mosfet.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-semiconductors-mosfet` (MOSFET); task scope: shared family scope across `var-semiconductors-mosfet-n-enhancement`, `var-semiconductors-mosfet-p-enhancement`, `var-semiconductors-mosfet-n-depletion`, `var-semiconductors-mosfet-p-depletion`, `var-semiconductors-mosfet-gan-power`, `var-semiconductors-mosfet-sic-power`; fidelity `F0`; concern `DOCS`.
- Exact pins: `1:D` (passive; electrical/optical/thermal), `2:G` (input; electrical/optical/thermal), `3:S` (passive; electrical/optical/thermal), `4:B` (optional; electrical/optical/thermal).
- Exact parameters/defaults/limits: `threshold_voltage`=2 V with limits finite; `transconductance_parameter`=1 A/V^2 with limits >0; `channel_modulation`=0 1/V with limits >=0; `on_resistance`=0.1 ohm with limits >=0; `body_diode_saturation_current`=1e-12 A with limits >0; `temperature`=300.15 K with limits >0.
- Supported analyses: `dc`, `ac`, `transient`, `noise`, `electrothermal`.
- Valid package mappings: `pkg-sot-23`, `pkg-to-92`, `pkg-to-220`, `pkg-qfn`, `pkg-custom-parametric`.
- Golden references: `GOLD-SEM-MOSFET-NOMINAL`, `GOLD-SEM-MOSFET-BOUNDARY`, `GOLD-SEM-MOSFET-FAILURE`.
- Import mappings applicable to this family: `SPICE .model/.subckt`, `Verilog-A/AMS 2023`, `CSV/PWL`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 10-15; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [MOSFET family-specific implementation reference](../../catalog/families/fam-semiconductors-mosfet.md#family-specific-implementation-reference), registry row `fam-semiconductors-mosfet`, and shared family scope across `var-semiconductors-mosfet-n-enhancement`, `var-semiconductors-mosfet-p-enhancement`, `var-semiconductors-mosfet-n-depletion`, `var-semiconductors-mosfet-p-depletion`, `var-semiconductors-mosfet-gan-power`, `var-semiconductors-mosfet-sic-power`.
- Exact pin vector: `1:D` (passive; electrical/optical/thermal), `2:G` (input; electrical/optical/thermal), `3:S` (passive; electrical/optical/thermal), `4:B` (optional; electrical/optical/thermal).
- Exact parameter vector: `threshold_voltage`=2 V with limits finite; `transconductance_parameter`=1 A/V^2 with limits >0; `channel_modulation`=0 1/V with limits >=0; `on_resistance`=0.1 ohm with limits >=0; `body_diode_saturation_current`=1e-12 A with limits >0; `temperature`=300.15 K with limits >0.
- Declared analyses: `dc`, `ac`, `transient`, `noise`, `electrothermal`; declared package bindings: `pkg-sot-23`, `pkg-to-92`, `pkg-to-220`, `pkg-qfn`, `pkg-custom-parametric`.
- This documentation concern introduces no equation. It publishes the core behavior supported by completed catalog, symbol, model, validation, thermal, and failure evidence for `fam-semiconductors-mosfet`. Import mappings are planned extensions and remain explicitly unavailable/unclaimable until the separate IMPORT card is `Done`.
- Exact reference vectors: `GOLD-SEM-MOSFET-NOMINAL`, `GOLD-SEM-MOSFET-BOUNDARY`, `GOLD-SEM-MOSFET-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-semiconductors-mosfet-shared-f0-docs.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-semiconductors-mosfet.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One evidence-backed final capability section in `families/fam-semiconductors-mosfet.md` for `fam-semiconductors-mosfet`, listing exact variants, tiers, analyses, packages, provenance, limitations, and task/test links.
- Synchronized registry, coverage, traceability, task-index, risk, and release-checklist records with no claim beyond completed evidence; each unfinished optional import mapping is labelled planned and unsupported rather than blocking the core documentation release.
- Scope is limited to `CMP-SEMICONDUCTORS-MOSFET-SHARED-F0-DOCS`: shared family scope across `var-semiconductors-mosfet-n-enhancement`, `var-semiconductors-mosfet-p-enhancement`, `var-semiconductors-mosfet-n-depletion`, `var-semiconductors-mosfet-p-depletion`, `var-semiconductors-mosfet-gan-power`, `var-semiconductors-mosfet-sic-power`, fidelity `F0`, concern `DOCS`, and requirements REQ-009, REQ-010, REQ-011, REQ-012, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, REQ-038.

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

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `1:D` (passive; electrical/optical/thermal), `2:G` (input; electrical/optical/thermal), `3:S` (passive; electrical/optical/thermal), `4:B` (optional; electrical/optical/thermal); reject any package map outside `pkg-sot-23`, `pkg-to-92`, `pkg-to-220`, `pkg-qfn`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `threshold_voltage`=2 V with limits finite; `transconductance_parameter`=1 A/V^2 with limits >0; `channel_modulation`=0 1/V with limits >=0; `on_resistance`=0.1 ohm with limits >=0; `body_diode_saturation_current`=1e-12 A with limits >0; `temperature`=300.15 K with limits >0.
- Support only `dc`, `ac`, `transient`, `noise`, `electrothermal`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- A missing required concern/test/result/provenance/limitation link, contradictory capability claim, orphan ID, or premature `Released` state blocks documentation completion. An unfinished optional IMPORT card does not block the core release, but claiming its format does.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-SEMICONDUCTORS-MOSFET-SHARED-F0-DOCS-NOMINAL`
- `TEST-CMP-SEMICONDUCTORS-MOSFET-SHARED-F0-DOCS-BOUNDARY`
- `TEST-CMP-SEMICONDUCTORS-MOSFET-SHARED-F0-DOCS-FAILURE`

## Acceptance

1. The exact output for `CMP-SEMICONDUCTORS-MOSFET-SHARED-F0-DOCS` exists and is limited to shared family scope across `var-semiconductors-mosfet-n-enhancement`, `var-semiconductors-mosfet-p-enhancement`, `var-semiconductors-mosfet-n-depletion`, `var-semiconductors-mosfet-p-depletion`, `var-semiconductors-mosfet-gan-power`, `var-semiconductors-mosfet-sic-power`, `F0`, and `DOCS`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-semiconductors-mosfet` and its family specification.
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
