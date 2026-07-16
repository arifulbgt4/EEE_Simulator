# PLAT-HPC-003 - Define scalable worker-pool orchestration

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-HPC-001](../epics/epic-hpc-001.md) |
| Release | R11 |
| Requirements | REQ-017, REQ-029, REQ-030, REQ-032, REQ-059 |
| Concern | `scalable_hpc_worker_pool_orchestration` |
| Effort | S |
| Depends on | PLAT-HPC-002; PLAT-API-014; PLAT-OPS-012 |
| Blocks | PLAT-HPC-004, PLAT-HPC-011 |

## Objective

Define one scheduler-neutral orchestration contract that partitions an accepted HPC workload into immutable shards, leases them only to compatible isolated pools, and converges retries, cancellation, drain, scale, and partial failure to one authoritative deterministic job state.

## Context to read

- [Local, Cloud, and Worker Architecture](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md), job state machine and worker lifecycle
- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md), attempts, events, fencing, cancellation
- [Deployment Operations and Observability](../../architecture/DEPLOYMENT_OPERATIONS_AND_OBSERVABILITY.md), worker pools and autoscaling
- [Security, Privacy, and Sandboxing](../../architecture/SECURITY_PRIVACY_AND_SANDBOXING.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- Accepted adapter and isolation contracts/evidence from `PLAT-HPC-002`.
- Completed `PLAT-API-014` lease, duplicate-delivery, recovery, and authoritative-publication evidence.
- Completed `PLAT-OPS-012` capacity, drain, scale, and queue-policy evidence.

## Public contracts

- `HpcWorkerPoolProfile`
- `HpcWorkloadClass`
- `HpcShardPlan`
- `HpcShardIdentity`
- `HpcShardLease`
- `HpcShardAttempt`
- `HpcPoolEvent`
- `HpcOrchestrationManifest`

`HpcShardIdentity` derives from the immutable execution-plan hash, partition-algorithm revision, and logical shard ordinal—not from worker, queue delivery, attempt, or completion order. Retries create new attempts under the same shard identity.

## Exact inputs and reference basis

- Accepted execution plan; adapter capability; workload class; pool/image/profile revisions; region/data-residency class; resource estimate; tenant quota reservation; priority and fairness class; partition algorithm/revision; shard count and bounds; retry/cancel/checkpoint policy; queue event sequence; lease duration and fencing; capacity snapshot; expected artifact policy.
- Nominal fixtures: one shard/one worker and multi-shard/multi-worker. Boundary fixtures: zero eligible capacity, one available slot, exact queue/lease/attempt limit, scale-to-zero, drain at lease boundary, cancellation during dispatch and completion publication.
- Failure fixtures: duplicate delivery, stale fence, lost heartbeat, worker crash, pool eviction, incompatible image, region mismatch, poisoned shard, repeated retry, queue outage, control-plane restart, partial result, starvation, and quota revocation.
- This concern has no numerical solver equation. State transitions follow the accepted job state machine. Selection uses only server-authoritative compatibility, quota, priority/fairness, capacity, locality, and policy inputs; every tie is resolved by a documented stable key.

## Allowed files

- `docs/tasks/platform/plat-hpc-003-define-scalable-worker-pool-orchestration.md`
- `docs/tasks/epics/epic-hpc-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/DEPLOYMENT_OPERATIONS_AND_OBSERVABILITY.md`
- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`
- `docs/quality/PERFORMANCE_BENCHMARKS.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No orchestrator, queue, autoscaler, cluster, deployment, source/test path, or provider configuration is authorized while `Planned`.

## Expected outputs and known limitations

- Versioned schemas/examples for pool, workload, shard, lease, attempt, event, and orchestration manifests; a complete state/diagnostic table; and reproducible scheduling/failure evidence.
- Human-readable, non-color-only queue, capacity, cancellation, and failure summaries. The contract is scheduler-neutral and does not promise capacity, latency, or fairness beyond measured named profiles.

## Required behavior and diagnostics

- `PLAT_HPC_003_NOMINAL`: all shards have stable identities, compatible leases, fenced attempts, bounded ordered events, and exactly one accepted terminal disposition.
- `PLAT_HPC_003_BOUNDARY`: exact pool, shard, lease, retry, queue, fairness, and scale limits produce their declared state without off-by-one admission.
- `PLAT_HPC_003_NO_ELIGIBLE_POOL`: reject or remain durably queued according to policy, with exact capability/region/quota mismatch reasons; never route to a weaker pool.
- `PLAT_HPC_003_STALE_FENCE`: reject heartbeat, checkpoint, result, cost, and terminal writes from a superseded attempt.
- `PLAT_HPC_003_SHARD_EXHAUSTED`: terminate or quarantine a repeatedly failing shard at the declared attempt limit and preserve every attempt cause.
- `PLAT_HPC_003_STARVATION`: emit an actionable policy breach when bounded wait/fairness guarantees fail; priority cannot starve protected classes indefinitely.
- `PLAT_HPC_003_CANCEL_RACE`: cancellation wins or loses only by the documented authoritative transition/fence order; no new shard starts after the cancellation barrier.
- `PLAT_HPC_003_PARTIAL_PUBLICATION`: temporary shard artifacts remain non-authoritative until the complete manifest or explicitly declared partial-result policy is accepted.

## Acceptance tests and evidence

1. `TEST-PLAT-HPC-003-ACCEPTANCE` validates stable partition/shard identities, compatible pool selection, scaling, draining, fairness, cancellation, fenced publication, and deterministic terminal aggregation.
2. `TEST-PLAT-HPC-003-FAILURE` executes every diagnostic above plus queue/control-plane outage and pool loss; no duplicate authoritative result, quota bypass, cross-region route, or sandbox downgrade occurs.
3. A replay with different worker count, lease reassignment, retry placement, and completion order preserves shard identities and declared final state.
4. Evidence includes immutable plans/profiles/images, capacity and quota snapshots, queue/event timelines, leases/fences, attempts, scale decisions, artifact states, resource usage, diagnostics, and limitations.

## Documentation updates on completion

- Synchronize this card/epic, indexes, worker/API/operations/security contracts, performance evidence, atomic tests, RTM, risks, and G11 checklist.
- Record exact fairness, wait, lease, retry, scaling, drain, locality, placement, and partial-publication policies plus measured boundary evidence.

## Forbidden scope

- Do not define MPI rank behavior, Monte Carlo sample derivation, thermal domain decomposition, result reduction, checkpoint format, storage lifecycle, or billing algorithms owned by later cards.
- Do not use best-effort routing that weakens sandbox, license, region, image, quota, or capability requirements.
- Do not infer pool suitability from labels or Source PDF prose.

## Definition of Done

- [ ] All public identities, state transitions, tie-breakers, limits, fences, and diagnostics are versioned and testable.
- [ ] Nominal, capacity, fairness, retry, worker loss, stale fence, cancellation, outage, drain, and scale evidence passes.
- [ ] Repartition/retry/scheduling changes cannot create duplicate authority or mutate immutable shard identities.
- [ ] Central records and G11 evidence are synchronized before status advances.
- [ ] No runtime infrastructure was created or modified by this documentation task.
