# PLAT-IMP-003 - Implement Verilog and SystemVerilog source packaging

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-IMP-001](../epics/epic-imp-001.md) |
| Release | R7 |
| Requirements | REQ-024, REQ-032 |
| Concern | `implement_verilog_and_systemverilog_source_packaging` |
| Effort | S |
| Depends on | PLAT-IMP-002 |

## Objective

Implement Verilog and SystemVerilog source packaging. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/catalog/MODEL_IMPORT_EXPORT_FORMATS.md](../../catalog/MODEL_IMPORT_EXPORT_FORMATS.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-IMP-002`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/catalog/MODEL_IMPORT_EXPORT_FORMATS.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/catalog/MODEL_IMPORT_EXPORT_FORMATS.md` clauses governing **Verilog and SystemVerilog source packaging**, together with every acceptance obligation in REQ-024, REQ-032.
- Prerequisite input: the completion evidence for `PLAT-IMP-002`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_IMP_003_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_verilog_and_systemverilog_source_packaging`: source bytes, declared format/version, model text, logical and package pins, units, provenance, licenses, and import limits; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-IMP-003.
- Evidence input: `TEST-PLAT-IMP-003-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-IMP-003-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-imp-003-implement-verilog-and-systemverilog-source-packaging.md`
- `docs/tasks/epics/epic-imp-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/catalog/MODEL_IMPORT_EXPORT_FORMATS.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001` without widening this concern.

## Reference data and test IDs

- Normative reference: `docs/catalog/MODEL_IMPORT_EXPORT_FORMATS.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-IMP-003-ACCEPTANCE`
- `TEST-PLAT-IMP-003-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_verilog_and_systemverilog_source_packaging` for **Verilog and SystemVerilog source packaging**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-IMP-003` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is normalized model or data records with diagnostics and provenance.
- Failure outcome: `PLAT_IMP_003_INVALID_INPUT` and `PLAT_IMP_003_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-IMP-003-ACCEPTANCE` and `TEST-PLAT-IMP-003-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-024, REQ-032, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-imp-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/catalog/MODEL_IMPORT_EXPORT_FORMATS.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_IMP_003_NOMINAL`: processing a minimal valid **Verilog and SystemVerilog source packaging** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_IMP_003_BOUNDARY`: the **Verilog and SystemVerilog source packaging** fixture matrix covers minimal valid file, maximum member size, unknown optional field, vendor extension, duplicate alias, and round-trip edge; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_IMP_003_INVALID_INPUT`: reject malformed syntax, unsupported version, unsafe archive path, ambiguous pin map, missing unit, or unknown redistribution right before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_IMP_003_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-IMP-002`; no implicit migration or downgrade is allowed.
- `PLAT_IMP_003_EXECUTION_FAILURE`: contain parser rejection, sandbox limit, semantic conversion loss, checksum mismatch, license quarantine, or non-deterministic export with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-IMP-003-ACCEPTANCE` proves that **Implement Verilog and SystemVerilog source packaging** accepts the minimal valid input and produces the documented deterministic state transition or output, produces normalized model or data records with diagnostics and provenance, and satisfies every metadata requirement: REQ-024, REQ-032.
2. `TEST-PLAT-IMP-003-FAILURE` executes `PLAT_IMP_003_INVALID_INPUT`, `PLAT_IMP_003_PREREQUISITE_MISMATCH`, and `PLAT_IMP_003_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/catalog/MODEL_IMPORT_EXPORT_FORMATS.md`, prerequisite `PLAT-IMP-002`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-IMP-003 card, its epic, test registry entries `TEST-PLAT-IMP-003-ACCEPTANCE` and `TEST-PLAT-IMP-003-FAILURE`, requirement links REQ-024, REQ-032, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
