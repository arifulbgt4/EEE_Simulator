# VAL-GRC-016 - Validate MOSFET low-side switch

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Target | MOSFET low-side switch |
| Requirements | REQ-009, REQ-010, REQ-011, REQ-014, REQ-017 |
| Golden fixture | GRC-016 |
| Release | R2 |
| Concern | Validation only |
| Depends on | Applicable model, engine, interface, package, and fixture-definition tasks |

## Objective

Produce independent, reproducible evidence for **Threshold region, on loss, switching transient** without changing the model or feature under test.

## Context to read

- [Golden reference circuits](../../quality/GOLDEN_REFERENCE_CIRCUITS.md)
- [Numerical accuracy targets](../../quality/NUMERICAL_ACCURACY_TARGETS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- Applicable component family, package, engine, and public-contract documents.

## Reference and inputs

- Record the analytical solution or an independent pinned reference engine/dataset.
- Record exact circuit/project parameters, operating envelope, analysis settings, probes, initial state, engine/model/package versions, environment, and deterministic seed.
- Include nominal, boundary, invalid, and relevant temperature/failure vectors.

## Deliverables

- Machine-readable candidate and reference results.
- Human-readable comparison covering: **Threshold region, on loss, switching transient**.
- Structured diagnostics for every invalid or non-convergent vector.
- Traceability and coverage links for all families/variants/packages using this fixture.

## Acceptance

1. Assertions pass the exact limits in `NUMERICAL_ACCURACY_TARGETS.md` or a stricter family-specific limit.
2. The reference is independent of the implementation under test and includes version/provenance/license details.
3. Repeated execution with identical inputs and seed reproduces the required deterministic state and event order.
4. Boundary/failure vectors return the specified result or structured diagnostic, never a silent approximation.
5. Requirement, task, component/package coverage, and release evidence are updated together.

## Definition of Done

- [ ] Reference, inputs, expected values/features, and tolerances are complete.
- [ ] Nominal, boundary, and failure evidence passes.
- [ ] Environment and provenance make the evidence reproducible.
- [ ] No implementation behavior was changed inside this validation-only task.
