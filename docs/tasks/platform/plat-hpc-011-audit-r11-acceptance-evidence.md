# PLAT-HPC-011 - Audit R11 acceptance evidence

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-HPC-001](../epics/epic-hpc-001.md) |
| Release | R11 |
| Requirements | REQ-006, REQ-007, REQ-010, REQ-013, REQ-015, REQ-017, REQ-019, REQ-024, REQ-029, REQ-030, REQ-032, REQ-033, REQ-035, REQ-042, REQ-043, REQ-045, REQ-046, REQ-053, REQ-055, REQ-056, REQ-059, REQ-061, REQ-063 |
| Concern | `r11_acceptance_evidence_audit` |
| Effort | S |
| Depends on | PLAT-HPC-001; PLAT-HPC-002; PLAT-HPC-003; PLAT-HPC-004; PLAT-HPC-005; PLAT-HPC-006; PLAT-HPC-007; PLAT-HPC-008; PLAT-HPC-009; PLAT-HPC-010 |
| Blocks | Gate G11 HPC; G13 GPU/research |

## Objective

Independently audit every mandatory R11 contract and immutable evidence artifact, publish all findings, and issue exactly one fail-closed G11 release decision without modifying the implementation or evidence under review.

## Context to read

- [Release Gates](../../planning/RELEASE_GATES.md), G11 and downstream G13
- [Release Acceptance Checklists](../../quality/RELEASE_ACCEPTANCE_CHECKLISTS.md), R11
- [Requirements Traceability Matrix](../../quality/REQUIREMENTS_TRACEABILITY_MATRIX.md)
- [Test and Validation Strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- `PLAT-HPC-001` through `PLAT-HPC-010` are `Done` with immutable acceptance/failure evidence, current limitations, and no unresolved mandatory dependency.
- Every cross-epic prerequisite named by those cards is complete and resolves from the evidence matrix.
- Proposed atomic tests are registered and have current results: `TEST-PLAT-HPC-001-ACCEPTANCE/FAILURE` through `TEST-PLAT-HPC-010-ACCEPTANCE/FAILURE`.
- Current legal/license, security, privacy, capacity, recovery, reproducibility, numerical/physical, performance, accessibility where applicable, and operations reviewers are identified by role and independence.

## Public contracts

- `G11AuditPlan`
- `G11EvidenceInventory`
- `G11AuditFinding`
- `G11EvidenceException`
- `G11AcceptanceManifest`
- `G11ReleaseDecision`

The audit inventory contains every requirement, ADR, epic/task, test, risk, dependency/license decision, architecture contract, official technical source, fixture, execution environment, image/SBOM, artifact, checkpoint/replay, benchmark, cost/usage, and reviewer evidence identity required by R11.

## Exact inputs and audit rules

- Accepted `G11EntryDecision`; all task contracts and results; central task/test/RTM/risk/dependency/release records; engine/legal/sandbox evidence; workload/orchestration/MPI fixtures; Monte Carlo/thermal/reduction/checkpoint/artifact/quota/cost/observability results; exact versions/hashes; environments; timestamps; owners; expirations; exceptions; limitations; incident/open-finding state.
- Required audit dimensions: completeness, identity/integrity, bidirectional traceability, source authority, compatibility, isolation, license/distribution, deterministic/reproducible behavior, numerical/physical evidence class, security/privacy, performance/scale, accessibility of user-facing diagnostics where applicable, operations/recovery, cost/capacity, retention/retrieval, and downstream gate dependency.
- Finding severities are `Critical`, `High`, `Medium`, `Low`, and `Informational`; states are `open`, `accepted_exception`, `remediated`, and `verified_closed`. Mandatory dimensions cannot use a blanket exception. Any open Critical/High finding, missing mandatory artifact, rejected/unknown license decision, sandbox failure, reproducibility failure, broken traceability, or expired evidence makes the decision `failed`.
- An exception requires exact scope, requirement/risk, rationale, owner, approver role, compensating control, user-visible limitation, expiry, re-test trigger, and evidence. It cannot relax security isolation, legal authorization, artifact integrity, tenant separation, or claimed scientific accuracy.
- Canonical decision digest uses the accepted `PLAT-HPC-001` evidence canonicalizer over the complete inventory, findings, exceptions, reviewer attestations, and disposition.
- Nominal fixture: complete passing R11 evidence set. Boundary fixtures: evidence at review expiry, one allowed Medium exception at exact expiry, tolerance exactly met, exact resource/cost limit, and G13 dependency resolution. Failure fixtures: each mandatory evidence class missing/stale/conflicting, Source PDF-only technical claim, open Critical/High finding, license unknown, sandbox escape, deterministic/replay mismatch, numerical/physical overclaim, cross-tenant retrieval, quota/ledger discrepancy, and unsynchronized central count/link.

## Allowed files

- `docs/tasks/platform/plat-hpc-011-audit-r11-acceptance-evidence.md`
- `docs/tasks/epics/epic-hpc-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`
- `docs/architecture/DEPLOYMENT_OPERATIONS_AND_OBSERVABILITY.md`
- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`
- `docs/quality/TEST_AND_VALIDATION_STRATEGY.md`
- `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`
- `docs/quality/PERFORMANCE_BENCHMARKS.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/DEPENDENCY_AND_LICENSE_MATRIX.md`
- `docs/planning/RISK_REGISTER.md`

No audit-evidence, implementation, runtime-test, test-under-review, runtime configuration, external-engine, evidence-observation, quota/ledger, artifact, cluster, or release-deployment path is authorized while this card is `Planned`. Before promotion to `Ready`, completed `PLAT-GOV-001` must supply exact immutable audit/evidence and runtime-test paths without widening the audit concern. The audit may read, but never change, evidence under review.

## Expected outputs and known limitations

- Versioned audit-plan/inventory/finding/exception/manifest/decision schemas, complete finding set, deterministic decision digest, independent reviewer attestations, and downstream-gate status.
- A human-readable, keyboard-reachable, non-color-only audit summary linked to machine evidence. The audit proves only the exact reviewed revisions and expires at its declared review boundary; later changes require a new audit.

## Required behavior and diagnostics

- `PLAT_HPC_011_NOMINAL`: inventory resolves completely, independent reviewers verify evidence, no mandatory finding remains, and one immutable `G11ReleaseDecision: accepted` is published with digest.
- `PLAT_HPC_011_BOUNDARY`: exact expiry, tolerance, resource, cost, exception, and review boundaries are evaluated without rounding or silent grace.
- `PLAT_HPC_011_EVIDENCE_MISSING`: list every missing expected ID/type/owner and fail G11; do not stop at the first gap.
- `PLAT_HPC_011_EVIDENCE_STALE_OR_CONFLICTING`: identify superseded/expired/hash-mismatched/incompatible duplicates and fail until resolved by new evidence.
- `PLAT_HPC_011_SOURCE_UNCONFIRMED`: reject a technical claim supported only by Source PDF citations, informal prose, unpinned secondary material, or undocumented expert judgment.
- `PLAT_HPC_011_LICENSE_OR_SECURITY_FAILED`: fail on unknown/rejected/expired legal decision, core-process boundary breach, redistribution without approval, sandbox failure, tenant leak, or unresolved mandatory security finding.
- `PLAT_HPC_011_REPRODUCIBILITY_OR_ACCURACY_FAILED`: fail on deterministic sample drift, incompatible/failed replay, undeclared approximation, failed thermal/conservation envelope, or physical/scientific overclaim.
- `PLAT_HPC_011_OPERATIONS_FAILED`: fail on recovery, artifact integrity/retrieval, quota/cost reconciliation, mandatory telemetry, alert, capacity, cancellation, or bounded-retention evidence gap.
- `PLAT_HPC_011_TRACEABILITY_DRIFT`: fail when any requirement/task/test/risk/license/gate link, count, status, or evidence digest disagrees.
- `PLAT_HPC_011_REVIEW_CONFLICT`: preserve competing reviewer findings and escalate; never choose acceptance by majority or suppress dissent without resolved evidence.

## Acceptance tests and evidence

1. `TEST-PLAT-HPC-011-ACCEPTANCE` audits the complete valid inventory, recomputes hashes/counts/traceability, verifies reviewer independence and boundaries, and reproduces the accepted decision digest.
2. `TEST-PLAT-HPC-011-FAILURE` injects every diagnostic class individually and in combination; G11 remains failed and G13 dependency unresolved with a complete finding list.
3. A second independent audit from the immutable bundle produces the same inventory digest, finding states, and decision or records an explicit review conflict that fails the gate.
4. Evidence includes audit tool/schema revisions, exact commands, full expected/actual inventory, link/count validation, reviewer roles/attestations, findings/exceptions, decision digest, limitations, expiry/review dates, and downstream gate status.

## Documentation updates on completion

- Synchronize this card/epic, platform and master task indexes, requirement/test mappings, RTM, risks, dependency/license matrix, G11 checklist, release gate evidence, and documented counts in one reviewed change.
- Register `TEST-PLAT-HPC-011-ACCEPTANCE` and `TEST-PLAT-HPC-011-FAILURE`, attach immutable evidence, and record all open/deferred limitations.

## Forbidden scope

- Do not repair implementation/evidence during audit, alter observed results, downgrade finding severity to pass, accept missing artifacts, waive legal/security/integrity/tenant/accuracy obligations, or mark upstream tasks `Done`.
- Do not accept documentation existence, Source PDF citations, planned tests, or self-attestation as execution evidence.
- Do not release/deploy R11 or unblock G13 from this documentation-only card.

## Definition of Done

- [ ] Inventory, findings, exceptions, manifest, decision, reviewer, expiry, and digest contracts are exact and versioned.
- [ ] Passing and every failure-class audit fixture produce the expected fail-closed decision and complete finding set.
- [ ] Independent recomputation verifies hashes, counts, bidirectional links, source authority, and decision digest.
- [ ] Central records and immutable G11 evidence are synchronized before status advances.
- [ ] G11 is accepted only when every mandatory finding is verified closed; otherwise the published decision is failed.
