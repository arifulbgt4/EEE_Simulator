# PLAT-PROJ-004 - Define reusable package definition and pin-map records

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-PROJ-001](../epics/epic-proj-001.md) |
| Release | R1 |
| Requirements | REQ-005, REQ-006, REQ-023, REQ-038 |
| Concern | `define_reusable_package_definition_and_pin_map_records` |
| Effort | S |
| Depends on | PLAT-PROJ-003 |

## Objective

Define reusable package definition and pin-map records. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/PROJECT_FILE_FORMAT.md](../../architecture/PROJECT_FILE_FORMAT.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-PROJ-003`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/PROJECT_FILE_FORMAT.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/PROJECT_FILE_FORMAT.md` clauses governing **reusable package definition and pin-map records**, together with every acceptance obligation in REQ-005, REQ-006, REQ-023, REQ-038.
- Prerequisite input: the completion evidence for `PLAT-PROJ-003`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_PROJ_004_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `define_reusable_package_definition_and_pin_map_records`: manifest and member schemas, stable IDs, hierarchy, component/model/package references, assets, digests, versions, and migrations; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-PROJ-004.
- Evidence input: `TEST-PLAT-PROJ-004-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-PROJ-004-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-proj-004-define-reusable-package-definition-and-pin-map-records.md`
- `docs/tasks/epics/epic-proj-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/PROJECT_FILE_FORMAT.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001` without widening this concern.

## Reference data and test IDs

- Normative reference: `docs/architecture/PROJECT_FILE_FORMAT.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-PROJ-004-ACCEPTANCE`
- `TEST-PLAT-PROJ-004-FAILURE`

## Deliverables

- A versioned normative contract named `define_reusable_package_definition_and_pin_map_records` for **reusable package definition and pin-map records**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-PROJ-004` fixture resolves every required field, default, invariant, version rule, and public input/output without ambiguity; the published outcome is portable deterministic project records and migration or recovery diagnostics.
- Failure outcome: `PLAT_PROJ_004_SCHEMA_INVALID` and `PLAT_PROJ_004_COMPATIBILITY_CONFLICT` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-PROJ-004-ACCEPTANCE` and `TEST-PLAT-PROJ-004-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-005, REQ-006, REQ-023, REQ-038, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-proj-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/PROJECT_FILE_FORMAT.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_PROJ_004_NOMINAL`: processing a minimal valid **reusable package definition and pin-map records** fixture resolves every required field, default, invariant, version rule, and public input/output without ambiguity; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_PROJ_004_BOUNDARY`: the **reusable package definition and pin-map records** fixture matrix covers minimal archive, optional member absence, unknown optional field, maximum path/depth/size, and major-version edge; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_PROJ_004_SCHEMA_INVALID`: reject a missing manifest field, duplicate ID, broken reference, unsafe path, digest mismatch, invalid pin map, or unsupported required feature before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_PROJ_004_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-PROJ-003`; no implicit migration or downgrade is allowed.
- `PLAT_PROJ_004_COMPATIBILITY_CONFLICT`: contain round-trip data loss, nondeterministic packing, migration failure, corrupted archive, partial recovery ambiguity, or executable-content launch with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-PROJ-004-ACCEPTANCE` proves that **Define reusable package definition and pin-map records** resolves every required field, default, invariant, version rule, and public input/output without ambiguity, produces portable deterministic project records and migration or recovery diagnostics, and satisfies every metadata requirement: REQ-005, REQ-006, REQ-023, REQ-038.
2. `TEST-PLAT-PROJ-004-FAILURE` executes `PLAT_PROJ_004_SCHEMA_INVALID`, `PLAT_PROJ_004_PREREQUISITE_MISMATCH`, and `PLAT_PROJ_004_COMPATIBILITY_CONFLICT` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/PROJECT_FILE_FORMAT.md`, prerequisite `PLAT-PROJ-003`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-PROJ-004 card, its epic, test registry entries `TEST-PLAT-PROJ-004-ACCEPTANCE` and `TEST-PLAT-PROJ-004-FAILURE`, requirement links REQ-005, REQ-006, REQ-023, REQ-038, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
