# PLAT-EXT-015 - Enforce adapter isolation and resource supervision

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-029, REQ-032, REQ-033, REQ-035, REQ-056 |
| Concern | `enforce_adapter_isolation_and_resource_supervision` |
| Effort | S |
| Depends on | PLAT-EXT-014; PLAT-SEC-005; PLAT-SEC-006; PLAT-SEC-007 |
| Blocks | PLAT-EXT-016 |

## Objective

Prove that every ngspice adapter lifecycle path runs within the accepted process/container boundary and enforces the declared network, filesystem, privilege, CPU, memory, process, time, scratch, and output policies.

## Context to read

- [Security, Privacy, and Sandboxing](../../architecture/SECURITY_PRIVACY_AND_SANDBOXING.md)
- [Local, Cloud, and Worker Architecture](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md)
- [ADR-0008](../../decisions/ADR-0008.md)
- [Open Source and Third-Party Licenses](../../architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- `PLAT-EXT-014`, `PLAT-SEC-005`, `PLAT-SEC-006`, and `PLAT-SEC-007` Done with exact policy/limit digests.

## Public contracts

- `ExternalAdapterSandboxProfileV1`, `ResourceBudget`, `SupervisorEvent`, `IsolationEvidence`, and `ResourceTerminationDiagnostic`.

## Inputs

- Pinned adapter/engine artifact, full lifecycle fixtures, no-network policy, read-only runtime image, writable scratch mount, identity/capabilities/seccomp-or-equivalent policy, exact CPU/memory/process/time/output limits, cancellation deadline, and audit controls.

## Allowed files

- `docs/tasks/platform/plat-ext-015-enforce-adapter-isolation-and-resource-supervision.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while `Planned`; exact implementation, infrastructure-fixture, and test paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-015-ACCEPTANCE`, `TEST-PLAT-EXT-015-FAILURE`, fixture `EXT-ISOLATION-RESOURCE-V1`.

## Deliverables

- Versioned sandbox profile and supervisor rules applied to validate/prepare/run/stream/pause/checkpoint/resume/cancel/dispose as applicable.
- Evidence for outbound-network denial, read-only runtime, bounded scratch, least privilege, process-tree containment, every resource ceiling, output backpressure, timeout/cancel escalation, secret/host-path redaction, and post-run cleanup.
- Stable diagnostics naming the exceeded policy, configured/observed value, terminal state, last accepted tick, and retained/quarantined artifacts.

## Documentation updates

Synchronize task/epic, security/worker/license contracts, indexes, tests, RTM, risk, and R3 checklist.

## Allowed scope

Isolation and resource supervision of the ngspice adapter lifecycle.

## Forbidden scope

No network exception, writable runtime image, privileged execution, host filesystem access, unbounded child/output, Xyce/HPC worker, license conclusion, or numerical accuracy claim.

## Required behavior and edge cases

- Each limit is tested below, at, and above its exact boundary; exceeding it gives one bounded terminal result and cannot affect another attempt.
- Network/filesystem/privilege escape attempts fail closed and produce redacted audit evidence.
- Worker/supervisor crash, fork/child escape, output flood, memory pressure, CPU/time exhaustion, and cancellation escalation leave no orphan and no authoritative complete result.
- Isolation policy digest is included in every attempt/result provenance record.

## Acceptance tests

1. Acceptance runs every applicable lifecycle path within the exact profile and proves enforcement telemetry, tenant/attempt isolation, and cleanup.
2. Failure exercises every escape and resource boundary plus supervisor/worker loss, proving containment, correct diagnostic, terminal state, and absence of orphan/cross-attempt effect.
3. Evidence includes immutable image/artifact/policy/config digests, observed maxima, process/mount/network state, terminal event order, and reviewer disposition.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Every isolation control and resource limit has current boundary/failure evidence.
- [ ] All escape/exhaustion cases are contained with no false success or orphan.
- [ ] Traceability, risks, and R3 checklist are synchronized.
- [ ] Xyce/HPC work remains outside scope.
