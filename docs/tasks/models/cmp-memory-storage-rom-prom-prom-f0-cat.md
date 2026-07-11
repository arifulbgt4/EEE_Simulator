# CMP-MEMORY-STORAGE-ROM-PROM-PROM-F0-CAT - Specify Prom catalog preset

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-memory-storage-rom-prom` - ROM and PROM |
| Variant | `var-memory-storage-rom-prom-prom` - Prom |
| Fidelity | F0 |
| Concern | CAT |
| Release | R8 |
| Requirements | REQ-018, REQ-021, REQ-025, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Applicable registry, package, engine, and preceding family-concern tasks |

## Single outcome

Create the complete, immutable catalog definition for **Prom** without implementing a different fidelity or sibling preset.

## Context to read

- [Family specification](../../catalog/families/fam-memory-storage-rom-prom.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Aliases: ROM and PROM, Rom Prom, rom-prom
- Pins: A:ADDRESS(input), D:DATA(bidirectional), C:CONTROL(input), VDD:VDD(power), VSS:VSS(power)
- Parameters: width [bit], propagation_delay [s], logic_family [1]
- Supported analyses: digital-event, timing, firmware
- Package mappings: pkg-dip, pkg-soic, pkg-tssop, pkg-qfp, pkg-qfn, pkg-bga, pkg-custom-parametric
- Golden references: GOLD-MEM-ROM_PROM-NOMINAL, GOLD-MEM-ROM_PROM-BOUNDARY, GOLD-MEM-ROM_PROM-FAILURE
- Provenance basis: Project-defined canonical family; Source PDF, pp. 24-28

## Deliverables

- Stable variant identity, aliases, defaults, limits, supported tiers, analyses, and lifecycle state.
- Explicit schematic-symbol, physical-appearance, and package references: pkg-dip, pkg-soic, pkg-tssop, pkg-qfp, pkg-qfn, pkg-bga, pkg-custom-parametric.
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
3. The preset selects only declared model tiers (F0, F2, F3) and never implies manufacturer certification.
4. Registry, family specification, package mapping, coverage, task, test, and release traceability agree.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
