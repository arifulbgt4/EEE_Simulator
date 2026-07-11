# EPIC-PROJ-001 - Project format and lifecycle

## Outcome

Deliver the complete **Project format and lifecycle** capability for release R1, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-006, REQ-023, REQ-038
- Release: R1
- Entry: Gate G0 documentation baseline and every task-level dependency below.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-PROJ-001](../platform/plat-proj-001-define-eesim-manifest-schema.md) | Define .eesim manifest schema | Gate G0 documentation baseline | Planned |
| [PLAT-PROJ-002](../platform/plat-proj-002-define-schematic-hierarchy-schema.md) | Define schematic hierarchy schema | PLAT-PROJ-001 | Planned |
| [PLAT-PROJ-003](../platform/plat-proj-003-define-component-model-and-asset-references.md) | Define component model and asset references | PLAT-PROJ-002 | Planned |
| [PLAT-PROJ-004](../platform/plat-proj-004-define-reusable-package-definition-and-pin-map-records.md) | Define reusable package definition and pin-map records | PLAT-PROJ-003 | Planned |
| [PLAT-PROJ-005](../platform/plat-proj-005-define-custom-package-designer-records-and-migrations.md) | Define custom package designer records and migrations | PLAT-PROJ-004 | Planned |
| [PLAT-PROJ-006](../platform/plat-proj-006-define-stimuli-testbench-and-measurement-records.md) | Define stimuli testbench and measurement records | PLAT-PROJ-005 | Planned |
| [PLAT-PROJ-007](../platform/plat-proj-007-define-simulation-settings-and-deterministic-seed-records.md) | Define simulation settings and deterministic seed records | PLAT-PROJ-006 | Planned |
| [PLAT-PROJ-008](../platform/plat-proj-008-define-result-provenance-and-immutable-run-records.md) | Define result provenance and immutable run records | PLAT-PROJ-007 | Planned |
| [PLAT-PROJ-009](../platform/plat-proj-009-define-packed-eesim-archive-layout.md) | Define packed .eesim archive layout | PLAT-PROJ-008 | Planned |
| [PLAT-PROJ-010](../platform/plat-proj-010-define-git-friendly-unpacked-project-layout.md) | Define Git-friendly unpacked project layout | PLAT-PROJ-009 | Planned |
| [PLAT-PROJ-011](../platform/plat-proj-011-define-archive-integrity-and-checksum-policy.md) | Define archive integrity and checksum policy | PLAT-PROJ-010 | Planned |
| [PLAT-PROJ-012](../platform/plat-proj-012-define-schema-version-compatibility-rules.md) | Define schema version compatibility rules | PLAT-PROJ-011 | Planned |
| [PLAT-PROJ-013](../platform/plat-proj-013-define-forward-migration-workflow.md) | Define forward migration workflow | PLAT-PROJ-012 | Planned |
| [PLAT-PROJ-014](../platform/plat-proj-014-define-corrupted-and-partial-project-recovery-behavior.md) | Define corrupted and partial project recovery behavior | PLAT-PROJ-013 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
