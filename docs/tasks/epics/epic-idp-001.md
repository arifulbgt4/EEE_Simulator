# EPIC-IDP-001 - Minimal personal identity and project persistence

## Outcome

Deliver **Minimal personal identity and project persistence** as a bounded, versioned capability with explicit scientific, security, compatibility, lifecycle, and validation evidence.

## Requirements and release

- Requirements: REQ-006, REQ-029, REQ-057, REQ-058
- Release: R1
- Entry: Gate G0 documentation baseline.
- Normative contract: `docs/architecture/DATA_DRIVEN_LIBRARY_AND_STORAGE_ARCHITECTURE.md`.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-IDP-001](../platform/plat-idp-001-define-provider-neutral-google-oidc-architecture.md) | Define provider-neutral Google OIDC architecture | Gate G0 documentation baseline | Planned |
| [PLAT-IDP-002](../platform/plat-idp-002-define-guest-to-account-migration.md) | Define guest to account migration | PLAT-IDP-001 | Planned |
| [PLAT-IDP-003](../platform/plat-idp-003-define-personal-cloud-project-persistence.md) | Define personal cloud project persistence | PLAT-IDP-002 | Planned |
| [PLAT-IDP-004](../platform/plat-idp-004-define-indexeddb-cache-and-sync.md) | Define IndexedDB cache and sync | PLAT-IDP-003 | Planned |

## Exit criteria

- [ ] Every listed task is `Done` with linked current evidence.
- [ ] Requirements, ADRs, schemas, immutable revisions, tests, risks, and release evidence resolve bidirectionally.
- [ ] Nominal, boundary, invalid, compatibility, security, and resource behavior is explicit.
- [ ] Provenance, license, trust, validity, accuracy/uncertainty, lineage, and limitations are complete where applicable.
- [ ] No runtime capability is claimed merely because its documentation exists.
