# PLAT-EXT-018 - Run R3 external analog adapter acceptance audit

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-008, REQ-017, REQ-024, REQ-029, REQ-032, REQ-035, REQ-042, REQ-043, REQ-053, REQ-056 |
| Concern | `run_r3_external_analog_adapter_acceptance_audit` |
| Effort | S |
| Depends on | PLAT-EXT-001; PLAT-EXT-002; PLAT-EXT-003; PLAT-EXT-004; PLAT-EXT-005; PLAT-EXT-006; PLAT-EXT-007; PLAT-EXT-008; PLAT-EXT-009; PLAT-EXT-010; PLAT-EXT-011; PLAT-EXT-012; PLAT-EXT-013; PLAT-EXT-014; PLAT-EXT-015; PLAT-EXT-016; PLAT-EXT-017 |
| Blocks | PLAT-EXT-019 |

## Objective

Audit the entire R3 external analog adapter milestone and publish one evidence-backed `accepted|rejected|blocked` release disposition without changing implementation or test results.

## Context to read

- [Release Acceptance Checklists](../../quality/RELEASE_ACCEPTANCE_CHECKLISTS.md)
- [Requirements Traceability Matrix](../../quality/REQUIREMENTS_TRACEABILITY_MATRIX.md)
- [Test and Validation Strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Open Source and Third-Party Licenses](../../architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md)
- [EPIC-EXT-001](../epics/epic-ext-001.md)

## Exact prerequisites

- `PLAT-EXT-001`, `PLAT-EXT-002`, `PLAT-EXT-003`, `PLAT-EXT-004`, `PLAT-EXT-005`, `PLAT-EXT-006`, `PLAT-EXT-007`, `PLAT-EXT-008`, `PLAT-EXT-009`, `PLAT-EXT-010`, `PLAT-EXT-011`, `PLAT-EXT-012`, `PLAT-EXT-013`, `PLAT-EXT-014`, `PLAT-EXT-015`, `PLAT-EXT-016`, and `PLAT-EXT-017` are Done with their exact evidence digests.

## Public contracts

- `ExternalAnalogR3AcceptanceReportV1`, `AdapterAcceptanceFinding`, `CapabilityDisposition`, `DistributionDisposition`, and `ReleaseBlocker`.

## Inputs

- All task/test/evidence manifests; lifecycle matrix; build/SBOM/license records; capability/translation/mapping artifacts; sandbox/resource evidence; provenance closure; GRC-011..020 differential evidence; requirements, risks, limitations, and R3 checklist.

## Allowed files

- `docs/tasks/platform/plat-ext-018-run-r3-external-analog-adapter-acceptance-audit.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/quality/TEST_AND_VALIDATION_STRATEGY.md`
- `docs/planning/RISK_REGISTER.md`
- `docs/planning/DEPENDENCY_AND_LICENSE_MATRIX.md`
- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`

No implementation, model, or result file may be modified. Exact immutable audit report and evidence paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-018-ACCEPTANCE`, `TEST-PLAT-EXT-018-FAILURE`, fixture `EXT-R3-ACCEPTANCE-AUDIT-V1`.

## Deliverables

- Machine-readable and human-readable audit enumerating every required task/test/contract/evidence digest, capability and unsupported operation, finding/severity/owner, unresolved blocker, known limitation, execution approval, and separate distribution approval.
- Proof of no orphan task/test/requirement/risk, no missing lifecycle operation, no false complete result, no Xyce/HPC work, and no `Source PDF` claim treated as technical evidence.

## Documentation updates

Synchronize audit card/epic, indexes, tests, RTM, risks, dependency/license records, and R3 checklist only after findings are resolved or explicitly block.

## Allowed scope

Read-only conformance and evidence audit of the R3 adapter milestone.

## Forbidden scope

No implementation fix, evidence fabrication, waiver without accepted decision, task status auto-promotion, model retuning, adapter distribution, R7 import work, Xyce, or HPC.

## Required behavior and edge cases

- Missing, stale, conflicting, unverifiable, tampered, or circular evidence yields `blocked` or `rejected`, never a warning-only pass.
- Execution success cannot imply license/distribution approval; unsupported pause/checkpoint/resume may be accepted only when capability negotiation and user-visible behavior are complete.
- All counts derive from explicit manifests and filesystem evidence, not prose totals.
- Re-running the audit over identical inputs produces the same ordered findings/report digest.

## Acceptance tests

1. Acceptance proves complete bidirectional evidence and zero release blockers across all 17 tasks and named requirements.
2. Failure removes/mutates each evidence class and injects false capability, false success, stale source, license conflict, orphan trace, PDF-only claim, and Xyce/HPC contamination; each blocks with exact finding.
3. Evidence includes audit tool/version, input manifest digest, ordered findings, reviewer approvals, execution/distribution dispositions, and report digest.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] All 17 task outcomes and tests are explicitly audited.
- [ ] Technical, security, provenance, numerical, and license evidence is current and source-qualified.
- [ ] Release and distribution dispositions are separate and reproducible.
- [ ] The R3 milestone is accepted or honestly blocked with exact findings.
