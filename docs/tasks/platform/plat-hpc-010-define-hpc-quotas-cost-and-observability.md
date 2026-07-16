# PLAT-HPC-010 - Define HPC quotas, cost, and observability

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-HPC-001](../epics/epic-hpc-001.md) |
| Release | R11 |
| Requirements | REQ-030, REQ-032, REQ-033, REQ-053, REQ-055, REQ-059 |
| Concern | `hpc_quota_cost_and_observability` |
| Effort | S |
| Depends on | PLAT-HPC-009; PLAT-API-010; PLAT-API-011; PLAT-OPS-007; PLAT-OPS-008; PLAT-OPS-012 |
| Blocks | PLAT-HPC-011 |

## Objective

Define one reconciled HPC admission, quota, cost, usage, metrics, traces, alert, and capacity contract that prevents unreserved work and uncontrolled spend while preserving tenant privacy and complete workload-to-artifact provenance.

## Context to read

- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md), quota/admission and job lifecycle
- [Deployment Operations and Observability](../../architecture/DEPLOYMENT_OPERATIONS_AND_OBSERVABILITY.md), SLOs, telemetry, capacity, alerts
- [Local, Cloud, and Worker Architecture](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md), resource profiles
- [Security, Privacy, and Sandboxing](../../architecture/SECURITY_PRIVACY_AND_SANDBOXING.md), data minimization and abuse controls
- [Performance Benchmarks](../../quality/PERFORMANCE_BENCHMARKS.md)

## Exact prerequisites

- Completed `PLAT-API-010` quota/admission estimation and `PLAT-API-011` usage/cost ledger.
- Completed `PLAT-OPS-007`, `PLAT-OPS-008`, and `PLAT-OPS-012` metrics, tracing, capacity, and autoscaling evidence.
- Accepted archive/restore cost and lifecycle signals from `PLAT-HPC-009` and all upstream HPC identity/resource contracts.

## Public contracts

- `HpcQuotaPolicy`
- `HpcQuotaReservation`
- `HpcAdmissionEstimate`
- `HpcCostRateCard`
- `HpcCostEstimate`
- `HpcUsageRecord`
- `HpcUsageReconciliation`
- `HpcTelemetryEnvelope`
- `HpcServiceLevelObjective`
- `HpcCapacitySnapshot`
- `HpcAlertEvent`

Every policy/rate/estimate/usage record pins tenant/project, workload/job/attempt/shard/allocation/artifact identities; region/profile/engine; policy/rate revisions and currency/unit; reserved and actual CPU/GPU/node/rank/memory/wall/scratch/network/result/archive/restore units; limits; timestamps; state/fence; attribution; and audit correlation.

## Exact inputs, calculations, and reference data

- Authorized principal/tenant/project; immutable workload estimate; requested profile/priority/deadline; current quotas/reservations/usage; capacity; rate card and taxes/credits policy if applicable; hard/soft cost ceiling; retry/checkpoint/archive/egress estimates; actual scheduler/worker/storage metrics; cancellation and terminal events; SLO/alert thresholds; privacy classification; telemetry sampling/retention; reconciliation window.
- Estimate calculation is a versioned sum of declared resource quantity times rate for each billable dimension plus declared fixed/transfer/archive operations; units, rounding, minimums, free tier, taxes/credits, uncertainty/margin, and currency are explicit. Unknown rate or quantity cannot be treated as zero.
- Reservation is atomic with admission. Each actual usage unit belongs to one fenced attempt/allocation/artifact operation; duplicate/stale records are idempotently rejected. Reconciliation states estimated, reserved, actual, released, disputed, corrected, and final amounts without mutating history.
- Nominal fixtures: admitted job under quota; multi-shard retry/checkpoint/archive usage; cancellation/refund/release; capacity scale. Boundary fixtures: exact quota/cost/SLO/capacity limit, smallest billable interval, rate revision at submission boundary, zero-cost explicitly free operation, maximum telemetry cardinality, and final reconciliation window.
- Failure fixtures: quota exhausted, capacity absent, unknown/stale rate, overflow/negative quantity, duplicate/stale usage, missing fence, cost ceiling crossed, scheduler-vs-worker discrepancy, storage usage lag, telemetry backend outage, high-cardinality labels, sensitive payload field, alert storm, and ledger reconciliation mismatch.
- Rates and provider behavior require pinned primary contracts/source records and current dates; benchmarks require reproducible named profiles. Source PDF prose is not cost, capacity, quota, or SLO evidence.

## Allowed files

