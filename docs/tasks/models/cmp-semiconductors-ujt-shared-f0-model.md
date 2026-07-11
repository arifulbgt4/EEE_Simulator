# CMP-SEMICONDUCTORS-UJT-SHARED-F0-MODEL - Implement Unijunction transistor F0 model

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-semiconductors-ujt` - Unijunction transistor |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | MODEL |
| Release | R3 |
| Requirements | REQ-009, REQ-010, REQ-011, REQ-012, REQ-014, REQ-015, REQ-016, REQ-022, REQ-023, REQ-037, REQ-038 |
| Depends on | Applicable registry, package, engine, and preceding family-concern tasks |

## Single outcome

Implement one model tier, **F0**, for **Unijunction transistor** using the family equations/behavior and no higher-fidelity claims.

## Context to read

- [Family specification](../../catalog/families/fam-semiconductors-ujt.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Aliases: Unijunction transistor, Ujt, ujt
- Pins: 1:P(passive), 2:N(passive)
- Parameters: model [1], temperature [K], area_multiplier [1]
- Supported analyses: dc, ac, transient, noise, electrothermal
- Package mappings: pkg-sot-23, pkg-to-92, pkg-to-220, pkg-qfn, pkg-custom-parametric
- Golden references: GOLD-SEM-UJT-NOMINAL, GOLD-SEM-UJT-BOUNDARY, GOLD-SEM-UJT-FAILURE
- Provenance basis: Project-defined canonical family; Source PDF, pp. 10-15

## Deliverables

- Tier-specific state, equations/stamps/events and parameter validation.
- Initialization, update, power and structured diagnostic behavior.
- Declared analysis capability with unsupported-analysis rejection.

## Allowed scope

- One family, fidelity **F0**, and concern **MODEL** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject invalid parameters, missing/duplicate pins, unsupported analyses, unavailable fidelity, incompatible domains, and invalid package maps with structured diagnostics.
- Preserve component identity, nets, parameters, model state, and simulation result when switching schematic and physical views.
- Keep realistic appearance illustrative unless sourced dimensions are explicitly verified.

## Acceptance

1. Nominal and limiting-case model assertions pass.
2. Conservation/truth/timing invariants appropriate to the tier pass.
3. Results remain inside the declared validation envelope.
4. Registry, family specification, package mapping, coverage, task, test, and release traceability agree.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
