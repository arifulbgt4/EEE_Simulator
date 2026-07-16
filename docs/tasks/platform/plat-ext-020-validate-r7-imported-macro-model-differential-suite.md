# PLAT-EXT-020 - Validate R7 imported macro-model differential suite

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R7 |
| Requirements | REQ-014, REQ-017, REQ-024, REQ-042, REQ-043, REQ-049, REQ-053, REQ-063 |
| Concern | `validate_r7_imported_macro_model_differential_suite` |
| Effort | S |
| Depends on | PLAT-EXT-019 |
| Blocks | PLAT-EXT-021 |

## Objective

Validate every exact case in `R7-EXT-MACRO-SUITE-V1` against its declared independent reference and operating envelope without modifying imported models, adapter behavior, or fixtures.

## Context to read

- [Numerical Accuracy Targets](../../quality/NUMERICAL_ACCURACY_TARGETS.md)
- [Test and Validation Strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Source and Evidence Policy](../../SOURCE_AND_EVIDENCE_POLICY.md)
- [Model Import and Export Formats](../../catalog/MODEL_IMPORT_EXPORT_FORMATS.md)
- [Physical Benchmark and Correlation Contract](../../quality/PHYSICAL_BENCHMARK_AND_CORRELATION_CONTRACT.md)

## Exact prerequisites

- `PLAT-EXT-019` Done with immutable `R7-EXT-MACRO-SUITE-V1`, reviewed bundle/handoff, exact model/case IDs, and provenance/license/trust evidence.

## Public contracts

- `ImportedMacroDifferentialSuiteV1`, `MacroModelCaseResult`, `ValidityDecision`, `ToleranceEnvelope`, `DivergenceDiagnostic`, and `MacroModelEvidenceBundle`.

## Inputs

- Exact frozen suite cases/model revisions; ngspice and independent reference identities; analyses/probes/environment/config/seed; supported syntax/transform records; per-case validity, uncertainty, tolerances/metrics, expected failures, and known limitations.

## Allowed files

- `docs/tasks/platform/plat-ext-020-validate-r7-imported-macro-model-differential-suite.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`
- `docs/quality/TEST_AND_VALIDATION_STRATEGY.md`
- `docs/quality/PHYSICAL_BENCHMARK_AND_CORRELATION_CONTRACT.md`
- `docs/SOURCE_AND_EVIDENCE_POLICY.md`
- `docs/catalog/MODEL_IMPORT_EXPORT_FORMATS.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/validation/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No implementation, model, or source-fixture edit is authorized. Exact immutable candidate/reference result and evidence paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-020-ACCEPTANCE`, `TEST-PLAT-EXT-020-FAILURE`, and every exact test ID frozen in `R7-EXT-MACRO-SUITE-V1`.

## Deliverables

- Candidate/reference raw results, deterministic comparison outputs, metric/tolerance/validity decisions, convergence/failure comparison, transformation impact, provenance closure, and status for every exact case.
- Coverage proof that no suite case/model was skipped, inherited without evidence, or counted twice; deviations outside validity are `out_of_validity`, not a pass/fail accuracy claim.

## Documentation updates

Synchronize card/epic, accuracy/validation/import/coverage records, indexes, tests, RTM, risks, and R7 checklist.

## Allowed scope

Validation of the frozen R7 imported macro-model suite only.

## Forbidden scope

No model tuning, tolerance widening after results, hidden exclusion, physical-correlation claim from simulation comparison, vendor-market coverage claim, PDF expected value, Xyce/HPC, or rerun-until-pass policy.

## Required behavior and edge cases

- Every case reports supported subset, operating envelope, actual metric, tolerance/rationale, uncertainty/limitations, convergence and diagnostic status.
- Same inputs reproduce the declared determinism/tolerance class; reference disagreement or non-convergence remains visible.
- Missing rights/trust/source/revision, transformed semantics, out-of-validity input, stale digest, and unqualified reference block/reject the case.
- Differential agreement is labeled only `differentially_verified`; physical claims require independent physical evidence.

## Acceptance tests

1. Acceptance executes and accounts for every frozen case with complete current evidence inside validity and declared limits.
2. Failure injects missing/extra/duplicate case, altered model/reference, tolerance manipulation, stale/revoked source, out-of-validity input, convergence mismatch, and false physical claim; each is rejected.
3. Evidence records raw/processed digests, exact engines/models/transforms/config/seed/environment, metrics/tolerances, status, diagnostic differences, coverage, and reviewer.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Every frozen model/case is accounted for with pass, reject, out-of-validity, or explicit blocker.
- [ ] No implementation/model/fixture was changed.
- [ ] Differential/failure/provenance/coverage evidence passes.
- [ ] R7 records are synchronized without market-wide claims.
