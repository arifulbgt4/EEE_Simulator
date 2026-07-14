# PLAT-REAL-005 - Implement thermal resistance and capacitance state

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-REAL-001](../epics/epic-real-001.md) |
| Release | R4 |
| Requirements | REQ-014, REQ-015, REQ-016 |
| Concern | `implement_thermal_resistance_and_capacitance_state` |
| Effort | S |
| Depends on | PLAT-REAL-004 |

## Objective

Implement thermal resistance and capacitance state. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md](../../architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-REAL-004`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/SIMULATION_ENGINE.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/SIMULATION_ENGINE.md` clauses governing **thermal resistance and capacitance state**, together with every acceptance obligation in REQ-014, REQ-015, REQ-016.
- Prerequisite input: the completion evidence for `PLAT-REAL-004`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_REAL_005_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_thermal_resistance_and_capacitance_state`: component and package definitions, scalable geometry, physical dimensions, render exaggeration, logical pins, pin maps, markings, and provenance; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-REAL-005.
- Evidence input: `TEST-PLAT-REAL-005-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-REAL-005-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-real-005-implement-thermal-resistance-and-capacitance-state.md`
- `docs/tasks/epics/epic-real-001.md`
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
- `TEST-PLAT-REAL-005-ACCEPTANCE`
- `TEST-PLAT-REAL-005-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_thermal_resistance_and_capacitance_state` for **thermal resistance and capacitance state**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-REAL-005` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is recognizable accessible physical/package projection and pin-equivalence evidence.
- Failure outcome: `PLAT_REAL_005_INVALID_INPUT` and `PLAT_REAL_005_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-REAL-005-ACCEPTANCE` and `TEST-PLAT-REAL-005-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-014, REQ-015, REQ-016, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-real-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/SIMULATION_ENGINE.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_REAL_005_NOMINAL`: processing a minimal valid **thermal resistance and capacitance state** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_REAL_005_BOUNDARY`: the **thermal resistance and capacitance state** fixture matrix covers minimum/maximum pin count, rotation and mirror, distant zoom, high contrast, exposed pad, and illustrative-dimension edge; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_REAL_005_INVALID_INPUT`: reject a duplicate or missing pin, pin-map mismatch, non-finite dimension, colliding geometry, invisible orientation cue, or unlicensed artwork before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_REAL_005_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-REAL-004`; no implicit migration or downgrade is allowed.
- `PLAT_REAL_005_EXECUTION_FAILURE`: contain electrical identity change on view switch, misleading dimensional claim, inaccessible marking, renderer freeze, or package-version mutation with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-REAL-005-ACCEPTANCE` proves that **Implement thermal resistance and capacitance state** accepts the minimal valid input and produces the documented deterministic state transition or output, produces recognizable accessible physical/package projection and pin-equivalence evidence, and satisfies every metadata requirement: REQ-014, REQ-015, REQ-016.
2. `TEST-PLAT-REAL-005-FAILURE` executes `PLAT_REAL_005_INVALID_INPUT`, `PLAT_REAL_005_PREREQUISITE_MISMATCH`, and `PLAT_REAL_005_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/SIMULATION_ENGINE.md`, prerequisite `PLAT-REAL-004`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-REAL-005 card, its epic, test registry entries `TEST-PLAT-REAL-005-ACCEPTANCE` and `TEST-PLAT-REAL-005-FAILURE`, requirement links REQ-014, REQ-015, REQ-016, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
