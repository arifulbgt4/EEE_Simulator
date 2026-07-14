# CMP-DIGITAL-LOGIC-MUX-CODEC-SHARED-F0-SYM - Create symbol and physical representation for Multiplexer and code converter

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-digital-logic-mux-codec` - Multiplexer and code converter |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | SYM |
| Release | R5 |
| Requirements | REQ-018, REQ-021, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Create original, electrically unambiguous schematic and recognizable physical representations for **Multiplexer and code converter**, including accessible orientation/polarity cues and reusable package mapping.

## Exact prerequisites

- `CMP-DIGITAL-LOGIC-MUX-CODEC-MULTIPLEXER-F0-CAT`
- `CMP-DIGITAL-LOGIC-MUX-CODEC-DEMULTIPLEXER-F0-CAT`
- `CMP-DIGITAL-LOGIC-MUX-CODEC-ENCODER-F0-CAT`
- `CMP-DIGITAL-LOGIC-MUX-CODEC-DECODER-F0-CAT`
- `PLAT-SYM-007`
- `CMP-PACKAGE-DIP-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-SOIC-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-TSSOP-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-QFP-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-QFN-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-BGA-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-CUSTOM-PARAMETRIC-TEMPLATE-F0-VALIDATION`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/families/fam-digital-logic-mux-codec.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Stable family: `fam-digital-logic-mux-codec` (Multiplexer and code converter); task scope: shared family scope across `var-digital-logic-mux-codec-multiplexer`, `var-digital-logic-mux-codec-demultiplexer`, `var-digital-logic-mux-codec-encoder`, `var-digital-logic-mux-codec-decoder`; fidelity `F0`; concern `SYM`.
- Exact pins: `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power).
- Exact parameters/defaults/limits: `data_width`=1 bit with limits 1..4096; `channel_count`=2 1 with limits 2..4096; `select_width`=1 bit with limits 1..64; `propagation_delay`=0 s with limits >=0.
- Supported analyses: `digital-event`, `timing`, `truth-table`.
- Valid package mappings: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Golden references: `GOLD-DIG-MUX_CODEC-NOMINAL`, `GOLD-DIG-MUX_CODEC-BOUNDARY`, `GOLD-DIG-MUX_CODEC-FAILURE`.
- Import mappings applicable to this family: `Verilog/SystemVerilog`, `VCD/FST`, `HEX/ELF`.
- Provenance basis: Project-defined canonical family; Source PDF, pp. 21-26; symbol license: Apache-2.0 original artwork; model license: per-model SPDX identifier required.

## Public contracts

- Named entities: `ComponentDefinition`, `ComponentVariant`, `PinDefinition`, `ParameterDefinition`, `ModelBinding`, `AnalysisCapability`, `FailureDefinition`, `ModelProvenance`, `PhysicalRepresentation`, `DevicePackageBinding`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Canonical source: [Multiplexer and code converter family-specific implementation reference](../../catalog/families/fam-digital-logic-mux-codec.md#family-specific-implementation-reference), registry row `fam-digital-logic-mux-codec`, and shared family scope across `var-digital-logic-mux-codec-multiplexer`, `var-digital-logic-mux-codec-demultiplexer`, `var-digital-logic-mux-codec-encoder`, `var-digital-logic-mux-codec-decoder`.
- Exact pin vector: `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power).
- Exact parameter vector: `data_width`=1 bit with limits 1..4096; `channel_count`=2 1 with limits 2..4096; `select_width`=1 bit with limits 1..64; `propagation_delay`=0 s with limits >=0.
- Declared analyses: `digital-event`, `timing`, `truth-table`; declared package bindings: `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- This symbol/appearance concern has no electrical equation. It preserves the exact pin vector and family rule while implementing original scalable geometry and explicit package maps.
- Exact reference vectors: `GOLD-DIG-MUX_CODEC-NOMINAL`, `GOLD-DIG-MUX_CODEC-BOUNDARY`, `GOLD-DIG-MUX_CODEC-FAILURE`. Nominal uses the registry defaults above; boundary evaluates every declared limit and supported state; failure covers each declared failure mode plus invalid/non-finite parameters, pin-map mismatch, unsupported analysis, and unavailable fidelity.
- Numerical comparisons use `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`; missing model-specific constants or independent reference data are a named blocker and may not be guessed.

## Allowed files

- `docs/tasks/models/cmp-digital-logic-mux-codec-shared-f0-sym.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/component-registry.yaml`
- `docs/catalog/families/fam-digital-logic-mux-codec.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- One original `sym-digital-logic-mux-codec` schematic definition with anchors for `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power).
- One scalable physical-view binding for every declared package `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`, including non-color orientation/polarity/pin-one cues, accessible text, and logical-to-package pin-equivalence evidence.
- Scope is limited to `CMP-DIGITAL-LOGIC-MUX-CODEC-SHARED-F0-SYM`: shared family scope across `var-digital-logic-mux-codec-multiplexer`, `var-digital-logic-mux-codec-demultiplexer`, `var-digital-logic-mux-codec-encoder`, `var-digital-logic-mux-codec-decoder`, fidelity `F0`, concern `SYM`, and requirements REQ-018, REQ-021, REQ-022, REQ-023, REQ-037, REQ-038.

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

- Reject a missing, duplicate, reordered, or domain-incompatible pin from `1..N:INPUTS` (input; digital/power), `N+1..M:OUTPUTS` (output; digital/power), `VDD:VDD` (power; digital/power), `VSS:VSS` (power; digital/power); reject any package map outside `pkg-dip`, `pkg-soic`, `pkg-tssop`, `pkg-qfp`, `pkg-qfn`, `pkg-bga`, `pkg-custom-parametric`.
- Reject non-finite values and any value outside this exact parameter contract: `data_width`=1 bit with limits 1..4096; `channel_count`=2 1 with limits 2..4096; `select_width`=1 bit with limits 1..64; `propagation_delay`=0 s with limits >=0.
- Support only `digital-event`, `timing`, `truth-table`; return a structured unsupported-analysis/fidelity diagnostic for every other request.
- Rotation, mirroring, LOD, high contrast, and view switching must preserve pin identity and selection; invisible orientation/polarity or color-only meaning fails validation.
- Schematic/physical/package view switching preserves instance ID, nets, parameters, model state, selected package revision, results, selection, and undo history.

## Acceptance test IDs

- `TEST-CMP-DIGITAL-LOGIC-MUX-CODEC-SHARED-F0-SYM-NOMINAL`
- `TEST-CMP-DIGITAL-LOGIC-MUX-CODEC-SHARED-F0-SYM-BOUNDARY`
- `TEST-CMP-DIGITAL-LOGIC-MUX-CODEC-SHARED-F0-SYM-FAILURE`

## Acceptance

1. The exact output for `CMP-DIGITAL-LOGIC-MUX-CODEC-SHARED-F0-SYM` exists and is limited to shared family scope across `var-digital-logic-mux-codec-multiplexer`, `var-digital-logic-mux-codec-demultiplexer`, `var-digital-logic-mux-codec-encoder`, `var-digital-logic-mux-codec-decoder`, `F0`, and `SYM`.
2. The family-specific relation/state rule, pin vector, parameter defaults/limits, analysis list, and package list above agree with `fam-digital-logic-mux-codec` and its family specification.
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
