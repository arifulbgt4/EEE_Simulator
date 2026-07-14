# PLAT-NON-005 - Implement source stepping

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-NON-001](../epics/epic-non-001.md) |
| Release | R3 |
| Requirements | REQ-008, REQ-017 |
| Concern | `implement_source_stepping` |
| Effort | S |
| Depends on | PLAT-NON-004 |

## Objective

Implement source stepping. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/SIMULATION_ENGINE.md](../../architecture/SIMULATION_ENGINE.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-NON-004`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/SIMULATION_ENGINE.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/SIMULATION_ENGINE.md` clauses governing **source stepping**, together with every acceptance obligation in REQ-008, REQ-017.
- Prerequisite input: the completion evidence for `PLAT-NON-004`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_NON_005_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_source_stepping`: nonlinear model equations, Jacobians, iteration state, initial guesses, tolerances, continuation settings, temperature, and failure state; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-NON-005.
- Evidence input: `TEST-PLAT-NON-005-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-NON-005-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-non-005-implement-source-stepping.md`
- `docs/tasks/epics/epic-non-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/SIMULATION_ENGINE.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001` without widening this concern.

## Reference data and test IDs

- Normative reference: `docs/architecture/SIMULATION_ENGINE.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-NON-005-ACCEPTANCE`
- `TEST-PLAT-NON-005-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_source_stepping` for **source stepping**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-NON-005` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is converged nonlinear state or explicit bounded solver diagnostics.
- Failure outcome: `PLAT_NON_005_INVALID_INPUT` and `PLAT_NON_005_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-NON-005-ACCEPTANCE` and `TEST-PLAT-NON-005-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-008, REQ-017, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-non-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/SIMULATION_ENGINE.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_NON_005_NOMINAL`: processing a minimal valid **source stepping** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_NON_005_BOUNDARY`: the **source stepping** fixture matrix covers cutoff and saturation edges, breakdown threshold, near-zero derivative, iteration limit, and minimum timestep; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_NON_005_INVALID_INPUT`: reject a non-finite model value, invalid derivative, unsupported parameter range, missing initial state, or inconsistent model capability before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_NON_005_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-NON-004`; no implicit migration or downgrade is allowed.
- `PLAT_NON_005_EXECUTION_FAILURE`: contain non-convergence, oscillating iteration, timestep underflow, thermal runaway, model timeout, or irreversible-state rollback with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-NON-005-ACCEPTANCE` proves that **Implement source stepping** accepts the minimal valid input and produces the documented deterministic state transition or output, produces converged nonlinear state or explicit bounded solver diagnostics, and satisfies every metadata requirement: REQ-008, REQ-017.
2. `TEST-PLAT-NON-005-FAILURE` executes `PLAT_NON_005_INVALID_INPUT`, `PLAT_NON_005_PREREQUISITE_MISMATCH`, and `PLAT_NON_005_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/SIMULATION_ENGINE.md`, prerequisite `PLAT-NON-004`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-NON-005 card, its epic, test registry entries `TEST-PLAT-NON-005-ACCEPTANCE` and `TEST-PLAT-NON-005-FAILURE`, requirement links REQ-008, REQ-017, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
