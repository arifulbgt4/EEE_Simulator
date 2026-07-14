# CMP-RF-COMMUNICATIONS-RF-PORT-NETWORK-SHARED-F0-SYM - Create symbol and physical representation for RF port and network model

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-rf-communications-rf-port-network` - RF port and network model |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | SYM |
| Release | R7 |
| Requirements | REQ-011, REQ-012, REQ-024, REQ-028, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Create original, electrically unambiguous schematic and recognizable physical representations for **RF port and network model**, including accessible orientation/polarity cues and reusable package mapping.

## Exact prerequisites

- `CMP-RF-COMMUNICATIONS-RF-PORT-NETWORK-RF-PORT-F1-CAT`
- `CMP-RF-COMMUNICATIONS-RF-PORT-NETWORK-TERMINATION-F1-CAT`
- `CMP-RF-COMMUNICATIONS-RF-PORT-NETWORK-S-PARAMETER-BLACK-BOX-F1-CAT`
- `PLAT-SYM-007`
- `CMP-PACKAGE-RF-MODULE-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-QFN-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-BGA-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-CUSTOM-PARAMETRIC-TEMPLATE-F0-VALIDATION`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-rf-communications-rf-port-network.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-rf-communications-rf-port-network` (RF port and network model); task scope: shared family scope across `var-rf-communications-rf-port-network-rf-port`, `var-rf-communications-rf-port-network-termination`, `var-rf-communications-rf-port-network-s-parameter-black-box`; fidelity `F0`; concern `SYM`.
- Exact pins: `IN:RF_IN` (passive; rf/electrical/communications), `OUT:RF_OUT` (passive; rf/electrical/communications), `GND:GROUND` (reference; rf/electrical/communications).
- Exact parameters/defaults/limits: `port_count`=2 1 with limits 1..1024; `reference_impedance`=50 ohm with limits >0; `start_frequency`=1e6 Hz with limits >=0; `stop_frequency`=1e9 Hz with limits >start_frequency; `data_digest`=unset 1 with limits valid digest before Ready.
- Supported analyses: `ac`, `s-parameter`, `noise`, `modulation`.
- Valid package mappings: `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Golden references: `GOLD-RFC-RF_PORT_NETWORK-NOMINAL`, `GOLD-RFC-RF_PORT_NETWORK-BOUNDARY`, `GOLD-RFC-RF_PORT_NETWORK-FAILURE`.
- Import mappings applicable to this family: `Touchstone 2.1`, `IBIS 8.0`, `CSV`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 28-35; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [RF port and network model family-specific implementation reference](../../catalog/families/fam-rf-communications-rf-port-network.md#family-specific-implementation-reference), registry row `fam-rf-communications-rf-port-network`, and shared family scope across `var-rf-communications-rf-port-network-rf-port`, `var-rf-communications-rf-port-network-termination`, `var-rf-communications-rf-port-network-s-parameter-black-box`.
- Exact pin vector: `IN:RF_IN` (passive; rf/electrical/communications), `OUT:RF_OUT` (passive; rf/electrical/communications), `GND:GROUND` (reference; rf/electrical/communications).
- Exact parameter vector: `port_count`=2 1 with limits 1..1024; `reference_impedance`=50 ohm with limits >0; `start_frequency`=1e6 Hz with limits >=0; `stop_frequency`=1e9 Hz with limits >start_frequency; `data_digest`=unset 1 with limits valid digest before Ready.
- Declared analyses: `ac`, `s-parameter`, `noise`, `modulation`; declared package bindings: `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- This symbol/appearance concern has no electrical equation. It preserves the exact pin vector and family rule while implementing original scalable geometry and explicit package maps.
- Exact reference vectors: `GOLD-RFC-RF_PORT_NETWORK-NOMINAL`, `GOLD-RFC-RF_PORT_NETWORK-BOUNDARY`, `GOLD-RFC-RF_PORT_NETWORK-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-rf-communications-rf-port-network-shared-f0-sym.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-rf-communications-rf-port-network.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One original `sym-rf-communications-rf-port-network` schematic definition with anchors for `IN:RF_IN` (passive; rf/electrical/communications), `OUT:RF_OUT` (passive; rf/electrical/communications), `GND:GROUND` (reference; rf/electrical/communications).
- One scalable physical-view binding for every declared package `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`, including non-color orientation/polarity/pin-one cues, accessible text, and logical-to-package pin-equivalence evidence.
- Scope is limited to `CMP-RF-COMMUNICATIONS-RF-PORT-NETWORK-SHARED-F0-SYM`: shared family scope across `var-rf-communications-rf-port-network-rf-port`, `var-rf-communications-rf-port-network-termination`, `var-rf-communications-rf-port-network-s-parameter-black-box`, fidelity `F0`, concern `SYM`, and requirements REQ-011, REQ-012, REQ-024, REQ-028, REQ-022, REQ-023, REQ-037, REQ-038.

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

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `IN:RF_IN` (passive; rf/electrical/communications), `OUT:RF_OUT` (passive; rf/electrical/communications), `GND:GROUND` (reference; rf/electrical/communications); reject any package map outside `pkg-rf-module`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `port_count`=2 1 with limits 1..1024; `reference_impedance`=50 ohm with limits >0; `start_frequency`=1e6 Hz with limits >=0; `stop_frequency`=1e9 Hz with limits >start_frequency; `data_digest`=unset 1 with limits valid digest before Ready.
- Support only `ac`, `s-parameter`, `noise`, `modulation`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Rotation, mirroring, LOD, high contrast, and view switching must preserve pin identity and selection; invisible orientation/polarity or color-only meaning fails validation.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-RF-COMMUNICATIONS-RF-PORT-NETWORK-SHARED-F0-SYM-NOMINAL`
- `TEST-CMP-RF-COMMUNICATIONS-RF-PORT-NETWORK-SHARED-F0-SYM-BOUNDARY`
- `TEST-CMP-RF-COMMUNICATIONS-RF-PORT-NETWORK-SHARED-F0-SYM-FAILURE`

## Acceptance

1. The exact output for `CMP-RF-COMMUNICATIONS-RF-PORT-NETWORK-SHARED-F0-SYM` exists and is limited to shared family scope across `var-rf-communications-rf-port-network-rf-port`, `var-rf-communications-rf-port-network-termination`, `var-rf-communications-rf-port-network-s-parameter-black-box`, `F0`, and `SYM`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-rf-communications-rf-port-network` and its family specification.
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
