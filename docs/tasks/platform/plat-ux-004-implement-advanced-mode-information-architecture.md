# PLAT-UX-004 - Implement Advanced mode information architecture

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-UX-001](../epics/epic-ux-001.md) |
| Release | R1 |
| Requirements | REQ-003, REQ-034 |
| Concern | `implement_advanced_mode_information_architecture` |
| Effort | S |
| Depends on | PLAT-UX-003 |

## Objective

Implement Advanced mode information architecture. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/USER_ROLES_AND_USE_CASES.md](../../USER_ROLES_AND_USE_CASES.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-UX-003`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md` clauses governing **Advanced mode information architecture**, together with every acceptance obligation in REQ-003, REQ-034.
- Prerequisite input: the completion evidence for `PLAT-UX-003`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_UX_004_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_advanced_mode_information_architecture`: user mode, navigation state, commands, panels, help content, localization keys, diagnostics, and saved preferences; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-UX-004.
- Evidence input: `TEST-PLAT-UX-004-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-UX-004-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-ux-004-implement-advanced-mode-information-architecture.md`
- `docs/tasks/epics/epic-ux-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001` without widening this concern.

## Reference data and test IDs

- Normative reference: `docs/architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-UX-004-ACCEPTANCE`
- `TEST-PLAT-UX-004-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_advanced_mode_information_architecture` for **Advanced mode information architecture**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-UX-004` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is consistent localized workspace behavior and usability evidence.
- Failure outcome: `PLAT_UX_004_INVALID_INPUT` and `PLAT_UX_004_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-UX-004-ACCEPTANCE` and `TEST-PLAT-UX-004-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-003, REQ-034, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-ux-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_UX_004_NOMINAL`: processing a minimal valid **Advanced mode information architecture** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_UX_004_BOUNDARY`: the **Advanced mode information architecture** fixture matrix covers first-run state, empty project, text expansion, bidirectional layout, missing preference, reduced motion, and narrow supported viewport; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_UX_004_INVALID_INPUT`: reject a missing localization key, unavailable command, stale navigation target, unsafe help link, or inconsistent mode capability before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_UX_004_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-UX-003`; no implicit migration or downgrade is allowed.
- `PLAT_UX_004_EXECUTION_FAILURE`: contain dead-end workflow, hidden diagnostic, semantic change by user mode, inaccessible control, or unrecoverable preference state with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-UX-004-ACCEPTANCE` proves that **Implement Advanced mode information architecture** accepts the minimal valid input and produces the documented deterministic state transition or output, produces consistent localized workspace behavior and usability evidence, and satisfies every metadata requirement: REQ-003, REQ-034.
2. `TEST-PLAT-UX-004-FAILURE` executes `PLAT_UX_004_INVALID_INPUT`, `PLAT_UX_004_PREREQUISITE_MISMATCH`, and `PLAT_UX_004_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md`, prerequisite `PLAT-UX-003`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-UX-004 card, its epic, test registry entries `TEST-PLAT-UX-004-ACCEPTANCE` and `TEST-PLAT-UX-004-FAILURE`, requirement links REQ-003, REQ-034, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
