# PLAT-OFF-008 - Validate offline restart and crash recovery

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-OFF-001](../epics/epic-off-001.md) |
| Release | R1 |
| Requirements | REQ-006, REQ-029 |
| Concern | `validate_offline_restart_and_crash_recovery` |
| Effort | S |
| Depends on | PLAT-OFF-007 |

## Objective

Validate offline restart and crash recovery. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/STORAGE_VERSIONING_AND_COLLABORATION.md](../../architecture/STORAGE_VERSIONING_AND_COLLABORATION.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-OFF-007`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/STORAGE_VERSIONING_AND_COLLABORATION.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/STORAGE_VERSIONING_AND_COLLABORATION.md` clauses governing **offline restart and crash recovery**, together with every acceptance obligation in REQ-006, REQ-029.
- Prerequisite input: the completion evidence for `PLAT-OFF-007`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_OFF_008_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `validate_offline_restart_and_crash_recovery`: IndexedDB schema and transactions, command journals, snapshots, cached assets, quota state, migrations, and backup packages; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-OFF-008.
- Evidence input: `TEST-PLAT-OFF-008-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-OFF-008-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-off-008-validate-offline-restart-and-crash-recovery.md`
- `docs/tasks/epics/epic-off-001.md`
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
- `TEST-PLAT-OFF-008-ACCEPTANCE`
- `TEST-PLAT-OFF-008-FAILURE`

## Deliverables

- A reproducible validation report named `validate_offline_restart_and_crash_recovery` for **offline restart and crash recovery**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-OFF-008` fixture classifies every pinned reference fixture against its expected value, tolerance, and diagnostic; the published outcome is atomically recoverable local project state and storage diagnostics.
- Failure outcome: `PLAT_OFF_008_FIXTURE_INVALID` and `PLAT_OFF_008_REFERENCE_MISMATCH` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-OFF-008-ACCEPTANCE` and `TEST-PLAT-OFF-008-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-006, REQ-029, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-off-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/STORAGE_VERSIONING_AND_COLLABORATION.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_OFF_008_NOMINAL`: processing a minimal valid **offline restart and crash recovery** fixture classifies every pinned reference fixture against its expected value, tolerance, and diagnostic; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_OFF_008_BOUNDARY`: the **offline restart and crash recovery** fixture matrix covers first save, empty database, quota warning, interrupted transaction, version upgrade, offline restart, and crash-replay edge; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_OFF_008_FIXTURE_INVALID`: reject a corrupt record, checksum mismatch, unsupported schema, incomplete journal batch, unauthorized cache entry, or malformed backup before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_OFF_008_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-OFF-007`; no implicit migration or downgrade is allowed.
- `PLAT_OFF_008_REFERENCE_MISMATCH`: contain transaction abort, quota exhaustion, migration failure, stale cache, crash recovery divergence, or silent unsynchronized-data loss with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-OFF-008-ACCEPTANCE` proves that **Validate offline restart and crash recovery** classifies every pinned reference fixture against its expected value, tolerance, and diagnostic, produces atomically recoverable local project state and storage diagnostics, and satisfies every metadata requirement: REQ-006, REQ-029.
2. `TEST-PLAT-OFF-008-FAILURE` executes `PLAT_OFF_008_FIXTURE_INVALID`, `PLAT_OFF_008_PREREQUISITE_MISMATCH`, and `PLAT_OFF_008_REFERENCE_MISMATCH` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/STORAGE_VERSIONING_AND_COLLABORATION.md`, prerequisite `PLAT-OFF-007`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-OFF-008 card, its epic, test registry entries `TEST-PLAT-OFF-008-ACCEPTANCE` and `TEST-PLAT-OFF-008-FAILURE`, requirement links REQ-006, REQ-029, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
