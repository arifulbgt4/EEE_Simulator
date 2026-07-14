# PLAT-RF-006 - Implement RF amplifier mixer oscillator and filter blocks

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-RF-001](../epics/epic-rf-001.md) |
| Release | R7 |
| Requirements | REQ-024, REQ-028 |
| Concern | `implement_rf_amplifier_mixer_oscillator_and_filter_blocks` |
| Effort | S |
| Depends on | PLAT-RF-005 |

## Objective

Implement RF amplifier mixer oscillator and filter blocks. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/catalog/COMPONENT_TAXONOMY.md](../../catalog/COMPONENT_TAXONOMY.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-RF-005`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md` clauses governing **RF amplifier mixer oscillator and filter blocks**, together with every acceptance obligation in REQ-024, REQ-028.
- Prerequisite input: the completion evidence for `PLAT-RF-005`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_RF_006_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_rf_amplifier_mixer_oscillator_and_filter_blocks`: RF ports, reference impedances, frequency grids, S-parameters, network topology, channel models, and conversion settings; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-RF-006.
- Evidence input: `TEST-PLAT-RF-006-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-RF-006-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-rf-006-implement-rf-amplifier-mixer-oscillator-and-filter-blocks.md`
- `docs/tasks/epics/epic-rf-001.md`
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
- `TEST-PLAT-RF-006-ACCEPTANCE`
- `TEST-PLAT-RF-006-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_rf_amplifier_mixer_oscillator_and_filter_blocks` for **RF amplifier mixer oscillator and filter blocks**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-RF-006` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is validated RF network response and frequency-domain diagnostics.
- Failure outcome: `PLAT_RF_006_INVALID_INPUT` and `PLAT_RF_006_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-RF-006-ACCEPTANCE` and `TEST-PLAT-RF-006-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-024, REQ-028, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-rf-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_RF_006_NOMINAL`: processing a minimal valid **RF amplifier mixer oscillator and filter blocks** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_RF_006_BOUNDARY`: the **RF amplifier mixer oscillator and filter blocks** fixture matrix covers frequency-envelope edge, zero or extreme impedance, single-port/two-port limit, passivity edge, and time-domain transform boundary; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_RF_006_INVALID_INPUT`: reject a malformed Touchstone record, inconsistent port count, non-monotonic frequency, missing reference impedance, or non-finite matrix value before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_RF_006_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-RF-005`; no implicit migration or downgrade is allowed.
- `PLAT_RF_006_EXECUTION_FAILURE`: contain passivity or causality violation, unstable transform, unsupported band, reference mismatch, or resource-limited network solve with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-RF-006-ACCEPTANCE` proves that **Implement RF amplifier mixer oscillator and filter blocks** accepts the minimal valid input and produces the documented deterministic state transition or output, produces validated RF network response and frequency-domain diagnostics, and satisfies every metadata requirement: REQ-024, REQ-028.
2. `TEST-PLAT-RF-006-FAILURE` executes `PLAT_RF_006_INVALID_INPUT`, `PLAT_RF_006_PREREQUISITE_MISMATCH`, and `PLAT_RF_006_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`, prerequisite `PLAT-RF-005`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-RF-006 card, its epic, test registry entries `TEST-PLAT-RF-006-ACCEPTANCE` and `TEST-PLAT-RF-006-FAILURE`, requirement links REQ-024, REQ-028, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
