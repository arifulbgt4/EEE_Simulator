# PLAT-MIX-003 - Implement analog-to-digital threshold adapter

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-MIX-001](../epics/epic-mix-001.md) |
| Release | R5 |
| Requirements | REQ-001, REQ-002, REQ-019, REQ-020 |
| Concern | `implement_analog_to_digital_threshold_adapter` |
| Effort | S |
| Depends on | PLAT-MIX-002 |

## Objective

Implement analog-to-digital threshold adapter. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md](../../architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-MIX-002`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md` clauses governing **analog-to-digital threshold adapter**, together with every acceptance obligation in REQ-001, REQ-002, REQ-019, REQ-020.
- Prerequisite input: the completion evidence for `PLAT-MIX-002`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_MIX_003_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_analog_to_digital_threshold_adapter`: integer time quantum, partition capabilities, analog crossings, digital events, boundary adapters, thermal steps, seeds, and checkpoints; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-MIX-003.
- Evidence input: `TEST-PLAT-MIX-003-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-MIX-003-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-mix-003-implement-analog-to-digital-threshold-adapter.md`
- `docs/tasks/epics/epic-mix-001.md`
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
- `TEST-PLAT-MIX-003-ACCEPTANCE`
- `TEST-PLAT-MIX-003-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_analog_to_digital_threshold_adapter` for **analog-to-digital threshold adapter**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-MIX-003` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is globally ordered cross-domain state and reproducible co-simulation evidence.
- Failure outcome: `PLAT_MIX_003_INVALID_INPUT` and `PLAT_MIX_003_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-MIX-003-ACCEPTANCE` and `TEST-PLAT-MIX-003-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-001, REQ-002, REQ-019, REQ-020, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-mix-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_MIX_003_NOMINAL`: processing a minimal valid **analog-to-digital threshold adapter** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_MIX_003_BOUNDARY`: the **analog-to-digital threshold adapter** fixture matrix covers same-timestamp events, threshold equality, hysteresis edge, Z/X drive, minimum quantum, maximum tick, and checkpoint safe point; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_MIX_003_INVALID_INPUT`: reject an overflowing timebase, contradictory threshold, missing domain adapter, unsupported partition capability, or stale checkpoint before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_MIX_003_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-MIX-002`; no implicit migration or downgrade is allowed.
- `PLAT_MIX_003_EXECUTION_FAILURE`: contain event-order divergence, threshold chatter, partition overrun, zero-time oscillation, incompatible checkpoint, or nondeterministic replay with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-MIX-003-ACCEPTANCE` proves that **Implement analog-to-digital threshold adapter** accepts the minimal valid input and produces the documented deterministic state transition or output, produces globally ordered cross-domain state and reproducible co-simulation evidence, and satisfies every metadata requirement: REQ-001, REQ-002, REQ-019, REQ-020.
2. `TEST-PLAT-MIX-003-FAILURE` executes `PLAT_MIX_003_INVALID_INPUT`, `PLAT_MIX_003_PREREQUISITE_MISMATCH`, and `PLAT_MIX_003_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`, prerequisite `PLAT-MIX-002`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-MIX-003 card, its epic, test registry entries `TEST-PLAT-MIX-003-ACCEPTANCE` and `TEST-PLAT-MIX-003-FAILURE`, requirement links REQ-001, REQ-002, REQ-019, REQ-020, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
