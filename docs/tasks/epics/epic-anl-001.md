# EPIC-ANL-001 - Analysis modes and parameter studies

## Outcome

Deliver the complete **Analysis modes and parameter studies** capability for release R3, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-011, REQ-012, REQ-013
- Release: R3
- Entry: Gate G0 documentation baseline and every task-level dependency below.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-ANL-001](../platform/plat-anl-001-implement-dc-sweep-analysis.md) | Implement DC sweep analysis | Gate G0 documentation baseline | Planned |
| [PLAT-ANL-002](../platform/plat-anl-002-implement-ac-small-signal-analysis.md) | Implement AC small-signal analysis | PLAT-ANL-001 | Planned |
| [PLAT-ANL-003](../platform/plat-anl-003-implement-frequency-grid-policies.md) | Implement frequency-grid policies | PLAT-ANL-002 | Planned |
| [PLAT-ANL-004](../platform/plat-anl-004-implement-noise-source-aggregation-contract.md) | Implement noise-source aggregation contract | PLAT-ANL-003 | Planned |
| [PLAT-ANL-005](../platform/plat-anl-005-implement-thermal-noise-analysis.md) | Implement thermal noise analysis | PLAT-ANL-004 | Planned |
| [PLAT-ANL-006](../platform/plat-anl-006-implement-shot-and-flicker-noise-analysis.md) | Implement shot and flicker noise analysis | PLAT-ANL-005 | Planned |
| [PLAT-ANL-007](../platform/plat-anl-007-implement-parameter-sweep-orchestration.md) | Implement parameter sweep orchestration | PLAT-ANL-006 | Planned |
| [PLAT-ANL-008](../platform/plat-anl-008-implement-monte-carlo-distribution-sampling.md) | Implement Monte Carlo distribution sampling | PLAT-ANL-007 | Planned |
| [PLAT-ANL-009](../platform/plat-anl-009-implement-deterministic-random-seed-policy.md) | Implement deterministic random seed policy | PLAT-ANL-008 | Planned |
| [PLAT-ANL-010](../platform/plat-anl-010-implement-batch-yield-and-statistics-summaries.md) | Implement batch yield and statistics summaries | PLAT-ANL-009 | Planned |
| [PLAT-ANL-011](../platform/plat-anl-011-implement-fourier-and-harmonic-measurement.md) | Implement Fourier and harmonic measurement | PLAT-ANL-010 | Planned |
| [PLAT-ANL-012](../platform/plat-anl-012-validate-analyses-against-independent-references.md) | Validate analyses against independent references | PLAT-ANL-011 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
