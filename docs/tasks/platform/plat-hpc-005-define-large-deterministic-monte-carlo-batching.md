# PLAT-HPC-005 - Define large deterministic Monte Carlo batching

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-HPC-001](../epics/epic-hpc-001.md) |
| Release | R11 |
| Requirements | REQ-013, REQ-017, REQ-030, REQ-043, REQ-046, REQ-053, REQ-059 |
| Concern | `large_deterministic_monte_carlo_batching` |
| Effort | S |
| Depends on | PLAT-HPC-004; PLAT-ANL-008; PLAT-REAL-021 |
| Blocks | PLAT-HPC-007, PLAT-HPC-011 |

## Objective

Define one large-run Monte Carlo batching contract whose global sample identities, parameter draws, classification inputs, and provenance remain unchanged when batch size, worker count, rank placement, retry count, or completion order changes.

## Context to read

- [Simulation Engine](../../architecture/SIMULATION_ENGINE.md), parameter sweep and Monte Carlo
- [Applied Physics and Real-World Fidelity](../../architecture/APPLIED_PHYSICS_AND_REAL_WORLD_FIDELITY.md), uncertainty and deterministic seeds
- [Numerical Accuracy Targets](../../quality/NUMERICAL_ACCURACY_TARGETS.md), deterministic replay
- [Local, Cloud, and Worker Architecture](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- Completed `PLAT-ANL-008` sampler/distribution contract and deterministic fixtures.
- Completed `PLAT-REAL-021` uncertainty, correlation, evidence-state, and physical-lineage contract.
- Accepted MPI/HPC execution profile from `PLAT-HPC-004`.

## Public contracts

- `MonteCarloRunPlan`
- `MonteCarloSampleIdentity`
- `MonteCarloBatchPlan`
- `MonteCarloBatchAttempt`
- `MonteCarloSampleOutcome`
- `MonteCarloBatchManifest`

`MonteCarloSampleIdentity` is exactly `(run_plan_hash, sampler_revision, master_seed, global_sample_index)`. The sampler derives each random stream solely from that identity and the declared variable/correlation-group identity. Batch and worker identities are never seed inputs.

## Exact inputs, equations, and reference data

- Immutable model/project/execution revisions; analysis; distributions, truncation, correlations, mismatch/lot/process grouping; sampler and seed-derivation revisions; master seed; global half-open sample interval `[0, sample_count)`; batch partition revision and size; pass/fail/metric specification; engine/image/MPI profile; retry/cancel/checkpoint policy; output and retention request; uncertainty and reference envelope.
- Partition invariant: ordered batch intervals are disjoint, cover `[0, sample_count)` exactly once, and preserve each global index. For batch size `b > 0`, batch `k` owns `[k*b, min((k+1)*b, sample_count))`.
- Statistical calculations and confidence/coverage claims use only algorithms, finite-sample rules, and precision specified by `PLAT-ANL-008`/`PLAT-REAL-021` or an explicitly reviewed revision. This card does not invent a confidence claim.
- Nominal fixtures: one sample, one batch; multiple batches/ranks; correlated variables; pass/fail metric. Boundary fixtures: sample_count 1 and maximum declared count, batch size 1 and maximum, final short batch, truncated distribution edge, zero-variance variable, cancellation/checkpoint at batch edge.
- Failure fixtures: sample_count/batch zero or overflow, interval gap/overlap, duplicate/missing sample, unknown distribution, invalid correlation matrix, out-of-validity draw, non-finite result, engine failure, retry with changed input, quota exhaustion, and aggregate requested before completion policy permits it.
- Independent analytical/statistical references and exact sampler specifications must be pinned by version/hash. Source PDF prose is not statistical or deterministic evidence.

## Allowed files

- `docs/tasks/platform/plat-hpc-005-define-large-deterministic-monte-carlo-batching.md`
- `docs/tasks/epics/epic-hpc-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/SIMULATION_ENGINE.md`
- `docs/architecture/APPLIED_PHYSICS_AND_REAL_WORLD_FIDELITY.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`
- `docs/quality/PERFORMANCE_BENCHMARKS.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No sampler, solver, worker, source/test path, benchmark execution, or cloud run is authorized while `Planned`.

## Expected outputs and known limitations

- Versioned run/sample/batch/attempt/outcome/manifest schemas, partition and seed-identity conformance vectors, diagnostics catalog, and deterministic replay evidence.
- Human-readable, non-color-only progress, incomplete-coverage, and failed-sample summaries. Deterministic draws do not guarantee deterministic third-party floating output, statistical confidence, or physical accuracy beyond the declared evidence class.

## Required behavior and diagnostics

- `PLAT_HPC_005_NOMINAL`: the partition covers every global index exactly once; sample parameter draws and outcome identities match the single-worker reference regardless of batching/scheduling.
- `PLAT_HPC_005_BOUNDARY`: exact sample/batch/distribution/correlation/validity/output limits and the final short interval are handled without gap or overflow.
- `PLAT_HPC_005_PARTITION_INVALID`: reject zero/negative/overflowing size, gap, overlap, duplicate interval, or index outside `[0, sample_count)`.
- `PLAT_HPC_005_DISTRIBUTION_INVALID`: reject unknown units/dimensions, invalid/truncated range, non-positive required scale, inconsistent correlation, or unsupported sampler revision.
- `PLAT_HPC_005_SAMPLE_CONFLICT`: quarantine duplicate outcomes that disagree in input hash, draw digest, engine/profile, or result digest; identical idempotent duplicates cannot double-count.
- `PLAT_HPC_005_SAMPLE_FAILED`: retain the sample identity, exact failure diagnostic, retry eligibility, and denominator policy; never silently redraw or renumber.
- `PLAT_HPC_005_REPRODUCIBILITY_MISMATCH`: fail comparison when a sample draw differs under identical immutable inputs or when a retry changes any pinned dependency.
- `PLAT_HPC_005_QUOTA_OR_CANCELLED`: stop new admission at the authoritative barrier, retain completed identities, mark incomplete coverage, and never present partial statistics as complete.

## Acceptance tests and evidence

1. `TEST-PLAT-HPC-005-ACCEPTANCE` compares single-worker, multi-batch, multi-rank, shuffled completion, and retry runs; global identities and parameter draws are bit-identical and outcomes meet the declared engine tolerance/determinism class.
2. `TEST-PLAT-HPC-005-FAILURE` exercises all diagnostics, duplicate conflict, non-finite result, cancellation, quota exhaustion, and corrupted batch manifest.
3. Coverage evidence proves no missing/duplicate global index and binds each outcome to model, sampler, seed, variable, engine, image, partition, attempt, and result hashes.
4. Statistical evidence states algorithm/revision, finite-sample limitations, failed-sample policy, partial-result status, and uncertainty; it cannot overstate physical accuracy.

## Documentation updates on completion

- Synchronize this card/epic, indexes, simulation/physics contracts, numerical/performance targets, tests, RTM, risks, and G11 checklist.
- Add deterministic partition/reduction drift and invalid-correlation risk links if not already explicit.

## Forbidden scope

- Do not change distribution semantics from `PLAT-ANL-008`, redraw failed samples, use batch/rank/time as a seed, discard failed samples silently, or merge outcomes in completion order.
- Do not own streaming aggregate algorithms/retention, checkpoint format, artifact storage, quotas, cost, or observability defined later.
- Do not claim scalability, statistical confidence, or physical correlation from Source PDF citations.

## Definition of Done

- [ ] Sample/batch identities, intervals, seed inputs, units, correlation, failure, partial-result, and diagnostic rules are exact.
- [ ] Single/multi-worker, batch-size, shuffled completion, retry, boundary, failure, cancellation, and quota evidence passes.
- [ ] Sample draws and coverage reproduce independently from immutable inputs.
- [ ] Central records and G11 evidence are synchronized before status advances.
- [ ] No runtime Monte Carlo work was implemented or executed by this documentation task.
