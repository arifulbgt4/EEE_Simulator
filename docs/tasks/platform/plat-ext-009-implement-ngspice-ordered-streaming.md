# PLAT-EXT-009 - Implement ngspice ordered streaming

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-007, REQ-017, REQ-024, REQ-029, REQ-033 |
| Concern | `implement_ngspice_ordered_streaming` |
| Effort | S |
| Depends on | PLAT-EXT-008 |
| Blocks | PLAT-EXT-010 |

## Objective

Convert bounded ngspice callbacks/output into one ordered, backpressured canonical stream while preserving diagnostics, accepted simulation ticks, gaps, and terminal state.

## Context to read

- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [Simulation Engine](../../architecture/SIMULATION_ENGINE.md)
- [Performance, Browser, Accessibility, and I18n](../../architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md)
- [ADR-0008](../../decisions/ADR-0008.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- `PLAT-EXT-008` active authoritative run attempt.

## Public contracts

- `NgspiceCallbackEnvelope`, `ExternalStreamSequencer`, canonical `SimulationEvent`, `WaveformChunk`, `Diagnostic`, and `StreamTerminal`.

## Inputs

- Run/correlation authority, bounded callback records, output mapping version, integer timebase, channel map, byte/frequency limits, buffer budget, and backpressure policy.

## Allowed files

- `docs/tasks/platform/plat-ext-009-implement-ngspice-ordered-streaming.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/SIMULATION_ENGINE.md`
- `docs/architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while `Planned`; exact implementation and test paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-009-ACCEPTANCE`, `TEST-PLAT-EXT-009-FAILURE`, fixture `EXT-NGSPICE-STREAM-V1`.

## Deliverables

- Callback capture boundary, monotonically sequenced stream, bounded queue, chunk construction, progress coalescing rule, terminal drain/close rule, and exact dropped/coalesced accounting.
- Stable diagnostics for callback overflow, malformed vector, output limit, consumer stall, sequence conflict, callback-after-terminal, and engine output corruption.

## Documentation updates

Synchronize task/epic, API/engine/performance contracts, indexes, tests, RTM, risk, and R3 checklist.

## Allowed scope

Ordered stream capture and canonical delivery for an already-running attempt.

## Forbidden scope

No viewport-only substitution, unbounded buffering, raw stderr as API, hidden diagnostic loss, numerical correction, or lifecycle actions owned by later tasks.

## Required behavior and edge cases

- State, diagnostics, chunk availability, and terminal events are never dropped; only superseded progress may be coalesced with accounting.
- Duplicate identical callback delivery is idempotent; conflicting sequence data fails/quarantines the result.
- Slow consumers trigger bounded backpressure or declared cancellation, never memory growth without limit.
- Terminal publication waits for accepted buffered records or explicitly marks an incomplete/partial stream.

## Acceptance tests

1. Acceptance proves ordering, chunk checksums, tick/channel mapping, bounded buffering, legal progress coalescing, and exact terminal close.
2. Failure injects duplicate/conflicting/out-of-order/malformed/oversized/late callbacks and consumer stalls; evidence proves bounded containment and no false complete result.
3. Evidence records raw callback fixture, mapping/stream versions, run identity, queue high-water marks, coalescing counts, canonical digest, and terminal disposition.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Ordered bounded streaming and backpressure evidence passes.
- [ ] Required records cannot disappear silently.
- [ ] Traceability and R3 records are synchronized.
- [ ] Pause/checkpoint/cancel/dispose remain separate tasks.
