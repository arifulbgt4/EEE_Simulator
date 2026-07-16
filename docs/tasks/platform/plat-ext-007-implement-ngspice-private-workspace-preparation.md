# PLAT-EXT-007 - Implement ngspice private workspace preparation

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-024, REQ-029, REQ-032, REQ-053, REQ-056 |
| Concern | `implement_ngspice_private_workspace_preparation` |
| Effort | S |
| Depends on | PLAT-EXT-006 |
| Blocks | PLAT-EXT-008 |

## Objective

Materialize one validated request into a bounded, private, non-networked, engine-ready workspace and immutable preparation manifest without starting simulation.

## Context to read

- [Local, Cloud, and Worker Architecture](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md)
- [Security, Privacy, and Sandboxing](../../architecture/SECURITY_PRIVACY_AND_SANDBOXING.md)
- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [ADR-0008](../../decisions/ADR-0008.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- `PLAT-EXT-006` accepted validation decision whose input/build/policy digests still match.

## Public contracts

- `NgspicePreparationRequestV1`, `PrivateWorkspaceManifest`, `PreparedExecutionHandle`, and `PreparationDiagnostic`.

## Inputs

- Validated input bytes/digest, approved model/resource closure, sandbox profile, byte/file/depth limits, scratch allocation, ownership, retention, and preparation deadline.

## Allowed files

- `docs/tasks/platform/plat-ext-007-implement-ngspice-private-workspace-preparation.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while `Planned`; exact implementation and test paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-007-ACCEPTANCE`, `TEST-PLAT-EXT-007-FAILURE`, fixture `EXT-NGSPICE-PREPARE-V1`.

## Deliverables

- Workspace layout/ownership contract, read-only approved inputs, bounded writable scratch, no-network assertion, path normalization, content verification, prepared-handle lifetime, and cleanup-on-failure rule.
- Manifest of every materialized byte, source digest, local private path identifier, permissions, size, and final workspace digest; host paths are not public output.

## Documentation updates

Synchronize this card, epic, worker/security contracts, indexes, test/RTM/risk records, and R3 checklist.

## Allowed scope

Preparation of a single validated private workspace.

## Forbidden scope

No run, external retrieval, shared mutable cache without content-addressed isolation, host-path exposure, persistent secret, or unvalidated artifact.

## Required behavior and edge cases

- Preparation rechecks validation/build/policy/input digests and fails if any changed.
- Traversal, symlink escape, special file, archive bomb, duplicate normalized path, quota exhaustion, short write, and checksum mismatch roll back all authoritative prepared state.
- Repeated idempotent preparation either returns the same immutable handle or a distinct fully isolated handle according to the documented policy.
- Crash/timeout leaves only quarantined evidence subject to retention and cannot make a handle runnable.

## Acceptance tests

1. Acceptance proves exact bytes, permissions, quota accounting, no-network state, manifest digest, and absence of engine start.
2. Failure injects every path/archive/quota/I/O/digest/race error and proves rollback, cleanup, bounded evidence, and no host disclosure.
3. Evidence binds preparation to validation, build, policy, model, and input digests.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Workspace is private, bounded, reproducible, and fully manifested.
- [ ] Failure cleanup and invalidation evidence passes.
- [ ] Traceability and R3 records are synchronized.
- [ ] No run behavior was implemented.
