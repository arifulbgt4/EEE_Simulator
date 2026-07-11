# CMP-PASSIVES-CAPACITOR-SHARED-F4-THERMAL - Implement Capacitor electrothermal behavior

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-passives-capacitor` - Capacitor |
| Variant | `shared` |
| Fidelity | F4 |
| Concern | THERMAL |
| Release | R2 |
| Requirements | REQ-009, REQ-010, REQ-011, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037 |
| Depends on | Applicable registry, package, engine, and preceding family-concern tasks |

## Single outcome

Implement only the F4 power, temperature and electrothermal feedback concern for **Capacitor**.

## Context to read

- [Family specification](../../catalog/families/fam-passives-capacitor.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Aliases: Capacitor, Capacitor, capacitor
- Pins: 1:P(passive), 2:N(passive)
- Parameters: nominal [SI], tolerance [1], temperature_coefficient [1/K]
- Supported analyses: dc, ac, transient, noise, monte-carlo
- Package mappings: pkg-radial-2, pkg-axial-2, pkg-smd-chip
- Golden references: GOLD-PAS-CAPACITOR-NOMINAL, GOLD-PAS-CAPACITOR-BOUNDARY, GOLD-PAS-CAPACITOR-FAILURE
- Provenance basis: Project-defined canonical family; Source PDF, pp. 8-13

## Deliverables

- Power balance and thermal state.
- Temperature coefficients, ambient/coupling boundaries and derating.
- Thermal warnings and runaway diagnostics.

## Allowed scope

- One family, fidelity **F4**, and concern **THERMAL** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject invalid parameters, missing/duplicate pins, unsupported analyses, unavailable fidelity, incompatible domains, and invalid package maps with structured diagnostics.
- Preserve component identity, nets, parameters, model state, and simulation result when switching schematic and physical views.
- Keep realistic appearance illustrative unless sourced dimensions are explicitly verified.

## Acceptance

1. Steady/dynamic thermal targets pass.
2. Energy and temperature remain finite inside declared limits.
3. Limit crossing and runaway produce declared outcomes.
4. Registry, family specification, package mapping, coverage, task, test, and release traceability agree.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
