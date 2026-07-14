# PLAT-WASM-003 - Build single-threaded WASM capability path

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-WASM-001](../epics/epic-wasm-001.md) |
| Release | R2 |
| Requirements | REQ-029, REQ-033 |
| Concern | `build_single_threaded_wasm_capability_path` |
| Effort | S |
| Depends on | PLAT-WASM-002 |

## Objective

Build single-threaded WASM capability path. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-WASM-002`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md` clauses governing **single-threaded WASM capability path**, together with every acceptance obligation in REQ-029, REQ-033.
- Prerequisite input: the completion evidence for `PLAT-WASM-002`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_WASM_003_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `build_single_threaded_wasm_capability_path`: TypeScript/Rust protocol schemas, WASM build digests, Worker capabilities, transfer buffers, memory limits, headers, and cancellation signals; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-WASM-003.
- Evidence input: `TEST-PLAT-WASM-003-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-WASM-003-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-wasm-003-build-single-threaded-wasm-capability-path.md`
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
- `TEST-PLAT-WASM-003-ACCEPTANCE`
- `TEST-PLAT-WASM-003-FAILURE`

## Deliverables

- A digest-addressed build artifact and compatibility record named `build_single_threaded_wasm_capability_path` for **single-threaded WASM capability path**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-WASM-003` fixture produces the documented artifact and passes its interface, provenance, and compatibility checks; the published outcome is versioned off-main-thread execution behavior and build-equivalence evidence.
- Failure outcome: `PLAT_WASM_003_BUILD_INPUT_INVALID` and `PLAT_WASM_003_BUILD_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-WASM-003-ACCEPTANCE` and `TEST-PLAT-WASM-003-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-029, REQ-033, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-wasm-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_WASM_003_NOMINAL`: processing a minimal valid **single-threaded WASM capability path** fixture produces the documented artifact and passes its interface, provenance, and compatibility checks; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_WASM_003_BOUNDARY`: the **single-threaded WASM capability path** fixture matrix covers single-thread fallback, threaded startup, zero-length and maximum buffer, memory-growth edge, cancellation poll, and Worker restart; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_WASM_003_BUILD_INPUT_INVALID`: reject a protocol-version mismatch, malformed message, stale build digest, absent cross-origin isolation, detached buffer, or illegal memory range before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_WASM_003_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-WASM-002`; no implicit migration or downgrade is allowed.
- `PLAT_WASM_003_BUILD_FAILURE`: contain Worker crash, deadlock, main-thread block, out-of-memory, lost cancellation, corrupt transfer, or threaded/single-thread result divergence with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-WASM-003-ACCEPTANCE` proves that **Build single-threaded WASM capability path** produces the documented artifact and passes its interface, provenance, and compatibility checks, produces versioned off-main-thread execution behavior and build-equivalence evidence, and satisfies every metadata requirement: REQ-029, REQ-033.
2. `TEST-PLAT-WASM-003-FAILURE` executes `PLAT_WASM_003_BUILD_INPUT_INVALID`, `PLAT_WASM_003_PREREQUISITE_MISMATCH`, and `PLAT_WASM_003_BUILD_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`, prerequisite `PLAT-WASM-002`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-WASM-003 card, its epic, test registry entries `TEST-PLAT-WASM-003-ACCEPTANCE` and `TEST-PLAT-WASM-003-FAILURE`, requirement links REQ-029, REQ-033, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
