# CMP-CONNECTIVITY-HIERARCHICAL-PORT-SHARED-F0-DOCS - Document Hierarchical port

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-connectivity-hierarchical-port` - Hierarchical port |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | DOCS |
| Release | R1 |
| Requirements | REQ-004, REQ-005, REQ-008, REQ-022, REQ-023, REQ-037 |
| Depends on | Applicable registry, package, engine, and preceding family-concern tasks |

## Single outcome

Publish user and contributor documentation for **Hierarchical port** without changing its model, symbol, package, or validation behavior.

## Context to read

- [Family specification](../../catalog/families/fam-connectivity-hierarchical-port.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Aliases: Hierarchical port, Hierarchical Port, hierarchical-port
- Pins: 1:PORT(bidirectional)
- Parameters: nominal [SI], temperature [K], tolerance [1]
- Supported analyses: connectivity, erc
- Package mappings: pkg-virtual
- Golden references: GOLD-CON-HIERARCHICAL_PORT-NOMINAL, GOLD-CON-HIERARCHICAL_PORT-BOUNDARY, GOLD-CON-HIERARCHICAL_PORT-FAILURE
- Provenance basis: Project-defined canonical family; Source PDF, pp. 6-8

## Deliverables

- Purpose, variants, pins, parameters, fidelity/analysis matrix and examples.
- Physical/package selection, limitations, provenance and troubleshooting.
- Links to every golden test and atomic task.

## Allowed scope

- One family, fidelity **F0**, and concern **DOCS** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject invalid parameters, missing/duplicate pins, unsupported analyses, unavailable fidelity, incompatible domains, and invalid package maps with structured diagnostics.
- Preserve component identity, nets, parameters, model state, and simulation result when switching schematic and physical views.
- Keep realistic appearance illustrative unless sourced dimensions are explicitly verified.

## Acceptance

1. A beginner can select and wire the component without guessing.
2. An advanced user can identify the exact model/accuracy envelope.
3. All links, IDs and examples agree with the registry.
4. Registry, family specification, package mapping, coverage, task, test, and release traceability agree.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
