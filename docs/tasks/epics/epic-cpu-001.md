# EPIC-CPU-001 - Educational CPU hierarchy

## Outcome

Deliver the complete **Educational CPU hierarchy** capability for release R8, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-002, REQ-025
- Release: R8
- Entry: Gate G7 complete catalog.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-CPU-001](../platform/plat-cpu-001-define-educational-cpu-abstraction-levels.md) | Define educational CPU abstraction levels | Gate G7 complete catalog | Planned |
| [PLAT-CPU-002](../platform/plat-cpu-002-implement-register-and-register-file-blocks.md) | Implement register and register-file blocks | PLAT-CPU-001 | Planned |
| [PLAT-CPU-003](../platform/plat-cpu-003-implement-alu-and-flag-behavior.md) | Implement ALU and flag behavior | PLAT-CPU-002 | Planned |
| [PLAT-CPU-004](../platform/plat-cpu-004-implement-program-counter-and-instruction-register.md) | Implement program counter and instruction register | PLAT-CPU-003 | Planned |
| [PLAT-CPU-005](../platform/plat-cpu-005-implement-instruction-decoder.md) | Implement instruction decoder | PLAT-CPU-004 | Planned |
| [PLAT-CPU-006](../platform/plat-cpu-006-implement-hardwired-control-unit.md) | Implement hardwired control unit | PLAT-CPU-005 | Planned |
| [PLAT-CPU-007](../platform/plat-cpu-007-implement-microcoded-control-option.md) | Implement microcoded control option | PLAT-CPU-006 | Planned |
| [PLAT-CPU-008](../platform/plat-cpu-008-implement-address-data-and-control-buses.md) | Implement address data and control buses | PLAT-CPU-007 | Planned |
| [PLAT-CPU-009](../platform/plat-cpu-009-define-one-bit-reference-cpu.md) | Define one-bit reference CPU | PLAT-CPU-008 | Planned |
| [PLAT-CPU-010](../platform/plat-cpu-010-define-four-bit-reference-cpu-and-isa.md) | Define four-bit reference CPU and ISA | PLAT-CPU-009 | Planned |
| [PLAT-CPU-011](../platform/plat-cpu-011-define-eight-bit-reference-cpu-and-isa.md) | Define eight-bit reference CPU and ISA | PLAT-CPU-010 | Planned |
| [PLAT-CPU-012](../platform/plat-cpu-012-implement-assembler-specification.md) | Implement assembler specification | PLAT-CPU-011 | Planned |
| [PLAT-CPU-013](../platform/plat-cpu-013-implement-program-loader-and-reset-flow.md) | Implement program loader and reset flow | PLAT-CPU-012 | Planned |
| [PLAT-CPU-014](../platform/plat-cpu-014-implement-breakpoints-stepping-and-state-inspection.md) | Implement breakpoints stepping and state inspection | PLAT-CPU-013 | Planned |
| [PLAT-CPU-015](../platform/plat-cpu-015-implement-datapath-and-control-visualization.md) | Implement datapath and control visualization | PLAT-CPU-014 | Planned |
| [PLAT-CPU-016](../platform/plat-cpu-016-validate-reference-cpu-program-suites.md) | Validate reference CPU program suites | PLAT-CPU-015 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
