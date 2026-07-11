# CMP-INSTRUMENTS-BENCH-SUPPLY-SHARED-F0-VALIDATION - Validate Bench supply F0

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Family | `fam-instruments-bench-supply` - Bench supply |
| Variant | `shared` |
| Fidelity | F0 |
| Concern | VALIDATION |
| Release | R2 |
| Requirements | REQ-007, REQ-021, REQ-022, REQ-023, REQ-034, REQ-037 |
| Depends on | Applicable registry, package, engine, and preceding family-concern tasks |

## Single outcome

Produce independent validation evidence for **Bench supply** at **F0** without modifying the model under test.

## Context to read

- [Family specification](../../catalog/families/fam-instruments-bench-supply.md)
- [Component registry](../../catalog/component-registry.yaml)
- [Component model contract](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Package and physical appearance](../../catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Normative inputs

- Aliases: Bench supply, Bench Supply, bench-supply
- Pins: CH+:CHANNEL+(input), CH-:CHANNEL-(input), COM:COMMON(reference)
- Parameters: nominal [SI], temperature [K], tolerance [1]
- Supported analyses: measurement, dc, ac, transient, digital
- Package mappings: pkg-virtual
- Golden references: GOLD-INS-BENCH_SUPPLY-NOMINAL, GOLD-INS-BENCH_SUPPLY-BOUNDARY, GOLD-INS-BENCH_SUPPLY-FAILURE
- Provenance basis: Project-defined canonical family; Source PDF, pp. 20-23

## Deliverables

- Analytical or independent reference vectors.
- Nominal, boundary, invalid, temperature and applicable failure comparisons.
- Versioned evidence with environment, settings and tolerances.

## Allowed scope

- One family, fidelity **F0**, and concern **VALIDATION** only.

## Forbidden scope

- Do not change another variant, invent a manufacturer SKU, copy protected IEC/vendor artwork, combine another concern, or claim an unsupported analysis/fidelity.
- Do not embed package geometry in the electrical model; use an explicit reusable package and validated logical-to-physical pin map.

## Required edge and failure behavior

- Reject invalid parameters, missing/duplicate pins, unsupported analyses, unavailable fidelity, incompatible domains, and invalid package maps with structured diagnostics.
- Preserve component identity, nets, parameters, model state, and simulation result when switching schematic and physical views.
- Keep realistic appearance illustrative unless sourced dimensions are explicitly verified.

## Acceptance

1. Every declared golden assertion for the tier passes.
2. The reference is independent and reproducible.
3. Failure results are structured and never silently approximated.
4. Registry, family specification, package mapping, coverage, task, test, and release traceability agree.

## Known limitations to preserve

Only the listed analyses, fidelity tiers, parameter range, and validated package mappings may be claimed.

## Definition of Done

- [ ] The single deliverable concern is complete and independently reviewable.
- [ ] Nominal, boundary, invalid, and relevant failure evidence passes.
- [ ] Provenance, license, accuracy envelope, and unsupported behavior are visible.
- [ ] No adjacent component, tier, concern, or package contract changed silently.
