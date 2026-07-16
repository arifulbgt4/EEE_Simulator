# PLAT-EXT-016 - Record engine, model, license, and result provenance

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-024, REQ-035, REQ-042, REQ-053, REQ-063 |
| Concern | `record_engine_model_license_and_result_provenance` |
| Effort | S |
| Depends on | PLAT-EXT-015; PLAT-GOV-008 |
| Blocks | PLAT-EXT-017 |

## Objective

Bind each external analog attempt, partial/final result, checkpoint, and evidence bundle to immutable engine, adapter, model, input, configuration, seed, isolation, source, trust, license, and distribution records.

## Context to read

- [Applied Physics and Real-World Fidelity](../../architecture/APPLIED_PHYSICS_AND_REAL_WORLD_FIDELITY.md)
- [Open Source and Third-Party Licenses](../../architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md)
- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [Source and Evidence Policy](../../SOURCE_AND_EVIDENCE_POLICY.md)
- [ADR-0008](../../decisions/ADR-0008.md)

## Exact prerequisites

- `PLAT-EXT-015` isolation evidence; `PLAT-GOV-008` release artifact/provenance manifest contract.

## Public contracts

- `ExternalEngineProvenanceManifestV1`, `ModelExecutionClosure`, `LicenseDisposition`, `EvidenceSourceRecord`, `ResultProvenance`, and `RevocationRecord`.

## Inputs

- Planned registry seed `mdl-external-adapter-ngspice@1.0.0`; engine source/build/artifact/SBOM/license/notice records; adapter/protocol/translator/mapping versions; exact execution/model dependency closure; request/config/seed/timebase/environment; sandbox policy; attempt/events/chunks/result/checkpoint digests; evidence sources and reviewer states.

## Allowed files

- `docs/tasks/platform/plat-ext-016-record-engine-model-license-and-result-provenance.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/architecture/APPLIED_PHYSICS_AND_REAL_WORLD_FIDELITY.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`
- `docs/SOURCE_AND_EVIDENCE_POLICY.md`
- `docs/planning/DEPENDENCY_AND_LICENSE_MATRIX.md`
- `docs/catalog/model-registry.yaml`
- `NOTICE.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while `Planned`; exact implementation and test paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-016-ACCEPTANCE`, `TEST-PLAT-EXT-016-FAILURE`, fixture `EXT-PROVENANCE-CLOSURE-V1`.

## Deliverables

- Canonically serialized provenance manifest with complete dependency DAG/closure, immutable digests, source identity, trust/evidence state, license/redistribution disposition, adapter capability/isolation identity, determinism class, accuracy status, and limitations.
- Independent states for `execution_allowed`, `hosted_use_allowed`, `redistribution_allowed`, and `released`; one cannot imply another.
- Quarantine/revocation/supersession rules preserving historical result identity without continued use/distribution.

## Documentation updates

Synchronize card/epic, source/evidence and license contracts, dependency/NOTICE where applicable, indexes, tests, RTM, risk, and R3 checklist.

## Allowed scope

Provenance, trust, license disposition, and result lineage records for the external adapter.

## Forbidden scope

No legal advice, permission inferred from engine execution, mutable published record, unknown-rights publication, hard deletion of referenced evidence, or `Source PDF` as technical/license proof.

## Required behavior and edge cases

- Missing/ambiguous source, digest, model dependency, license, trust, build, isolation, or result link blocks release and applicable execution/publication.
- Same manifest inputs serialize identically; dependency cycles, mutable aliases, and digest conflicts reject.
- Partial/cancelled/failed results retain full provenance and cannot inherit complete/validated status.
- Revocation prevents new use/publication by digest while old projects/results remain auditable.

## Acceptance tests

1. Acceptance resolves every result/checkpoint/evidence artifact to the complete principle/model/input/engine/adapter/isolation/license chain with no orphan.
2. Failure removes or mutates each required field/edge and tests cycle, unknown rights, revoked artifact, conflicting digest, and false distribution implication.
3. Evidence compares manifest, SBOM, NOTICE, dependency matrix, runtime artifact, and release records and reports every mismatch.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Provenance closure is complete, immutable, deterministic, and bidirectional.
- [ ] Execution, hosting, redistribution, and release dispositions remain distinct.
- [ ] Failure/revocation evidence and synchronized records pass.
