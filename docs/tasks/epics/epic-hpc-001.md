# EPIC-HPC-001 - Large analog and HPC execution

## Outcome

Deliver the complete **Large analog and HPC execution** capability for R11: eligible large SPICE-compatible, deterministic Monte Carlo, and distributed thermal workloads run through isolated, scalable, observable, restartable, and license-governed worker infrastructure while preserving exact input, engine, partition, checkpoint, result, and environment lineage.

This epic treats the repository requirements and accepted ADRs, official engine documentation pinned by version, and reproducible test evidence as technical authorities. The feasibility Source PDF is contextual only and is not acceptance evidence or a confirmed technical specification.

## Requirements and release

- Requirements: REQ-006, REQ-007, REQ-010, REQ-013, REQ-015, REQ-017, REQ-019, REQ-024, REQ-029, REQ-030, REQ-032, REQ-033, REQ-035, REQ-042, REQ-043, REQ-045, REQ-046, REQ-053, REQ-055, REQ-056, REQ-059, REQ-061, REQ-063
- Release: R11
- Gate: G11 HPC
- Required predecessor: G10 Cloud/collaboration
- Exact entry evidence: accepted G10 release manifest plus completed `PLAT-API-014`, `PLAT-OPS-014`, `PLAT-SEC-015`, and `PLAT-IMP-012` evidence
- Downstream gate: G13 may consume G11 only after `PLAT-HPC-011` publishes an accepted G11 decision

The requirement mapping above is synchronized into the central task indexes, requirements traceability matrix, test registry, risks, roadmap, and release checklist by the documentation-baseline integration change. This epic does not itself claim that any requirement or test has passed.

## Included concerns

- G11 entry, dependency, and evidence contract.
- Xyce-class isolated adapter, external-engine capability declaration, sandbox, license, and redistribution boundary.
- Scalable worker-pool orchestration, shard leasing, fencing, retry, cancellation, drain, and failure recovery.
- MPI/HPC execution profiles with scheduler-neutral launch manifests, rank topology, resource limits, and collective-failure handling.
- Large deterministic Monte Carlo batching with stable global sample identities independent of pool size, batch size, retries, or completion order.
- Distributed thermal-grid partitioning with explicit boundary exchange, convergence, conservation, and partial-failure semantics.
- Streaming reduction with deterministic merge order, bounded raw/derived retention, backpressure, and visible loss/approximation policy.
- Checkpoint/restart compatibility and end-to-end reproducibility bundles.
- Large artifact archival, authorization, integrity, lifecycle, and retrieval.
- Quotas, admission, cost, usage accounting, metrics, traces, alerts, privacy, and operational capacity evidence.
- A final R11 audit that fails closed on missing isolation, license, reproducibility, security, performance, or traceability evidence.

## Atomic tasks

| Task | Single outcome | Exact dependencies | Status |
|---|---|---|---|
| [PLAT-HPC-001](../platform/plat-hpc-001-define-g11-entry-and-evidence-contract.md) | Define the G11 entry and evidence contract | G10, PLAT-API-014, PLAT-OPS-014, PLAT-SEC-015, PLAT-IMP-012 | Planned |
| [PLAT-HPC-002](../platform/plat-hpc-002-define-xyce-isolated-adapter-and-license-boundary.md) | Define the Xyce isolated adapter, sandbox, and license boundary | PLAT-HPC-001, PLAT-SEC-015, PLAT-IMP-012 | Planned |
| [PLAT-HPC-003](../platform/plat-hpc-003-define-scalable-worker-pool-orchestration.md) | Define scalable HPC worker-pool orchestration | PLAT-HPC-002, PLAT-API-014, PLAT-OPS-012 | Planned |
| [PLAT-HPC-004](../platform/plat-hpc-004-define-mpi-hpc-execution-profile.md) | Define the MPI/HPC execution profile | PLAT-HPC-003 | Planned |
| [PLAT-HPC-005](../platform/plat-hpc-005-define-large-deterministic-monte-carlo-batching.md) | Define deterministic large Monte Carlo batching | PLAT-HPC-004, PLAT-ANL-008, PLAT-REAL-021 | Planned |
| [PLAT-HPC-006](../platform/plat-hpc-006-define-distributed-thermal-grid-workloads.md) | Define distributed thermal-grid workloads | PLAT-HPC-004, PLAT-REAL-006, PLAT-REAL-021 | Planned |
| [PLAT-HPC-007](../platform/plat-hpc-007-define-streaming-reduction-and-bounded-retention.md) | Define streaming reduction and bounded retention | PLAT-HPC-005, PLAT-HPC-006, PLAT-PERF-004, PLAT-PERF-005 | Planned |
| [PLAT-HPC-008](../platform/plat-hpc-008-define-checkpoint-restart-and-reproducibility.md) | Define checkpoint, restart, and reproducibility behavior | PLAT-HPC-007, PLAT-API-009 | Planned |
| [PLAT-HPC-009](../platform/plat-hpc-009-define-large-artifact-archival-and-retrieval.md) | Define large artifact archival and retrieval | PLAT-HPC-008, PLAT-API-006, PLAT-API-012 | Planned |
| [PLAT-HPC-010](../platform/plat-hpc-010-define-hpc-quotas-cost-and-observability.md) | Define HPC quotas, cost controls, and observability | PLAT-HPC-009, PLAT-API-010, PLAT-API-011, PLAT-OPS-007, PLAT-OPS-008, PLAT-OPS-012 | Planned |
| [PLAT-HPC-011](../platform/plat-hpc-011-audit-r11-acceptance-evidence.md) | Audit R11 acceptance evidence and publish the G11 decision | PLAT-HPC-001..010 | Planned |

