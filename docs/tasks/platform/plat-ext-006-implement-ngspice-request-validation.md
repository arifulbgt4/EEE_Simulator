# PLAT-EXT-006 - Implement ngspice request validation

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-017, REQ-024, REQ-032, REQ-042, REQ-056 |
| Concern | `implement_ngspice_request_validation` |
| Effort | S |
| Depends on | PLAT-EXT-005 |
| Blocks | PLAT-EXT-007 |

## Objective

Validate one normalized request and ngspice-private input against negotiated capability, trust, policy, units, limits, and build compatibility without preparing a workspace or executing ngspice.

## Context to read

- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [Simulation Engine](../../architecture/SIMULATION_ENGINE.md)
- [Security, Privacy, and Sandboxing](../../architecture/SECURITY_PRIVACY_AND_SANDBOXING.md)
- [Model Import and Export Formats](../../catalog/MODEL_IMPORT_EXPORT_FORMATS.md)
- [ADR-0008](../../decisions/ADR-0008.md)

## Exact prerequisites

- `PLAT-EXT-005` approved build/control-boundary evidence.

## Public contracts

- `NgspiceValidationRequestV1`, `NgspiceValidationDecision`, `ValidationDiagnostic`, and `ValidatedInputDigest`.

## Inputs

- Immutable normalized request/private-input manifest; capability/build/policy/model/license/trust digests; dimensions; analysis settings; limits; prohibited directives/includes/functions; and expected artifact closure.

## Allowed files

- `docs/tasks/platform/plat-ext-006-implement-ngspice-request-validation.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/SIMULATION_ENGINE.md`
- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`
- `docs/catalog/MODEL_IMPORT_EXPORT_FORMATS.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while `Planned`; exact implementation and test paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-006-ACCEPTANCE`, `TEST-PLAT-EXT-006-FAILURE`, fixture `EXT-NGSPICE-VALIDATION-V1`.

## Deliverables

- Pure validation decision with exact accepted input digest, build/capability/policy identity, warnings, blocking diagnostics, and expiry/invalidation rule.
- Complete rejection matrix for unsupported analysis/model/directive, unsafe include/path, mutable reference, unknown dimension/license/trust, resource estimate overflow, stale digest, and incompatible build.

## Documentation updates

Synchronize this card, epic, validation contract, indexes, test/RTM/risk records, and R3 checklist after evidence.

## Allowed scope

Pre-execution ngspice validation only.

## Forbidden scope

No directory/file creation, library load, prepare/run/callback, auto-rewrite, implicit include retrieval, or acceptance based on filename extension.

## Required behavior and edge cases

- Validation is deterministic and side-effect free for identical digests.
- Unknown required field, model, directive, dimension, executable capability, license, or trust state fails closed.
- Warnings cannot waive a blocking policy and every accepted warning is content-addressed in the decision.
- Validation cannot guarantee numerical convergence; it reports syntactic/policy/capability acceptance only.

## Acceptance tests

1. Acceptance covers minimal DC/transient/AC requests and exact supported boundaries without touching filesystem or engine.
2. Failure covers malicious paths/includes, oversized input, stale/mutable references, digest/build/policy mismatch, unsafe directive, non-finite settings, and unsupported capability.
3. Evidence records zero preparation/execution side effects plus exact decision/diagnostic digests.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Every validation rule and limit has nominal/boundary/failure evidence.
- [ ] Validation is pure, deterministic, and fail-closed.
- [ ] Traceability and R3 records are synchronized.
- [ ] No preparation or execution scope was added.
