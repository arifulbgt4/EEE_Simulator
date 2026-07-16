# PLAT-HPC-002 - Define Xyce isolated adapter and license boundary

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-HPC-001](../epics/epic-hpc-001.md) |
| Release | R11 |
| Requirements | REQ-024, REQ-030, REQ-032, REQ-035, REQ-042, REQ-056, REQ-063 |
| Concern | `xyce_isolated_adapter_and_license_boundary` |
| Effort | S |
| Depends on | PLAT-HPC-001; PLAT-SEC-015; PLAT-IMP-012 |
| Blocks | PLAT-HPC-003, PLAT-HPC-011 |

## Objective

Define one versioned Xyce-class `EngineAdapter` contract that can execute only in a separately built and operated isolated worker, declares its exact supported capability subset, and fails closed when sandbox, input, provenance, license, or redistribution evidence is absent.

## Context to read

- [Simulation Engine](../../architecture/SIMULATION_ENGINE.md), external-engine adapter boundary
- [Local, Cloud, and Worker Architecture](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md), cloud worker lifecycle
- [Security, Privacy, and Sandboxing](../../architecture/SECURITY_PRIVACY_AND_SANDBOXING.md), untrusted compute profiles
- [Open Source and Third-Party Licenses](../../architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md), external engines
- [Dependency and License Matrix](../../planning/DEPENDENCY_AND_LICENSE_MATRIX.md), Xyce row

## Exact prerequisites

- Accepted `G11EntryDecision` from `PLAT-HPC-001`.
- Completed `PLAT-SEC-015` sandbox/adversarial corpus evidence and `PLAT-IMP-012` SPICE unsupported-syntax/security evidence.
- Current, explicit legal review of the exact engine version, source/build origin, image contents, interaction method, deployment mode, distribution mode, and jurisdiction. A repository statement or upstream license label alone is not legal approval.

## Public contracts

- `XyceAdapterCapability`
- `ExternalEngineIdentity`
- `ExternalEngineLicenseDecision`
- `XyceExecutionBundle`
- `XyceAdapterEvent`
- `XyceAdapterResultManifest`

The adapter lifecycle is `discoverCapabilities -> validate -> prepare -> run -> stream -> pause? -> checkpoint? -> resume? -> cancel -> dispose`. `pause`, `checkpoint`, and `resume` are advertised only when the pinned engine/version/profile and compatibility evidence support them; unsupported lifecycle calls return a stable diagnostic.

## Exact inputs and reference basis

- Immutable resolved model/netlist bundle; analysis request; engine binary and container-image digests; adapter/schema versions; capability subset; resource and network policy; allowed file manifest; environment variables allowlist; locale/timezone; seed; execution timebase; requested output set; license decision; and expected diagnostics.
- Valid fixtures: minimal DC and transient cases using only the declared supported syntax. Boundary fixtures: maximum accepted input/output size, allowed analysis option limit, cancellation at startup and output flush, and zero-result run.
- Failure fixtures: path traversal/include escape, unsupported directive, shell/metacommand injection, outbound-network attempt, root-filesystem write, process fan-out, resource overrun, malformed output, unexpected exit, stale lease, corrupt image/input hash, and license denial.
- Primary source candidates are the exact versioned official Xyce documentation and licensing material referenced by the dependency matrix. The task must archive locators/version/date/hash where redistribution permits. The Source PDF is not technical evidence.
- This concern introduces no solver equation. It preserves engine output and reports the pinned engine's declared numerical method/limits without reinterpreting or silently normalizing unsupported behavior.

## Allowed files