## Central traceability synchronization

The documentation baseline synchronizes this epic through the following central records; any future task status change must update them in the same change:

- requirement links shown above and `TEST-REQ-006`, `TEST-REQ-007`, `TEST-REQ-010`, `TEST-REQ-013`, `TEST-REQ-015`, `TEST-REQ-017`, `TEST-REQ-019`, `TEST-REQ-024`, `TEST-REQ-029`, `TEST-REQ-030`, `TEST-REQ-032`, `TEST-REQ-033`, `TEST-REQ-035`, `TEST-REQ-042`, `TEST-REQ-043`, `TEST-REQ-045`, `TEST-REQ-046`, `TEST-REQ-053`, `TEST-REQ-055`, `TEST-REQ-056`, `TEST-REQ-059`, `TEST-REQ-061`, and `TEST-REQ-063`;
- atomic tests `TEST-PLAT-HPC-001-ACCEPTANCE/FAILURE` through `TEST-PLAT-HPC-011-ACCEPTANCE/FAILURE`;
- risk links at minimum to RSK-007, RSK-010, RSK-012, RSK-018, RSK-019, RSK-020, RSK-027, RSK-050, RSK-057, RSK-059, and RSK-060;
- explicit new risk review for MPI collective deadlock or partial-rank failure, scheduler/pool starvation, deterministic-reduction drift, checkpoint incompatibility, artifact-integrity or retrieval failure, and HPC capacity/cost exhaustion if existing risks do not fully cover them;
- the G11 checklist evidence names defined by `PLAT-HPC-001` and audited by `PLAT-HPC-011`.

## Exit criteria

- [ ] `PLAT-HPC-001` through `PLAT-HPC-010` are `Done`, and `PLAT-HPC-011` independently audits their immutable evidence.
- [ ] G10 predecessor evidence and every cross-epic dependency resolve to immutable revisions and content hashes.
- [ ] Xyce-class execution cannot link into, execute inside, or be redistributed with the Apache-2.0 core without an explicit current legal decision; unknown or rejected license state fails closed.
- [ ] Untrusted workloads have no outbound network, use digest-pinned images, read-only roots, private scratch, non-root identities, allowlisted capabilities, and enforced CPU/memory/time/process/output limits.
- [ ] Pool size, batch size, retry count, lease reassignment, and completion order do not change deterministic Monte Carlo sample identities or declared aggregate results.
- [ ] Distributed thermal fixtures meet declared convergence, boundary continuity, conservation, accuracy, and partial-failure rules.
- [ ] Streaming reduction and retention preserve declared statistics, error bounds, provenance, and retrieval guarantees without unbounded memory or storage growth.
- [ ] Every restart uses a compatible checkpoint or fails with a stable diagnostic; no task silently resumes under changed engine, model, partition, numerical, image, or MPI revisions.
- [ ] Artifact authorization, integrity, lifecycle, legal hold, export, deletion, and retrieval evidence passes across tenant, region, and retention boundaries.
- [ ] Quota reservation, cost estimate, usage ledger, telemetry, privacy, alert, cancellation, and capacity evidence is complete and reconciled.
- [ ] `PLAT-HPC-011` publishes an immutable `G11AcceptanceManifest` and `G11ReleaseDecision`; G11 remains failed if any mandatory finding is open.
- [ ] Central indexes, tests, traceability, risks, dependency/license records, roadmap, and G11 release evidence are synchronized before any task is marked `Ready` or `Done`.

## Known limitations

- This is a documentation-only backlog. It authorizes no runtime code, cluster configuration, scheduler deployment, container image, package change, database migration, external-engine distribution, or cloud resource creation.
- Exact source/test paths must be appended under completed `PLAT-GOV-001` before implementation cards can become `Ready`.
- Xyce, MPI implementation, scheduler, cluster provider, numerical partitioning algorithm, retention durations, quota values, and pricing rates remain versioned deployment choices; each must be pinned and evidenced by its owning card rather than inferred from this epic.
