# PLAT-EXT-002 - Implement capability discovery and operation negotiation

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-017, REQ-024, REQ-029, REQ-032, REQ-042 |
| Concern | `implement_capability_discovery_and_operation_negotiation` |
| Effort | S |
| Depends on | PLAT-EXT-001 |
| Blocks | PLAT-EXT-003 |

## Objective

Resolve a requested analog execution into an immutable supported, unsupported, or conditional capability decision before validation or engine execution.

## Context to read

- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [Simulation Engine](../../architecture/SIMULATION_ENGINE.md)
- [Multi-Fidelity and Co-Simulation](../../architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md)
- [ADR-0008](../../decisions/ADR-0008.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- `PLAT-EXT-001` Done with `EngineAdapterLifecycleV1` and its evidence digest.

## Public contracts

- `EngineCapabilityManifestV1`, `AnalysisCapability`, `ModelKindCapability`, `OperationSupport`, `ResourceCapability`, `DeterminismCapability`, and `CapabilityDecision`.

## Inputs

- Adapter/build digest; platform/ABI identity; requested analysis, fidelity, model kinds, lifecycle operations, checkpoint mode, determinism class, resource profile, and output formats.
- Capability values must come from the pinned implementation/build and verified upstream behavior; `Source PDF` citations cannot assert support.
- Prerequisite lifecycle version and immutable request capability digest.

## Allowed files

- `docs/tasks/platform/plat-ext-002-implement-capability-discovery-and-operation-negotiation.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No source/test implementation path is authorized until promotion to `Ready` appends exact paths from `PLAT-GOV-001`.

## Reference data and test IDs

- `TEST-PLAT-EXT-002-ACCEPTANCE`
- `TEST-PLAT-EXT-002-FAILURE`
- Fixture `EXT-CAPABILITY-NEGOTIATION-V1` with supported, unsupported, conditional, stale, and contradictory manifests.

## Deliverables

- A canonical manifest with version, adapter/engine/build digests, analyses, model kinds, fidelity, lifecycle operations, platform constraints, numeric/determinism declaration, limits, and expiry/revalidation rule.
- A pure negotiation result naming every accepted capability, rejected capability, required condition, and stable diagnostic.
- Cache identity and invalidation rules that prevent reuse across different build, policy, platform, or capability digests.

## Documentation updates

Update this card, epic, API capability contract, indexes, test registry, RTM, risk record, and R3 checklist after evidence exists.

## Allowed scope

Capability discovery and negotiation only; no validation of a concrete netlist and no engine startup.

## Forbidden scope

- No prepare/run/stream behavior, engine auto-install, silent downgrade, implicit fidelity substitution, Xyce/HPC, or mutable capability alias.
- No capability inferred solely from a version label, PDF statement, UI flag, or file extension.

## Required behavior and edge cases

- Same manifest/request/policy digests produce the same ordered decision.
- Unknown required capability, contradictory bounds, expired manifest, missing build digest, or unsupported operation fails before execution.
- Conditional support lists exact preconditions; unmet conditions are rejection, not best-effort execution.
- Numeric determinism and checkpoint compatibility are explicit values, never implied by engine name.
- Capability reduction after restart invalidates preparation; an additive optional capability does not reinterpret an accepted request.

## Acceptance tests

1. `TEST-PLAT-EXT-002-ACCEPTANCE` proves exact negotiation for every fixture and reproducible decision serialization.
2. `TEST-PLAT-EXT-002-FAILURE` proves fail-closed handling of stale, unsigned/untrusted, contradictory, incomplete, and incompatible manifests without engine execution.
3. Evidence records adapter/build/policy/platform digests, requested and resolved capabilities, conditions, diagnostics, and lifecycle version.
4. Traceability links every declared capability to pinned implementation or upstream evidence and marks unresolved claims unsupported.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Manifest and decision schemas are versioned and complete.
- [ ] No unsupported capability is silently accepted or downgraded.
- [ ] Acceptance/failure evidence and synchronized records pass.
- [ ] Task remains one concern and adds no engine execution.
