# EPIC-NON-001 - Nonlinear simulation and convergence

## Outcome

Deliver the complete **Nonlinear simulation and convergence** capability for release R3, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-008, REQ-017
- Release: R3
- Entry: Gate G2 linear analog.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-NON-001](../platform/plat-non-001-define-nonlinear-device-evaluation-contract.md) | Define nonlinear device evaluation contract | Gate G2 linear analog | Planned |
| [PLAT-NON-002](../platform/plat-non-002-implement-residual-and-jacobian-assembly.md) | Implement residual and Jacobian assembly | PLAT-NON-001 | Planned |
| [PLAT-NON-003](../platform/plat-non-003-implement-newton-iteration.md) | Implement Newton iteration | PLAT-NON-002 | Planned |
| [PLAT-NON-004](../platform/plat-non-004-implement-bounded-damping-and-line-search.md) | Implement bounded damping and line search | PLAT-NON-003 | Planned |
| [PLAT-NON-005](../platform/plat-non-005-implement-source-stepping.md) | Implement source stepping | PLAT-NON-004 | Planned |
| [PLAT-NON-006](../platform/plat-non-006-implement-conductance-stepping.md) | Implement conductance stepping | PLAT-NON-005 | Planned |
| [PLAT-NON-007](../platform/plat-non-007-implement-nonlinear-timestep-rejection-and-retry.md) | Implement nonlinear timestep rejection and retry | PLAT-NON-006 | Planned |
| [PLAT-NON-008](../platform/plat-non-008-implement-convergence-and-iteration-limits.md) | Implement convergence and iteration limits | PLAT-NON-007 | Planned |
| [PLAT-NON-009](../platform/plat-non-009-implement-non-convergence-diagnostic-payload.md) | Implement non-convergence diagnostic payload | PLAT-NON-008 | Planned |
| [PLAT-NON-010](../platform/plat-non-010-implement-diode-nonlinear-infrastructure.md) | Implement diode nonlinear infrastructure | PLAT-NON-009 | Planned |
| [PLAT-NON-011](../platform/plat-non-011-implement-bjt-nonlinear-infrastructure.md) | Implement BJT nonlinear infrastructure | PLAT-NON-010 | Planned |
| [PLAT-NON-012](../platform/plat-non-012-implement-mosfet-nonlinear-infrastructure.md) | Implement MOSFET nonlinear infrastructure | PLAT-NON-011 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
