# PLAT-EXT-021 - Run R7 external analog adapter acceptance audit

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R7 |
| Requirements | REQ-014, REQ-017, REQ-024, REQ-032, REQ-035, REQ-042, REQ-043, REQ-049, REQ-053, REQ-056, REQ-063 |
| Concern | `run_r7_external_analog_adapter_acceptance_audit` |
| Effort | S |
| Depends on | PLAT-EXT-018; PLAT-EXT-019; PLAT-EXT-020 |
| Blocks | None |

## Objective

Audit the R3 adapter foundation plus R7 reviewed-bundle and macro-model evidence and publish the final external analog adapter `accepted|rejected|blocked` disposition for R7.

## Context to read

- [Release Acceptance Checklists](../../quality/RELEASE_ACCEPTANCE_CHECKLISTS.md)
- [Requirements Traceability Matrix](../../quality/REQUIREMENTS_TRACEABILITY_MATRIX.md)
- [Test and Validation Strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Open Source and Third-Party Licenses](../../architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md)
- [EPIC-EXT-001](../epics/epic-ext-001.md)

## Exact prerequisites

- `PLAT-EXT-018` accepted current R3 audit, `PLAT-EXT-019` reviewed bundle/handoff evidence, and `PLAT-EXT-020` complete R7 differential evidence; the audit manifest enumerates every inherited R3 evidence digest explicitly.

## Public contracts

- `ExternalAnalogR7AcceptanceReportV1`, `ImportedModelFinding`, `CoverageDisposition`, `ExecutionDisposition`, `DistributionDisposition`, and `ReleaseBlocker`.

## Inputs

- Current R3 audit; reviewed SPICE closure/handoff and frozen suite; R7 differential/coverage evidence; trust/license/provenance/revocation records; sandbox/resource evidence; requirements/tasks/tests/risks/limitations; R7 checklist and distribution manifest.

## Allowed files

- `docs/tasks/platform/plat-ext-021-run-r7-external-analog-adapter-acceptance-audit.md`
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

No implementation, model, fixture, or result mutation is authorized. Exact immutable audit report and evidence paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-021-ACCEPTANCE`, `TEST-PLAT-EXT-021-FAILURE`, fixture `EXT-R7-ACCEPTANCE-AUDIT-V1`.

## Deliverables

- Deterministic audit report enumerating inherited and R7 task/test/evidence digests, exact model/case coverage, findings/blockers, supported/unsupported syntax and capabilities, validity/accuracy status, trust/license/redistribution, security/resource results, limitations, and separate execution/distribution decisions.
- Proof that every imported model used was immutable/reviewed, every frozen case accounted for, no unknown-rights/revoked content released, no PDF citation treated as technical evidence, and no Xyce/HPC work entered the epic.

## Documentation updates

Synchronize audit/epic, indexes, tests, RTM, risks, coverage, dependency/license records, and R7 checklist after honest disposition.

## Allowed scope

Read-only R7 external analog adapter evidence audit.

## Forbidden scope

No fixing/tuning, waiver fabrication, hidden model/case removal, broad vendor coverage claim, distribution action, new adapter, Xyce/HPC, or change to R11 responsibilities.

## Required behavior and edge cases

- Missing/stale/tampered/conflicting evidence, incomplete suite coverage, trust/license ambiguity, revocation, false accuracy/physical claim, or R3 regression blocks acceptance.
- Execution permission, hosted availability, redistribution, and production release remain independently evaluated.
- Exact manifest-derived counts replace prose totals and duplicate/inherited cases cannot inflate coverage.
- Identical audit inputs produce the same ordered findings and report digest.

## Acceptance tests

1. Acceptance proves complete, bidirectional, current evidence and zero blockers for R3 inheritance plus every R7 case/model.
2. Failure injects orphan/duplicate/omitted case, stale R3 audit, revoked/unknown-rights content, altered result, false physical claim, PDF-only source, license conflict, sandbox regression, and Xyce/HPC contamination; each blocks.
3. Evidence records audit version/input digest, exact counts, findings/severity/owner, reviewer approvals, execution/hosting/redistribution/release dispositions, and final report digest.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] R3 inheritance and all R7 tasks/cases are explicitly audited.
- [ ] Technical, numerical, security, provenance, trust, and license evidence is current.
- [ ] No unverified source claim or hidden scope satisfies acceptance.
- [ ] R7 is accepted or honestly blocked with exact reproducible findings.
