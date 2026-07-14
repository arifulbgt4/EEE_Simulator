# PLAT-PERF-004 - Implement waveform ring buffer and decimation

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-PERF-001](../epics/epic-perf-001.md) |
| Release | R2 |
| Requirements | REQ-033 |
| Concern | `implement_waveform_ring_buffer_and_decimation` |
| Effort | S |
| Depends on | PLAT-PERF-003 |

## Objective

Implement waveform ring buffer and decimation. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/quality/PERFORMANCE_BENCHMARKS.md](../../quality/PERFORMANCE_BENCHMARKS.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-PERF-003`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md` clauses governing **waveform ring buffer and decimation**, together with every acceptance obligation in REQ-033.
- Prerequisite input: the completion evidence for `PLAT-PERF-003`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_PERF_004_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_waveform_ring_buffer_and_decimation`: pinned benchmark fixtures, build and registry digests, reference hardware/browser profiles, trial counts, metrics, and budgets; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-PERF-004.
- Evidence input: `TEST-PLAT-PERF-004-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-PERF-004-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-perf-004-implement-waveform-ring-buffer-and-decimation.md`
- `docs/tasks/epics/epic-perf-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001` without widening this concern.

## Reference data and test IDs

- Normative reference: `docs/architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-PERF-004-ACCEPTANCE`
- `TEST-PLAT-PERF-004-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_waveform_ring_buffer_and_decimation` for **waveform ring buffer and decimation**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-PERF-004` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is reproducible performance measurements and release-gate disposition.
- Failure outcome: `PLAT_PERF_004_INVALID_INPUT` and `PLAT_PERF_004_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-PERF-004-ACCEPTANCE` and `TEST-PLAT-PERF-004-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-033, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-perf-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_PERF_004_NOMINAL`: processing a minimal valid **waveform ring buffer and decimation** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_PERF_004_BOUNDARY`: the **waveform ring buffer and decimation** fixture matrix covers cold and warm runs, p95 threshold, peak-memory edge, renderer fallback, unsupported capability, and sample-count minimum; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_PERF_004_INVALID_INPUT`: reject an unpinned workload, undocumented environment, insufficient trials, mixed build identity, or missing measurement unit before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_PERF_004_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-PERF-003`; no implicit migration or downgrade is allowed.
- `PLAT_PERF_004_EXECUTION_FAILURE`: contain budget regression, main-thread stall, memory exhaustion, frame-rate floor breach, nondeterministic result, or invalid benchmark comparison with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-PERF-004-ACCEPTANCE` proves that **Implement waveform ring buffer and decimation** accepts the minimal valid input and produces the documented deterministic state transition or output, produces reproducible performance measurements and release-gate disposition, and satisfies every metadata requirement: REQ-033.
2. `TEST-PLAT-PERF-004-FAILURE` executes `PLAT_PERF_004_INVALID_INPUT`, `PLAT_PERF_004_PREREQUISITE_MISMATCH`, and `PLAT_PERF_004_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md`, prerequisite `PLAT-PERF-003`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-PERF-004 card, its epic, test registry entries `TEST-PLAT-PERF-004-ACCEPTANCE` and `TEST-PLAT-PERF-004-FAILURE`, requirement links REQ-033, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
