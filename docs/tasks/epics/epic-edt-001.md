# EPIC-EDT-001 - Schematic editor

## Outcome

Deliver the complete **Schematic editor** capability for release R1, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-004, REQ-005, REQ-037, REQ-038
- Release: R1
- Entry: Gate G0 documentation baseline and every task-level dependency below.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-EDT-001](../platform/plat-edt-001-define-editor-document-and-viewport-state.md) | Define editor document and viewport state | Gate G0 documentation baseline | Planned |
| [PLAT-EDT-002](../platform/plat-edt-002-implement-component-placement-and-preview.md) | Implement component placement and preview | PLAT-EDT-001 | Planned |
| [PLAT-EDT-003](../platform/plat-edt-003-implement-selection-and-multi-selection.md) | Implement selection and multi-selection | PLAT-EDT-002 | Planned |
| [PLAT-EDT-004](../platform/plat-edt-004-implement-move-rotate-mirror-and-delete-operations.md) | Implement move rotate mirror and delete operations | PLAT-EDT-003 | Planned |
| [PLAT-EDT-005](../platform/plat-edt-005-implement-undo-and-redo-transaction-model.md) | Implement undo and redo transaction model | PLAT-EDT-004 | Planned |
| [PLAT-EDT-006](../platform/plat-edt-006-implement-orthogonal-wire-creation.md) | Implement orthogonal wire creation | PLAT-EDT-005 | Planned |
| [PLAT-EDT-007](../platform/plat-edt-007-implement-junction-crossover-and-no-connect-behavior.md) | Implement junction crossover and no-connect behavior | PLAT-EDT-006 | Planned |
| [PLAT-EDT-008](../platform/plat-edt-008-implement-wire-rerouting-after-component-movement.md) | Implement wire rerouting after component movement | PLAT-EDT-007 | Planned |
| [PLAT-EDT-009](../platform/plat-edt-009-implement-net-and-power-labels.md) | Implement net and power labels | PLAT-EDT-008 | Planned |
| [PLAT-EDT-010](../platform/plat-edt-010-implement-buses-taps-splitters-and-mergers.md) | Implement buses taps splitters and mergers | PLAT-EDT-009 | Planned |
| [PLAT-EDT-011](../platform/plat-edt-011-implement-hierarchical-ports-and-subcircuit-navigation.md) | Implement hierarchical ports and subcircuit navigation | PLAT-EDT-010 | Planned |
| [PLAT-EDT-012](../platform/plat-edt-012-implement-property-inspector-and-validated-editing.md) | Implement property inspector and validated editing | PLAT-EDT-011 | Planned |
| [PLAT-EDT-013](../platform/plat-edt-013-implement-copy-paste-duplicate-and-clipboard-portability.md) | Implement copy paste duplicate and clipboard portability | PLAT-EDT-012 | Planned |
| [PLAT-EDT-014](../platform/plat-edt-014-implement-search-filter-and-focus-navigation.md) | Implement search filter and focus navigation | PLAT-EDT-013 | Planned |
| [PLAT-EDT-015](../platform/plat-edt-015-implement-zoom-pan-minimap-and-fit-to-content.md) | Implement zoom pan minimap and fit-to-content | PLAT-EDT-014 | Planned |
| [PLAT-EDT-016](../platform/plat-edt-016-implement-schematic-and-physical-view-switching.md) | Implement schematic and physical-view switching | PLAT-EDT-015 | Planned |
| [PLAT-EDT-017](../platform/plat-edt-017-implement-package-aware-breadboard-placement-and-pin-mapping.md) | Implement package-aware breadboard placement and pin mapping | PLAT-EDT-016 | Planned |
| [PLAT-EDT-018](../platform/plat-edt-018-implement-editor-diagnostics-overlays.md) | Implement editor diagnostics overlays | PLAT-EDT-017 | Planned |
| [PLAT-EDT-019](../platform/plat-edt-019-implement-svg-and-print-ready-schematic-export.md) | Implement SVG and print-ready schematic export | PLAT-EDT-018 | Planned |
| [PLAT-EDT-020](../platform/plat-edt-020-validate-large-canvas-interaction-budgets.md) | Validate large-canvas interaction budgets | PLAT-EDT-019 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
