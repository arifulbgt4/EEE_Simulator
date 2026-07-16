# EPIC-EXT-001 - External analog engine adapters

## Outcome

Deliver an engine-neutral, deterministic, isolated external-analog adapter path and an ngspice reference implementation. R3 supplies the lifecycle, normalized contracts, ngspice execution path, differential evidence, and acceptance audit needed by nonlinear analog work. R7 extends that path to reviewed imported SPICE bundles and production-catalog macro-model validation.

This epic is documentation-only while every included task remains `Planned`. It does not claim that ngspice is installed, linked, distributed, or validated.

## Requirements and release

- Requirements: `REQ-007`, `REQ-008`, `REQ-009`, `REQ-010`, `REQ-011`, `REQ-014`, `REQ-017`, `REQ-024`, `REQ-029`, `REQ-030`, `REQ-032`, `REQ-033`, `REQ-035`, `REQ-041`, `REQ-042`, `REQ-043`, `REQ-049`, `REQ-053`, `REQ-056`, `REQ-063`
- R3 milestone: `PLAT-EXT-001` through `PLAT-EXT-018`; entry is Gate G2 Linear analog.
- R7 milestone: `PLAT-EXT-019` through `PLAT-EXT-021`; entry is Gate G6 Electronics MVP plus the named import tasks.
- R3 exit evidence contributes to Gate G3 Nonlinear analog; R7 exit evidence contributes to Gate G7 Complete catalog.
- Prerequisite epics: `EPIC-GOV-001`, `EPIC-QA-001`, `EPIC-SEC-001`, `EPIC-NET-001`, and `EPIC-WASM-001`; R7 tasks also consume `EPIC-IMP-001` outputs.
- Excluded release: Xyce and large/HPC analog execution remain R11 work and are not dependencies, deliverables, or fallback behavior of this epic.
- The R3 adapter is a bounded reference/differential execution path. Hosted job dispatch, leases, quotas, SSE delivery, and production cloud-worker operations remain R10 concerns and are not reimplemented here.

## Technical authority and evidence policy

