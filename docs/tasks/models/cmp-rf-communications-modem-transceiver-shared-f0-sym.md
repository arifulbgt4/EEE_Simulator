# CMP-RF-COMMUNICATIONS-MODEM-TRANSCEIVER-SHARED-F0-SYM - Create symbol and physical representation for Modem and transceiver

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-rf-communications-modem-transceiver` - Modem and transceiver |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | SYM |
| Release | R7 |
| Requirements | REQ-011, REQ-012, REQ-024, REQ-028, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Applicable registry, package, engine, and preceding family-concern tasks |

## Single outcome

Create original, electrically unambiguous schematic and recognizable physical representations for **Modem and transceiver**, including accessible orientation/polarity cues and reusable package mapping.

## Context to read

- [Family specification](../../catalog/families/fam-rf-communications-modem-transceiver.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Aliases: Modem and transceiver, Modem Transceiver, modem-transceiver
- Pins: IN:RF_IN(passive), OUT:RF_OUT(passive), GND:GROUND(reference)
- Parameters: reference_impedance [ohm], center_frequency [Hz], bandwidth [Hz]
- Supported analyses: ac, s-parameter, noise, modulation
- Package mappings: pkg-rf-module, pkg-qfn, pkg-bga, pkg-custom-parametric
- Golden references: GOLD-RFC-MODEM_TRANSCEIVER-NOMINAL, GOLD-RFC-MODEM_TRANSCEIVER-BOUNDARY, GOLD-RFC-MODEM_TRANSCEIVER-FAILURE
- Provenance basis: Project-defined canonical family; Source PDF, pp. 28-35

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
