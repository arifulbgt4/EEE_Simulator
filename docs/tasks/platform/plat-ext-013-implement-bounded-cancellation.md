# PLAT-EXT-013 - Implement bounded cancellation

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-017, REQ-024, REQ-029, REQ-030, REQ-032 |
| Concern | `implement_bounded_cancellation` |
| Effort | S |
| Depends on | PLAT-EXT-012; PLAT-WASM-007 |
| Blocks | PLAT-EXT-014 |

## Objective

Cancel an active external analog attempt cooperatively and then enforce supervisor termination of all descendants within a declared, tested bound.

## Context to read

- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [Local, Cloud, and Worker Architecture](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md)
- [Security, Privacy, and Sandboxing](../../architecture/SECURITY_PRIVACY_AND_SANDBOXING.md)
- [ADR-0008](../../decisions/ADR-0008.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- `PLAT-EXT-012` completed lifecycle through resume policy; `PLAT-WASM-007` cancellation/yield contract.

## Public contracts

- `AdapterCancelRequestV1`, `CancellationPolicy`, `CancellationOutcome`, `DescendantTerminationEvidence`, and `CancelDiagnostic`.

## Inputs

- Attempt/authority/correlation identity, current state/tick/stream sequence, cooperative-stop mechanism, supervisor escalation stages, configured grace/deadline values, descendant set, partial-result policy, and retention policy.

## Allowed files

- `docs/tasks/platform/plat-ext-013-implement-bounded-cancellation.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while `Planned`; exact implementation and test paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-013-ACCEPTANCE`, `TEST-PLAT-EXT-013-FAILURE`, fixture `EXT-BOUNDED-CANCEL-V1`.

## Deliverables

- Idempotent cancellation state/race rules, cooperative request, escalation sequence, exact configured bounds, descendant discovery/termination, stream close, temporary-state disposition, and partial-result qualification.
- Diagnostics for stale authority, already terminal, cooperative timeout, forced termination, descendant escape, cleanup failure, and terminal race.

## Documentation updates

Synchronize card/epic, cancellation contracts, indexes, tests, RTM, risk, and R3 checklist.

## Allowed scope

Cancellation of one attempt and its descendants.

## Forbidden scope

No retry, new attempt, result success conversion, indefinite wait, orphan process, host-wide kill, or disposal of unrelated shared artifacts.

## Required behavior and edge cases

- Repeated identical cancellation returns one outcome; conflicting actor/authority cannot cancel.
- Cooperative completion inside the bound and forced termination after the bound have distinct diagnostics/evidence.
- Completion/failure/cancel race yields one terminal state and ordered final stream; retained output is explicitly partial with last accepted tick.
- All descendants, callbacks, pipes, and temporary execution resources are closed or a release-blocking cleanup failure is recorded.

## Acceptance tests

1. Acceptance measures configured cancellation bounds for cooperative and forced paths and proves descendant/stream cleanup.
2. Failure covers unresponsive engine, child spawn, callback flood, stale/duplicate request, simultaneous completion, supervisor loss, and cleanup failure without orphan or false success.
3. Evidence records monotonic control timings, simulation tick separately, process tree before/after, terminal sequence, retained artifact disposition, and diagnostic codes.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Cooperative and forced cancellation meet declared bounds.
- [ ] No descendant or authoritative running state survives.
- [ ] Race/partial/cleanup evidence and synchronized records pass.
- [ ] Retry and disposal remain separate concerns.
