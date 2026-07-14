# CMP-PACKAGE-SOIC-TEMPLATE-F0-VALIDATION - Validate Small-outline IC pin map and appearance

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `pkg-soic` - Small-outline IC |
| Variant | `template` |
| Fidelity | F0 |
| Concern | VALIDATION |
| Release | R1 |
| Requirements | REQ-037, REQ-038 |
| Depends on | Exact prerequisite IDs listed below |

## Single outcome

Validate dimensions/ranges, collision-free pins, numbering, pin-one cues, rotation and logical-to-physical equivalence.

## Exact prerequisites

- `CMP-PACKAGE-SOIC-TEMPLATE-F0-SYM`
- `PLAT-SYM-012`
- `PLAT-QA-001`

Every ID above must be `Done` or its named predecessor gate accepted before this card may become `Ready`.

## Context to read

- [Family specification](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Package registry](../../catalog/package-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Aliases: Small-outline IC
- Pins: family-defined parameterized pins
- Parameters: none
- Supported analyses: physical-view, pin-map-validation
- Package mappings: pkg-soic
- Golden references: GRC-051, GRC-054
- Provenance basis: Registry-defined source required

## Public contracts

- Named entities: `PackageDefinition`, `DevicePackageBinding`, `PhysicalRepresentation`, `PinMap`, `.eesim package revision record`.
- [Component Model Contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Equations and reference data

- Package registry entry `pkg-soic` revision `1.0.0` is the only geometry/default source for this task.
- Concern-specific golden references: GRC-051, GRC-054. `NUMERICAL_ACCURACY_TARGETS.md` defines comparison and evidence rules.
- This concern has no electrical model equation; geometry and numbering use the declarative package constraints only.

## Allowed files

- `docs/tasks/models/cmp-package-soic-template-f0-validation.md`
- `docs/tasks/models/task-manifest.yaml`
- `docs/tasks/models/INDEX.md`
- `docs/catalog/package-registry.yaml`
- `docs/catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md`
- `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001`; it may not widen the family, variant, tier, concern, or documentation allowlist.

## Deliverables

- Validate dimensions/ranges, collision-free pins, numbering, pin-one cues, rotation and logical-to-physical equivalence.
- Package-registry and custom-designer compatibility evidence.
- Explicit logical-to-physical pin-map behavior and limitations.

## Documentation updates

- This task card, `docs/tasks/models/task-manifest.yaml`, and `docs/tasks/models/INDEX.md`.
- The exact registry/family records in the allowlist and `docs/catalog/COMPONENT_COVERAGE_MATRIX.md`.
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`, the named golden evidence, and the applicable release checklist.
- Provenance, license, limitations, and package/pin-map records changed by this concern only.

## Allowed scope

- One family, fidelity **F0**, and concern **VALIDATION** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject invalid parameters, missing/duplicate pins, unsupported analyses, unavailable fidelity, incompatible domains, and invalid package maps with structured diagnostics.
- Preserve component identity, nets, parameters, model state, and simulation result when switching schematic and physical views.
- Keep realistic appearance illustrative unless sourced dimensions are explicitly verified.

## Acceptance test IDs

- `TEST-CMP-PACKAGE-SOIC-TEMPLATE-F0-VALIDATION-NOMINAL`
- `TEST-CMP-PACKAGE-SOIC-TEMPLATE-F0-VALIDATION-BOUNDARY`
- `TEST-CMP-PACKAGE-SOIC-TEMPLATE-F0-VALIDATION-FAILURE`

## Acceptance

1. Pin count, dimensions, pitch and geometry obey the registry constraints.
2. Pin-one/polarity, numbering and orientation remain visible at supported rotations and levels of detail.
3. The package stays reusable and electrically separate from every device model.
4. Registry, family specification, package mapping, coverage, task, test, and release traceability agree.

## Known limitations to preserve

This record does not certify PCB land pattern, enclosure fit, creepage, clearance, thermal resistance, or manufacturability.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
