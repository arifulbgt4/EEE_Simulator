# PLAT-API-002 - Implement request validation and capability routing

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-API-001](../epics/epic-api-001.md) |
| Release | R10 |
| Requirements | REQ-029, REQ-030 |
| Concern | `implement_request_validation_and_capability_routing` |
| Effort | S |
| Depends on | PLAT-API-001 |

## Objective

Implement request validation and capability routing. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/API_AND_WORKER_PROTOCOLS.md](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-API-001`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/API_AND_WORKER_PROTOCOLS.md` clauses governing **request validation and capability routing**, together with every acceptance obligation in REQ-029, REQ-030.
- Prerequisite input: the completion evidence for `PLAT-API-001`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_API_002_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_request_validation_and_capability_routing`: versioned requests, job and attempt IDs, idempotency keys, leases and fences, event sequences, checkpoints, and quota profiles; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-API-002.
- Evidence input: `TEST-PLAT-API-002-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-API-002-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-api-002-implement-request-validation-and-capability-routing.md`
- `docs/tasks/epics/epic-api-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001` without widening this concern.

## Reference data and test IDs

- Normative reference: `docs/architecture/API_AND_WORKER_PROTOCOLS.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-API-002-ACCEPTANCE`
- `TEST-PLAT-API-002-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_request_validation_and_capability_routing` for **request validation and capability routing**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-API-002` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is authoritative job state, ordered events, and checksummed result references.
- Failure outcome: `PLAT_API_002_INVALID_INPUT` and `PLAT_API_002_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-API-002-ACCEPTANCE` and `TEST-PLAT-API-002-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-029, REQ-030, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-api-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_API_002_NOMINAL`: processing a minimal valid **request validation and capability routing** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_API_002_BOUNDARY`: the **request validation and capability routing** fixture matrix covers duplicate submission, duplicate delivery, lease expiry, SSE reconnect, cancellation race, and event-retention expiry; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_API_002_INVALID_INPUT`: reject a malformed request, unauthorized project revision, reused key with a changed body, stale fence, or incompatible checkpoint before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_API_002_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-API-001`; no implicit migration or downgrade is allowed.
- `PLAT_API_002_EXECUTION_FAILURE`: contain quota rejection, worker loss, corrupt result chunk, queue outage, cancellation timeout, or terminal-state conflict with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-API-002-ACCEPTANCE` proves that **Implement request validation and capability routing** accepts the minimal valid input and produces the documented deterministic state transition or output, produces authoritative job state, ordered events, and checksummed result references, and satisfies every metadata requirement: REQ-029, REQ-030.
2. `TEST-PLAT-API-002-FAILURE` executes `PLAT_API_002_INVALID_INPUT`, `PLAT_API_002_PREREQUISITE_MISMATCH`, and `PLAT_API_002_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/API_AND_WORKER_PROTOCOLS.md`, prerequisite `PLAT-API-001`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-API-002 card, its epic, test registry entries `TEST-PLAT-API-002-ACCEPTANCE` and `TEST-PLAT-API-002-FAILURE`, requirement links REQ-029, REQ-030, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
