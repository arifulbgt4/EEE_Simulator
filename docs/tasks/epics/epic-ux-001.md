# EPIC-UX-001 - Application shell and user modes

## Outcome

Deliver the complete **Application shell and user modes** capability for release R1, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-003, REQ-034
- Release: R1
- Entry: Gate G0 documentation baseline.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-UX-001](../platform/plat-ux-001-specify-application-navigation-and-workspace-shell.md) | Specify application navigation and workspace shell | Gate G0 documentation baseline | Planned |
| [PLAT-UX-002](../platform/plat-ux-002-implement-beginner-mode-information-architecture.md) | Implement Beginner mode information architecture | PLAT-UX-001 | Planned |
| [PLAT-UX-003](../platform/plat-ux-003-implement-intermediate-mode-information-architecture.md) | Implement Intermediate mode information architecture | PLAT-UX-002 | Planned |
| [PLAT-UX-004](../platform/plat-ux-004-implement-advanced-mode-information-architecture.md) | Implement Advanced mode information architecture | PLAT-UX-003 | Planned |
| [PLAT-UX-005](../platform/plat-ux-005-implement-research-mode-information-architecture.md) | Implement Research mode information architecture | PLAT-UX-004 | Planned |
| [PLAT-UX-006](../platform/plat-ux-006-define-command-palette-and-global-shortcuts.md) | Define command palette and global shortcuts | PLAT-UX-005 | Planned |
| [PLAT-UX-007](../platform/plat-ux-007-define-contextual-help-and-guided-error-system.md) | Define contextual help and guided-error system | PLAT-UX-006 | Planned |
| [PLAT-UX-008](../platform/plat-ux-008-define-localization-ready-message-catalog-contract.md) | Define localization-ready message catalog contract | PLAT-UX-007 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
