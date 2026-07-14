# PLAT-AUTH-002 - Implement user profile and account lifecycle

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-AUTH-001](../epics/epic-auth-001.md) |
| Release | R10 |
| Requirements | REQ-031, REQ-032 |
| Concern | `implement_user_profile_and_account_lifecycle` |
| Effort | S |
| Depends on | PLAT-AUTH-001 |

## Objective

Implement user profile and account lifecycle. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md](../../architecture/SECURITY_PRIVACY_AND_SANDBOXING.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-AUTH-001`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md` clauses governing **user profile and account lifecycle**, together with every acceptance obligation in REQ-031, REQ-032.
- Prerequisite input: the completion evidence for `PLAT-AUTH-001`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_AUTH_002_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_user_profile_and_account_lifecycle`: identity claims, sessions and tokens, organization membership, project roles, object grants, invitations, and audit context; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-AUTH-002.
- Evidence input: `TEST-PLAT-AUTH-002-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-AUTH-002-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-auth-002-implement-user-profile-and-account-lifecycle.md`
- `docs/tasks/epics/epic-auth-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001` without widening this concern.

## Reference data and test IDs

- Normative reference: `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-AUTH-002-ACCEPTANCE`
- `TEST-PLAT-AUTH-002-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_user_profile_and_account_lifecycle` for **user profile and account lifecycle**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-AUTH-002` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is least-privilege authorization decisions and auditable identity state.
- Failure outcome: `PLAT_AUTH_002_INVALID_INPUT` and `PLAT_AUTH_002_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-AUTH-002-ACCEPTANCE` and `TEST-PLAT-AUTH-002-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-031, REQ-032, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-auth-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_AUTH_002_NOMINAL`: processing a minimal valid **user profile and account lifecycle** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_AUTH_002_BOUNDARY`: the **user profile and account lifecycle** fixture matrix covers token expiry, role change during a request, invitation expiry, owner transfer, public/unlisted transition, and session revocation; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_AUTH_002_INVALID_INPUT`: reject an untrusted issuer, malformed claim, missing tenant scope, unknown role, stale invitation, or cross-object grant before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_AUTH_002_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-AUTH-001`; no implicit migration or downgrade is allowed.
- `PLAT_AUTH_002_EXECUTION_FAILURE`: contain authentication failure, authorization denial, revoked session, cross-tenant access attempt, or incomplete audit event with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-AUTH-002-ACCEPTANCE` proves that **Implement user profile and account lifecycle** accepts the minimal valid input and produces the documented deterministic state transition or output, produces least-privilege authorization decisions and auditable identity state, and satisfies every metadata requirement: REQ-031, REQ-032.
2. `TEST-PLAT-AUTH-002-FAILURE` executes `PLAT_AUTH_002_INVALID_INPUT`, `PLAT_AUTH_002_PREREQUISITE_MISMATCH`, and `PLAT_AUTH_002_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`, prerequisite `PLAT-AUTH-001`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-AUTH-002 card, its epic, test registry entries `TEST-PLAT-AUTH-002-ACCEPTANCE` and `TEST-PLAT-AUTH-002-FAILURE`, requirement links REQ-031, REQ-032, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
