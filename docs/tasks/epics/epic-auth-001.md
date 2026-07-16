# EPIC-AUTH-001 - Identity organizations and authorization

## Outcome

Deliver the advanced **organizations and authorization** capability for release R10 on top of the provider-neutral personal identity established by `EPIC-IDP-001`. This epic owns organizations, membership, invitations, complex project roles, public visibility, cross-tenant controls, and advanced revocation/audit; it does not move those features into R1.

## Requirements and release

- Requirements: REQ-031, REQ-032, REQ-057, REQ-060
- Release: R10
- Entry: Gate G6 Electronics MVP.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-AUTH-001](../platform/plat-auth-001-define-oidc-compatible-identity-contract.md) | Define OIDC-compatible identity contract | Gate G6 Electronics MVP | Planned |
| [PLAT-AUTH-002](../platform/plat-auth-002-implement-user-profile-and-account-lifecycle.md) | Implement user profile and account lifecycle | PLAT-AUTH-001 | Planned |
| [PLAT-AUTH-003](../platform/plat-auth-003-implement-organization-and-membership-lifecycle.md) | Implement organization and membership lifecycle | PLAT-AUTH-002 | Planned |
| [PLAT-AUTH-004](../platform/plat-auth-004-define-project-roles-and-permission-matrix.md) | Define project roles and permission matrix | PLAT-AUTH-003 | Planned |
| [PLAT-AUTH-005](../platform/plat-auth-005-implement-object-level-authorization.md) | Implement object-level authorization | PLAT-AUTH-004 | Planned |
| [PLAT-AUTH-006](../platform/plat-auth-006-implement-invitation-acceptance-and-expiry.md) | Implement invitation acceptance and expiry | PLAT-AUTH-005 | Planned |
| [PLAT-AUTH-007](../platform/plat-auth-007-implement-public-unlisted-and-private-visibility.md) | Implement public unlisted and private visibility | PLAT-AUTH-006 | Planned |
| [PLAT-AUTH-008](../platform/plat-auth-008-implement-session-and-token-revocation.md) | Implement session and token revocation | PLAT-AUTH-007 | Planned |
| [PLAT-AUTH-009](../platform/plat-auth-009-implement-authorization-audit-events.md) | Implement authorization audit events | PLAT-AUTH-008 | Planned |
| [PLAT-AUTH-010](../platform/plat-auth-010-validate-cross-tenant-access-denial.md) | Validate cross-tenant access denial | PLAT-AUTH-009 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
- [ ] `PLAT-AUTH-001/002` extend, rather than replace or duplicate, the R1 provider-neutral subject/session/account contract and preserve guest/offline use.
