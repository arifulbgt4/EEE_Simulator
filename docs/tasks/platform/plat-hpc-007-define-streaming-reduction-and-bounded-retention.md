# PLAT-HPC-007 - Define streaming reduction and bounded retention

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-HPC-001](../epics/epic-hpc-001.md) |
| Release | R11 |
| Requirements | REQ-007, REQ-013, REQ-017, REQ-030, REQ-033, REQ-043, REQ-053, REQ-055, REQ-059 |
| Concern | `streaming_reduction_and_bounded_retention` |
| Effort | S |
| Depends on | PLAT-HPC-005; PLAT-HPC-006; PLAT-PERF-004; PLAT-PERF-005 |
| Blocks | PLAT-HPC-008, PLAT-HPC-011 |

## Objective

Define one streaming-reduction contract that produces deterministic, provenance-complete aggregates from Monte Carlo and thermal result streams while enforcing explicit memory, queue, output, raw-data, waveform, and derived-artifact retention bounds.

## Context to read

- [Performance, Browser, Accessibility, and I18N](../../architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md), waveform bounds and reduction
- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md), chunk/event transport
- [Storage, Versioning, and Collaboration](../../architecture/STORAGE_VERSIONING_AND_COLLABORATION.md), result lifecycle
- [Numerical Accuracy Targets](../../quality/NUMERICAL_ACCURACY_TARGETS.md)
- [Performance Benchmarks](../../quality/PERFORMANCE_BENCHMARKS.md)

## Exact prerequisites

- Accepted immutable sample and batch identities from `PLAT-HPC-005`.
- Accepted thermal grid, partition, probe, and result identities from `PLAT-HPC-006`.
- Completed `PLAT-PERF-004` waveform ring-buffer/decimation and `PLAT-PERF-005` selective-probe contracts.

## Public contracts

- `StreamingReductionPlan`
- `ReductionInputChunk`
- `ReductionAccumulatorState`
- `ReductionMergeNode`
- `ReductionResultManifest`
- `RetentionClass`
- `RetentionDecision`
- `BackpressureEvent`

The plan pins input identity/range, metric and unit, finite/non-finite policy, accumulator algorithm/revision/precision, canonical merge tree, chunk/output bounds, approximation and error envelope, requested probes/statistics/quantiles, raw/derived retention classes, and lineage.

## Exact inputs, equations, and reference data

- Ordered logical sample/cell/time identities; chunk hashes and sequence/range; metric schema/units; reduction operations; numeric type/precision; missing/failed/non-finite policy; canonical merge algorithm; error/overflow policy; memory/in-flight/chunk/result/diagnostic bounds; raw/waveform/summary retention classes; tenant/project/policy; object lifecycle; cancellation and partial-result policy.
- For mean/variance where the accepted plan selects the pairwise count/mean/`M2` algorithm, combining ordered states `A` and `B` uses `n=n_A+n_B`, `delta=mean_B-mean_A`, `mean=mean_A+delta*n_B/n`, and `M2=M2_A+M2_B+delta^2*n_A*n_B/n`. Empty-state handling, precision, overflow, and final sample/population divisor are explicit.
- The merge tree is built from logical input ranges and algorithm revision, not arrival time. A changed chunk size may change leaves but must resolve through a declared canonical logical-range tree or a newly versioned tolerance class; completion-order merging is forbidden.
- Min/max/count, sums, histograms, quantiles, yield, thermal extrema/integrals, and decimated waveform outputs are supported only when named by the plan. Approximate quantiles/decimation must state algorithm, retained state, deterministic behavior, and worst-case or empirically validated error envelope.
- Nominal fixtures: ordered and shuffled chunks; one and multiple workers; Monte Carlo count/mean/variance/yield; thermal min/max/integral; retained raw plus summary. Boundary fixtures: empty allowed/forbidden stream, one observation, exact memory/in-flight/output limit, final partial chunk, all-failed policy, extreme finite values, retention expiry edge, and slow consumer.
- Failure fixtures: duplicate/conflicting/missing range, unit/schema mismatch, non-finite input, numeric overflow, accumulator incompatibility, corrupt chunk, out-of-order beyond buffer policy, backpressure timeout, storage unavailable, retention-policy conflict, cancellation, and unauthorized raw retention.
- Analytical reduction fixtures and pinned algorithm specifications are reference data. Source PDF citations are not numerical or retention evidence.

## Allowed files

