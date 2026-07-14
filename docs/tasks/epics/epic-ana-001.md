# EPIC-ANA-001 - Linear analog simulation

## Outcome

Deliver the complete **Linear analog simulation** capability for release R2, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-008, REQ-009, REQ-010, REQ-029, REQ-033
- Release: R2
- Entry: Gate G1 editor foundation.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-ANA-001](../platform/plat-ana-001-define-sparse-matrix-storage-contract.md) | Define sparse matrix storage contract | Gate G1 editor foundation | Planned |
| [PLAT-ANA-002](../platform/plat-ana-002-implement-mna-unknown-and-equation-indexing.md) | Implement MNA unknown and equation indexing | PLAT-ANA-001 | Planned |
| [PLAT-ANA-003](../platform/plat-ana-003-implement-resistor-and-conductance-stamping.md) | Implement resistor and conductance stamping | PLAT-ANA-002 | Planned |
| [PLAT-ANA-004](../platform/plat-ana-004-implement-independent-voltage-source-stamping.md) | Implement independent voltage source stamping | PLAT-ANA-003 | Planned |
| [PLAT-ANA-005](../platform/plat-ana-005-implement-independent-current-source-stamping.md) | Implement independent current source stamping | PLAT-ANA-004 | Planned |
| [PLAT-ANA-006](../platform/plat-ana-006-implement-controlled-source-stamping.md) | Implement controlled source stamping | PLAT-ANA-005 | Planned |
| [PLAT-ANA-007](../platform/plat-ana-007-implement-capacitor-companion-models.md) | Implement capacitor companion models | PLAT-ANA-006 | Planned |
| [PLAT-ANA-008](../platform/plat-ana-008-implement-inductor-and-coupled-inductor-companion-models.md) | Implement inductor and coupled-inductor companion models | PLAT-ANA-007 | Planned |
| [PLAT-ANA-009](../platform/plat-ana-009-implement-sparse-factorization-and-reuse-policy.md) | Implement sparse factorization and reuse policy | PLAT-ANA-008 | Planned |
| [PLAT-ANA-010](../platform/plat-ana-010-implement-dc-operating-point-solve.md) | Implement DC operating-point solve | PLAT-ANA-009 | Planned |
| [PLAT-ANA-011](../platform/plat-ana-011-implement-transient-integration-methods.md) | Implement transient integration methods | PLAT-ANA-010 | Planned |
| [PLAT-ANA-012](../platform/plat-ana-012-implement-initial-conditions-and-startup-policy.md) | Implement initial conditions and startup policy | PLAT-ANA-011 | Planned |
| [PLAT-ANA-013](../platform/plat-ana-013-implement-adaptive-timestep-and-local-error-control.md) | Implement adaptive timestep and local error control | PLAT-ANA-012 | Planned |
| [PLAT-ANA-014](../platform/plat-ana-014-implement-structured-linear-solver-diagnostics.md) | Implement structured linear-solver diagnostics | PLAT-ANA-013 | Planned |
| [PLAT-ANA-015](../platform/plat-ana-015-validate-linear-golden-circuits-and-conservation-invariants.md) | Validate linear golden circuits and conservation invariants | PLAT-ANA-014 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
