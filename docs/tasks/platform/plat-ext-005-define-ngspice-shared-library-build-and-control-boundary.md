# PLAT-EXT-005 - Define ngspice shared-library build and control boundary

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-024, REQ-032, REQ-035, REQ-042, REQ-056 |
| Concern | `define_ngspice_shared_library_build_and_control_boundary` |
| Effort | S |
| Depends on | PLAT-EXT-004; PLAT-GOV-005; PLAT-GOV-008 |
| Blocks | PLAT-EXT-006 |

## Objective

Pin and document the exact ngspice build, shared-library control surface, callback ownership, concurrency policy, artifact boundary, and legal disposition used by the R3 reference adapter.

## Context to read

- [ADR-0008](../../decisions/ADR-0008.md)
- [Open Source and Third-Party Licenses](../../architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md)
- [Security, Privacy, and Sandboxing](../../architecture/SECURITY_PRIVACY_AND_SANDBOXING.md)
- [Dependency and License Matrix](../../planning/DEPENDENCY_AND_LICENSE_MATRIX.md)
- [Official ngspice shared-library documentation](https://ngspice.sourceforge.io/shared.html)

## Exact prerequisites

- `PLAT-EXT-004`, `PLAT-GOV-005`, and `PLAT-GOV-008` completion evidence.

## Public contracts

- `NgspiceBuildManifestV1`, `NgspiceSharedLibraryBoundary`, `NgspiceCallbackMap`, `AdapterConcurrencyPolicy`, `DistributionDisposition`, and planned registry record `mdl-external-adapter-ngspice@1.0.0`.

## Inputs

- Planned registry seed `mdl-external-adapter-ngspice@1.0.0`, exact upstream release/source commit, source archive digest, build recipe/toolchain/options, produced artifact digests, callbacks/symbols actually used, bundled code models/resources, license files, notices, platform ABI, and security review.
- Claims must be verified against the pinned upstream source/manual and built artifact. `Source PDF` citations and an unpinned website alone are insufficient.

## Allowed files

- `docs/tasks/platform/plat-ext-005-define-ngspice-shared-library-build-and-control-boundary.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`
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

- `TEST-PLAT-EXT-005-ACCEPTANCE`, `TEST-PLAT-EXT-005-FAILURE`, fixture `EXT-NGSPICE-BUILD-BOUNDARY-V1`.

## Deliverables

- Reproducible build/artifact manifest, ABI/symbol/callback inventory, ownership/thread/concurrency/reentrancy decision, load/unload policy, crash boundary, supported platform matrix, and replacement/export path.
- A synchronized immutable revision of `mdl-external-adapter-ngspice` whose capability, provenance, license, isolation, limitation, and evidence fields match the pinned adapter artifact; the planning seed itself is not execution evidence.
- Separate execution and distribution decisions. A successful build does not authorize bundling or linking into the Apache-2.0 core.
- Stable diagnostics for digest, ABI, symbol, license, notice, artifact, callback, and policy mismatch.

## Documentation updates

Synchronize this card, epic, license/dependency records, NOTICE when applicable, indexes, tests, RTM, risk, and R3 checklist.

## Allowed scope

The pinned ngspice shared-library artifact and its adapter/process boundary only.

## Forbidden scope

No ngspice execution, model import, numerical validation, Xyce/HPC, dynamic download, unreviewed bundled library, or license conclusion based only on process isolation.

## Required behavior and edge cases

- Runtime rejects an unpinned, substituted, ABI-incompatible, unexpectedly bundled, or digest-mismatched artifact before loading.
- Callback threading/ownership and concurrent-instance behavior are recorded from verified pinned evidence; unresolved behavior forces serialization or blocks release.
- Core and distribution manifests can omit the adapter without breaking canonical project/result contracts.
- Revoked or disputed artifacts are quarantined by digest without rewriting prior result provenance.

## Acceptance tests

1. Acceptance reconstructs the manifest from the pinned artifact and matches every digest, symbol, option, callback, license, notice, and platform field.
2. Failure evidence rejects altered binaries, missing callbacks/licenses/notices, ABI mismatch, unsupported concurrency, and unauthorized core bundling.
3. Evidence includes upstream source/manual identity, build log digest, SBOM fragment, scan/review disposition, and explicit execution/distribution decisions.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Exact build, control, isolation, and legal facts are evidence-backed.
- [ ] Unknown facts block rather than become defaults.
- [ ] Records and R3 evidence are synchronized.
- [ ] No engine run or distribution was performed by this documentation task.
