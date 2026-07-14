# PLAT-ARCH-004 - Define workload and disk-image provenance

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-ARCH-001](../epics/epic-arch-001.md) |
| Release | R12 |
| Requirements | REQ-001, REQ-028 |
| Concern | `define_workload_and_disk_image_provenance` |
| Effort | S |
| Depends on | PLAT-ARCH-003 |

## Objective

Define workload and disk-image provenance. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/SYSTEM_ARCHITECTURE.md](../../architecture/SYSTEM_ARCHITECTURE.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-ARCH-003`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md` clauses governing **workload and disk-image provenance**, together with every acceptance obligation in REQ-001, REQ-028.
- Prerequisite input: the completion evidence for `PLAT-ARCH-003`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_ARCH_004_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `define_workload_and_disk_image_provenance`: engine capability manifests, workload and image digests, machine configurations, checkpoints, instruction events, and statistics records; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-ARCH-004.
- Evidence input: `TEST-PLAT-ARCH-004-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-ARCH-004-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-arch-004-define-workload-and-disk-image-provenance.md`
- `docs/tasks/epics/epic-arch-001.md`
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
- `TEST-PLAT-ARCH-004-ACCEPTANCE`
- `TEST-PLAT-ARCH-004-FAILURE`

## Deliverables

- A versioned normative contract named `define_workload_and_disk_image_provenance` for **workload and disk-image provenance**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-ARCH-004` fixture resolves every required field, default, invariant, version rule, and public input/output without ambiguity; the published outcome is architecture-engine state, normalized statistics, and provenance-bound reports.
- Failure outcome: `PLAT_ARCH_004_SCHEMA_INVALID` and `PLAT_ARCH_004_COMPATIBILITY_CONFLICT` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-ARCH-004-ACCEPTANCE` and `TEST-PLAT-ARCH-004-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-001, REQ-028, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-arch-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_ARCH_004_NOMINAL`: processing a minimal valid **workload and disk-image provenance** fixture resolves every required field, default, invariant, version rule, and public input/output without ambiguity; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_ARCH_004_BOUNDARY`: the **workload and disk-image provenance** fixture matrix covers an empty workload, unsupported ISA or device, minimum and maximum cache/DRAM values, multicore limit, and checkpoint-version edge; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_ARCH_004_SCHEMA_INVALID`: reject an unknown capability, untrusted image, contradictory machine configuration, unmapped statistic, or mismatched workload digest before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_ARCH_004_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-ARCH-003`; no implicit migration or downgrade is allowed.
- `PLAT_ARCH_004_COMPATIBILITY_CONFLICT`: contain adapter negotiation failure, engine timeout or crash, resource exhaustion, invalid event mapping, or incompatible checkpoint with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-ARCH-004-ACCEPTANCE` proves that **Define workload and disk-image provenance** resolves every required field, default, invariant, version rule, and public input/output without ambiguity, produces architecture-engine state, normalized statistics, and provenance-bound reports, and satisfies every metadata requirement: REQ-001, REQ-028.
2. `TEST-PLAT-ARCH-004-FAILURE` executes `PLAT_ARCH_004_SCHEMA_INVALID`, `PLAT_ARCH_004_PREREQUISITE_MISMATCH`, and `PLAT_ARCH_004_COMPATIBILITY_CONFLICT` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`, prerequisite `PLAT-ARCH-003`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-ARCH-004 card, its epic, test registry entries `TEST-PLAT-ARCH-004-ACCEPTANCE` and `TEST-PLAT-ARCH-004-FAILURE`, requirement links REQ-001, REQ-028, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
