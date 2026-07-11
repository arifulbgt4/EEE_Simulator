# CMP-SOURCES-LOADS-MAINS-SOURCE-SINGLE-PHASE-F0-CAT - Specify Single Phase catalog preset

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-sources-loads-mains-source` - Mains source |
| Variant | `var-sources-loads-mains-source-single-phase` - Single Phase |
| Fidelity | F0 |
| Concern | CAT |
| Release | R2 |
| Requirements | REQ-008, REQ-009, REQ-010, REQ-022, REQ-023, REQ-037 |
| Depends on | Applicable registry, package, engine, and preceding family-concern tasks |

## Single outcome

Create the complete, immutable catalog definition for **Single Phase** without implementing a different fidelity or sibling preset.

## Context to read

- [Family specification](../../catalog/families/fam-sources-loads-mains-source.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Aliases: Mains source, Mains Source, mains-source
- Pins: 1:P(passive), 2:N(passive)
- Parameters: magnitude [SI], frequency [Hz], phase [rad]
- Supported analyses: dc, ac, transient, noise
- Package mappings: pkg-virtual
- Golden references: GOLD-SRC-MAINS_SOURCE-NOMINAL, GOLD-SRC-MAINS_SOURCE-BOUNDARY, GOLD-SRC-MAINS_SOURCE-FAILURE
- Provenance basis: Project-defined canonical family; Source PDF, pp. 8-10

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
3. The preset selects only declared model tiers (F0, F1, F2, F3, F4) and never implies manufacturer certification.
4. Registry, family specification, package mapping, coverage, task, test, and release traceability agree.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
