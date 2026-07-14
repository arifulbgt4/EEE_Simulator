# PLAT-COL-004 - Implement concurrent schematic edit merge

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-COL-001](../epics/epic-col-001.md) |
| Release | R10 |
| Requirements | REQ-031 |
| Concern | `implement_concurrent_schematic_edit_merge` |
| Effort | S |
| Depends on | PLAT-COL-003 |

## Objective

Implement concurrent schematic edit merge. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/STORAGE_VERSIONING_AND_COLLABORATION.md](../../architecture/STORAGE_VERSIONING_AND_COLLABORATION.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-COL-003`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/STORAGE_VERSIONING_AND_COLLABORATION.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/STORAGE_VERSIONING_AND_COLLABORATION.md` clauses governing **concurrent schematic edit merge**, together with every acceptance obligation in REQ-031.
- Prerequisite input: the completion evidence for `PLAT-COL-003`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_COL_004_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_concurrent_schematic_edit_merge`: CRDT operations, causal vectors, stable entity IDs, draft snapshots, presence messages, comments, and immutable revision records; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-COL-004.
- Evidence input: `TEST-PLAT-COL-004-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-COL-004-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-col-004-implement-concurrent-schematic-edit-merge.md`
- `docs/tasks/epics/epic-col-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/STORAGE_VERSIONING_AND_COLLABORATION.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001` without widening this concern.

## Reference data and test IDs

- Normative reference: `docs/architecture/STORAGE_VERSIONING_AND_COLLABORATION.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-COL-004-ACCEPTANCE`
- `TEST-PLAT-COL-004-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_concurrent_schematic_edit_merge` for **concurrent schematic edit merge**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-COL-004` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is converged collaboration state and immutable revision evidence.
- Failure outcome: `PLAT_COL_004_INVALID_INPUT` and `PLAT_COL_004_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-COL-004-ACCEPTANCE` and `TEST-PLAT-COL-004-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-031, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-col-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/STORAGE_VERSIONING_AND_COLLABORATION.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_COL_004_NOMINAL`: processing a minimal valid **concurrent schematic edit merge** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_COL_004_BOUNDARY`: the **concurrent schematic edit merge** fixture matrix covers offline replay, duplicate operation, delete-versus-edit, concurrent net edit, hierarchy cycle, and package pin-map conflict; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_COL_004_INVALID_INPUT`: reject a malformed operation, missing causal dependency, unauthorized actor, stale schema, duplicate ID, or oversized message before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_COL_004_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-COL-003`; no implicit migration or downgrade is allowed.
- `PLAT_COL_004_EXECUTION_FAILURE`: contain non-convergent state, silently lost edit, invalid electrical merge, disconnected WebSocket, or mutable simulation revision with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-COL-004-ACCEPTANCE` proves that **Implement concurrent schematic edit merge** accepts the minimal valid input and produces the documented deterministic state transition or output, produces converged collaboration state and immutable revision evidence, and satisfies every metadata requirement: REQ-031.
2. `TEST-PLAT-COL-004-FAILURE` executes `PLAT_COL_004_INVALID_INPUT`, `PLAT_COL_004_PREREQUISITE_MISMATCH`, and `PLAT_COL_004_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/STORAGE_VERSIONING_AND_COLLABORATION.md`, prerequisite `PLAT-COL-003`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-COL-004 card, its epic, test registry entries `TEST-PLAT-COL-004-ACCEPTANCE` and `TEST-PLAT-COL-004-FAILURE`, requirement links REQ-031, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
