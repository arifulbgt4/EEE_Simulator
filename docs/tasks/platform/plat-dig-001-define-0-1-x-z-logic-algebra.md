# PLAT-DIG-001 - Define 0 1 X Z logic algebra

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-DIG-001](../epics/epic-dig-001.md) |
| Release | R5 |
| Requirements | REQ-018, REQ-021 |
| Concern | `define_0_1_x_z_logic_algebra` |
| Effort | S |
| Depends on | Gate G4 realism |

## Objective

Define 0 1 X Z logic algebra. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md](../../architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `Gate G4 realism`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md` clauses governing **0 1 X Z logic algebra**, together with every acceptance obligation in REQ-018, REQ-021.
- Prerequisite input: the completion evidence for `Gate G4 realism`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_DIG_001_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `define_0_1_x_z_logic_algebra`: four-state logic values, drivers and strengths, event timestamps, propagation delays, buses, clocks, and timing constraints; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-DIG-001.
- Evidence input: `TEST-PLAT-DIG-001-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-DIG-001-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-dig-001-define-0-1-x-z-logic-algebra.md`
- `docs/tasks/epics/epic-dig-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001` without widening this concern.

## Reference data and test IDs

- Normative reference: `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-DIG-001-ACCEPTANCE`
- `TEST-PLAT-DIG-001-FAILURE`

## Deliverables

- A versioned normative contract named `define_0_1_x_z_logic_algebra` for **0 1 X Z logic algebra**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-DIG-001` fixture resolves every required field, default, invariant, version rule, and public input/output without ambiguity; the published outcome is ordered digital state transitions and timing diagnostics.
- Failure outcome: `PLAT_DIG_001_SCHEMA_INVALID` and `PLAT_DIG_001_COMPATIBILITY_CONFLICT` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-DIG-001-ACCEPTANCE` and `TEST-PLAT-DIG-001-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-018, REQ-021, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-dig-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_DIG_001_NOMINAL`: processing a minimal valid **0 1 X Z logic algebra** fixture resolves every required field, default, invariant, version rule, and public input/output without ambiguity; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_DIG_001_BOUNDARY`: the **0 1 X Z logic algebra** fixture matrix covers simultaneous events, zero-delay delta cycle, Z-only net, equal-strength contention, minimum pulse, and setup/hold edge; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_DIG_001_SCHEMA_INVALID`: reject an illegal logic value, negative delay, width mismatch, duplicate driver identity, or missing timing reference before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_DIG_001_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `Gate G4 realism`; no implicit migration or downgrade is allowed.
- `PLAT_DIG_001_COMPATIBILITY_CONFLICT`: contain contention, floating state, zero-time oscillation, setup/hold violation, metastability policy breach, or event-limit exhaustion with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-DIG-001-ACCEPTANCE` proves that **Define 0 1 X Z logic algebra** resolves every required field, default, invariant, version rule, and public input/output without ambiguity, produces ordered digital state transitions and timing diagnostics, and satisfies every metadata requirement: REQ-018, REQ-021.
2. `TEST-PLAT-DIG-001-FAILURE` executes `PLAT_DIG_001_SCHEMA_INVALID`, `PLAT_DIG_001_PREREQUISITE_MISMATCH`, and `PLAT_DIG_001_COMPATIBILITY_CONFLICT` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`, prerequisite `Gate G4 realism`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-DIG-001 card, its epic, test registry entries `TEST-PLAT-DIG-001-ACCEPTANCE` and `TEST-PLAT-DIG-001-FAILURE`, requirement links REQ-018, REQ-021, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
