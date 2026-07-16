# EPIC-MIX-001 - Mixed-signal scheduler and boundaries

## Outcome

Deliver the complete **Mixed-signal scheduler and boundaries** capability for release R5, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-001, REQ-002, REQ-019, REQ-020
- Release: R5
- Entry: Gate G4 Applied Physics and Real-World Fidelity.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-MIX-001](../platform/plat-mix-001-define-global-integer-simulation-timebase.md) | Define global integer simulation timebase | Gate G4 Applied Physics and Real-World Fidelity | Planned |
| [PLAT-MIX-002](../platform/plat-mix-002-define-same-timestamp-event-ordering.md) | Define same-timestamp event ordering | PLAT-MIX-001 | Planned |
| [PLAT-MIX-003](../platform/plat-mix-003-implement-analog-to-digital-threshold-adapter.md) | Implement analog-to-digital threshold adapter | PLAT-MIX-002 | Planned |
| [PLAT-MIX-004](../platform/plat-mix-004-implement-threshold-ambiguity-and-hysteresis.md) | Implement threshold ambiguity and hysteresis | PLAT-MIX-003 | Planned |
| [PLAT-MIX-005](../platform/plat-mix-005-implement-digital-to-analog-output-driver.md) | Implement digital-to-analog output driver | PLAT-MIX-004 | Planned |
| [PLAT-MIX-006](../platform/plat-mix-006-implement-output-impedance-slew-and-current-limits.md) | Implement output impedance slew and current limits | PLAT-MIX-005 | Planned |
| [PLAT-MIX-007](../platform/plat-mix-007-implement-analog-step-to-next-digital-event.md) | Implement analog step to next digital event | PLAT-MIX-006 | Planned |
| [PLAT-MIX-008](../platform/plat-mix-008-implement-digital-event-boundary-condition-update.md) | Implement digital event boundary-condition update | PLAT-MIX-007 | Planned |
| [PLAT-MIX-009](../platform/plat-mix-009-implement-multirate-thermal-scheduling.md) | Implement multirate thermal scheduling | PLAT-MIX-008 | Planned |
| [PLAT-MIX-010](../platform/plat-mix-010-implement-cross-engine-checkpoint-state.md) | Implement cross-engine checkpoint state | PLAT-MIX-009 | Planned |
| [PLAT-MIX-011](../platform/plat-mix-011-implement-deterministic-mixed-signal-replay.md) | Implement deterministic mixed-signal replay | PLAT-MIX-010 | Planned |
| [PLAT-MIX-012](../platform/plat-mix-012-validate-mixed-signal-scheduler-fixtures.md) | Validate mixed-signal scheduler fixtures | PLAT-MIX-011 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
