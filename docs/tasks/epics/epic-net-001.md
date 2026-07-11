# EPIC-NET-001 - Units topology and netlist

## Outcome

Deliver the complete **Units topology and netlist** capability for release R2, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-008, REQ-023
- Release: R2
- Entry: Gate G0 documentation baseline and every task-level dependency below.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-NET-001](../platform/plat-net-001-define-si-quantity-and-unit-parser.md) | Define SI quantity and unit parser | Gate G0 documentation baseline | Planned |
| [PLAT-NET-002](../platform/plat-net-002-define-parameter-dimensional-validation.md) | Define parameter dimensional validation | PLAT-NET-001 | Planned |
| [PLAT-NET-003](../platform/plat-net-003-implement-electrical-net-extraction.md) | Implement electrical net extraction | PLAT-NET-002 | Planned |
| [PLAT-NET-004](../platform/plat-net-004-implement-branch-and-reference-node-identification.md) | Implement branch and reference-node identification | PLAT-NET-003 | Planned |
| [PLAT-NET-005](../platform/plat-net-005-implement-hierarchy-flattening-and-name-scoping.md) | Implement hierarchy flattening and name scoping | PLAT-NET-004 | Planned |
| [PLAT-NET-006](../platform/plat-net-006-implement-incompatible-domain-connection-diagnostics.md) | Implement incompatible-domain connection diagnostics | PLAT-NET-005 | Planned |
| [PLAT-NET-007](../platform/plat-net-007-implement-floating-short-and-source-loop-diagnostics.md) | Implement floating short and source-loop diagnostics | PLAT-NET-006 | Planned |
| [PLAT-NET-008](../platform/plat-net-008-define-canonical-internal-netlist-contract.md) | Define canonical internal netlist contract | PLAT-NET-007 | Planned |
| [PLAT-NET-009](../platform/plat-net-009-implement-spice-compatible-netlist-export-mapping.md) | Implement SPICE-compatible netlist export mapping | PLAT-NET-008 | Planned |
| [PLAT-NET-010](../platform/plat-net-010-implement-result-probe-to-schematic-mapping.md) | Implement result probe to schematic mapping | PLAT-NET-009 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
