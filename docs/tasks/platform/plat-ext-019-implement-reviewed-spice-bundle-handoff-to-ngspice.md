# PLAT-EXT-019 - Implement reviewed SPICE bundle handoff to ngspice

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R7 |
| Requirements | REQ-024, REQ-032, REQ-042, REQ-049, REQ-053, REQ-056, REQ-063 |
| Concern | `implement_reviewed_spice_bundle_handoff_to_ngspice` |
| Effort | S |
| Depends on | Gate G6 Electronics MVP; PLAT-EXT-018; PLAT-DATA-007; PLAT-LIB-014; PLAT-IMP-001; PLAT-IMP-002; PLAT-IMP-011; PLAT-IMP-012 |
| Blocks | PLAT-EXT-020 |

## Objective

Resolve one authorized, immutable, fully closed imported SPICE model bundle into the normalized ngspice adapter input without network lookup, mutable aliases, or unreviewed executable content.

## Context to read

- [Model Import and Export Formats](../../catalog/MODEL_IMPORT_EXPORT_FORMATS.md)
- [Hierarchical Model and Library Architecture](../../architecture/HIERARCHICAL_MODEL_AND_LIBRARY_ARCHITECTURE.md)
- [Data-Driven Library and Storage Architecture](../../architecture/DATA_DRIVEN_LIBRARY_AND_STORAGE_ARCHITECTURE.md)
- [Security, Privacy, and Sandboxing](../../architecture/SECURITY_PRIVACY_AND_SANDBOXING.md)
- [Open Source and Third-Party Licenses](../../architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md)

## Exact prerequisites

- Gate G6 and `PLAT-EXT-018`, `PLAT-DATA-007`, `PLAT-LIB-014`, `PLAT-IMP-001`, `PLAT-IMP-002`, `PLAT-IMP-011`, `PLAT-IMP-012` Done.

## Public contracts

- `ReviewedSpiceBundleV1`, `SpiceDependencyClosure`, `ImportedModelExecutionDecision`, `SpiceToNgspiceHandoffManifest`, and `HandoffDiagnostic`.

## Inputs

- Exact source bytes/digests, supported syntax/version, include/subcircuit dependency DAG, logical/pin/parameter/unit maps, generic/vendor lineage, provenance, trust, license/redistribution, quarantine state, validation status, executable classification, adapter/build capability, and resource estimate.

## Allowed files

- `docs/tasks/platform/plat-ext-019-implement-reviewed-spice-bundle-handoff-to-ngspice.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/catalog/MODEL_IMPORT_EXPORT_FORMATS.md`
- `docs/architecture/HIERARCHICAL_MODEL_AND_LIBRARY_ARCHITECTURE.md`
- `docs/architecture/DATA_DRIVEN_LIBRARY_AND_STORAGE_ARCHITECTURE.md`
- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`
- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No central storage schema or direct engine-to-database access is authorized. Exact bundle, handoff fixture, implementation, test, and evidence paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-019-ACCEPTANCE`, `TEST-PLAT-EXT-019-FAILURE`, fixture `EXT-R7-SPICE-HANDOFF-V1`.

## Deliverables

- Deterministic closure resolution and handoff manifest enumerating every member, include edge, subcircuit, model/parameter/pin map, transformation, trust/license decision, source/target digest, adapter capability, and limit.
- A frozen `R7-EXT-MACRO-SUITE-V1` case manifest consumed by `PLAT-EXT-020`; it must enumerate exact model revision and case IDs before this task is Done.
- Stable diagnostics for cycle, missing/remote include, traversal, ambiguous symbol/pin/parameter, unsupported syntax/extension, unknown units/rights/trust, revocation, digest mismatch, and resource overflow.

## Documentation updates

Synchronize task/epic, import/library/security/license records, indexes, tests, RTM, risks, and R7 checklist.

## Allowed scope

Handoff of one reviewed imported SPICE closure to the existing ngspice adapter.

## Forbidden scope

No arbitrary vendor SKU claim, network include, shell/native plugin, model rewrite without recorded transform, direct engine-to-database/storage dependency, Xyce/HPC, or execution of quarantined/unknown-rights content.

## Required behavior and edge cases

- Same immutable closure and adapter policy produce byte-identical handoff/manifests.
- All includes are content-addressed, acyclic, inside the authorized closure, and validated before preparation.
- Vendor overrides remain bounded by generic-device inheritance and exact package/pin binding; ordering code alone grants no capability or validity.
- Execution, publication, and redistribution decisions remain separate and revocation blocks new handoffs by digest.

## Acceptance tests

1. Acceptance proves complete deterministic closure, exact mapping, policy decisions, no runtime lookup, and successful handoff to pre-execution validation.
2. Failure covers every syntax/include/DAG/map/unit/trust/license/revocation/quota/digest case and proves no workspace or execution occurs.
3. Evidence records source/closure/handoff/adapter/policy digests, transformations, provenance, limitations, and the exact R7 macro-suite manifest.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Closure and handoff are immutable, complete, deterministic, and policy-approved.
- [ ] R7 suite case/model IDs are exactly enumerated.
- [ ] Failure/quarantine/revocation evidence and synchronized records pass.
- [ ] No Xyce/HPC or direct storage coupling was added.
