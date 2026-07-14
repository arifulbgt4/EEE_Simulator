# CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F0-DOCS - Document Transmission gate

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-switch-protection-transmission-gate` - Transmission gate |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | DOCS |
| Release | R7 |
| Requirements | REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Publish user and contributor documentation for **Transmission gate** without changing its model, symbol, package, or validation behavior.

## Exact prerequisites

- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-CMOS-F0-CAT`
- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-BIDIRECTIONAL-F0-CAT`
- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F0-SYM`
- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F0-MODEL`
- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F0-VALIDATION`
- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F1-MODEL`
- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F1-VALIDATION`
- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F2-MODEL`
- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F2-VALIDATION`
- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F3-MODEL`
- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F3-VALIDATION`
- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F4-MODEL`
- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F4-VALIDATION`
- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F4-THERMAL`
- `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F4-FAILURE`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-switch-protection-transmission-gate.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-switch-protection-transmission-gate` (Transmission gate); task scope: shared family scope across `var-switch-protection-transmission-gate-cmos`, `var-switch-protection-transmission-gate-bidirectional`; fidelity `F0`; concern `DOCS`.
- Exact pins: `1:P` (passive; electrical/control), `2:N` (passive; electrical/control).
- Exact parameters/defaults/limits: `on_resistance`=10 ohm with limits >=0; `off_resistance`=1e12 ohm with limits >0; `control_threshold`=2.5 V with limits finite; `propagation_delay`=0 s with limits >=0; `charge_injection`=0 C with limits >=0.
- Supported analyses: `dc`, `transient`, `electrothermal`, `fault`.
- Valid package mappings: `pkg-custom-parametric`.
- Golden references: `GOLD-SWP-TRANSMISSION_GATE-NOMINAL`, `GOLD-SWP-TRANSMISSION_GATE-BOUNDARY`, `GOLD-SWP-TRANSMISSION_GATE-FAILURE`.
- Import mappings applicable to this family: `SPICE .model/.subckt`, `Verilog-A/AMS 2023`, `CSV/PWL`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 10-14; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Transmission gate family-specific implementation reference](../../catalog/families/fam-switch-protection-transmission-gate.md#family-specific-implementation-reference), registry row `fam-switch-protection-transmission-gate`, and shared family scope across `var-switch-protection-transmission-gate-cmos`, `var-switch-protection-transmission-gate-bidirectional`.
- Exact pin vector: `1:P` (passive; electrical/control), `2:N` (passive; electrical/control).
- Exact parameter vector: `on_resistance`=10 ohm with limits >=0; `off_resistance`=1e12 ohm with limits >0; `control_threshold`=2.5 V with limits finite; `propagation_delay`=0 s with limits >=0; `charge_injection`=0 C with limits >=0.
- Declared analyses: `dc`, `transient`, `electrothermal`, `fault`; declared package bindings: `pkg-custom-parametric`.
- This documentation concern introduces no equation. It publishes the core behavior supported by completed catalog, symbol, model, validation, thermal, and failure evidence for `fam-switch-protection-transmission-gate`. Import mappings are planned extensions and remain explicitly unavailable/unclaimable until the separate IMPORT card is `Done`.
- Exact reference vectors: `GOLD-SWP-TRANSMISSION_GATE-NOMINAL`, `GOLD-SWP-TRANSMISSION_GATE-BOUNDARY`, `GOLD-SWP-TRANSMISSION_GATE-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-switch-protection-transmission-gate-shared-f0-docs.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-switch-protection-transmission-gate.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One evidence-backed final capability section in `families/fam-switch-protection-transmission-gate.md` for `fam-switch-protection-transmission-gate`, listing exact variants, tiers, analyses, packages, provenance, limitations, and task/test links.
- Synchronized registry, coverage, traceability, task-index, risk, and release-checklist records with no claim beyond completed evidence; each unfinished optional import mapping is labelled planned and unsupported rather than blocking the core documentation release.
- Scope is limited to `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F0-DOCS`: shared family scope across `var-switch-protection-transmission-gate-cmos`, `var-switch-protection-transmission-gate-bidirectional`, fidelity `F0`, concern `DOCS`, and requirements REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037.

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

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `1:P` (passive; electrical/control), `2:N` (passive; electrical/control); reject any package map outside `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `on_resistance`=10 ohm with limits >=0; `off_resistance`=1e12 ohm with limits >0; `control_threshold`=2.5 V with limits finite; `propagation_delay`=0 s with limits >=0; `charge_injection`=0 C with limits >=0.
- Support only `dc`, `transient`, `electrothermal`, `fault`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- A missing required concern/test/result/provenance/limitation link, contradictory capability claim, orphan ID, or premature `Released` state blocks documentation completion. An unfinished optional IMPORT card does not block the core release, but claiming its format does.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F0-DOCS-NOMINAL`
- `TEST-CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F0-DOCS-BOUNDARY`
- `TEST-CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F0-DOCS-FAILURE`

## Acceptance

1. The exact output for `CMP-SWITCH-PROTECTION-TRANSMISSION-GATE-SHARED-F0-DOCS` exists and is limited to shared family scope across `var-switch-protection-transmission-gate-cmos`, `var-switch-protection-transmission-gate-bidirectional`, `F0`, and `DOCS`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-switch-protection-transmission-gate` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
