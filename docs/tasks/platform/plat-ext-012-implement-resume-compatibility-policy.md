# PLAT-EXT-012 - Implement resume compatibility policy

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-017, REQ-024, REQ-029, REQ-053 |
| Concern | `implement_resume_compatibility_policy` |
| Effort | S |
| Depends on | PLAT-EXT-011 |
| Blocks | PLAT-EXT-013 |

## Objective

Resume only from a complete checkpoint whose immutable compatibility fingerprint exactly satisfies the current adapter, engine, plan, model, policy, and state-format contract.

## Context to read

- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [Local, Cloud, and Worker Architecture](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md)
- [Deployment, Operations, and Observability](../../architecture/DEPLOYMENT_OPERATIONS_AND_OBSERVABILITY.md)
- [ADR-0008](../../decisions/ADR-0008.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- `PLAT-EXT-011` checkpoint capability/publication evidence.

## Public contracts

- `AdapterResumeRequestV1`, `ResumeCompatibilityDecision`, `RestoredStateManifest`, and `ResumeDiagnostic`.

## Inputs

- Checkpoint bytes/digest/fingerprint, current build/adapter/plan/model/policy/resource identities, discovered resume support, target run authority, and restore deadline.

## Allowed files

- `docs/tasks/platform/plat-ext-012-implement-resume-compatibility-policy.md`
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

- `TEST-PLAT-EXT-012-ACCEPTANCE`, `TEST-PLAT-EXT-012-FAILURE`, fixture `EXT-RESUME-COMPATIBILITY-V1`.

## Deliverables

- Exact compatibility comparison, checksum/authentication, restore staging, atomic paused-to-running transition, restored tick/sequence/state manifest, unsupported behavior, and rollback rule.
- Compatibility may use an explicitly versioned reviewed transform only if a separate accepted contract names every transformed field; no implicit migration.

## Documentation updates

Synchronize task/epic, resume contracts, indexes, tests, RTM, risk, and R3 checklist.

## Allowed scope

Resume compatibility validation and restore transition only.

## Forbidden scope

No best-effort restore, human-version-only matching, mutable alias resolution, checkpoint rewrite, silent seed/state reset, or retry orchestration.

## Required behavior and edge cases

- Any build, adapter, state-format, plan, model, timebase, capability, or policy incompatibility rejects before authoritative state changes.
- Corruption, truncation, replay under another authority, expired authorization, quota, and restore timeout roll back to a non-running state.
- Successful resume continues from the exact accepted tick/sequence/random state and emits correlated restored/running events once.
- Unsupported resume is explicit even when checkpoint storage exists.

## Acceptance tests

1. Acceptance proves identical compatible restore, exact state/tick continuity, idempotent command behavior, and ordered events.
2. Failure mutates each fingerprint field and checkpoint bytes independently, plus authority/timeout/quota races; every case rejects or rolls back deterministically.
3. Evidence records old/new identities, compatibility decision, restored-state digest, and no implicit migration.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Resume occurs only for exact compatible state.
- [ ] Corruption/mismatch/race rollback evidence passes.
- [ ] Records are synchronized; cancellation remains separate.
