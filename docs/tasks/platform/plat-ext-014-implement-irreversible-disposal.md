# PLAT-EXT-014 - Implement irreversible disposal

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-024, REQ-029, REQ-032, REQ-053 |
| Concern | `implement_irreversible_disposal` |
| Effort | XS |
| Depends on | PLAT-EXT-013 |
| Blocks | PLAT-EXT-015 |

## Objective

Release all private adapter state after a terminal outcome and make every later lifecycle call invalid while preserving only policy-authorized immutable evidence.

## Context to read

- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [Security, Privacy, and Sandboxing](../../architecture/SECURITY_PRIVACY_AND_SANDBOXING.md)
- [Deployment, Operations, and Observability](../../architecture/DEPLOYMENT_OPERATIONS_AND_OBSERVABILITY.md)
- [ADR-0008](../../decisions/ADR-0008.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- `PLAT-EXT-013` terminal/cancellation and descendant-cleanup evidence.

## Public contracts

- `AdapterDisposeRequestV1`, `DisposalManifest`, `RetainedEvidenceManifest`, and `DisposeDiagnostic`.

## Inputs

- Terminal adapter state, private workspace/handle/process/callback/stream/checkpoint references, retention classification, evidence digests, disposal deadline, and legal/security hold policy.

## Allowed files

- `docs/tasks/platform/plat-ext-014-implement-irreversible-disposal.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`
- `docs/architecture/DEPLOYMENT_OPERATIONS_AND_OBSERVABILITY.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while `Planned`; exact implementation and test paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-014-ACCEPTANCE`, `TEST-PLAT-EXT-014-FAILURE`, fixture `EXT-DISPOSAL-V1`.

## Deliverables

- Idempotent terminal-to-disposed transition, inventory-based cleanup, retained/quarantined/deleted classification, handle invalidation, callback detachment, library/process release policy, and bounded disposal evidence.
- Stable diagnostics for non-terminal dispose request, retained-secret violation, incomplete inventory, cleanup failure, and use-after-dispose.

## Documentation updates

Synchronize task/epic, disposal/retention contracts, indexes, tests, RTM, risk, and R3 checklist.

## Allowed scope

Disposal of one adapter instance and its private state.

## Forbidden scope

No deletion of published results/audit evidence, hard deletion of referenced immutable artifacts, disposal of other attempts, reinitialization, or use of a disposed handle.

## Required behavior and edge cases

- Disposal occurs after terminal state; repeated dispose is idempotent and returns the original manifest.
- Every inventoried resource has exactly one retained/quarantined/deleted outcome with reason and digest where retained.
- Cleanup failure leaves the instance unusable, emits release-blocking evidence, and cannot restore execution.
- Every later command receives `EXT_ADAPTER_DISPOSED` without accessing freed private state.

## Acceptance tests

1. Acceptance inventories and accounts for workspace, handles, processes, callbacks, buffers, checkpoints, streams, and retained evidence; later operations all reject.
2. Failure covers non-terminal request, missing inventory member, permission/I/O failure, retention conflict, duplicate request, and concurrent callback without resource reuse or evidence loss.
3. Evidence records before/after inventory, retention policy, disposal timing, manifest digest, and use-after-dispose results.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Disposal is complete, bounded, idempotent, and irreversible.
- [ ] Retained evidence is minimal, authorized, and content-addressed.
- [ ] Failure/use-after-dispose evidence and synchronized records pass.
