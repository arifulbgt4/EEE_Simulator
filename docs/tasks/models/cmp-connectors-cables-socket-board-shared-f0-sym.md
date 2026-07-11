# CMP-CONNECTORS-CABLES-SOCKET-BOARD-SHARED-F0-SYM - Create symbol and physical representation for Socket and prototyping board

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-connectors-cables-socket-board` - Socket and prototyping board |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | SYM |
| Release | R7 |
| Requirements | REQ-005, REQ-014, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Applicable registry, package, engine, and preceding family-concern tasks |

## Single outcome

Create original, electrically unambiguous schematic and recognizable physical representations for **Socket and prototyping board**, including accessible orientation/polarity cues and reusable package mapping.

## Context to read

- [Family specification](../../catalog/families/fam-connectors-cables-socket-board.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Aliases: Socket and prototyping board, Socket Board, socket-board
- Pins: 1..N:CONTACTS(passive), S:SHIELD(passive)
- Parameters: contact_count [1], contact_resistance [ohm], pitch [m]
- Supported analyses: connectivity, dc, ac, signal-integrity
- Package mappings: pkg-connector-parametric, pkg-cable-parametric, pkg-custom-parametric
- Golden references: GOLD-CAB-SOCKET_BOARD-NOMINAL, GOLD-CAB-SOCKET_BOARD-BOUNDARY, GOLD-CAB-SOCKET_BOARD-FAILURE
- Provenance basis: Project-defined canonical family; Source PDF, pp. 18-21

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
