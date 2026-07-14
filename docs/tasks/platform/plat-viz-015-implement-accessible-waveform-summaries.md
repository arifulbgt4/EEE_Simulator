# PLAT-VIZ-015 - Implement accessible waveform summaries

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-VIZ-001](../epics/epic-viz-001.md) |
| Release | R2 |
| Requirements | REQ-007, REQ-021, REQ-034, REQ-037 |
| Concern | `implement_accessible_waveform_summaries` |
| Effort | S |
| Depends on | PLAT-VIZ-014 |

## Objective

Implement accessible waveform summaries. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md](../../architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-VIZ-014`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md` clauses governing **accessible waveform summaries**, together with every acceptance obligation in REQ-007, REQ-021, REQ-034, REQ-037.
- Prerequisite input: the completion evidence for `PLAT-VIZ-014`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_VIZ_015_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_accessible_waveform_summaries`: probe definitions, quantities and SI units, waveform/event chunks, instruments, renderer state, decimation policy, and accessible summaries; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-VIZ-015.
- Evidence input: `TEST-PLAT-VIZ-015-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-VIZ-015-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-viz-015-implement-accessible-waveform-summaries.md`
- `docs/tasks/epics/epic-viz-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001` without widening this concern.

## Reference data and test IDs

- Normative reference: `docs/architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-VIZ-015-ACCEPTANCE`
- `TEST-PLAT-VIZ-015-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_accessible_waveform_summaries` for **accessible waveform summaries**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-VIZ-015` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is truthful measurement, waveform, instrument, and visual diagnostic state.
- Failure outcome: `PLAT_VIZ_015_INVALID_INPUT` and `PLAT_VIZ_015_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-VIZ-015-ACCEPTANCE` and `TEST-PLAT-VIZ-015-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-007, REQ-021, REQ-034, REQ-037, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-viz-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_VIZ_015_NOMINAL`: processing a minimal valid **accessible waveform summaries** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_VIZ_015_BOUNDARY`: the **accessible waveform summaries** fixture matrix covers empty trace, first/last sample, X/Z state, discontinuity, 100000-sample limit, viewport edge, and context loss; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_VIZ_015_INVALID_INPUT`: reject an unknown probe, unit mismatch, corrupt chunk, non-finite sample, missing gap marker, or unsupported instrument mode before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_VIZ_015_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-VIZ-014`; no implicit migration or downgrade is allowed.
- `PLAT_VIZ_015_EXECUTION_FAILURE`: contain misleading interpolation, raw-data mutation, renderer loss, input-loading error, frame-budget breach, or inaccessible result with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-VIZ-015-ACCEPTANCE` proves that **Implement accessible waveform summaries** accepts the minimal valid input and produces the documented deterministic state transition or output, produces truthful measurement, waveform, instrument, and visual diagnostic state, and satisfies every metadata requirement: REQ-007, REQ-021, REQ-034, REQ-037.
2. `TEST-PLAT-VIZ-015-FAILURE` executes `PLAT_VIZ_015_INVALID_INPUT`, `PLAT_VIZ_015_PREREQUISITE_MISMATCH`, and `PLAT_VIZ_015_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md`, prerequisite `PLAT-VIZ-014`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-VIZ-015 card, its epic, test registry entries `TEST-PLAT-VIZ-015-ACCEPTANCE` and `TEST-PLAT-VIZ-015-FAILURE`, requirement links REQ-007, REQ-021, REQ-034, REQ-037, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
