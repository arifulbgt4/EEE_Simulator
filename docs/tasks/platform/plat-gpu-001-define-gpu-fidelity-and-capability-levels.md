# PLAT-GPU-001 - Define GPU fidelity and capability levels

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-GPU-001](../epics/epic-gpu-001.md) |
| Release | R13 |
| Requirements | REQ-028 |
| Concern | `define_gpu_fidelity_and_capability_levels` |
| Effort | S |
| Depends on | Gates G11 HPC and G12 architecture |

## Objective

Define GPU fidelity and capability levels. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/SYSTEM_ARCHITECTURE.md](../../architecture/SYSTEM_ARCHITECTURE.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `Gates G11 HPC and G12 architecture`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md` clauses governing **GPU fidelity and capability levels**, together with every acceptance obligation in REQ-028.
- Prerequisite input: the completion evidence for `Gates G11 HPC and G12 architecture`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_GPU_001_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `define_gpu_fidelity_and_capability_levels`: GPU capability manifests, kernels or traces, SIMT and memory configurations, raster/compute state, checkpoints, and power statistics; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-GPU-001.
- Evidence input: `TEST-PLAT-GPU-001-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-GPU-001-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-gpu-001-define-gpu-fidelity-and-capability-levels.md`
- `docs/tasks/epics/epic-gpu-001.md`
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
- `TEST-PLAT-GPU-001-ACCEPTANCE`
- `TEST-PLAT-GPU-001-FAILURE`

## Deliverables

- A versioned normative contract named `define_gpu_fidelity_and_capability_levels` for **GPU fidelity and capability levels**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-GPU-001` fixture resolves every required field, default, invariant, version rule, and public input/output without ambiguity; the published outcome is normalized GPU execution state, performance/power statistics, and provenance evidence.
- Failure outcome: `PLAT_GPU_001_SCHEMA_INVALID` and `PLAT_GPU_001_COMPATIBILITY_CONFLICT` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-GPU-001-ACCEPTANCE` and `TEST-PLAT-GPU-001-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-028, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-gpu-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_GPU_001_NOMINAL`: processing a minimal valid **GPU fidelity and capability levels** fixture resolves every required field, default, invariant, version rule, and public input/output without ambiguity; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_GPU_001_BOUNDARY`: the **GPU fidelity and capability levels** fixture matrix covers empty kernel, single warp, maximum occupancy, divergent branch, memory-limit edge, and checkpoint boundary; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_GPU_001_SCHEMA_INVALID`: reject an unsupported instruction, malformed trace, contradictory topology, illegal memory configuration, or missing workload digest before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_GPU_001_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `Gates G11 HPC and G12 architecture`; no implicit migration or downgrade is allowed.
- `PLAT_GPU_001_COMPATIBILITY_CONFLICT`: contain adapter crash, trace divergence, deadlock, resource exhaustion, checkpoint incompatibility, or reference-statistic mismatch with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-GPU-001-ACCEPTANCE` proves that **Define GPU fidelity and capability levels** resolves every required field, default, invariant, version rule, and public input/output without ambiguity, produces normalized GPU execution state, performance/power statistics, and provenance evidence, and satisfies every metadata requirement: REQ-028.
2. `TEST-PLAT-GPU-001-FAILURE` executes `PLAT_GPU_001_SCHEMA_INVALID`, `PLAT_GPU_001_PREREQUISITE_MISMATCH`, and `PLAT_GPU_001_COMPATIBILITY_CONFLICT` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`, prerequisite `Gates G11 HPC and G12 architecture`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-GPU-001 card, its epic, test registry entries `TEST-PLAT-GPU-001-ACCEPTANCE` and `TEST-PLAT-GPU-001-FAILURE`, requirement links REQ-028, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
