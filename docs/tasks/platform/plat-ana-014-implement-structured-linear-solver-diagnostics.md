# PLAT-ANA-014 - Implement structured linear-solver diagnostics

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-ANA-001](../epics/epic-ana-001.md) |
| Release | R2 |
| Requirements | REQ-008, REQ-009, REQ-010, REQ-029, REQ-033 |
| Concern | `implement_structured_linear_solver_diagnostics` |
| Effort | S |
| Depends on | PLAT-ANA-013 |

## Objective

Implement structured linear-solver diagnostics. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/SIMULATION_ENGINE.md](../../architecture/SIMULATION_ENGINE.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-ANA-013`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/SIMULATION_ENGINE.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/SIMULATION_ENGINE.md` clauses governing **structured linear-solver diagnostics**, together with every acceptance obligation in REQ-008, REQ-009, REQ-010, REQ-029, REQ-033.
- Prerequisite input: the completion evidence for `PLAT-ANA-013`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_ANA_014_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_structured_linear_solver_diagnostics`: netlist stamps, node and branch indexes, matrix coefficients, timesteps, initial conditions, and solver tolerances; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-ANA-014.
- Evidence input: `TEST-PLAT-ANA-014-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-ANA-014-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-ana-014-implement-structured-linear-solver-diagnostics.md`
- `docs/tasks/epics/epic-ana-001.md`
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
- `TEST-PLAT-ANA-014-ACCEPTANCE`
- `TEST-PLAT-ANA-014-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_structured_linear_solver_diagnostics` for **structured linear-solver diagnostics**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-ANA-014` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is deterministic matrix or solution state with numerical diagnostics.
- Failure outcome: `PLAT_ANA_014_INVALID_INPUT` and `PLAT_ANA_014_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-ANA-014-ACCEPTANCE` and `TEST-PLAT-ANA-014-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-008, REQ-009, REQ-010, REQ-029, REQ-033, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-ana-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/SIMULATION_ENGINE.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_ANA_014_NOMINAL`: processing a minimal valid **structured linear-solver diagnostics** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_ANA_014_BOUNDARY`: the **structured linear-solver diagnostics** fixture matrix covers open and short limits, zero-valued elements, minimum timestep, singular topology, and near-tolerance convergence; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_ANA_014_INVALID_INPUT`: reject a duplicate unknown, non-finite coefficient, dimension mismatch, illegal timestep, or unresolved reference node before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_ANA_014_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-ANA-013`; no implicit migration or downgrade is allowed.
- `PLAT_ANA_014_EXECUTION_FAILURE`: contain a singular matrix, non-convergence, timestep underflow, non-finite solution, or conservation violation with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-ANA-014-ACCEPTANCE` proves that **Implement structured linear-solver diagnostics** accepts the minimal valid input and produces the documented deterministic state transition or output, produces deterministic matrix or solution state with numerical diagnostics, and satisfies every metadata requirement: REQ-008, REQ-009, REQ-010, REQ-029, REQ-033.
2. `TEST-PLAT-ANA-014-FAILURE` executes `PLAT_ANA_014_INVALID_INPUT`, `PLAT_ANA_014_PREREQUISITE_MISMATCH`, and `PLAT_ANA_014_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/SIMULATION_ENGINE.md`, prerequisite `PLAT-ANA-013`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-ANA-014 card, its epic, test registry entries `TEST-PLAT-ANA-014-ACCEPTANCE` and `TEST-PLAT-ANA-014-FAILURE`, requirement links REQ-008, REQ-009, REQ-010, REQ-029, REQ-033, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
