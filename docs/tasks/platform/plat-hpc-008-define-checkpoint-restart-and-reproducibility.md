# PLAT-HPC-008 - Define checkpoint, restart, and reproducibility

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-HPC-001](../epics/epic-hpc-001.md) |
| Release | R11 |
| Requirements | REQ-013, REQ-015, REQ-019, REQ-030, REQ-043, REQ-053, REQ-059 |
| Concern | `hpc_checkpoint_restart_and_reproducibility` |
| Effort | S |
| Depends on | PLAT-HPC-007; PLAT-API-009 |
| Blocks | PLAT-HPC-009, PLAT-HPC-011 |

## Objective

Define one HPC checkpoint/restart contract that captures an atomic, compatibility-verifiable computation cut and proves whether resumed Monte Carlo or thermal execution reproduces the declared uninterrupted-run result class with complete lineage.

## Context to read

- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md), checkpoint/resume lifecycle
- [Local, Cloud, and Worker Architecture](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md), worker recovery
- [Multi-Fidelity and Co-Simulation](../../architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md), deterministic scheduler boundaries
- [Numerical Accuracy Targets](../../quality/NUMERICAL_ACCURACY_TARGETS.md)
- [Storage, Versioning, and Collaboration](../../architecture/STORAGE_VERSIONING_AND_COLLABORATION.md)

## Exact prerequisites

- Completed `PLAT-API-009` job checkpoint/resume state and authorization contract.
- Accepted streaming reducer and retention boundaries from `PLAT-HPC-007`.
- Immutable Monte Carlo sample/batch and thermal partition/exchange identities from `PLAT-HPC-005` and `PLAT-HPC-006` as inherited through `PLAT-HPC-007`.

## Public contracts

- `HpcCheckpointRequest`
- `HpcCheckpointBarrier`
- `HpcCheckpointManifest`
- `HpcCheckpointShardState`
- `HpcRestartCompatibilityDecision`
- `HpcRestartAttempt`
- `HpcReproducibilityBundle`
- `HpcReplayComparison`

The manifest pins project/model/execution/analysis/sampler/partition/reducer/engine/adapter/image/MPI/scheduler/profile revisions and hashes; global logical progress; per-shard/rank state; reducer state; pending messages/exchanges; numerical state; environment; seed/timebase; artifact chunks; fence; schema/endianness/precision; and compatibility policy.

## Exact inputs, rules, and reference data

- Current fenced attempt; accepted quiescence/barrier phase; logical progress ranges; pending/in-flight events and messages; engine-native and canonical state; solver/integrator/preconditioner state where required; sample or thermal partition states; accumulator state; exact versions/hashes; environment/locale/timezone; CPU/accelerator class where compatibility requires it; output state; credentials policy; encryption/integrity; retention; checkpoint cadence; cancellation/deadline.
- Atomicity rule: a checkpoint is publishable only after every required shard/rank reaches the same declared logical barrier and every manifest/chunk is uploaded, hashed, authorized, and committed; otherwise it remains temporary and non-resumable.
- Compatibility is an explicit predicate over every pinned field. A changed field is allowed only by a versioned migration/equivalence rule with evidence; “same major version,” latest image, or available worker is insufficient.
- Reproducibility class is explicit: bit-identical, deterministic logical/classification equivalence, numerical tolerance envelope, or non-reproducible/unsupported. It includes the exact comparison metrics and reasons.
- Nominal fixtures: uninterrupted versus one checkpoint/resume for Monte Carlo and thermal workload; restart on a different eligible host; repeated restart. Boundary fixtures: checkpoint before first unit, after last complete unit, exact cadence/size/time limit, final reduction boundary, cancellation around commit, and expiry edge.
- Failure fixtures: missing/corrupt chunk, split barrier, stale fence, changed engine/image/model/sampler/partition/reducer/MPI/profile, unsupported migration, partial upload, object-store outage, no eligible worker, expired credentials/checkpoint, duplicate commit, and replay mismatch.
- Reference is the uninterrupted execution under identical pinned inputs plus independent deterministic fixture expectations. Source PDF page citations cannot prove checkpoint compatibility or reproducibility.

## Allowed files

