# EPIC-REAL-001 - Applied Physics and real-world behavior

## Outcome

Deliver the complete **Applied Physics and real-world behavior** capability for release R4. Preserve every existing tolerance, parasitic, leakage, electrothermal, derating, aging, failure, visualization, and deterministic-seed commitment while adding environment, manufacturing/mismatch, interconnection, source, instrument, uncertainty, physical-correlation, and hard-gate evidence.

## Requirements and release

- Requirements: REQ-013, REQ-014, REQ-015, REQ-016, REQ-039, REQ-043, REQ-044, REQ-045, REQ-046, REQ-047
- Release: R4
- Entry: Gate G3 nonlinear analog.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-REAL-001](../platform/plat-real-001-define-tolerance-distribution-metadata.md) | Define tolerance distribution metadata | Gate G3 nonlinear analog | Planned |
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
| [PLAT-REAL-015](../platform/plat-real-015-define-environmental-physics-profiles.md) | Define environmental physics profiles | PLAT-REAL-014 | Planned |
| [PLAT-REAL-016](../platform/plat-real-016-define-manufacturing-variation-and-mismatch.md) | Define manufacturing variation and mismatch | PLAT-REAL-015 | Planned |
| [PLAT-REAL-017](../platform/plat-real-017-define-aging-and-degradation-physics.md) | Define aging and degradation physics | PLAT-REAL-016 | Planned |
| [PLAT-REAL-018](../platform/plat-real-018-define-interconnection-physics.md) | Define interconnection physics | PLAT-REAL-017 | Planned |
| [PLAT-REAL-019](../platform/plat-real-019-define-power-source-physics.md) | Define power source physics | PLAT-REAL-018 | Planned |
| [PLAT-REAL-020](../platform/plat-real-020-define-instrument-loading-physics.md) | Define instrument loading physics | PLAT-REAL-019 | Planned |
| [PLAT-REAL-021](../platform/plat-real-021-integrate-uncertainty-and-physical-correlation.md) | Integrate uncertainty and physical correlation | PLAT-REAL-020 | Planned |
| [PLAT-REAL-022](../platform/plat-real-022-validate-expanded-r4-fixtures-and-hard-gate.md) | Validate expanded R4 fixtures and hard gate | PLAT-REAL-021, VAL-GRC-055..066 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
- [ ] GRC-021, GRC-022, GRC-026, and GRC-055..066 evidence meets the declared G4 model and physical-correlation envelopes; GRC-023..025 specifications and dependencies remain intact for their R7 evidence gate.
- [ ] Gate G4 is proven as a mandatory predecessor of G5 and G6; R5-R13 remain unrenumbered.
