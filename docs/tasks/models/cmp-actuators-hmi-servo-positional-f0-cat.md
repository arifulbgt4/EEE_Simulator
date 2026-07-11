# CMP-ACTUATORS-HMI-SERVO-POSITIONAL-F0-CAT - Specify Positional catalog preset

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-actuators-hmi-servo` - Servo |
| Variant | `var-actuators-hmi-servo-positional` - Positional |
| Fidelity | F0 |
| Concern | CAT |
| Release | R7 |
| Requirements | REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Applicable registry, package, engine, and preceding family-concern tasks |

## Single outcome

Create the complete, immutable catalog definition for **Positional** without implementing a different fidelity or sibling preset.

## Context to read

- [Family specification](../../catalog/families/fam-actuators-hmi-servo.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Aliases: Servo, Servo, servo
- Pins: 1:DRIVE+(input), 2:DRIVE-(input), M:MECHANICAL_OR_DISPLAY(physical)
- Parameters: drive_rating [SI], efficiency [1], inertia [SI]
- Supported analyses: dc, transient, electromechanical
- Package mappings: pkg-electromechanical, pkg-display-module, pkg-custom-parametric
- Golden references: GOLD-ACT-SERVO-NOMINAL, GOLD-ACT-SERVO-BOUNDARY, GOLD-ACT-SERVO-FAILURE
- Provenance basis: Project-defined canonical family; Source PDF, pp. 17-21

## Deliverables

- Stable variant identity, aliases, defaults, limits, supported tiers, analyses, and lifecycle state.
- Explicit schematic-symbol, physical-appearance, and package references: pkg-electromechanical, pkg-display-module, pkg-custom-parametric.
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
3. The preset selects only declared model tiers (F0, F1, F2, F3, F4) and never implies manufacturer certification.
4. Registry, family specification, package mapping, coverage, task, test, and release traceability agree.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
