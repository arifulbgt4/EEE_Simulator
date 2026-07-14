# EPIC-DIG-001 - Event-driven digital simulation

## Outcome

Deliver the complete **Event-driven digital simulation** capability for release R5, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-018, REQ-021
- Release: R5
- Entry: Gate G4 realism.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-DIG-001](../platform/plat-dig-001-define-0-1-x-z-logic-algebra.md) | Define 0 1 X Z logic algebra | Gate G4 realism | Planned |
| [PLAT-DIG-002](../platform/plat-dig-002-define-drive-strength-and-resolution-rules.md) | Define drive-strength and resolution rules | PLAT-DIG-001 | Planned |
| [PLAT-DIG-003](../platform/plat-dig-003-implement-deterministic-event-priority-queue.md) | Implement deterministic event priority queue | PLAT-DIG-002 | Planned |
| [PLAT-DIG-004](../platform/plat-dig-004-implement-primitive-combinational-evaluation.md) | Implement primitive combinational evaluation | PLAT-DIG-003 | Planned |
| [PLAT-DIG-005](../platform/plat-dig-005-implement-propagation-and-inertial-delay.md) | Implement propagation and inertial delay | PLAT-DIG-004 | Planned |
| [PLAT-DIG-006](../platform/plat-dig-006-implement-tri-state-open-drain-and-bus-resolution.md) | Implement tri-state open-drain and bus resolution | PLAT-DIG-005 | Planned |
| [PLAT-DIG-007](../platform/plat-dig-007-implement-sequential-state-primitives.md) | Implement sequential state primitives | PLAT-DIG-006 | Planned |
| [PLAT-DIG-008](../platform/plat-dig-008-implement-clocks-reset-and-enable-behavior.md) | Implement clocks reset and enable behavior | PLAT-DIG-007 | Planned |
| [PLAT-DIG-009](../platform/plat-dig-009-implement-setup-and-hold-checks.md) | Implement setup and hold checks | PLAT-DIG-008 | Planned |
| [PLAT-DIG-010](../platform/plat-dig-010-implement-metastability-indication-policy.md) | Implement metastability indication policy | PLAT-DIG-009 | Planned |
| [PLAT-DIG-011](../platform/plat-dig-011-implement-fan-out-and-loading-diagnostics.md) | Implement fan-out and loading diagnostics | PLAT-DIG-010 | Planned |
| [PLAT-DIG-012](../platform/plat-dig-012-implement-contention-and-floating-bus-diagnostics.md) | Implement contention and floating-bus diagnostics | PLAT-DIG-011 | Planned |
| [PLAT-DIG-013](../platform/plat-dig-013-implement-digital-waveform-and-activity-recording.md) | Implement digital waveform and activity recording | PLAT-DIG-012 | Planned |
| [PLAT-DIG-014](../platform/plat-dig-014-implement-digital-checkpoint-and-restore.md) | Implement digital checkpoint and restore | PLAT-DIG-013 | Planned |
| [PLAT-DIG-015](../platform/plat-dig-015-validate-exhaustive-truth-and-timing-fixtures.md) | Validate exhaustive truth and timing fixtures | PLAT-DIG-014 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
