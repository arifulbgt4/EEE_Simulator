# CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-SHARED-F0-DOCS - Document Impedance and RF instrument

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-instruments-impedance-rf-instrument` - Impedance and RF instrument |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | DOCS |
| Release | R2 |
| Requirements | REQ-007, REQ-021, REQ-022, REQ-023, REQ-034, REQ-037 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Publish user and contributor documentation for **Impedance and RF instrument** without changing its model, symbol, package, or validation behavior.

## Exact prerequisites

- `CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-LCR-METER-F0-CAT`
- `CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-SPECTRUM-ANALYZER-F0-CAT`
- `CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-NETWORK-ANALYZER-F0-CAT`
- `CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-SHARED-F0-SYM`
- `CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-SHARED-F0-MODEL`
- `CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-SHARED-F0-VALIDATION`
- `CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-SHARED-F1-MODEL`
- `CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-SHARED-F1-VALIDATION`
- `CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-SHARED-F2-MODEL`
- `CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-SHARED-F2-VALIDATION`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-instruments-impedance-rf-instrument.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-instruments-impedance-rf-instrument` (Impedance and RF instrument); task scope: shared family scope across `var-instruments-impedance-rf-instrument-lcr-meter`, `var-instruments-impedance-rf-instrument-spectrum-analyzer`, `var-instruments-impedance-rf-instrument-network-analyzer`; fidelity `F0`; concern `DOCS`.
- Exact pins: `CH+:CHANNEL+` (input; measurement/electrical), `CH-:CHANNEL-` (input; measurement/electrical), `COM:COMMON` (reference; measurement/electrical).
- Exact parameters/defaults/limits: `port_count`=2 1 with limits 1..64; `start_frequency`=10 Hz with limits >=0; `stop_frequency`=1e9 Hz with limits >start_frequency; `point_count`=201 1 with limits 2..1000000; `reference_impedance`=50 ohm with limits >0; `stimulus_level`=0.1 V with limits >=0.
- Supported analyses: `measurement`, `dc`, `ac`, `transient`, `digital`.
- Valid package mappings: `pkg-virtual`.
- Golden references: `GOLD-INS-IMPEDANCE_RF_INSTRUMENT-NOMINAL`, `GOLD-INS-IMPEDANCE_RF_INSTRUMENT-BOUNDARY`, `GOLD-INS-IMPEDANCE_RF_INSTRUMENT-FAILURE`.
- Import mappings applicable to this family: `SPICE .model/.subckt`, `Verilog-A/AMS 2023`, `CSV/PWL`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 20-23; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Impedance and RF instrument family-specific implementation reference](../../catalog/families/fam-instruments-impedance-rf-instrument.md#family-specific-implementation-reference), registry row `fam-instruments-impedance-rf-instrument`, and shared family scope across `var-instruments-impedance-rf-instrument-lcr-meter`, `var-instruments-impedance-rf-instrument-spectrum-analyzer`, `var-instruments-impedance-rf-instrument-network-analyzer`.
- Exact pin vector: `CH+:CHANNEL+` (input; measurement/electrical), `CH-:CHANNEL-` (input; measurement/electrical), `COM:COMMON` (reference; measurement/electrical).
- Exact parameter vector: `port_count`=2 1 with limits 1..64; `start_frequency`=10 Hz with limits >=0; `stop_frequency`=1e9 Hz with limits >start_frequency; `point_count`=201 1 with limits 2..1000000; `reference_impedance`=50 ohm with limits >0; `stimulus_level`=0.1 V with limits >=0.
- Declared analyses: `measurement`, `dc`, `ac`, `transient`, `digital`; declared package bindings: `pkg-virtual`.
- This documentation concern introduces no equation. It publishes the core behavior supported by completed catalog, symbol, model, validation, thermal, and failure evidence for `fam-instruments-impedance-rf-instrument`. Import mappings are planned extensions and remain explicitly unavailable/unclaimable until the separate IMPORT card is `Done`.
- Exact reference vectors: `GOLD-INS-IMPEDANCE_RF_INSTRUMENT-NOMINAL`, `GOLD-INS-IMPEDANCE_RF_INSTRUMENT-BOUNDARY`, `GOLD-INS-IMPEDANCE_RF_INSTRUMENT-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-instruments-impedance-rf-instrument-shared-f0-docs.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-instruments-impedance-rf-instrument.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One evidence-backed final capability section in `families/fam-instruments-impedance-rf-instrument.md` for `fam-instruments-impedance-rf-instrument`, listing exact variants, tiers, analyses, packages, provenance, limitations, and task/test links.
- Synchronized registry, coverage, traceability, task-index, risk, and release-checklist records with no claim beyond completed evidence; each unfinished optional import mapping is labelled planned and unsupported rather than blocking the core documentation release.
- Scope is limited to `CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-SHARED-F0-DOCS`: shared family scope across `var-instruments-impedance-rf-instrument-lcr-meter`, `var-instruments-impedance-rf-instrument-spectrum-analyzer`, `var-instruments-impedance-rf-instrument-network-analyzer`, fidelity `F0`, concern `DOCS`, and requirements REQ-007, REQ-021, REQ-022, REQ-023, REQ-034, REQ-037.

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

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `CH+:CHANNEL+` (input; measurement/electrical), `CH-:CHANNEL-` (input; measurement/electrical), `COM:COMMON` (reference; measurement/electrical); reject any package map outside `pkg-virtual`.
- Reject non-finite values and any value outside this exact parameter contract: `port_count`=2 1 with limits 1..64; `start_frequency`=10 Hz with limits >=0; `stop_frequency`=1e9 Hz with limits >start_frequency; `point_count`=201 1 with limits 2..1000000; `reference_impedance`=50 ohm with limits >0; `stimulus_level`=0.1 V with limits >=0.
- Support only `measurement`, `dc`, `ac`, `transient`, `digital`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- A missing required concern/test/result/provenance/limitation link, contradictory capability claim, orphan ID, or premature `Released` state blocks documentation completion. An unfinished optional IMPORT card does not block the core release, but claiming its format does.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-SHARED-F0-DOCS-NOMINAL`
- `TEST-CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-SHARED-F0-DOCS-BOUNDARY`
- `TEST-CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-SHARED-F0-DOCS-FAILURE`

## Acceptance

1. The exact output for `CMP-INSTRUMENTS-IMPEDANCE-RF-INSTRUMENT-SHARED-F0-DOCS` exists and is limited to shared family scope across `var-instruments-impedance-rf-instrument-lcr-meter`, `var-instruments-impedance-rf-instrument-spectrum-analyzer`, `var-instruments-impedance-rf-instrument-network-analyzer`, `F0`, and `DOCS`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-instruments-impedance-rf-instrument` and its family specification.
3. This task's nominal, boundary, and failure test IDs pass with retained inputs, expected/actual outputs, versions, provenance, deterministic seed where applicable, and evidence digests.
4. Every invalid/unsupported case named above returns the documented structured diagnostic; there is no silent fallback, inferred pin map, guessed constant, or undeclared fidelity.
5. Requirements REQ-007, REQ-021, REQ-022, REQ-023, REQ-034, REQ-037, registry, family specification, package mapping, coverage, task indexes, test registry, risk record, and applicable release checklist are synchronized.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
