# PLAT-ANL-002 - Implement AC small-signal analysis

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-ANL-001](../epics/epic-anl-001.md) |
| Release | R3 |
| Requirements | REQ-011, REQ-012, REQ-013 |
| Concern | `implement_ac_small_signal_analysis` |
| Effort | S |
| Depends on | PLAT-ANL-001 |

## Objective

Implement AC small-signal analysis. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/SIMULATION_ENGINE.md](../../architecture/SIMULATION_ENGINE.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-ANL-001`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/SIMULATION_ENGINE.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/SIMULATION_ENGINE.md` clauses governing **AC small-signal analysis**, together with every acceptance obligation in REQ-011, REQ-012, REQ-013.
- Prerequisite input: the completion evidence for `PLAT-ANL-001`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_ANL_002_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_ac_small_signal_analysis`: analysis requests, sweep grids, source spectra, seeds, distributions, retained channels, and reference envelopes; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-ANL-002.
- Evidence input: `TEST-PLAT-ANL-002-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-ANL-002-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-anl-002-implement-ac-small-signal-analysis.md`
- `docs/tasks/epics/epic-anl-001.md`
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
- `TEST-PLAT-ANL-002-ACCEPTANCE`
- `TEST-PLAT-ANL-002-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_ac_small_signal_analysis` for **AC small-signal analysis**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-ANL-002` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is versioned analysis results and statistical or frequency-domain evidence.
- Failure outcome: `PLAT_ANL_002_INVALID_INPUT` and `PLAT_ANL_002_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-ANL-002-ACCEPTANCE` and `TEST-PLAT-ANL-002-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-011, REQ-012, REQ-013, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-anl-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/SIMULATION_ENGINE.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_ANL_002_NOMINAL`: processing a minimal valid **AC small-signal analysis** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_ANL_002_BOUNDARY`: the **AC small-signal analysis** fixture matrix covers a single-point grid, zero-noise contributor, extreme parameter value, final retained sample, and configured sample-count limit; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_ANL_002_INVALID_INPUT`: reject an empty or reversed grid, unsupported analysis/model pairing, invalid distribution, missing seed, or non-finite bound before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_ANL_002_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-ANL-001`; no implicit migration or downgrade is allowed.
- `PLAT_ANL_002_EXECUTION_FAILURE`: contain a non-finite result, reference-envelope deviation, cancelled batch, resource limit, or nondeterministic sample order with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-ANL-002-ACCEPTANCE` proves that **Implement AC small-signal analysis** accepts the minimal valid input and produces the documented deterministic state transition or output, produces versioned analysis results and statistical or frequency-domain evidence, and satisfies every metadata requirement: REQ-011, REQ-012, REQ-013.
2. `TEST-PLAT-ANL-002-FAILURE` executes `PLAT_ANL_002_INVALID_INPUT`, `PLAT_ANL_002_PREREQUISITE_MISMATCH`, and `PLAT_ANL_002_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/SIMULATION_ENGINE.md`, prerequisite `PLAT-ANL-001`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-ANL-002 card, its epic, test registry entries `TEST-PLAT-ANL-002-ACCEPTANCE` and `TEST-PLAT-ANL-002-FAILURE`, requirement links REQ-011, REQ-012, REQ-013, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
