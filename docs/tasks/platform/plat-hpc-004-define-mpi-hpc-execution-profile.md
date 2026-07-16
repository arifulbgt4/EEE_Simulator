# PLAT-HPC-004 - Define MPI/HPC execution profile

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-HPC-001](../epics/epic-hpc-001.md) |
| Release | R11 |
| Requirements | REQ-017, REQ-030, REQ-032, REQ-035, REQ-053, REQ-056, REQ-059 |
| Concern | `mpi_hpc_execution_profile` |
| Effort | S |
| Depends on | PLAT-HPC-003 |
| Blocks | PLAT-HPC-005, PLAT-HPC-006, PLAT-HPC-011 |

## Objective

Define one scheduler-neutral, versioned MPI/HPC execution profile that resolves an accepted shard into an immutable allocation and rank launch manifest with bounded resources, deterministic rank identity, isolated communication, explicit collective-failure handling, and complete provenance.

## Context to read

- [Local, Cloud, and Worker Architecture](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md), resource profiles and worker lifecycle
- [Deployment Operations and Observability](../../architecture/DEPLOYMENT_OPERATIONS_AND_OBSERVABILITY.md), HPC pools
- [Security, Privacy, and Sandboxing](../../architecture/SECURITY_PRIVACY_AND_SANDBOXING.md), reviewed HPC profile
- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md), attempts, checkpoints, events
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- Accepted `HpcWorkerPoolProfile`, `HpcShardPlan`, lease/fence rules, and orchestration evidence from `PLAT-HPC-003`.
- A pinned scheduler/launcher and MPI implementation/version compatibility record, image/SBOM digest, node/runtime capability manifest, and security review for the exact deployment profile.
- The profile remains `Planned` if scheduler, MPI, network transport, collective behavior, failure semantics, or supported engine version is left as “applicable” or selected by an implementer.

## Public contracts

- `MpiHpcExecutionProfile`
- `HpcAllocationRequest`
- `HpcAllocationIdentity`
- `MpiRankTopology`
- `MpiLaunchManifest`
- `MpiEnvironmentAllowlist`
- `MpiCollectivePolicy`
- `MpiAttemptResult`

`MpiLaunchManifest` pins scheduler/launcher/MPI/engine/image revisions; allocation and shard IDs; node/rank/thread/GPU topology; rank-to-partition map; CPU/memory/scratch/time/process/network limits; placement/affinity; allowed environment; communication endpoints; input/output/checkpoint references; lease/fence; cancellation signals; and cleanup policy.

## Exact inputs and reference basis

- Immutable HPC shard/attempt, adapter capability, pool profile, scheduler/launcher/MPI identities and hashes, allocation constraints, exact node/rank/thread topology, binding/affinity policy, communication fabric class, environment allowlist, filesystem mounts, credentials, limits, timeout, heartbeat, collective/cancellation/checkpoint rules, expected artifacts, and test oracle.
- Nominal fixtures: single rank, multi-rank/single-node, and multi-node profile where supported. Boundary fixtures: one rank, maximum declared ranks/nodes, exact wall/memory/scratch/process limits, empty optional environment, cancellation immediately before/after collective, and node drain.
- Failure fixtures: unsupported rank count/topology, oversubscription denial, allocation timeout, launcher failure, rank nonzero exit, rank hang, collective mismatch/deadlock timeout, node loss, transport loss, inconsistent environment, stale fence, unexpected child process, network egress, and cleanup failure.
- Official, versioned scheduler/launcher/MPI documentation and the pinned engine profile are technical sources. Their exact locators, versions, retrieval dates, and hashes must be recorded. Source PDF references are contextual only.
- This task introduces no numerical simulation equation. Rank identity is the tuple `(allocation_revision, logical_partition_id, rank_ordinal)`; retry/host placement cannot mutate it. A collective result is authoritative only after every required rank and collective phase reaches its declared compatible terminal state.

## Allowed files

- `docs/tasks/platform/plat-hpc-004-define-mpi-hpc-execution-profile.md`
- `docs/tasks/epics/epic-hpc-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`
- `docs/architecture/DEPLOYMENT_OPERATIONS_AND_OBSERVABILITY.md`
- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`
- `docs/planning/DEPENDENCY_AND_LICENSE_MATRIX.md`
- `docs/planning/RISK_REGISTER.md`
- `docs/quality/PERFORMANCE_BENCHMARKS.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No scheduler, MPI runtime, cluster/network, container, source/test path, or cloud resource is authorized while `Planned`.

