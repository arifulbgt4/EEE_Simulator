# VAL-GRC-003 - Validate Current source and resistor

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Target | Current source and resistor |
| Requirements | REQ-008, REQ-009, REQ-010, REQ-011 |
| Golden fixture | GRC-003 |
| Test ID | TEST-GRC-003 |
| Release | R2 |
| Concern | Validation only |
| Depends on | Exact prerequisite IDs listed below |

## Exact prerequisites

- `PLAT-QA-001`
- `Gate G1 editor foundation`
- `CMP-SOURCES-LOADS-INDEPENDENT-CURRENT-SHARED-F1-VALIDATION`
- `CMP-PASSIVES-RESISTOR-SHARED-F1-VALIDATION`

Every named task must be `Done` and every named predecessor gate accepted before this card may become `Ready`.

## Public contracts

- `SimulationRequest`, `SimulationResult`, `Diagnostic`, deterministic provenance, and the applicable component/package contracts.
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Objective

Produce independent, reproducible evidence for **Compliance behavior and node voltage** without changing the model or feature under test.

## Context to read

- [Golden reference circuits](../../quality/GOLDEN_REFERENCE_CIRCUITS.md)
- [Numerical accuracy targets](../../quality/NUMERICAL_ACCURACY_TARGETS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- Applicable component family, package, engine, and public-contract documents.

## Reference and inputs

- Record the analytical solution or an independent pinned reference engine/dataset.
- Record exact circuit/project parameters, operating envelope, analysis settings, probes, initial state, engine/model/package versions, environment, and deterministic seed.
- Include nominal, boundary, invalid, and relevant temperature/failure vectors.

## Allowed files

- `docs/tasks/validation/val-grc-003.md`
- `docs/tasks/validation/INDEX.md`
- `docs/quality/GOLDEN_REFERENCE_CIRCUITS.md`
- `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`
- `docs/quality/TEST_AND_VALIDATION_STRATEGY.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

This validation-only card cannot modify the implementation under test. Exact fixture-data/result paths must be appended when the card is promoted to `Ready` under completed `PLAT-GOV-001`.

## Documentation updates

- This card, `docs/tasks/validation/INDEX.md`, `docs/quality/test-registry.yaml`, and the GRC-003 fixture row.
- Every referenced family/package coverage row, requirement traceability row, and applicable release checklist.
- Reference provenance, environment, limitations, and retained evidence links only; no implementation behavior.

## Acceptance test ID

- `TEST-GRC-003`

## Deliverables

- Machine-readable candidate and reference results.
- Human-readable comparison covering: **Compliance behavior and node voltage**.
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
