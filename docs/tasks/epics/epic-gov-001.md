# EPIC-GOV-001 - Open-source repository and governance

## Outcome

Deliver the complete **Open-source repository and governance** capability for release R1, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-034, REQ-035
- Release: R1
- Entry: Gate G0 documentation baseline.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-GOV-001](../platform/plat-gov-001-define-repository-layout-and-ownership-boundaries.md) | Define repository layout and ownership boundaries | Gate G0 documentation baseline | Planned |
| [PLAT-GOV-002](../platform/plat-gov-002-define-branch-and-review-policy.md) | Define branch and review policy | PLAT-GOV-001 | Planned |
| [PLAT-GOV-003](../platform/plat-gov-003-define-semantic-version-and-changelog-policy.md) | Define semantic version and changelog policy | PLAT-GOV-002 | Planned |
| [PLAT-GOV-004](../platform/plat-gov-004-define-continuous-integration-quality-gates.md) | Define continuous integration quality gates | PLAT-GOV-003 | Planned |
| [PLAT-GOV-005](../platform/plat-gov-005-define-dependency-update-and-license-review-workflow.md) | Define dependency update and license review workflow | PLAT-GOV-004 | Planned |
| [PLAT-GOV-006](../platform/plat-gov-006-define-issue-and-change-request-templates.md) | Define issue and change request templates | PLAT-GOV-005 | Planned |
| [PLAT-GOV-007](../platform/plat-gov-007-define-security-release-workflow.md) | Define security release workflow | PLAT-GOV-006 | Planned |
| [PLAT-GOV-008](../platform/plat-gov-008-define-release-artifact-and-provenance-manifest.md) | Define release artifact and provenance manifest | PLAT-GOV-007 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
