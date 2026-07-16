# PLAT-EXT-001 - Define versioned EngineAdapter lifecycle contract

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-017, REQ-024, REQ-029, REQ-032, REQ-056 |
| Concern | `define_versioned_engine_adapter_lifecycle_contract` |
| Effort | S |
| Depends on | Gate G2 Linear analog; PLAT-WASM-002; PLAT-QA-003; PLAT-SEC-008 |
| Blocks | PLAT-EXT-002 |

## Objective

Freeze one versioned `EngineAdapter` state machine covering discovery, validation, preparation, run, stream, pause, checkpoint, resume, cancel, and disposal, including legal transitions and terminal behavior.

## Context to read

- [ADR-0008](../../decisions/ADR-0008.md)
- [API and Worker Protocols, section 10](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [Local, Cloud, and Worker Architecture](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)
- [Product Requirements](../../PRODUCT_REQUIREMENTS.md)

## Exact prerequisites

- Gate G2 Linear analog acceptance evidence.
- `PLAT-WASM-002`, `PLAT-QA-003`, and `PLAT-SEC-008` completion evidence and immutable contract digests.

## Public contracts

- `EngineAdapterLifecycleV1`, `AdapterState`, `AdapterCommand`, `AdapterEvent`, `OperationDisposition`, `AdapterTerminalReason`, and `AdapterLifecycleDiagnostic` in `docs/architecture/API_AND_WORKER_PROTOCOLS.md`.
- Lifecycle invariants in ADR-0008; no engine-specific API may replace them.

## Inputs

- The ten operations and isolation constraints accepted by ADR-0008.
- Worker command/event envelope from `PLAT-WASM-002` and evidence format from `PLAT-QA-003`.
- Exact legal-state, idempotency, correlation, deadline, safe-point, terminal, and unsupported-operation fields to be resolved by this task; missing fields produce `EXT_LIFECYCLE_CONTRACT_INCOMPLETE`.
- `Source PDF` material is context only and is not a technical or conformance input.

## Allowed files

- `docs/tasks/platform/plat-ext-001-define-versioned-engine-adapter-lifecycle-contract.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact implementation and test paths defined by completed `PLAT-GOV-001`.

## Reference data and test IDs

- `TEST-PLAT-EXT-001-ACCEPTANCE`
- `TEST-PLAT-EXT-001-FAILURE`
- Fixture `EXT-LIFECYCLE-V1-MATRIX`, containing every state/operation pair and expected disposition.

## Deliverables

- A complete transition table from `new` through `discovered`, `validated`, `prepared`, `running`, `paused`, `completed|cancelled|failed`, and `disposed`.
- Command preconditions, response/event ordering, idempotency, timeout ownership, safe-point semantics, and cleanup obligations.
- Stable diagnostics for illegal order, unsupported operation, duplicate command conflict, stale correlation, timeout, terminal mutation, and use-after-dispose.
- Evidence schema binding each transition to adapter/build, request, correlation, prior-state, next-state, tick where applicable, and outcome digest.

## Documentation updates

Update this card, its epic, the API lifecycle section, task indexes, test registry, RTM, risk record, and R3 acceptance checklist when implementation evidence exists.

## Allowed scope

Only the engine-neutral lifecycle, state transitions, command/event semantics, and their evidence contract.

## Forbidden scope

- No ngspice-specific callback, netlist translation, numerical equation, UI, job-queue, Xyce, HPC, or imported-model implementation.
- No silent fallback, invented checkpoint support, application code, package configuration, dependency installation, or distribution approval.

## Required behavior and edge cases

- A legal command transitions once and emits one correlated accepted/rejected response; identical idempotent replay cannot create a second run.
- `stream` is observable only after `run` acceptance; `pause` and `checkpoint` occur only at declared safe points.
- An operation declared unsupported is rejected before state mutation with `EXT_OPERATION_UNSUPPORTED`.
- Calls before discovery, after a terminal state except `dispose`, or after `dispose` fail deterministically.
- Cancellation races have one authoritative terminal state and preserve the last accepted tick; disposal is irreversible.
- Unknown required protocol versions or fields fail closed; optional additive fields follow the documented compatibility rule.

## Acceptance tests

1. `TEST-PLAT-EXT-001-ACCEPTANCE` exhaustively evaluates `EXT-LIFECYCLE-V1-MATRIX`, including all ten operations, legal replay, terminal paths, and disposal.
2. `TEST-PLAT-EXT-001-FAILURE` covers every illegal transition, unsupported operation, correlation conflict, timeout, cancellation race, and use-after-dispose with stable diagnostics and no state leak.
3. Evidence records exact protocol and fixture digests, prerequisite versions, expected/actual transitions, event order, and requirement links.
4. The audit proves the lifecycle contract derives from accepted repository decisions and current evidence, not from an unconfirmed `Source PDF` citation.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Every state/operation cell has exactly one disposition.
- [ ] Nominal, boundary, failure, cancellation, and compatibility evidence passes.
- [ ] Public contracts, tests, RTM, risks, indexes, and R3 checklist are synchronized.
- [ ] No engine-specific or runtime scope was added.
