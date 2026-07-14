# PLAT-QA-009 - Create performance regression suite

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-QA-001](../epics/epic-qa-001.md) |
| Release | R0 |
| Requirements | REQ-017, REQ-022, REQ-023, REQ-034, REQ-035, REQ-036, REQ-037, REQ-038 |
| Concern | `create_performance_regression_suite` |
| Effort | S |
| Depends on | PLAT-QA-008 |

## Objective

Create performance regression suite. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/quality/TEST_AND_VALIDATION_STRATEGY.md](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-QA-008`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/quality/TEST_AND_VALIDATION_STRATEGY.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/quality/TEST_AND_VALIDATION_STRATEGY.md` clauses governing **performance regression suite**, together with every acceptance obligation in REQ-017, REQ-022, REQ-023, REQ-034, REQ-035, REQ-036, REQ-037, REQ-038.
- Prerequisite input: the completion evidence for `PLAT-QA-008`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_QA_009_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `create_performance_regression_suite`: stable requirement, task, test and gate IDs, registry records, fixtures, expected envelopes, evidence manifests, and release policies; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-QA-009.
- Evidence input: `TEST-PLAT-QA-009-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-QA-009-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-qa-009-create-performance-regression-suite.md`
- `docs/tasks/epics/epic-qa-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/TEST_AND_VALIDATION_STRATEGY.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

This documentation-only R0 task may be promoted to `Ready` after its exact predecessor is `Done`, using the paths above as its complete documentation/evidence allowlist; no application source or runtime-test path and no completed `PLAT-GOV-001` are required before G0. It does not authorize application code, package configuration, migrations, or deployment assets.

## Reference data and test IDs

- Normative reference: `docs/quality/TEST_AND_VALIDATION_STRATEGY.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-QA-009-ACCEPTANCE`
- `TEST-PLAT-QA-009-FAILURE`

## Deliverables

- A versioned test, corpus, or workflow artifact named `create_performance_regression_suite` for **performance regression suite**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-QA-009` fixture loads every declared case and resolves it to an explicit expected result, limit, and evidence owner; the published outcome is machine-auditable test evidence and release disposition.
- Failure outcome: `PLAT_QA_009_CASE_INVALID` and `PLAT_QA_009_EVIDENCE_INCOMPLETE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-QA-009-ACCEPTANCE` and `TEST-PLAT-QA-009-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-017, REQ-022, REQ-023, REQ-034, REQ-035, REQ-036, REQ-037, REQ-038, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-qa-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/quality/TEST_AND_VALIDATION_STRATEGY.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_QA_009_NOMINAL`: processing a minimal valid **performance regression suite** fixture loads every declared case and resolves it to an explicit expected result, limit, and evidence owner; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_QA_009_BOUNDARY`: the **performance regression suite** fixture matrix covers empty corpus, first/last registry entry, tolerance edge, expected failure, deferred model, and release-blocking severity boundary; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_QA_009_CASE_INVALID`: reject a duplicate or orphan ID, missing expected result, stale digest, undocumented tolerance, absent provenance, or ambiguous pass criterion before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_QA_009_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-QA-008`; no implicit migration or downgrade is allowed.
- `PLAT_QA_009_EVIDENCE_INCOMPLETE`: contain false pass, untested released model, traceability gap, reference-engine divergence, evidence tampering, or incomplete release bundle with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-QA-009-ACCEPTANCE` proves that **Create performance regression suite** loads every declared case and resolves it to an explicit expected result, limit, and evidence owner, produces machine-auditable test evidence and release disposition, and satisfies every metadata requirement: REQ-017, REQ-022, REQ-023, REQ-034, REQ-035, REQ-036, REQ-037, REQ-038.
2. `TEST-PLAT-QA-009-FAILURE` executes `PLAT_QA_009_CASE_INVALID`, `PLAT_QA_009_PREREQUISITE_MISMATCH`, and `PLAT_QA_009_EVIDENCE_INCOMPLETE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/quality/TEST_AND_VALIDATION_STRATEGY.md`, prerequisite `PLAT-QA-008`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-QA-009 card, its epic, test registry entries `TEST-PLAT-QA-009-ACCEPTANCE` and `TEST-PLAT-QA-009-FAILURE`, requirement links REQ-017, REQ-022, REQ-023, REQ-034, REQ-035, REQ-036, REQ-037, REQ-038, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
