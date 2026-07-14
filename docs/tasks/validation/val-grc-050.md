# VAL-GRC-050 - Validate Discrete, optoelectronic and power package physical set

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Target | Discrete, optoelectronic and power package physical set |
| Requirements | REQ-037 |
| Golden fixture | GRC-050 |
| Test ID | TEST-GRC-050 |
| Release | R1 |
| Concern | Validation only |
| Depends on | Exact prerequisite IDs listed below |

## Exact prerequisites

- `PLAT-QA-001`
- `Gate G0 documentation baseline`
- `CMP-PACKAGE-RADIAL-2-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-SMD-DIODE-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-LED-ROUND-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-LED-RECTANGULAR-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-LED-SMD-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-SOT-23-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-SOT-89-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-SOT-223-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-TO-92-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-TO-126-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-TO-220-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-TO-247-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-DPAK-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-D2PAK-TEMPLATE-F0-VALIDATION`
- `CMP-PACKAGE-POWER-MODULE-TEMPLATE-F0-VALIDATION`

Every named task must be `Done` and every named predecessor gate accepted before this card may become `Ready`.

## Public contracts

- `SimulationRequest`, `SimulationResult`, `Diagnostic`, deterministic provenance, and the applicable component/package contracts.
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Objective

Produce independent, reproducible evidence for **radial passive, diode, LED, SOT/TO/DPAK and power-module recognition; polarity/orientation, contact count and pin labels** without changing the model or feature under test.

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

- `docs/tasks/validation/val-grc-050.md`
- `docs/tasks/validation/INDEX.md`
- `docs/quality/GOLDEN_REFERENCE_CIRCUITS.md`
- `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`
- `docs/quality/TEST_AND_VALIDATION_STRATEGY.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

This validation-only card cannot modify the implementation under test. Exact fixture-data/result paths must be appended when the card is promoted to `Ready` under completed `PLAT-GOV-001`.

## Documentation updates

- This card, `docs/tasks/validation/INDEX.md`, `docs/quality/test-registry.yaml`, and the GRC-050 fixture row.
- Every referenced family/package coverage row, requirement traceability row, and applicable release checklist.
- Reference provenance, environment, limitations, and retained evidence links only; no implementation behavior.

## Acceptance test ID

- `TEST-GRC-050`

## Deliverables

- Machine-readable candidate and reference results.
- Human-readable comparison covering: **Polarity/orientation marks, recognizable bodies, lead count and pin labels**.
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
