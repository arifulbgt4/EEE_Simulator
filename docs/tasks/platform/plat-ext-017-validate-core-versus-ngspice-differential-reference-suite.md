# PLAT-EXT-017 - Validate core versus ngspice differential reference suite

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-EXT-001](../epics/epic-ext-001.md) |
| Release | R3 |
| Requirements | REQ-008, REQ-009, REQ-010, REQ-011, REQ-014, REQ-017, REQ-024, REQ-043 |
| Concern | `validate_core_versus_ngspice_differential_reference_suite` |
| Effort | S |
| Depends on | PLAT-EXT-016; PLAT-QA-003; PLAT-NON-012; PLAT-ANL-002; CMP-SEMICONDUCTORS-DIODE-SHARED-F3-VALIDATION; CMP-SEMICONDUCTORS-LED-SHARED-F4-VALIDATION; CMP-PASSIVES-RESISTOR-SHARED-F4-VALIDATION; CMP-SEMICONDUCTORS-BJT-SHARED-F3-VALIDATION; CMP-SEMICONDUCTORS-MOSFET-SHARED-F4-VALIDATION; CMP-SEMICONDUCTORS-MOSFET-SHARED-F3-VALIDATION; CMP-ANALOG-MIXED-SIGNAL-OPERATIONAL-AMPLIFIER-SHARED-F3-VALIDATION; CMP-PASSIVES-RESISTOR-SHARED-F1-VALIDATION; CMP-ANALOG-MIXED-SIGNAL-COMPARATOR-SHARED-F2-VALIDATION; CMP-ANALOG-MIXED-SIGNAL-TIMING-FILTER-CONVERSION-SHARED-F2-VALIDATION |
| Blocks | PLAT-EXT-018 |

## Objective

Produce reproducible analytical and Rust/WASM-core-versus-ngspice differential evidence for the exact R3 nonlinear fixture set without changing either engine or model under test.

## Context to read

- [Golden Reference Circuits](../../quality/GOLDEN_REFERENCE_CIRCUITS.md)
- [Numerical Accuracy Targets](../../quality/NUMERICAL_ACCURACY_TARGETS.md)
- [Test and Validation Strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Source and Evidence Policy](../../SOURCE_AND_EVIDENCE_POLICY.md)
- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md)

## Exact prerequisites

- `PLAT-EXT-016`, `PLAT-QA-003`, `PLAT-NON-012`, and `PLAT-ANL-002`.
- `CMP-SEMICONDUCTORS-DIODE-SHARED-F3-VALIDATION`, `CMP-SEMICONDUCTORS-LED-SHARED-F4-VALIDATION`, `CMP-PASSIVES-RESISTOR-SHARED-F4-VALIDATION`, `CMP-SEMICONDUCTORS-BJT-SHARED-F3-VALIDATION`, `CMP-SEMICONDUCTORS-MOSFET-SHARED-F4-VALIDATION`, `CMP-SEMICONDUCTORS-MOSFET-SHARED-F3-VALIDATION`, `CMP-ANALOG-MIXED-SIGNAL-OPERATIONAL-AMPLIFIER-SHARED-F3-VALIDATION`, `CMP-PASSIVES-RESISTOR-SHARED-F1-VALIDATION`, `CMP-ANALOG-MIXED-SIGNAL-COMPARATOR-SHARED-F2-VALIDATION`, and `CMP-ANALOG-MIXED-SIGNAL-TIMING-FILTER-CONVERSION-SHARED-F2-VALIDATION`.

## Public contracts

- `DifferentialSuiteManifestV1`, `DifferentialCase`, `ReferenceResult`, `ComparisonMetric`, `ToleranceEnvelope`, `DivergenceDiagnostic`, and `DifferentialEvidenceBundle`.

## Inputs

- GRC-011 through GRC-020 exact immutable fixtures; core/ngspice/model/config/seed/environment digests; analytical references where applicable; per-case validity and tolerance; waveform alignment/feature rules; known expected failures.

## Allowed files

- `docs/tasks/platform/plat-ext-017-validate-core-versus-ngspice-differential-reference-suite.md`
- `docs/tasks/epics/epic-ext-001.md`
- `docs/quality/GOLDEN_REFERENCE_CIRCUITS.md`
- `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`
- `docs/quality/TEST_AND_VALIDATION_STRATEGY.md`
- `docs/SOURCE_AND_EVIDENCE_POLICY.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/validation/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

This card cannot modify implementations or models. Exact immutable fixture, candidate/reference result, and evidence paths from completed `PLAT-GOV-001` must be appended before `Ready`.

## Reference data and test IDs

- `TEST-PLAT-EXT-017-ACCEPTANCE`, `TEST-PLAT-EXT-017-FAILURE`; GRC-011..020 and TEST-GRC-011..020.

## Deliverables

- One suite manifest enumerating every analysis, probe, operating envelope, alignment rule, scalar/waveform metric, `atol`/`rtol`, reference hierarchy, and failure expectation.
- Candidate/reference raw canonical results, comparison report, residuals/features, convergence/diagnostic comparison, provenance closure, and explicit `differentially_verified|rejected|out_of_validity|blocked` status per case.

## Documentation updates

Synchronize card/epic, GRC/accuracy/validation records, indexes, tests, RTM, risks, and R3 checklist.

## Allowed scope

Independent differential validation of GRC-011..020 only.

## Forbidden scope

No tuning after viewing residuals, fixture/model/engine change, hidden exclusion, physical-correlation claim, universal accuracy claim, viewport-decimated validation, or PDF-derived expected value.

## Required behavior and edge cases

- Exact logic/status outcomes match; numeric comparisons use declared SI metrics within validity ranges and default/stricter targets.
- Both engines receive semantically equivalent immutable plans; translation differences are reported, not ignored.
- Non-convergence, timestep underflow, non-finite output, diagnostic mismatch, and one-engine failure are evidence, never auto-retried into a hidden pass.
- Repeated identical runs meet declared determinism/tolerance classification; reference-engine agreement is not physical validation.

## Acceptance tests

1. Acceptance executes every GRC-011..020 case and produces complete, reproducible, provenance-bound comparisons meeting declared envelopes.
2. Failure injects out-of-range, altered reference, stale digest, alignment manipulation, missing probe, tolerance edge, non-convergence, and false-pass cases; audit rejects each.
3. Evidence records raw and processed digests, exact environment, engine/model/config/seed, metrics, tolerances/rationale, expected/actual status, diagnostics, and reviewer.

## Known limitations

- This is a documentation-only `Planned` card; it proves no runtime behavior, engine installation, numerical correctness, security control, test result, or release status.
- Engine-specific facts, including any ngspice capability, callback, build, version, or model behavior, remain unsupported until the exact upstream source/build and current project evidence are pinned and reviewed under the Source and Evidence Policy.
- Completing this concern cannot authorize engine or model redistribution; a separate current license and distribution review is mandatory.

## Definition of Done

- [ ] Every GRC-011..020 case has complete passing or explicit blocking/rejection evidence.
- [ ] No engine/model was changed and no physical claim was made.
- [ ] Differential, failure, determinism, and provenance evidence passes.
- [ ] All traceability and R3 records are synchronized.
