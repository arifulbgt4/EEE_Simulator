# CMP-CONNECTIVITY-WIRE-SHIELDED-WIRE-F0-CAT - Specify Shielded Wire catalog preset

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-connectivity-wire` - Wire and conductor |
| Variant | `var-connectivity-wire-shielded-wire` - Shielded Wire |
| Fidelity | F0 |
| Concern | CAT |
| Release | R1 |
| Requirements | REQ-004, REQ-005, REQ-008, REQ-022, REQ-023, REQ-037 |
| Depends on | Applicable registry, package, engine, and preceding family-concern tasks |

## Single outcome

Create the complete, immutable catalog definition for **Shielded Wire** without implementing a different fidelity or sibling preset.

## Context to read

- [Family specification](../../catalog/families/fam-connectivity-wire.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Aliases: Wire and conductor, Wire, wire
- Pins: 1:P(passive), 2:N(passive)
- Parameters: nominal [SI], temperature [K], tolerance [1]
- Supported analyses: connectivity, erc
- Package mappings: pkg-virtual
- Golden references: GOLD-CON-WIRE-NOMINAL, GOLD-CON-WIRE-BOUNDARY, GOLD-CON-WIRE-FAILURE
- Provenance basis: Project-defined canonical family; Source PDF, pp. 6-8

## Deliverables

- Stable variant identity, aliases, defaults, limits, supported tiers, analyses, and lifecycle state.
- Explicit schematic-symbol, physical-appearance, and package references: pkg-virtual.
- Variant-specific provenance, accuracy/usage limits, and golden assertions.

## Allowed scope

- One family and one variant, fidelity **F0**, and concern **CAT** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject invalid parameters, missing/duplicate pins, unsupported analyses, unavailable fidelity, incompatible domains, and invalid package maps with structured diagnostics.
- Preserve component identity, nets, parameters, model state, and simulation result when switching schematic and physical views.
- Keep realistic appearance illustrative unless sourced dimensions are explicitly verified.

## Acceptance

1. The variant ID is unique and its defaults stay inside the family parameter limits.
2. Every required logical pin maps exactly once to each supported physical package; NC and thermal pads remain explicit.
3. The preset selects only declared model tiers (F0, F1) and never implies manufacturer certification.
4. Registry, family specification, package mapping, coverage, task, test, and release traceability agree.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
