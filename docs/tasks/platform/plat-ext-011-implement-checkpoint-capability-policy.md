# PLAT-EXT-011 - Implement checkpoint capability policy

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-017, REQ-024, REQ-029, REQ-053 |
| Concern | `implement_checkpoint_capability_policy` |
| Effort | S |
| Depends on | PLAT-EXT-010 |
| Blocks | PLAT-EXT-012 |

## Objective

Publish a complete, checksum-verified checkpoint at a compatible paused safe point, or reject checkpointing before state mutation when the pinned adapter cannot support it.

## Context to read

- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [Local, Cloud, and Worker Architecture](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md)
- [Deployment, Operations, and Observability](../../architecture/DEPLOYMENT_OPERATIONS_AND_OBSERVABILITY.md)
- [ADR-0008](../../decisions/ADR-0008.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- `PLAT-EXT-010` pause disposition and safe-point evidence.

## Public contracts

- `AdapterCheckpointRequestV1`, canonical `Checkpoint`, `CheckpointCompatibilityFingerprint`, and `CheckpointDiagnostic`.

## Inputs

- Paused state/safe point, build/adapter/plan/model/input digests, accepted tick, engine and scheduler state where supported, random state, resource limits, encryption/retention policy, and discovered capability.

## Allowed files

- `docs/tasks/platform/plat-ext-011-implement-checkpoint-capability-policy.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/architecture/DEPLOYMENT_OPERATIONS_AND_OBSERVABILITY.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while `Planned`; exact implementation and test paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-011-ACCEPTANCE`, `TEST-PLAT-EXT-011-FAILURE`, fixture `EXT-CHECKPOINT-CAPABILITY-V1`.

## Deliverables

- Checkpoint completeness schema, content digest, atomic temporary-to-published transition, compatibility fingerprint, size/time limits, unsupported disposition, and cleanup/revocation rule.
- Explicit declaration of which ngspice state can be serialized from the pinned implementation. Missing required state blocks checkpoint support.

## Documentation updates

Synchronize card/epic, checkpoint contracts, indexes, test/RTM/risk records, and R3 checklist.

## Allowed scope

Checkpoint capability and publication only.

## Forbidden scope

No fabricated checkpoint, partial checkpoint labeled resumable, cross-build promise, resume execution, implicit model lookup, or object publication before checksum/metadata commit.

## Required behavior and edge cases

- Unsupported builds reject deterministically and remain safely paused/running per documented policy.
- Checkpoint is published atomically only after every required state and checksum validates.
- Quota, serialization, storage, encryption, timeout, or crash failure leaves no resumable authoritative artifact.
- Fingerprint includes exact build, adapter, execution plan, model closure, timebase, and state-format versions.

## Acceptance tests

1. Acceptance either reconstructs a complete checkpoint and matches its fingerprint/digest or proves the declared unsupported path with no mutation.
2. Failure injects missing state, incompatible format, quota, short write, checksum mismatch, timeout, and crash; no partial artifact is resumable.
3. Evidence records every included state identity, omitted/inapplicable field rationale, limits, and publication disposition.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Checkpoint support is complete and proven or explicitly unsupported.
- [ ] Atomicity, quota, corruption, and cleanup evidence passes.
- [ ] Records are synchronized; resume remains separate.