- `docs/tasks/platform/plat-hpc-010-define-hpc-quotas-cost-and-observability.md`
- `docs/tasks/epics/epic-hpc-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/DEPLOYMENT_OPERATIONS_AND_OBSERVABILITY.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`
- `docs/quality/PERFORMANCE_BENCHMARKS.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No quota/rate/ledger value, billing transaction, alert, telemetry backend, autoscaler, deployment, source/test path, or cloud capacity is authorized while `Planned`.

## Expected outputs and known limitations

- Versioned policy/reservation/estimate/rate/usage/reconciliation/telemetry/SLO/capacity/alert schemas, dimensional calculation examples, privacy-safe dashboards/alerts contract, and reconciliation evidence.
- Human-readable, keyboard-reachable, non-color-only quota/cost/progress/failure summaries. Estimates retain uncertainty and expiry; they are not fixed prices or capacity guarantees unless a separately accepted commercial contract says so.

## Required behavior and diagnostics

- `PLAT_HPC_010_NOMINAL`: reserve before dispatch, attribute each usage item once, stream privacy-safe telemetry, release unused capacity, and reconcile estimate/reservation/actual with one immutable audit trail.
- `PLAT_HPC_010_BOUNDARY`: exact quota, rate, currency/rounding, resource, cost ceiling, cardinality, SLO, capacity, retention, and reconciliation-time boundaries are enforced.
- `PLAT_HPC_010_QUOTA_DENIED`: reject admission or further retry/restore with exact exhausted dimension, current/reserved/requested amount, policy revision, reset/recovery action, and no unreserved launch.
- `PLAT_HPC_010_RATE_UNKNOWN`: block cost-bearing admission when a required rate/currency/unit/revision is missing, expired, incompatible, or ambiguous; never substitute zero/latest.
- `PLAT_HPC_010_COST_CEILING`: stop new shard/retry/restore admission at the declared hard barrier and initiate bounded cancellation/checkpoint policy without falsifying accrued usage.
- `PLAT_HPC_010_USAGE_CONFLICT`: quarantine duplicate-disagreeing, negative, overflowed, stale-fence, orphaned, or dimensionally invalid usage.
- `PLAT_HPC_010_RECONCILIATION_MISMATCH`: retain estimated/reserved/provider/worker/storage values, differences, correction event, owner, and status; never rewrite prior ledger events.
- `PLAT_HPC_010_TELEMETRY_PRIVACY`: reject schematic/model/source/firmware/waveform/secrets/credentials or unapproved high-cardinality values from default telemetry.
- `PLAT_HPC_010_OBSERVABILITY_DEGRADED`: buffer only within declared bounds, preserve core job safety/accounting, emit durable degradation state, and fail admission when mandatory accounting/audit cannot be guaranteed.
- `PLAT_HPC_010_SLO_OR_CAPACITY_BREACH`: create deduplicated severity/owner/runbook alert and capacity decision; alert storms cannot exhaust the control plane.

## Acceptance tests and evidence

1. `TEST-PLAT-HPC-010-ACCEPTANCE` validates admission/reservation, estimate calculation, multi-attempt usage attribution, cancellation/release, archive/restore cost, telemetry correlation, SLO/capacity evaluation, and final reconciliation.
2. `TEST-PLAT-HPC-010-FAILURE` exercises all diagnostics, concurrent admission race, stale/duplicate usage, overflow, ceiling crossing, backend outage, sensitive labels, alert storm, and capacity loss.
3. Load evidence measures admission and telemetry overhead, cardinality/storage bounds, ledger lag, reconciliation accuracy, cancellation barrier latency, alert delivery/deduplication, and capacity recovery on a named profile.
4. Evidence contains policy/rate/version sources, all dimensional calculations, capacity snapshots, reservations/ledger events, redacted telemetry schemas, trace correlation, alerts/runbook outcomes, expected/actual cost and usage, limitations, and privacy review.

## Documentation updates on completion

- Synchronize this card/epic, indexes, API/operations/worker/security contracts, benchmarks, tests, RTM, risks, and G11 checklist.
- Link cost-abuse, storage-growth, worker-loss, reproducibility, privacy, and capacity risks; add HPC reservation/reconciliation/capacity-exhaustion risks if not explicit.

## Forbidden scope

- Do not launch before reservation, infer missing rates as zero, use mutable/latest rates retroactively, double-charge retries, mutate ledger history, emit sensitive payloads, allow unbounded label cardinality, or make billing depend on Source PDF prose.
- Do not publish the final G11 decision owned by `PLAT-HPC-011`.
- Do not charge a user, alter a quota, or create infrastructure under this documentation task.

## Definition of Done

- [ ] Quota/reservation/estimate/rate/usage/reconciliation/telemetry/SLO/capacity/alert contracts and dimensional calculations are exact and versioned.
- [ ] Nominal, concurrent, quota, rate, cost ceiling, usage, reconciliation, privacy, outage, cardinality, alert, SLO, and capacity evidence passes.
- [ ] Resource, cost, telemetry, ledger, and cancellation bounds are measured and reconciled on named profiles.
- [ ] Central records and G11 evidence are synchronized before status advances.
- [ ] No live financial, quota, telemetry, or infrastructure state was changed.
