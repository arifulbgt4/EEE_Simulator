# PLAT-EXT-010 - Implement pause safe-point policy

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-017, REQ-024, REQ-029 |
| Concern | `implement_pause_safe_point_policy` |
| Effort | XS |
| Depends on | PLAT-EXT-009 |
| Blocks | PLAT-EXT-011 |

## Objective

Pause a running adapter only at a capability-declared safe point, or reject the operation as unsupported without changing authoritative state.

## Context to read

- [API and Worker Protocols, EngineAdapter lifecycle](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [Multi-Fidelity and Co-Simulation](../../architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md)
- [ADR-0008](../../decisions/ADR-0008.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- `PLAT-EXT-009` ordered stream and current run-state evidence.

## Public contracts

- `AdapterPauseRequestV1`, `PauseSafePoint`, `PauseDisposition`, and `PauseDiagnostic`.

## Inputs

- Run/correlation authority, current accepted tick/sequence, discovered pause capability, safe-point definition, pause deadline, and in-flight stream state. ngspice support must be proven from the pinned build; PDF context cannot assert it.

## Allowed files

- `docs/tasks/platform/plat-ext-010-implement-pause-safe-point-policy.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while `Planned`; exact implementation and test paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-010-ACCEPTANCE`, `TEST-PLAT-EXT-010-FAILURE`, fixture `EXT-PAUSE-SAFE-POINT-V1`.

## Deliverables

- Safe-point definition, request/idempotency/race rules, bounded acknowledgement, accepted-tick/sequence snapshot, and explicit `supported|unsupported|conditional` disposition.
- Diagnostics for unsupported pause, wrong state, stale authority, no safe point before deadline, terminal race, and inconsistent stream boundary.

## Documentation updates

Synchronize card/epic, lifecycle contract, indexes, tests, RTM, risk, and R3 checklist.

## Allowed scope

Pause negotiation and transition only.

## Forbidden scope

No checkpoint creation, resume, cancellation, process suspension outside the reviewed policy, invented upstream capability, or loss of buffered required events.

## Required behavior and edge cases

- Unsupported pause rejects before mutation and leaves the run active.
- Supported pause acknowledges only after a documented safe point and stream boundary; repeated identical request is idempotent.
- Completion/failure/cancel winning the race prevents a false paused state.
- Timeout reports exact last accepted tick/sequence and a deterministic running-or-terminal disposition.

## Acceptance tests

1. Acceptance covers supported and explicitly unsupported builds, safe-point boundary, idempotent replay, and event ordering.
2. Failure covers stale authority, wrong state, deadline, terminal/cancel race, and inconsistent callback boundary without ambiguous state.
3. Evidence pins build/capability, request, run, safe-point, tick/sequence, and disposition digests.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Pause support is truthful and state-safe.
- [ ] Nominal, unsupported, race, and timeout evidence passes.
- [ ] Records are synchronized; checkpoint/resume scope is untouched.