- Normative repository contracts are [ADR-0008](../../decisions/ADR-0008.md), [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md), [Simulation Engine](../../architecture/SIMULATION_ENGINE.md), [Security, Privacy, and Sandboxing](../../architecture/SECURITY_PRIVACY_AND_SANDBOXING.md), [Open Source and Third-Party Licenses](../../architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md), and the [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md).
- ngspice-specific capability or callback claims require a pinned ngspice release, immutable source/build digest, and the [official shared-library documentation](https://ngspice.sourceforge.io/shared.html) or the corresponding pinned upstream source/manual as evidence.
- `Source PDF` citations are feasibility/context citations only. They are not confirmed technical specifications, conformance evidence, license evidence, or proof that an engine operation is supported.
- Unsupported lifecycle operations are declared during capability discovery and rejected before execution. An adapter must not simulate support or silently substitute another engine.

## Included concerns

- Versioned `EngineAdapter` lifecycle and legal state transitions.
- Capability discovery, operation negotiation, and fail-closed validation.
- Deterministic canonical request, event, waveform, result, checkpoint, and diagnostic mappings.
- ngspice shared-library build/load/control boundary without linking ngspice into the Apache-2.0 public core.
- Private preparation, bounded run, ordered streaming, pause/checkpoint/resume negotiation, cancellation, and disposal.
- Process/container isolation, no-network policy, read-only runtime, bounded scratch, CPU/memory/process/time/output limits, and descendant cleanup.
- Engine, build, adapter, model, input, configuration, seed, license, isolation, and result provenance.
- Analytical and independent core-versus-ngspice differential validation with declared tolerances.
- Reviewed R7 SPICE bundle handoff and production macro-model differential evidence.
- Separate R3 and R7 acceptance audits with explicit unsupported-capability and distribution dispositions.

## Atomic tasks

| Task | Single outcome | Dependencies | Release | Status |
|---|---|---|---|---|
| [PLAT-EXT-001](../platform/plat-ext-001-define-versioned-engine-adapter-lifecycle-contract.md) | Freeze lifecycle states, commands, transitions, and terminal behavior | Gate G2; PLAT-WASM-002; PLAT-QA-003; PLAT-SEC-008 | R3 | Planned |
| [PLAT-EXT-002](../platform/plat-ext-002-implement-capability-discovery-and-operation-negotiation.md) | Negotiate supported analyses, models, lifecycle operations, limits, and determinism | PLAT-EXT-001 | R3 | Planned |
| [PLAT-EXT-003](../platform/plat-ext-003-implement-normalized-analog-request-translation.md) | Translate an immutable canonical plan into deterministic engine-private analog input | PLAT-EXT-002; PLAT-NET-009; PLAT-DATA-007 | R3 | Planned |
| [PLAT-EXT-004](../platform/plat-ext-004-implement-canonical-event-result-and-diagnostic-mapping.md) | Normalize ordered engine output without losing units, ticks, severity, or provenance | PLAT-EXT-003; PLAT-NET-010 | R3 | Planned |
| [PLAT-EXT-005](../platform/plat-ext-005-define-ngspice-shared-library-build-and-control-boundary.md) | Pin the reviewed ngspice build, callbacks, ownership, and isolation boundary | PLAT-EXT-004; PLAT-GOV-005; PLAT-GOV-008 | R3 | Planned |
| [PLAT-EXT-006](../platform/plat-ext-006-implement-ngspice-request-validation.md) | Validate normalized input and policy without preparation or execution | PLAT-EXT-005 | R3 | Planned |
| [PLAT-EXT-007](../platform/plat-ext-007-implement-ngspice-private-workspace-preparation.md) | Prepare one bounded private workspace and immutable preparation manifest | PLAT-EXT-006 | R3 | Planned |
| [PLAT-EXT-008](../platform/plat-ext-008-implement-ngspice-run-control.md) | Start and supervise one ngspice run from an accepted preparation | PLAT-EXT-007 | R3 | Planned |
| [PLAT-EXT-009](../platform/plat-ext-009-implement-ngspice-ordered-streaming.md) | Emit ordered canonical progress, diagnostics, and result chunks | PLAT-EXT-008 | R3 | Planned |
| [PLAT-EXT-010](../platform/plat-ext-010-implement-pause-safe-point-policy.md) | Pause only at a declared safe point or reject as unsupported | PLAT-EXT-009 | R3 | Planned |
| [PLAT-EXT-011](../platform/plat-ext-011-implement-checkpoint-capability-policy.md) | Publish a compatible checkpoint or reject before mutation | PLAT-EXT-010 | R3 | Planned |
| [PLAT-EXT-012](../platform/plat-ext-012-implement-resume-compatibility-policy.md) | Resume only from an exact compatible checkpoint | PLAT-EXT-011 | R3 | Planned |
| [PLAT-EXT-013](../platform/plat-ext-013-implement-bounded-cancellation.md) | Cancel cooperatively then terminate descendants within a bound | PLAT-EXT-012; PLAT-WASM-007 | R3 | Planned |
| [PLAT-EXT-014](../platform/plat-ext-014-implement-irreversible-disposal.md) | Dispose private state and reject all later operations | PLAT-EXT-013 | R3 | Planned |
| [PLAT-EXT-015](../platform/plat-ext-015-enforce-adapter-isolation-and-resource-supervision.md) | Enforce isolation and every declared resource limit | PLAT-EXT-014; PLAT-SEC-005; PLAT-SEC-006; PLAT-SEC-007 | R3 | Planned |
| [PLAT-EXT-016](../platform/plat-ext-016-record-engine-model-license-and-result-provenance.md) | Bind all outputs to immutable engine, model, license, isolation, and input evidence | PLAT-EXT-015; PLAT-GOV-008 | R3 | Planned |
| [PLAT-EXT-017](../platform/plat-ext-017-validate-core-versus-ngspice-differential-reference-suite.md) | Produce analytical and core-versus-ngspice differential evidence | PLAT-EXT-016; PLAT-QA-003; PLAT-NON-012; PLAT-ANL-002; CMP-SEMICONDUCTORS-DIODE-SHARED-F3-VALIDATION; CMP-SEMICONDUCTORS-LED-SHARED-F4-VALIDATION; CMP-PASSIVES-RESISTOR-SHARED-F4-VALIDATION; CMP-SEMICONDUCTORS-BJT-SHARED-F3-VALIDATION; CMP-SEMICONDUCTORS-MOSFET-SHARED-F4-VALIDATION; CMP-SEMICONDUCTORS-MOSFET-SHARED-F3-VALIDATION; CMP-ANALOG-MIXED-SIGNAL-OPERATIONAL-AMPLIFIER-SHARED-F3-VALIDATION; CMP-PASSIVES-RESISTOR-SHARED-F1-VALIDATION; CMP-ANALOG-MIXED-SIGNAL-COMPARATOR-SHARED-F2-VALIDATION; CMP-ANALOG-MIXED-SIGNAL-TIMING-FILTER-CONVERSION-SHARED-F2-VALIDATION | R3 | Planned |
| [PLAT-EXT-018](../platform/plat-ext-018-run-r3-external-analog-adapter-acceptance-audit.md) | Audit the complete R3 adapter milestone and publish a gate disposition | PLAT-EXT-001; PLAT-EXT-002; PLAT-EXT-003; PLAT-EXT-004; PLAT-EXT-005; PLAT-EXT-006; PLAT-EXT-007; PLAT-EXT-008; PLAT-EXT-009; PLAT-EXT-010; PLAT-EXT-011; PLAT-EXT-012; PLAT-EXT-013; PLAT-EXT-014; PLAT-EXT-015; PLAT-EXT-016; PLAT-EXT-017 | R3 | Planned |
| [PLAT-EXT-019](../platform/plat-ext-019-implement-reviewed-spice-bundle-handoff-to-ngspice.md) | Hand one reviewed, immutable imported SPICE closure to the adapter | Gate G6; PLAT-EXT-018; PLAT-DATA-007; PLAT-LIB-014; PLAT-IMP-001; PLAT-IMP-002; PLAT-IMP-011; PLAT-IMP-012 | R7 | Planned |
| [PLAT-EXT-020](../platform/plat-ext-020-validate-r7-imported-macro-model-differential-suite.md) | Validate declared R7 imported F3 macro-model envelopes and failures | PLAT-EXT-019 | R7 | Planned |
| [PLAT-EXT-021](../platform/plat-ext-021-run-r7-external-analog-adapter-acceptance-audit.md) | Audit imported-model, security, license, provenance, and differential evidence | PLAT-EXT-018; PLAT-EXT-019; PLAT-EXT-020 | R7 | Planned |

## Milestone exit criteria

### R3

- [ ] `PLAT-EXT-001` through `PLAT-EXT-018` are Done with bidirectional requirement/task/test/gate evidence.
- [ ] Every lifecycle command has a legal-state matrix, idempotency rule, timeout, diagnostic, and unsupported-operation behavior.
- [ ] The ngspice build and adapter are immutable, isolated, resource-bounded, provenance-bound, and absent from Apache-core artifacts unless a later approved distribution decision explicitly permits inclusion.
- [ ] Analytical and core-versus-ngspice cases meet their declared per-fixture envelopes; divergence and non-convergence cannot be converted into a pass.
- [ ] Xyce/HPC work is still absent and no silent engine fallback exists.

### R7

- [ ] `PLAT-EXT-019` through `PLAT-EXT-021` are Done after the R3 milestone and named import prerequisites.
- [ ] Imported SPICE closure, include resolution, pin mapping, trust, license, redistribution, executable classification, and immutable digest are validated before preparation.
- [ ] R7 macro-model evidence reports the exact supported subset, operating envelope, numerical tolerance, limitations, and unresolved or quarantined models.
- [ ] The final audit proves no PDF citation was used as technical conformance evidence and records a release/distribution decision separately from execution success.
