# EPIC-DATA-001 - Data-driven Library Service and lifecycle

## Outcome

Deliver **Data-driven Library Service and lifecycle** as a bounded, versioned capability with explicit scientific, security, compatibility, lifecycle, and validation evidence.

## Requirements and release

- Requirements: REQ-054, REQ-055, REQ-056, REQ-059, REQ-060, REQ-061, REQ-062, REQ-063
- Release: R1
- Entry: Gate G0 documentation baseline.
- Normative contract: `docs/architecture/DATA_DRIVEN_LIBRARY_AND_STORAGE_ARCHITECTURE.md`.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-DATA-001](../platform/plat-data-001-define-mixed-storage-responsibilities.md) | Define mixed storage responsibilities | Gate G0 documentation baseline | Planned |
| [PLAT-DATA-002](../platform/plat-data-002-define-the-versioned-library-service-api.md) | Define the versioned Library Service API | PLAT-DATA-001 | Planned |
| [PLAT-DATA-003](../platform/plat-data-003-define-library-publication-lifecycle.md) | Define library publication lifecycle | PLAT-DATA-002 | Planned |
| [PLAT-DATA-004](../platform/plat-data-004-define-system-library-permissions.md) | Define system library permissions | PLAT-DATA-003 | Planned |
| [PLAT-DATA-005](../platform/plat-data-005-define-user-library-permissions.md) | Define user library permissions | PLAT-DATA-004 | Planned |
| [PLAT-DATA-006](../platform/plat-data-006-define-validated-safe-crud-operations.md) | Define validated safe CRUD operations | PLAT-DATA-005 | Planned |
| [PLAT-DATA-007](../platform/plat-data-007-resolve-dependencies-and-reverse-dependencies.md) | Resolve dependencies and reverse dependencies | PLAT-DATA-006 | Planned |
| [PLAT-DATA-008](../platform/plat-data-008-validate-documentation-and-contract-consistency.md) | Validate documentation and contract consistency | PLAT-DATA-007 | Planned |

## Exit criteria

- [ ] Every listed task is `Done` with linked current evidence.
- [ ] Requirements, ADRs, schemas, immutable revisions, tests, risks, and release evidence resolve bidirectionally.
- [ ] Nominal, boundary, invalid, compatibility, security, and resource behavior is explicit.
- [ ] Provenance, license, trust, validity, accuracy/uncertainty, lineage, and limitations are complete where applicable.
- [ ] No runtime capability is claimed merely because its documentation exists.
