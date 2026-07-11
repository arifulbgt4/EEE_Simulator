# EPIC-WASM-001 - Rust WASM and worker runtime

## Outcome

Deliver the complete **Rust WASM and worker runtime** capability for release R2, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-029, REQ-033
- Release: R2
- Entry: Gate G0 documentation baseline and every task-level dependency below.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-WASM-001](../platform/plat-wasm-001-define-typescript-to-rust-ffi-contract.md) | Define TypeScript to Rust FFI contract | Gate G0 documentation baseline | Planned |
| [PLAT-WASM-002](../platform/plat-wasm-002-define-worker-command-and-event-protocol.md) | Define worker command and event protocol | PLAT-WASM-001 | Planned |
| [PLAT-WASM-003](../platform/plat-wasm-003-build-single-threaded-wasm-capability-path.md) | Build single-threaded WASM capability path | PLAT-WASM-002 | Planned |
| [PLAT-WASM-004](../platform/plat-wasm-004-build-threaded-wasm-capability-path.md) | Build threaded WASM capability path | PLAT-WASM-003 | Planned |
| [PLAT-WASM-005](../platform/plat-wasm-005-implement-cross-origin-isolation-capability-detection.md) | Implement cross-origin-isolation capability detection | PLAT-WASM-004 | Planned |
| [PLAT-WASM-006](../platform/plat-wasm-006-implement-worker-startup-shutdown-and-crash-recovery.md) | Implement worker startup shutdown and crash recovery | PLAT-WASM-005 | Planned |
| [PLAT-WASM-007](../platform/plat-wasm-007-implement-cancellation-and-cooperative-yield.md) | Implement cancellation and cooperative yield | PLAT-WASM-006 | Planned |
| [PLAT-WASM-008](../platform/plat-wasm-008-implement-memory-ownership-and-transfer-policy.md) | Implement memory ownership and transfer policy | PLAT-WASM-007 | Planned |
| [PLAT-WASM-009](../platform/plat-wasm-009-implement-chunked-waveform-transfer.md) | Implement chunked waveform transfer | PLAT-WASM-008 | Planned |
| [PLAT-WASM-010](../platform/plat-wasm-010-benchmark-worker-and-wasm-overhead.md) | Benchmark worker and WASM overhead | PLAT-WASM-009 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
