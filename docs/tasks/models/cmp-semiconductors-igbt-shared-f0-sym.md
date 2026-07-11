# CMP-SEMICONDUCTORS-IGBT-SHARED-F0-SYM - Create symbol and physical representation for Insulated-gate bipolar transistor

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-semiconductors-igbt` - Insulated-gate bipolar transistor |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | SYM |
| Release | R3 |
| Requirements | REQ-009, REQ-010, REQ-011, REQ-012, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Applicable registry, package, engine, and preceding family-concern tasks |

## Single outcome

Create original, electrically unambiguous schematic and recognizable physical representations for **Insulated-gate bipolar transistor**, including accessible orientation/polarity cues and reusable package mapping.

## Context to read

- [Family specification](../../catalog/families/fam-semiconductors-igbt.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Aliases: Insulated-gate bipolar transistor, Igbt, igbt
- Pins: 1:D(passive), 2:G(input), 3:S(passive), 4:B(optional)
- Parameters: model [1], temperature [K], area_multiplier [1]
- Supported analyses: dc, ac, transient, noise, electrothermal
- Package mappings: pkg-sot-23, pkg-to-92, pkg-to-220, pkg-qfn, pkg-custom-parametric
- Golden references: GOLD-SEM-IGBT-NOMINAL, GOLD-SEM-IGBT-BOUNDARY, GOLD-SEM-IGBT-FAILURE
- Provenance basis: Project-defined canonical family; Source PDF, pp. 10-15

## Deliverables

- Original scalable schematic geometry and pin anchors.
- Procedural/scalable physical body, leads, markings, materials, scale and level-of-detail rules.
- Symbol-to-package pin equivalence evidence.

## Allowed scope

- One family, fidelity **F0**, and concern **SYM** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject invalid parameters, missing/duplicate pins, unsupported analyses, unavailable fidelity, incompatible domains, and invalid package maps with structured diagnostics.
- Preserve component identity, nets, parameters, model state, and simulation result when switching schematic and physical views.
- Keep realistic appearance illustrative unless sourced dimensions are explicitly verified.

## Acceptance

1. All pins, polarity and orientation remain unambiguous without color alone.
2. Schematic/physical view switching preserves identity, connectivity and simulation state.
3. Golden visual renders and package equivalence checks pass.
4. Registry, family specification, package mapping, coverage, task, test, and release traceability agree.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
