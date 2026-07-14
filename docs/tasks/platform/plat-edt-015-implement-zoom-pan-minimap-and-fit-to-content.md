# PLAT-EDT-015 - Implement zoom pan minimap and fit-to-content

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EDT-001](../epics/epic-edt-001.md) |
| Release | R1 |
| Requirements | REQ-004, REQ-005, REQ-037, REQ-038 |
| Concern | `implement_zoom_pan_minimap_and_fit_to_content` |
| Effort | S |
| Depends on | PLAT-EDT-014 |

## Objective

Implement zoom pan minimap and fit-to-content. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md](../../architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-EDT-014`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md` clauses governing **zoom pan minimap and fit-to-content**, together with every acceptance obligation in REQ-004, REQ-005, REQ-037, REQ-038.
- Prerequisite input: the completion evidence for `PLAT-EDT-014`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_EDT_015_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_zoom_pan_minimap_and_fit_to_content`: component, pin, net, hierarchy, package, viewport, selection, command, and undo/redo records; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-EDT-015.
- Evidence input: `TEST-PLAT-EDT-015-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-EDT-015-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-edt-015-implement-zoom-pan-minimap-and-fit-to-content.md`
- `docs/tasks/epics/epic-edt-001.md`
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
- `TEST-PLAT-EDT-015-ACCEPTANCE`
- `TEST-PLAT-EDT-015-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_zoom_pan_minimap_and_fit_to_content` for **zoom pan minimap and fit-to-content**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-EDT-015` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is deterministic editor domain state and accessible visual projection.
- Failure outcome: `PLAT_EDT_015_INVALID_INPUT` and `PLAT_EDT_015_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-EDT-015-ACCEPTANCE` and `TEST-PLAT-EDT-015-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-004, REQ-005, REQ-037, REQ-038, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-edt-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_EDT_015_NOMINAL`: processing a minimal valid **zoom pan minimap and fit-to-content** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_EDT_015_BOUNDARY`: the **zoom pan minimap and fit-to-content** fixture matrix covers empty selection, crossing wires, half-grid pin, view switch, maximum zoom, clipboard boundary, and large-canvas limit; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_EDT_015_INVALID_INPUT`: reject a missing stable ID, incompatible pin connection, illegal transform, unresolved package pin, malformed command, or hierarchy cycle before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_EDT_015_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-EDT-014`; no implicit migration or downgrade is allowed.
- `PLAT_EDT_015_EXECUTION_FAILURE`: contain lost edit, unintended net merge, stale selection, undo divergence, renderer-context loss, or main-thread budget breach with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-EDT-015-ACCEPTANCE` proves that **Implement zoom pan minimap and fit-to-content** accepts the minimal valid input and produces the documented deterministic state transition or output, produces deterministic editor domain state and accessible visual projection, and satisfies every metadata requirement: REQ-004, REQ-005, REQ-037, REQ-038.
2. `TEST-PLAT-EDT-015-FAILURE` executes `PLAT_EDT_015_INVALID_INPUT`, `PLAT_EDT_015_PREREQUISITE_MISMATCH`, and `PLAT_EDT_015_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md`, prerequisite `PLAT-EDT-014`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-EDT-015 card, its epic, test registry entries `TEST-PLAT-EDT-015-ACCEPTANCE` and `TEST-PLAT-EDT-015-FAILURE`, requirement links REQ-004, REQ-005, REQ-037, REQ-038, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
