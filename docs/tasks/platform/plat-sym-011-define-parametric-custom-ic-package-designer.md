# PLAT-SYM-011 - Define parametric custom IC package designer

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-SYM-001](../epics/epic-sym-001.md) |
| Release | R1 |
| Requirements | REQ-022, REQ-023, REQ-037, REQ-038 |
| Concern | `define_parametric_custom_ic_package_designer` |
| Effort | S |
| Depends on | PLAT-SYM-010 |

## Objective

Define parametric custom IC package designer. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/catalog/COMPONENT_MODEL_CONTRACT.md](../../catalog/COMPONENT_MODEL_CONTRACT.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-SYM-010`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md` clauses governing **parametric custom IC package designer**, together with every acceptance obligation in REQ-022, REQ-023, REQ-037, REQ-038.
- Prerequisite input: the completion evidence for `PLAT-SYM-010`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_SYM_011_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `define_parametric_custom_ic_package_designer`: symbol IDs, pin geometry and semantics, IEC/ANSI-aligned conventions, package bindings, labels, themes, and provenance; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-SYM-011.
- Evidence input: `TEST-PLAT-SYM-011-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-SYM-011-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-sym-011-define-parametric-custom-ic-package-designer.md`
- `docs/tasks/epics/epic-sym-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001` without widening this concern.

## Reference data and test IDs

- Normative reference: `docs/catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-SYM-011-ACCEPTANCE`
- `TEST-PLAT-SYM-011-FAILURE`

## Deliverables

- A versioned normative contract named `define_parametric_custom_ic_package_designer` for **parametric custom IC package designer**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-SYM-011` fixture resolves every required field, default, invariant, version rule, and public input/output without ambiguity; the published outcome is original deterministic schematic symbols and visual-regression evidence.
- Failure outcome: `PLAT_SYM_011_SCHEMA_INVALID` and `PLAT_SYM_011_COMPATIBILITY_CONFLICT` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-SYM-011-ACCEPTANCE` and `TEST-PLAT-SYM-011-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-022, REQ-023, REQ-037, REQ-038, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-sym-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_SYM_011_NOMINAL`: processing a minimal valid **parametric custom IC package designer** fixture resolves every required field, default, invariant, version rule, and public input/output without ambiguity; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_SYM_011_BOUNDARY`: the **parametric custom IC package designer** fixture matrix covers single-pin symbol, maximum pin count, rotation/mirror, distant zoom, text expansion, and high-contrast rendering; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_SYM_011_SCHEMA_INVALID`: reject a duplicate pin, off-grid connection point, ambiguous crossover, missing polarity cue, unsafe text, or copied/unlicensed artwork before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_SYM_011_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-SYM-010`; no implicit migration or downgrade is allowed.
- `PLAT_SYM_011_COMPATIBILITY_CONFLICT`: contain electrical/visual pin mismatch, inaccessible state, nondeterministic geometry, renderer regression, or lost provenance with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-SYM-011-ACCEPTANCE` proves that **Define parametric custom IC package designer** resolves every required field, default, invariant, version rule, and public input/output without ambiguity, produces original deterministic schematic symbols and visual-regression evidence, and satisfies every metadata requirement: REQ-022, REQ-023, REQ-037, REQ-038.
2. `TEST-PLAT-SYM-011-FAILURE` executes `PLAT_SYM_011_SCHEMA_INVALID`, `PLAT_SYM_011_PREREQUISITE_MISMATCH`, and `PLAT_SYM_011_COMPATIBILITY_CONFLICT` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md`, prerequisite `PLAT-SYM-010`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-SYM-011 card, its epic, test registry entries `TEST-PLAT-SYM-011-ACCEPTANCE` and `TEST-PLAT-SYM-011-FAILURE`, requirement links REQ-022, REQ-023, REQ-037, REQ-038, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
