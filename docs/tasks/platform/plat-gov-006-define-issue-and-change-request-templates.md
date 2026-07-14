# PLAT-GOV-006 - Define issue and change request templates

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-GOV-001](../epics/epic-gov-001.md) |
| Release | R1 |
| Requirements | REQ-034, REQ-035 |
| Concern | `define_issue_and_change_request_templates` |
| Effort | S |
| Depends on | PLAT-GOV-005 |

## Objective

Define issue and change request templates. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/START_HERE.md](../../START_HERE.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-GOV-005`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md` clauses governing **issue and change request templates**, together with every acceptance obligation in REQ-034, REQ-035.
- Prerequisite input: the completion evidence for `PLAT-GOV-005`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_GOV_006_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `define_issue_and_change_request_templates`: repository policies, ownership records, stable identifiers, task lifecycle rules, release evidence, licenses, and contributor declarations; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-GOV-006.
- Evidence input: `TEST-PLAT-GOV-006-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-GOV-006-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-gov-006-define-issue-and-change-request-templates.md`
- `docs/tasks/epics/epic-gov-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001` without widening this concern.

## Reference data and test IDs

- Normative reference: `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-GOV-006-ACCEPTANCE`
- `TEST-PLAT-GOV-006-FAILURE`

## Deliverables

- A versioned normative contract named `define_issue_and_change_request_templates` for **issue and change request templates**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-GOV-006` fixture resolves every required field, default, invariant, version rule, and public input/output without ambiguity; the published outcome is auditable governance decisions and synchronized repository records.
- Failure outcome: `PLAT_GOV_006_SCHEMA_INVALID` and `PLAT_GOV_006_COMPATIBILITY_CONFLICT` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-GOV-006-ACCEPTANCE` and `TEST-PLAT-GOV-006-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-034, REQ-035, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-gov-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_GOV_006_NOMINAL`: processing a minimal valid **issue and change request templates** fixture resolves every required field, default, invariant, version rule, and public input/output without ambiguity; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_GOV_006_BOUNDARY`: the **issue and change request templates** fixture matrix covers first release, deprecated identifier, generated file, third-party boundary, ownership handoff, and exception expiry; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_GOV_006_SCHEMA_INVALID`: reject a duplicate stable ID, missing owner, ambiguous canonical path, unlicensed artifact, or unsynchronized task/test record before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_GOV_006_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-GOV-005`; no implicit migration or downgrade is allowed.
- `PLAT_GOV_006_COMPATIBILITY_CONFLICT`: contain scope expansion, policy conflict, released unvalidated work, broken provenance, or unauthorized repository mutation with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-GOV-006-ACCEPTANCE` proves that **Define issue and change request templates** resolves every required field, default, invariant, version rule, and public input/output without ambiguity, produces auditable governance decisions and synchronized repository records, and satisfies every metadata requirement: REQ-034, REQ-035.
2. `TEST-PLAT-GOV-006-FAILURE` executes `PLAT_GOV_006_SCHEMA_INVALID`, `PLAT_GOV_006_PREREQUISITE_MISMATCH`, and `PLAT_GOV_006_COMPATIBILITY_CONFLICT` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`, prerequisite `PLAT-GOV-005`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-GOV-006 card, its epic, test registry entries `TEST-PLAT-GOV-006-ACCEPTANCE` and `TEST-PLAT-GOV-006-FAILURE`, requirement links REQ-034, REQ-035, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
