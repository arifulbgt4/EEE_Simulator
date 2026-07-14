# EPIC-API-001 - Cloud simulation jobs

## Outcome

Deliver the complete **Cloud simulation jobs** capability for release R10, including normative behavior, failure handling, validation, documentation, security, accessibility, performance, compatibility, and operations where applicable.

## Requirements and release

- Requirements: REQ-029, REQ-030
- Release: R10
- Entry: Gate G6 Electronics MVP.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-API-001](../platform/plat-api-001-define-simulation-job-rest-resources.md) | Define simulation job REST resources | Gate G6 Electronics MVP | Planned |
| [PLAT-API-002](../platform/plat-api-002-implement-request-validation-and-capability-routing.md) | Implement request validation and capability routing | PLAT-API-001 | Planned |
| [PLAT-API-003](../platform/plat-api-003-implement-redis-streams-job-dispatch.md) | Implement Redis Streams job dispatch | PLAT-API-002 | Planned |
| [PLAT-API-004](../platform/plat-api-004-implement-worker-lease-heartbeat-and-expiry.md) | Implement worker lease heartbeat and expiry | PLAT-API-003 | Planned |
| [PLAT-API-005](../platform/plat-api-005-implement-sse-progress-diagnostic-and-result-stream.md) | Implement SSE progress diagnostic and result stream | PLAT-API-004 | Planned |
| [PLAT-API-006](../platform/plat-api-006-implement-result-chunk-storage-and-retrieval.md) | Implement result chunk storage and retrieval | PLAT-API-005 | Planned |
| [PLAT-API-007](../platform/plat-api-007-implement-cancellation-semantics.md) | Implement cancellation semantics | PLAT-API-006 | Planned |
| [PLAT-API-008](../platform/plat-api-008-implement-retry-and-idempotency-semantics.md) | Implement retry and idempotency semantics | PLAT-API-007 | Planned |
| [PLAT-API-009](../platform/plat-api-009-implement-checkpoint-and-resume-lifecycle.md) | Implement checkpoint and resume lifecycle | PLAT-API-008 | Planned |
| [PLAT-API-010](../platform/plat-api-010-implement-quota-and-admission-estimation.md) | Implement quota and admission estimation | PLAT-API-009 | Planned |
| [PLAT-API-011](../platform/plat-api-011-implement-usage-and-cost-ledger.md) | Implement usage and cost ledger | PLAT-API-010 | Planned |
| [PLAT-API-012](../platform/plat-api-012-implement-job-retention-and-deletion-policy.md) | Implement job retention and deletion policy | PLAT-API-011 | Planned |
| [PLAT-API-013](../platform/plat-api-013-implement-cloud-to-local-result-provenance.md) | Implement cloud-to-local result provenance | PLAT-API-012 | Planned |
| [PLAT-API-014](../platform/plat-api-014-validate-worker-loss-and-duplicate-delivery-recovery.md) | Validate worker loss and duplicate-delivery recovery | PLAT-API-013 | Planned |

## Exit criteria

- [ ] Every listed task is Done with linked evidence.
- [ ] Requirement, component/interface, test, and release traceability has no gap.
- [ ] Nominal and failure behavior are documented and validated.
- [ ] Security, performance, accessibility, compatibility, migration, and operational gates pass where applicable.
- [ ] Known limitations and deferred work are explicit.