- `docs/tasks/platform/plat-hpc-002-define-xyce-isolated-adapter-and-license-boundary.md`
- `docs/tasks/epics/epic-hpc-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/SIMULATION_ENGINE.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`
- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`
- `docs/catalog/MODEL_IMPORT_EXPORT_FORMATS.md`
- `docs/planning/DEPENDENCY_AND_LICENSE_MATRIX.md`
- `docs/planning/RISK_REGISTER.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`

No engine binary/image, build script, runtime adapter, source, deployment configuration, or external distribution is authorized while `Planned`.

## Expected outputs and known limitations

- Versioned schemas/examples for every public contract, an exact capability matrix, adapter/engine compatibility matrix, sandbox profile, legal-decision record, diagnostics catalog, and reproducible evidence manifest.
- A human-readable, non-color-only unsupported/error summary. Support is limited to the exact pinned engine/version/profile and declared syntax/analysis subset; no general SPICE or physical-accuracy claim follows.

## Required behavior and diagnostics

- `PLAT_HPC_002_NOMINAL`: validate and prepare a supported immutable bundle, emit ordered canonical events, and publish exactly one checksummed result manifest bound to current lease/fence and engine/image/adapter revisions.
- `PLAT_HPC_002_BOUNDARY`: documented parser, resource, output, cancellation, and supported-option limits are enforced at exact inclusive/exclusive edges.
- `PLAT_HPC_002_CAPABILITY_UNSUPPORTED`: reject an analysis, directive, model, lifecycle action, MPI mode, or output type not declared by the exact capability revision.
- `PLAT_HPC_002_INPUT_UNSAFE`: reject traversal, executable injection, escaped include, malformed encoding, unbounded expansion, or dependency outside the immutable bundle before launch.
- `PLAT_HPC_002_SANDBOX_VIOLATION`: terminate network, filesystem, privilege, process, syscall/capability, or quota violations; retain bounded forensic metadata without publishing success.
- `PLAT_HPC_002_LICENSE_BLOCKED`: do not build, run, bundle, download, or redistribute when the exact use/distribution action lacks an accepted decision.
- `PLAT_HPC_002_OUTPUT_INVALID`: reject corrupt, truncated, schema-incompatible, non-finite-without-diagnostic, oversized, or unexpected engine output.
- `PLAT_HPC_002_STALE_FENCE`: a stale attempt may upload only temporary quarantined artifacts and can never publish authoritative completion.

## Acceptance tests and evidence

1. `TEST-PLAT-HPC-002-ACCEPTANCE` proves capability discovery, supported-input validation, isolated lifecycle, ordered events, cancellation, cleanup, result publication, and exact engine/image/adapter/model provenance.
2. `TEST-PLAT-HPC-002-FAILURE` exercises every diagnostic above plus worker kill and duplicate delivery; the Apache core remains a separate process/artifact and no denied redistribution occurs.
3. Differential evidence compares only within an explicitly declared input/analysis/tolerance envelope; it never turns engine agreement into physical-validation evidence.
4. Evidence contains the legal decision ID/scope/expiry, SBOM and image digest, official-source locator/version/hash, sandbox profile, syscall/network/filesystem observations, resource usage, input/output hashes, event sequence, and limitations.

## Documentation updates on completion

- Synchronize this card/epic, indexes, dependency/license matrix, architecture, import policy, test registry, RTM, risk register, and G11 checklist.
- Record supported and unsupported syntax/analyses, checkpoint/cancel capability, adapter-to-engine compatibility matrix, replacement/export path, and legal review trigger.

## Forbidden scope

- No in-process linking, shared-library embedding, browser execution, implicit download, runtime package installation, network model retrieval, shell execution, or redistribution by assumption.
- Do not modify Xyce, claim full SPICE compatibility, claim physical accuracy from differential agreement, or silently translate unsupported input.
- Do not use Source PDF citations as engine capability, license, security, or accuracy proof.

## Definition of Done

- [ ] Contracts specify exact version, capability, lifecycle, input/output, event, diagnostic, sandbox, license, and provenance behavior.
- [ ] Nominal, boundary, malicious input, sandbox escape, resource, cancellation, stale lease, corrupt output, and legal denial evidence passes.
- [ ] The process/artifact boundary from the Apache core is independently demonstrated.
- [ ] Central records and G11 evidence are synchronized before status advances.
- [ ] No external engine distribution or runtime implementation was performed by this documentation task.
