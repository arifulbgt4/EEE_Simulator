# PLAT-EXT-008 - Implement ngspice run control

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-017, REQ-024, REQ-029, REQ-032 |
| Concern | `implement_ngspice_run_control` |
| Effort | S |
| Depends on | PLAT-EXT-007 |
| Blocks | PLAT-EXT-009 |

## Objective

Start and supervise exactly one ngspice execution from an accepted prepared handle, enforcing lifecycle, correlation, single-authority, startup deadline, and terminal-state rules.

## Context to read

- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [Local, Cloud, and Worker Architecture](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md)
- [Simulation Engine](../../architecture/SIMULATION_ENGINE.md)
- [ADR-0008](../../decisions/ADR-0008.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- `PLAT-EXT-007` valid prepared handle and workspace manifest.

## Public contracts

- `NgspiceRunCommandV1`, `ExternalRunAttempt`, `RunAuthorityToken`, `RunStateEvent`, and `RunDiagnostic`.

## Inputs

- Prepared handle/digest, pinned build, lifecycle/correlation ID, resource/sandbox profile, analysis command selected by normalized contract, startup deadline, and supervisor authority.

## Allowed files

- `docs/tasks/platform/plat-ext-008-implement-ngspice-run-control.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/architecture/SIMULATION_ENGINE.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while `Planned`; exact implementation and test paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-008-ACCEPTANCE`, `TEST-PLAT-EXT-008-FAILURE`, fixture `EXT-NGSPICE-RUN-V1`.

## Deliverables

- Single-start/idempotency rules, authority token, startup handshake, lifecycle transition, supervisor heartbeat, command allowlist, terminal ownership, and crash/launch diagnostic mapping.
- Proof that no user-supplied command line, shell, host path, environment secret, or arbitrary native option enters the run boundary.

## Documentation updates

Synchronize task/epic, API/worker/engine contracts, indexes, tests, RTM, risk, and R3 checklist.

## Allowed scope

Starting and supervising one prepared ngspice run; result streaming is owned by `PLAT-EXT-009`.

## Forbidden scope

No output normalization, pause/checkpoint/resume, cancellation policy, retry, second engine, shell execution, or unbounded descendant process.

## Required behavior and edge cases

- Only a matching unused prepared handle may transition to running; conflicting replay cannot start another attempt.
- Launch failure, missing symbol, callback registration failure, build substitution, startup timeout, premature exit, and supervisor loss produce one authoritative failure.
- Engine success is not result success until output validation/publication completes.
- Run control never blocks the browser main thread or API/control-plane process.

## Acceptance tests

1. Acceptance proves one start, exact lifecycle/event order, matching build/workspace/authority digests, and bounded startup.
2. Failure proves no duplicate run or partial authoritative success under replay, crash, missing callback, timeout, stale handle, supervisor loss, or hostile command injection.
3. Evidence captures attempt identity, allowed command/config identity, process/library boundary, timestamps for operations only, and simulation-tick authority separately.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Single-authority run control and startup failure behavior pass.
- [ ] No arbitrary command or duplicate attempt is possible.
- [ ] Traceability and R3 records are synchronized.
- [ ] Streaming and later lifecycle concerns remain separate.
