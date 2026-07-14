# PLAT-WASM-010 - Benchmark worker and WASM overhead

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-WASM-001](../epics/epic-wasm-001.md) |
| Release | R2 |
| Requirements | REQ-029, REQ-033 |
| Concern | `benchmark_worker_and_wasm_overhead` |
| Effort | S |
| Depends on | PLAT-WASM-009 |

## Objective

Benchmark worker and WASM overhead. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-WASM-009`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md` clauses governing **worker and WASM overhead**, together with every acceptance obligation in REQ-029, REQ-033.
- Prerequisite input: the completion evidence for `PLAT-WASM-009`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_WASM_010_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `benchmark_worker_and_wasm_overhead`: TypeScript/Rust protocol schemas, WASM build digests, Worker capabilities, transfer buffers, memory limits, headers, and cancellation signals; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-WASM-010.
- Evidence input: `TEST-PLAT-WASM-010-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-WASM-010-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-wasm-010-benchmark-worker-and-wasm-overhead.md`
- `docs/tasks/epics/epic-wasm-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001` without widening this concern.

## Reference data and test IDs

- Normative reference: `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-WASM-010-ACCEPTANCE`
- `TEST-PLAT-WASM-010-FAILURE`

## Deliverables

- A reproducible benchmark definition and result report named `benchmark_worker_and_wasm_overhead` for **worker and WASM overhead**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-WASM-010` fixture executes the pinned workload and records environment, trials, median, p95, maximum, resource use, and regression threshold; the published outcome is versioned off-main-thread execution behavior and build-equivalence evidence.
- Failure outcome: `PLAT_WASM_010_BENCHMARK_INVALID` and `PLAT_WASM_010_BUDGET_REGRESSION` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-WASM-010-ACCEPTANCE` and `TEST-PLAT-WASM-010-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-029, REQ-033, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-wasm-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_WASM_010_NOMINAL`: processing a minimal valid **worker and WASM overhead** fixture executes the pinned workload and records environment, trials, median, p95, maximum, resource use, and regression threshold; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_WASM_010_BOUNDARY`: the **worker and WASM overhead** fixture matrix covers single-thread fallback, threaded startup, zero-length and maximum buffer, memory-growth edge, cancellation poll, and Worker restart; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_WASM_010_BENCHMARK_INVALID`: reject a protocol-version mismatch, malformed message, stale build digest, absent cross-origin isolation, detached buffer, or illegal memory range before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_WASM_010_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-WASM-009`; no implicit migration or downgrade is allowed.
- `PLAT_WASM_010_BUDGET_REGRESSION`: contain Worker crash, deadlock, main-thread block, out-of-memory, lost cancellation, corrupt transfer, or threaded/single-thread result divergence with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-WASM-010-ACCEPTANCE` proves that **Benchmark worker and WASM overhead** executes the pinned workload and records environment, trials, median, p95, maximum, resource use, and regression threshold, produces versioned off-main-thread execution behavior and build-equivalence evidence, and satisfies every metadata requirement: REQ-029, REQ-033.
2. `TEST-PLAT-WASM-010-FAILURE` executes `PLAT_WASM_010_BENCHMARK_INVALID`, `PLAT_WASM_010_PREREQUISITE_MISMATCH`, and `PLAT_WASM_010_BUDGET_REGRESSION` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`, prerequisite `PLAT-WASM-009`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-WASM-010 card, its epic, test registry entries `TEST-PLAT-WASM-010-ACCEPTANCE` and `TEST-PLAT-WASM-010-FAILURE`, requirement links REQ-029, REQ-033, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
