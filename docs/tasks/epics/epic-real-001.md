# EPIC-REAL-001 - Non-ideal thermal and failure behavior

## Outcome

Deliver the complete **Non-ideal thermal and failure behavior** capability for release R4, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-014, REQ-015, REQ-016
- Release: R4
- Entry: Gate G0 documentation baseline and every task-level dependency below.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-REAL-001](../platform/plat-real-001-define-tolerance-distribution-metadata.md) | Define tolerance distribution metadata | Gate G0 documentation baseline | Planned |
| [PLAT-REAL-002](../platform/plat-real-002-define-parasitic-r-c-and-l-composition.md) | Define parasitic R C and L composition | PLAT-REAL-001 | Planned |
| [PLAT-REAL-003](../platform/plat-real-003-implement-leakage-behavior-contract.md) | Implement leakage behavior contract | PLAT-REAL-002 | Planned |
| [PLAT-REAL-004](../platform/plat-real-004-implement-component-power-calculation.md) | Implement component power calculation | PLAT-REAL-003 | Planned |
| [PLAT-REAL-005](../platform/plat-real-005-implement-thermal-resistance-and-capacitance-state.md) | Implement thermal resistance and capacitance state | PLAT-REAL-004 | Planned |
| [PLAT-REAL-006](../platform/plat-real-006-implement-ambient-and-thermal-coupling-boundaries.md) | Implement ambient and thermal-coupling boundaries | PLAT-REAL-005 | Planned |
| [PLAT-REAL-007](../platform/plat-real-007-implement-temperature-coefficient-feedback.md) | Implement temperature coefficient feedback | PLAT-REAL-006 | Planned |
| [PLAT-REAL-008](../platform/plat-real-008-implement-power-voltage-and-current-limit-diagnostics.md) | Implement power voltage and current limit diagnostics | PLAT-REAL-007 | Planned |
| [PLAT-REAL-009](../platform/plat-real-009-implement-derating-policy.md) | Implement derating policy | PLAT-REAL-008 | Planned |
| [PLAT-REAL-010](../platform/plat-real-010-implement-open-and-short-failure-states.md) | Implement open and short failure states | PLAT-REAL-009 | Planned |
| [PLAT-REAL-011](../platform/plat-real-011-implement-degraded-and-leakage-increase-failure-states.md) | Implement degraded and leakage-increase failure states | PLAT-REAL-010 | Planned |
| [PLAT-REAL-012](../platform/plat-real-012-implement-intermittent-failure-events.md) | Implement intermittent failure events | PLAT-REAL-011 | Planned |
| [PLAT-REAL-013](../platform/plat-real-013-implement-failure-injection-controls.md) | Implement failure injection controls | PLAT-REAL-012 | Planned |
| [PLAT-REAL-014](../platform/plat-real-014-validate-electrothermal-and-failure-golden-fixtures.md) | Validate electrothermal and failure golden fixtures | PLAT-REAL-013 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
