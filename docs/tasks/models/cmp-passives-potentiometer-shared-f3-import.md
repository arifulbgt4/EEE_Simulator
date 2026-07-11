# CMP-PASSIVES-POTENTIOMETER-SHARED-F3-IMPORT - Define import mapping for Potentiometer

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-passives-potentiometer` - Potentiometer |
| Variant | `shared` |
| Fidelity | F3 |
| Concern | IMPORT |
| Release | R2 |
| Requirements | REQ-009, REQ-010, REQ-011, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037 |
| Depends on | Applicable registry, package, engine, and preceding family-concern tasks |

## Single outcome

Implement and validate only the declared external-model mappings for **Potentiometer**.

## Context to read

- [Family specification](../../catalog/families/fam-passives-potentiometer.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Aliases: Potentiometer, Potentiometer, potentiometer
- Pins: 1:P(passive), 2:N(passive)
- Parameters: nominal [SI], tolerance [1], temperature_coefficient [1/K]
- Supported analyses: dc, ac, transient, noise, monte-carlo
- Package mappings: pkg-axial-2, pkg-smd-chip, pkg-radial-2
- Golden references: GOLD-PAS-POTENTIOMETER-NOMINAL, GOLD-PAS-POTENTIOMETER-BOUNDARY, GOLD-PAS-POTENTIOMETER-FAILURE
- Provenance basis: Project-defined canonical family; Source PDF, pp. 8-13

## Deliverables

- Supported syntax/subset and semantic mapping.
- Provenance/license capture and safe unsupported-syntax diagnostics.
- Round-trip or reference comparison fixtures where the format permits.

## Allowed scope

- One family, fidelity **F3**, and concern **IMPORT** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject invalid parameters, missing/duplicate pins, unsupported analyses, unavailable fidelity, incompatible domains, and invalid package maps with structured diagnostics.
- Preserve component identity, nets, parameters, model state, and simulation result when switching schematic and physical views.
- Keep realistic appearance illustrative unless sourced dimensions are explicitly verified.

## Acceptance

1. Unsupported constructs fail visibly.
2. Imported pin/parameter/unit semantics match the family contract.
3. Untrusted input limits and provenance rules pass.
4. Registry, family specification, package mapping, coverage, task, test, and release traceability agree.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