## Expected outputs and known limitations

- Versioned execution/allocation/rank/launch/environment/collective/result schemas, exact compatibility matrix, failure-state table, pinned primary-source record, and reproducible profile evidence.
- Portable contracts do not imply that every MPI implementation, scheduler, interconnect, collective, or fault-recovery mode is supported; unsupported combinations remain explicit diagnostics.

## Required behavior and diagnostics

- `PLAT_HPC_004_NOMINAL`: an eligible shard produces one accepted allocation and launch manifest; each rank receives only its immutable partition and least-privilege credentials, and all ranks terminate with one fenced attempt result.
- `PLAT_HPC_004_BOUNDARY`: exact rank/node/thread/memory/time/scratch/process/environment/collective limits are enforced and recorded.
- `PLAT_HPC_004_PROFILE_UNSUPPORTED`: reject incompatible engine/MPI/scheduler/image/topology/capability combinations before allocation.
- `PLAT_HPC_004_ALLOCATION_FAILED`: preserve durable queued/failed state, quota reservation disposition, retry eligibility, and scheduler diagnostic without a phantom running attempt.
- `PLAT_HPC_004_RANK_FAILED`: fail or checkpoint-restart the entire affected phase according to the declared profile; never omit a rank or silently accept a partial collective.
- `PLAT_HPC_004_COLLECTIVE_TIMEOUT`: terminate the allocation within the bounded cancellation/cleanup window and retain rank/phase evidence without indefinite resource hold.
- `PLAT_HPC_004_ISOLATION_VIOLATION`: terminate unauthorized egress, peer communication, mount/write, privilege, process, environment, or secret access.
- `PLAT_HPC_004_STALE_FENCE`: prevent stale ranks or allocation callbacks from publishing checkpoints, usage, results, or terminal authority.
- `PLAT_HPC_004_CLEANUP_INCOMPLETE`: quarantine affected nodes/scratch/artifacts and block successful completion until cleanup disposition is explicit.

## Acceptance tests and evidence

1. `TEST-PLAT-HPC-004-ACCEPTANCE` proves manifest resolution, stable rank topology, least privilege, single/multi-rank launch, ordered collective phases, cancellation, cleanup, and one fenced result.
2. `TEST-PLAT-HPC-004-FAILURE` exercises all diagnostics, including injected rank hang/loss, collective mismatch, allocation timeout, network egress, unexpected child, and stale completion.
3. Re-running the same logical partition with different eligible hosts preserves rank identities, inputs, expected event order class, and declared result/tolerance class; topology changes require a new launch manifest revision.
4. Evidence records official-source revisions, scheduler allocation/events, launcher command as a structured redacted manifest, rank mapping, environment allowlist, image/SBOM, network/filesystem observations, resource telemetry, cleanup proof, and limitations.

## Documentation updates on completion

- Synchronize this card/epic, indexes, worker/API/security/operations/license contracts, benchmark plan, tests, RTM, risks, and G11 checklist.
- Add explicit MPI collective deadlock/partial-rank/scheduler incompatibility risk treatment if existing risks do not name the accepted mitigation and evidence owner.

## Forbidden scope

- Do not choose a provider-specific scheduler API as a public domain contract, pass arbitrary launcher flags or environment variables, permit unrestricted rank-to-rank/network access, or accept partial collectives.
- Do not define Monte Carlo or thermal partition semantics, reductions, checkpoints, artifact retention, or costs owned by later cards.
- Do not infer MPI behavior, failure recovery, or scalability from the Source PDF.

## Definition of Done

- [ ] All profile, allocation, rank, launch, environment, collective, result, and diagnostic fields are exact and versioned.
- [ ] Nominal, rank/node/topology boundary, allocation, collective, security, cancellation, stale fence, and cleanup evidence passes.
- [ ] Official implementation/profile sources are pinned; portability limits and unsupported behavior are explicit.
- [ ] Central records and G11 evidence are synchronized before status advances.
- [ ] No MPI/HPC infrastructure was installed or changed by this documentation task.
