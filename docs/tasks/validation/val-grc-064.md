# VAL-GRC-064 - Validate Physical regulator load response

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Target | Physical regulator load response |
| Requirements | REQ-039, REQ-040, REQ-041, REQ-042, REQ-043, REQ-044, REQ-045, REQ-046, REQ-047 |
| Golden fixture | GRC-064 |
| Physical benchmark | PBC-010 |
| Test ID | TEST-GRC-064 |
| Release | R4 |
| Concern | Independent physical correlation only |
| Depends on | Exact prerequisite IDs below |

## Objective

Produce independent, reproducible physical-to-simulation correlation evidence for **Physical regulator load response** without changing the model, solver, instrument, or feature under test.

## Exact prerequisites

- `PLAT-QA-001`
- `Gate G3 nonlinear analog`
- `PLAT-PHY-007`
- `PLAT-PHY-008`
- `PLAT-REAL-021`

All named tasks and the predecessor gate must be complete before promotion to `Ready`. Exact component/model/package task IDs, specimen ordering codes, equipment records, and raw-data paths must be appended at promotion; documentation existence is not experimental evidence.

## Public contracts

- `docs/quality/PHYSICAL_BENCHMARK_AND_CORRELATION_CONTRACT.md`
- `docs/architecture/APPLIED_PHYSICS_AND_REAL_WORLD_FIDELITY.md`
- `docs/catalog/model-registry.yaml`
- `SimulationRequest`, `SimulationResult`, `Diagnostic`, model lineage, and deterministic provenance
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact inputs

The fixture manifest must pin stable fixture ID, exact schematic and `.eesim` digest, BOM, manufacturer ordering codes, packages, measured tolerances, specimen count, source and wiring, equipment IDs, calibration state/date, ambient/enclosure/airflow conditions, procedure revision, raw-data object digests, model and dependency revisions, simulation configuration, seed, processing method, expected/measured outputs, uncertainty budget, acceptance envelope, limitations, and analyst/reviewer identity.

## Allowed files

- `docs/tasks/validation/val-grc-064.md`
- `docs/tasks/validation/INDEX.md`
- `docs/quality/GOLDEN_REFERENCE_CIRCUITS.md`
- `docs/quality/PHYSICAL_BENCHMARK_AND_CORRELATION_CONTRACT.md`
- `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`
- `docs/quality/TEST_AND_VALIDATION_STRATEGY.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

This validation-only card cannot modify implementation, model, calibration, or measured data. Exact fixture/raw/result paths must be appended only when promotion rules are satisfied.

## Required assertions and failure cases

- Primary assertion: Measured regulation, dropout, transient response, ripple, current limit and heating.
- `GRC_064_NOMINAL`: candidate output is compared with retained physical measurements using the declared metric, interval, sample alignment, and category-specific envelope.
- `GRC_064_BOUNDARY`: minimum/maximum declared operating points, environmental bounds, instrument range, source limit, and applicable tolerance corners are classified explicitly.
- `GRC_064_DIMENSION_INVALID`: incompatible or missing units reject the fixture before comparison.
- `GRC_064_CALIBRATION_INVALID`: missing, expired, or out-of-scope calibration prevents a verified/correlated status.
- `GRC_064_VALIDITY_EXCEEDED`: out-of-envelope operation is reported as unsupported, never silently accepted or extrapolated as accurate.
- `GRC_064_LINEAGE_INCOMPLETE`: missing specimen, model, dependency, raw-data, processing, license, or digest lineage prevents publication.

## Acceptance

1. `TEST-GRC-064` evaluates nominal, boundary, invalid-unit, calibration, validity, and lineage vectors without using the implementation under test as its physical reference.
2. Expected and measured values, residual/error calculation, combined uncertainty, coverage factor or interval, category-specific threshold, and pass/fail/unsupported status are retained at every assertion point.
3. Reprocessing the immutable raw data with the same procedure, revisions, configuration, and seed reproduces the same evidence digest and classification.
4. Visual realism, a vendor typical curve, or agreement with another simulator is not substituted for calibrated physical evidence.
5. Requirement, model, component/package, task, test, risk, and R4 release evidence resolve bidirectionally.

## Known limitations

- This is a specified but unexecuted validation card; its existence is not passing evidence and cannot advance a component, model, platform feature, or release state.
- Evidence proves only the named fixture, assertions, reference identity, operating envelope, configuration, and uncertainty recorded by this card. It cannot establish broader device-population, vendor, physical-accuracy, security, performance, or compatibility claims.
- Exact primary/independent/physical reference records, license status, fixture/result paths, and current execution evidence must exist before acceptance. Source PDF context alone is never a valid reference, and this validation-only task cannot modify the model or implementation under test.

## Definition of Done

- [ ] Exact specimen, BOM, source, environment, equipment, calibration, procedure, raw data, models, and analysis inputs are immutable and complete.
- [ ] Nominal, boundary, invalid, and unsupported vectors have reproducible evidence.
- [ ] Accuracy and uncertainty claims stay inside the validated envelope and limitations are visible.
- [ ] No implementation behavior or measured evidence was altered by this validation task.
