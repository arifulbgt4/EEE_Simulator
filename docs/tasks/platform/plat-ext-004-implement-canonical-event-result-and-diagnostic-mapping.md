# PLAT-EXT-004 - Implement canonical event, result, and diagnostic mapping

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-007, REQ-017, REQ-024, REQ-029, REQ-043, REQ-053 |
| Concern | `implement_canonical_event_result_and_diagnostic_mapping` |
| Effort | S |
| Depends on | PLAT-EXT-003; PLAT-NET-010 |
| Blocks | PLAT-EXT-005 |

## Objective

Map untrusted external-engine progress, diagnostics, vectors, and terminal state into ordered canonical `SimulationEvent`, `WaveformChunk`, `Diagnostic`, and `SimulationResult` records.

## Context to read

- [API and Worker Protocols, sections 5-6 and 10](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [Simulation Engine](../../architecture/SIMULATION_ENGINE.md)
- [Numerical Accuracy Targets](../../quality/NUMERICAL_ACCURACY_TARGETS.md)
- [Test and Validation Strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- `PLAT-EXT-003` private-input manifest and ID map.
- `PLAT-NET-010` result-probe mapping evidence.

## Public contracts

- `ExternalOutputMappingV1`, `SimulationEvent`, `WaveformChunk`, `Diagnostic`, `Checkpoint`, `SimulationResult`, `MappingProvenance`, and `PartialResultDisposition`.

## Inputs

- Bounded raw callback/output records, private-to-canonical ID map, analysis/timebase configuration, unit/dimension declarations, adapter/engine/build identity, and lifecycle correlation.
- Exact tick conversion/rounding, chunk ordering, gap/duplicate policy, diagnostic severity mapping, output limits, and partial-result rules.

## Allowed files

- `docs/tasks/platform/plat-ext-004-implement-canonical-event-result-and-diagnostic-mapping.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/SIMULATION_ENGINE.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No implementation/test path is authorized until promotion to `Ready` appends exact paths from `PLAT-GOV-001`.

## Reference data and test IDs

- `TEST-PLAT-EXT-004-ACCEPTANCE`
- `TEST-PLAT-EXT-004-FAILURE`
- Fixture `EXT-OUTPUT-MAPPING-V1` with ordered, duplicate, gap, non-finite, oversized, partial, cancelled, crashed, and non-converged streams.

## Deliverables

- A mapping table for progress, engine messages, analysis vectors, complex values, operating-point values, accepted ticks, non-finite values, gaps, and terminal reasons.
- Sequence/idempotency, chunking/backpressure, checksum, exact unit/dimension, precision, tick-conversion, source-data qualification, and provenance rules.
- A bounded redaction policy: raw stderr is evidence only and cannot expose host paths, secrets, cross-tenant data, or become an unstructured public protocol.

## Documentation updates

Update this card, epic, API/engine contracts, task indexes, test registry, RTM, risk record, and R3 checklist after evidence exists.

## Allowed scope

Canonicalization and validation of external output only.

## Forbidden scope

- No engine control, execution, numerical post-hoc correction, viewport-only data substitution, silent dropped diagnostics, or conversion of failure/non-convergence into success.
- No claim that external output is trusted before schema, bounds, mapping, and digest validation complete.

## Required behavior and edge cases

- Ordered input yields monotonic canonical sequences; duplicate delivery is idempotent and a conflicting duplicate fails.
- Every channel resolves to one canonical entity, quantity, SI unit, dimension, precision, and provenance path.
- Non-finite values, missing ranges, vector-length mismatch, tick overflow, chunk gaps, output overflow, and unknown terminal state produce stable diagnostics.
- Cancelled/failed/timeout results may retain validated partial chunks but remain `partial` with last accepted tick.
- Backpressure may coalesce superseded progress only; state, diagnostic, data-availability, and terminal events cannot be dropped.

## Acceptance tests

1. `TEST-PLAT-EXT-004-ACCEPTANCE` proves deterministic serialization, ID/unit/tick preservation, checksum publication, event order, and partial-result qualification.
2. `TEST-PLAT-EXT-004-FAILURE` covers malformed, conflicting, secret-bearing, oversized, non-finite, unmapped, out-of-order, and false-success output with bounded rejection/quarantine.
3. Evidence records raw fixture digest, mapping version, input manifest, expected/actual canonical digest, discarded/redacted fields, and terminal disposition.
4. Differential values are not declared accurate by this mapping task; R3 numeric acceptance remains owned by `PLAT-EXT-017`, with imported R7 macro-model acceptance owned by `PLAT-EXT-020`.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Every supported external record has a canonical mapping or explicit rejection.
- [ ] Ordering, limits, redaction, partial, and failure evidence passes.
- [ ] Public contracts and traceability records are synchronized.
- [ ] No control or numerical-validation scope was added.