- `docs/tasks/platform/plat-hpc-007-define-streaming-reduction-and-bounded-retention.md`
- `docs/tasks/epics/epic-hpc-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/STORAGE_VERSIONING_AND_COLLABORATION.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`
- `docs/quality/PERFORMANCE_BENCHMARKS.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No streaming service, reducer, storage lifecycle, source/test path, deployment, or result deletion is authorized while `Planned`.

## Expected outputs and known limitations

- Versioned plan/chunk/accumulator/merge/result/retention/backpressure schemas, algorithm and error-envelope fixtures, bounded-resource evidence, and complete diagnostics.
- Human-readable, non-color-only coverage, approximation, retention, and partial-result summaries. Only reductions explicitly selected by the immutable plan are supported; raw-data deletion can limit future reanalysis and must be visible before policy takes effect.

## Required behavior and diagnostics

- `PLAT_HPC_007_NOMINAL`: valid logical ranges reduce once into the declared aggregates and manifest regardless of arrival order; retained artifacts match explicit policy.
- `PLAT_HPC_007_BOUNDARY`: exact numeric, chunk, in-flight, memory, output, error, retention, expiry, and consumer-lag limits are enforced.
- `PLAT_HPC_007_RANGE_INVALID`: reject missing, overlapping, duplicate-conflicting, or out-of-domain logical ranges; identical retries are idempotent.
- `PLAT_HPC_007_SCHEMA_OR_UNIT_MISMATCH`: reject incompatible metric, unit/dimension, algorithm, precision, accumulator, or manifest revision before merge.
- `PLAT_HPC_007_NUMERIC_INVALID`: classify non-finite/overflow/underflow according to declared policy; never convert it silently to zero or omit it.
- `PLAT_HPC_007_BACKPRESSURE_LIMIT`: pause bounded producers, spill only to approved bounded storage, or cancel/fail according to policy; never grow memory or queue without limit.
- `PLAT_HPC_007_APPROXIMATION_UNDECLARED`: reject an approximate quantile, histogram, waveform, or aggregate with no algorithm/error/retention declaration.
- `PLAT_HPC_007_RETENTION_DENIED`: reject unauthorized/conflicting raw retention or deletion and preserve required lineage/legal-hold state.
- `PLAT_HPC_007_PARTIAL_RESULT`: clearly mark coverage, missing/failed identities, denominator, limitations, and non-final status; partial cannot impersonate a complete aggregate.

## Acceptance tests and evidence

1. `TEST-PLAT-HPC-007-ACCEPTANCE` compares canonical ordered, shuffled, rechunked, retried, and different-worker streams; exact aggregates or declared tolerance/error envelopes and lineage match.
2. `TEST-PLAT-HPC-007-FAILURE` exercises all diagnostics, slow/failed consumers, storage outage, cancellation, corrupt chunks, numeric limits, retention expiry/hold conflict, and unauthorized access.
3. Stress evidence demonstrates declared peak memory, in-flight bytes/chunks, output size, producer pause/cancel latency, and storage growth bounds on the named reference profile.
4. Evidence records plan/chunk/range/algorithm/merge-tree hashes, units/precision, raw and reduced results, coverage, error bounds, resource telemetry, retention decisions, expected/actual diagnostics, and limitations.

## Documentation updates on completion

- Synchronize this card/epic, indexes, performance/API/storage contracts, numerical/performance evidence, tests, RTM, risks, and G11 checklist.
- Link bounded storage and reproducibility risks, and add deterministic-reduction/backpressure risks if not explicitly covered.

## Forbidden scope

- Do not merge in arrival order, ignore failed/missing observations, silently approximate, retain all raw data by default, delete held evidence, or weaken authorization.
- Do not define checkpoint compatibility, archival retrieval, quota pricing, or telemetry ownership from later cards.
- Do not claim numerical accuracy, scalability, or retention adequacy from Source PDF prose.

## Definition of Done

- [ ] All input/range/accumulator/merge/error/coverage/backpressure/retention contracts and diagnostics are exact and versioned.
- [ ] Ordered/shuffled/rechunked/retried, numeric, unit, memory, output, slow-consumer, partial, retention, and failure evidence passes.
- [ ] Peak resource and storage bounds are measured on a named profile; approximation/error and data-loss semantics are visible.
- [ ] Central records and G11 evidence are synchronized before status advances.
- [ ] No runtime reduction or storage deletion was performed by this documentation task.
