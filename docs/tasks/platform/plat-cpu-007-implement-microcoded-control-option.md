# PLAT-CPU-007 - Implement microcoded control option

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-CPU-001](../epics/epic-cpu-001.md) |
| Release | R8 |
| Requirements | REQ-002, REQ-025 |
| Concern | `implement_microcoded_control_option` |
| Effort | S |
| Depends on | PLAT-CPU-006 |

## Objective

Implement microcoded control option. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md](../../architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-CPU-006`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md` clauses governing **microcoded control option**, together with every acceptance obligation in REQ-002, REQ-025.
- Prerequisite input: the completion evidence for `PLAT-CPU-006`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_CPU_007_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_microcoded_control_option`: ISA definitions, datapath and control records, register state, buses, instructions, program images, breakpoints, and clock events; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-CPU-007.
- Evidence input: `TEST-PLAT-CPU-007-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-CPU-007-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-cpu-007-implement-microcoded-control-option.md`
- `docs/tasks/epics/epic-cpu-001.md`
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
- `TEST-PLAT-CPU-007-ACCEPTANCE`
- `TEST-PLAT-CPU-007-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_microcoded_control_option` for **microcoded control option**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-CPU-007` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is deterministic CPU architectural state, traces, and reference-program evidence.
- Failure outcome: `PLAT_CPU_007_INVALID_INPUT` and `PLAT_CPU_007_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-CPU-007-ACCEPTANCE` and `TEST-PLAT-CPU-007-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-002, REQ-025, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-cpu-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_CPU_007_NOMINAL`: processing a minimal valid **microcoded control option** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_CPU_007_BOUNDARY`: the **microcoded control option** fixture matrix covers reset, zero and maximum operand, address wrap, first and last register, branch edge, and single-step boundary; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_CPU_007_INVALID_INPUT`: reject an unknown opcode, illegal operand or register, contradictory control signal, malformed program image, or unsupported abstraction binding before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_CPU_007_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-CPU-006`; no implicit migration or downgrade is allowed.
- `PLAT_CPU_007_EXECUTION_FAILURE`: contain decode fault, bus contention, incorrect flag transition, non-progressing control state, breakpoint mismatch, or program-result divergence with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-CPU-007-ACCEPTANCE` proves that **Implement microcoded control option** accepts the minimal valid input and produces the documented deterministic state transition or output, produces deterministic CPU architectural state, traces, and reference-program evidence, and satisfies every metadata requirement: REQ-002, REQ-025.
2. `TEST-PLAT-CPU-007-FAILURE` executes `PLAT_CPU_007_INVALID_INPUT`, `PLAT_CPU_007_PREREQUISITE_MISMATCH`, and `PLAT_CPU_007_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`, prerequisite `PLAT-CPU-006`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-CPU-007 card, its epic, test registry entries `TEST-PLAT-CPU-007-ACCEPTANCE` and `TEST-PLAT-CPU-007-FAILURE`, requirement links REQ-002, REQ-025, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