- `docs/tasks/platform/plat-hpc-008-define-checkpoint-restart-and-reproducibility.md`
- `docs/tasks/epics/epic-hpc-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`
- `docs/architecture/STORAGE_VERSIONING_AND_COLLABORATION.md`
- `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No checkpoint implementation, object write/delete, worker restart, source/test path, or compatibility migration is authorized while `Planned`.

## Expected outputs and known limitations

- Versioned request/barrier/manifest/shard/compatibility/restart/bundle/comparison schemas, compatibility matrix, corruption/replay fixtures, and reproducibility evidence.
- Human-readable, non-color-only resume availability, incompatibility, expiry, and mismatch summaries. Resume is limited to exact supported engine/profile/state revisions; a checkpoint does not promise portability across arbitrary binaries, hardware, or numerical methods.

## Required behavior and diagnostics

- `PLAT_HPC_008_NOMINAL`: publish one atomic manifest, resume through a new fenced attempt, continue from the exact logical cut, and meet the declared uninterrupted comparison class without duplicate/omitted work.
- `PLAT_HPC_008_BOUNDARY`: exact cadence, size, time, progress, retention, compatibility, expiry, and cancellation boundaries are enforced.
- `PLAT_HPC_008_BARRIER_INCOMPLETE`: do not publish a resumable checkpoint if any required shard/rank/state/message is absent or not quiescent.
- `PLAT_HPC_008_CHECKPOINT_CORRUPT`: reject any manifest/chunk hash, size, schema, encryption, authorization, or dependency mismatch before allocation.
- `PLAT_HPC_008_INCOMPATIBLE`: return a field-by-field compatibility decision and compatible alternatives; no silent migration, approximation, or restart-from-zero masquerading as resume.
- `PLAT_HPC_008_STALE_FENCE`: reject old attempts' checkpoint commit, mutation, usage, or completion.
- `PLAT_HPC_008_REPLAY_MISMATCH`: retain both evidence bundles and report first divergent logical identity/metric, expected/actual, tolerance/reproducibility class, and dependency/environment difference.
- `PLAT_HPC_008_RESTART_UNAVAILABLE`: preserve the original checkpoint and durable retry/cancel/export options when no eligible worker/profile exists.
- `PLAT_HPC_008_EXPIRED`: deny resume after policy expiry unless an explicit legal-hold/archive/restore workflow produces a new authorized reference.

## Acceptance tests and evidence

1. `TEST-PLAT-HPC-008-ACCEPTANCE` compares uninterrupted, checkpointed, host-moved, repeated-restart, and retry executions for both Monte Carlo and thermal fixtures under each supported reproducibility class.
2. `TEST-PLAT-HPC-008-FAILURE` exercises every diagnostic, kill during barrier/upload/commit/resume, corrupt chunks, version mismatch, stale fence, storage outage, expiry, and no-capacity path.
3. Evidence proves atomic visibility, no duplicated/omitted logical identities, exact compatibility evaluation, bounded checkpoint overhead/size, deterministic cleanup, and retained original artifacts.
4. `HpcReproducibilityBundle` includes every input/model/engine/environment/configuration/seed/partition/checkpoint/result/evidence hash, official tool revisions, event timeline, expected/actual comparison, limitations, and verification command.

## Documentation updates on completion

- Synchronize this card/epic, indexes, API/worker/co-simulation/storage contracts, numerical evidence, tests, RTM, risks, and G11 checklist.
- Link worker-loss and engine-update risks and add split-barrier/checkpoint-migration risk if existing controls are insufficient.

## Forbidden scope

- Do not call a partial upload a checkpoint, resume across unapproved version/environment changes, discard the original on failed migration, duplicate logical work, or downgrade the reproducibility class silently.
- Do not define archive retrieval, pricing/quota, or telemetry concerns owned by later cards.
- Do not use Source PDF citations as checkpoint/restart/replay evidence.

## Definition of Done

- [ ] Checkpoint/barrier/shard/restart/bundle/comparison contracts and compatibility predicate are exact and versioned.
- [ ] Uninterrupted/resumed/host-moved/repeated, atomicity, corruption, incompatibility, kill, stale, expiry, outage, and replay evidence passes.
- [ ] Resource/size/latency overhead and reproducibility limitations are measured and visible.
- [ ] Central records and G11 evidence are synchronized before status advances.
- [ ] No runtime checkpoint or restart was performed by this documentation task.
