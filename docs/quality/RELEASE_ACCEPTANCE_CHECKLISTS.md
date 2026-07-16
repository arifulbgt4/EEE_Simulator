# Release Acceptance Checklists

## Universal release gate

- [ ] Scope and non-goals match the approved release gate.
- [ ] Every included requirement has an owner, task, test, and evidence link.
- [ ] Every applicable technical claim resolves to a reviewed official/primary source or approved physical/reference artifact under the [Source and Evidence Policy](../SOURCE_AND_EVIDENCE_POLICY.md), with exact version/location, applicability, license status, and conflicts recorded.
- [ ] Legacy `[Source PDF]` citations are treated only as unverified planning lineage; no equation, standard, accuracy, license, security, implementation, test, or release decision depends on them alone.
- [ ] No `Ready` or `In Progress` task is silently included as completed scope.
- [ ] Registry counts and coverage states are internally consistent.
- [ ] All released components have model, validation, provenance, limitations, and user documentation.
- [ ] Every released component satisfies its exact gate-scoped core profile; unfinished optional extensions are visibly unavailable and no gate-required capability is classified as optional.
- [ ] All normative schemas are versioned and compatibility behavior is documented.
- [ ] Published records use immutable revision IDs and content hashes; dependency/reverse-dependency resolution and lineage are complete.
- [ ] Scientific claims state validity, provenance, trust, accuracy/uncertainty, limitations, and evidence status without false precision.
- [ ] Golden, differential, integration, failure, security, performance, browser, and accessibility suites pass.
- [ ] Known limitations and deferred work are visible in release notes.
- [ ] Third-party licenses, notices, model redistribution rights, and process isolation have been reviewed.
- [ ] Rollback, migration, backup, and incident procedures are current.

## Documentation baseline gate (R0)

- [ ] The initial queue starts with `PLAT-QA-001` as the sole `Ready` R0 root task; later R0 tasks are promoted only after their exact predecessor is `Done`.
- [ ] `PLAT-GOV-001` remains `Planned` until the complete R0 evidence bundle is accepted at G0.
- [ ] Root governance and contributor documents exist.
- [ ] The project description and contributor path identify Applied Physics First and its principle-to-validation chain.
- [ ] The normative Source and Evidence Policy is linked from contributor, requirements, task, validation, and release entry points.
- [ ] Product, architecture, catalog, quality, planning, ADR, and task documents are cross-linked.
- [ ] The baseline contains exactly 162 families and 502 variants.
- [ ] The task baseline contains exactly 37 platform epics, 477 platform atomic tasks, 2,636 component/package atomic tasks, 66 validation tasks, and 3,179 atomic tasks in total.
- [ ] The scientific model registry validates and reports only the model records it actually enumerates; physics, primitive, composite, behavioral, and external-adapter kinds are distinguishable.
- [ ] All 502 variant pin profiles and all 502 variant semantic profiles resolve exactly once; unresolved model-plan references remain release-blocking.
- [ ] Parameter definitions declare dimensions/canonical SI or explicit unresolved diagnostics; no normalization invents physical values.
- [ ] Every variant has an atomic task card.
- [ ] Every production family has a family specification and applicable model/validation tasks.
- [ ] REQ-037/REQ-038 are traced to physical-appearance, package-registry, package-designer, pin-map and visual-regression tasks.
- [ ] REQ-039..063 are traced to ADR-0011..0020, architecture, epics, atomic tasks, stable tests, risks, gates, and evidence contracts.
- [ ] The roadmap contains exactly R0 through R13; R4 is named `Applied Physics and Real-World Fidelity`; the stable IDs and ordering of R5-R13 are unchanged and no R14 exists. Later-phase acceptance wording may be synchronized without renumbering those releases.
- [ ] Library Service, storage-independent engine bundle, mixed storage, immutable publication, safe CRUD, declarative/executable boundary, optional Google OIDC, guest migration, and personal persistence contracts are explicit.
- [ ] Package candidates are distinguished from concrete `DevicePackageBinding` records; no `package_refs` list is accepted as a pin map or release artifact.
- [ ] Requirement traceability has no orphan row.
- [ ] All source-brief-derived requirements preserve PDF page markers as unverified origin metadata, without representing them as confirmed technical sources.
- [ ] No executable application code or runtime configuration is introduced by the documentation-only milestone.

## Scheduled golden evidence

- [ ] G2/R2 includes GRC-001 through GRC-008.
- [ ] G3/R3 includes GRC-011 through GRC-020.
- [ ] G4/R4 includes preserved GRC-021 through GRC-026 scope plus GRC-055 through GRC-066 physical-correlation fixtures.
- [ ] G5/R5 includes GRC-027 through GRC-034.
- [ ] G7/R7 includes GRC-023 through GRC-025, GRC-036 through GRC-040, and every applicable family-specific fixture.
- [ ] G8/R8 includes GRC-035 and GRC-041 through GRC-043.

## Realistic Electronics MVP gate

- [ ] G4 Applied Physics and Real-World Fidelity has passed and no applicable real-world behavior is bypassed by G5 or this gate.
- [ ] Guest users can create, save offline, export, import, and reopen a project.
- [ ] Optional personal Google OIDC and private cloud persistence are production-hardened; guest migration is explicit/idempotent/non-destructive and guest/offline use remains fully supported.
- [ ] Exactly the 106 registry presets tagged `Realistic Electronics MVP` are evaluated for this gate; the 388 `Post-MVP catalog` presets remain visible but cannot be claimed as released.
- [ ] The early switch profile is limited to mechanical SPST, SPDT, and momentary plus voltage-controlled and ideal-controlled presets; mechanical DPST/DPDT and current-controlled presets remain R7 work even when they reuse the validated shared family core.
- [ ] Core connectivity, sources, RLC, the five basic-switch presets above, diode/LED, BJT, MOSFET, op-amp, basic gates, and instruments are released.
- [ ] Basic components have recognizable physical views, and released ICs have reusable package definitions plus published concrete `DevicePackageBinding` revisions with verified symbol/package pin equivalence.
- [ ] DC and transient analyses pass; AC, tolerance/Monte Carlo, power, temperature, leakage, and failure behavior meet the MVP scope.
- [ ] LED, RC, rectifier, transistor switch, CMOS inverter, ring oscillator, NAND, SR latch, one-bit memory, half adder, full adder, and thermal-failure demonstrations pass.
- [ ] Invalid circuits produce actionable diagnostics.
- [ ] UI remains responsive while simulations run in workers.
- [ ] Local result provenance and deterministic seeds are preserved.
- [ ] MVP performance, browser, and WCAG 2.2 AA gates pass.

## Complete catalog gate

- [ ] GRC-023 through GRC-025 and GRC-036 through GRC-040 pass with retained evidence.
- [ ] All 157 production families and 494 production variants are released or explicitly moved through an approved scope-change ADR.
- [ ] Deferred research families remain listed with rationale and entry criteria.
- [ ] SPICE, HDL, IBIS, Touchstone, waveform, stimulus, and firmware import policies are implemented and tested as scheduled.
- [ ] Vendor models retain provenance and redistribution restrictions.
- [ ] Vendor/order-code records inherit exact generic-device revisions through bounded dimensionally valid overrides and exact package/pin bindings; no duplicated internal model or unevidenced market-coverage claim is accepted.

## External analog adapter gates (R3/G3 and R7/G7)

- [ ] `PLAT-EXT-001` through `PLAT-EXT-018` are `Done` before G3 acceptance; capability discovery, validate, prepare, run, ordered stream, pause, checkpoint, resume, cancel, and dispose have explicit legal, unsupported, timeout, idempotency, safe-point, cleanup, and diagnostic behavior.
- [ ] The ngspice release/build and adapter are pinned by immutable digest; the shared-library/control claims resolve to reviewed official upstream evidence; no Source PDF citation is treated as capability, conformance, or license proof.
- [ ] The adapter uses a separate, no-network, resource-bounded, read-only-root execution boundary and records engine, build, adapter, model, input, configuration, seed, isolation, license, and result provenance.
- [ ] Analytical and core-versus-ngspice fixtures pass their declared envelopes; divergence, non-convergence, cancellation races, unsupported operations, cleanup failure, and resource exhaustion remain visible failures.
- [ ] `PLAT-EXT-019` through `PLAT-EXT-021` are `Done` before G7 acceptance; every imported SPICE closure has reviewed include resolution, pin mapping, trust, license/redistribution, executable classification, immutable digest, supported subset, operating envelope, limitations, quarantine disposition, and differential evidence.
- [ ] Passing execution never implies redistribution approval; the release/distribution disposition is retained separately.

## Applied Physics and Real-World Fidelity gate (R4/G4)

- [ ] Every included model documents physical principles, governing/engineering equations or approved algorithm, assumptions, approximation, numerical method, dependencies, fidelity, state, inputs/outputs, convergence expectations, and failure conditions.
- [ ] Every included governing equation, parameter, material property, standard, and claimed mechanism has an applicable reviewed official/primary source or accepted physical evidence record; Source PDF pages are not counted as this evidence.
- [ ] Canonical SI units, dimensions, ranges, temperature/frequency/operating validity, and invalid-input diagnostics pass.
- [ ] Provenance, license/redistribution, trust, validation state, accuracy/uncertainty envelope, limitations, deprecation, and replacement metadata are complete.
- [ ] Existing tolerance, Monte Carlo, leakage, ESR/ESL, parasitic R/C/L, noise, power-limit, electrothermal, derating, aging, failure, visualization, injection, and deterministic-seed obligations remain present.
- [ ] Environmental profiles, manufacturing variation/mismatch, aging/stress history, failure transitions, interconnection parasitics, source non-ideality, and instrument loading are modeled only at declared fidelity and validity.
- [ ] Tolerance changes are observable and seeded statistical reruns reproduce sample parameters and classifications.
- [ ] Electrical -> power -> thermal -> updated-electrical feedback is synchronized with the deterministic scheduler and covers steady/transient heat, cooling, runaway, shutdown, and failure where applicable.
- [ ] Failure states use declared thresholds, durations, accumulated stress, reversible/irreversible transitions, resulting electrical/thermal behavior, diagnostics, visualization, provenance, and evidence.
- [ ] GRC-021, GRC-022, GRC-026, and GRC-055..066 produce current retained G4 evidence. GRC-023..025 remain preserved catalog-bound specifications scheduled for R7 and are not circular G4 prerequisites. Physical fixtures include exact schematic/BOM/specimens, calibrated equipment, environment, procedure, raw data, model revisions, error calculation, uncertainty, criteria, and limitations.
- [ ] Accuracy reporting uses category-specific envelopes, does not display false precision, and distinguishes analytical, differential, estimated, and physical-correlation evidence.
- [ ] G5 and G6 dependency audits prove G4 cannot be bypassed. The release sequence remains exactly R0-R13.

## Educational computer gate

- [ ] GRC-035 and GRC-041 through GRC-043 pass with retained evidence.
- [ ] One-bit memory, register file, ALU, control unit, bus, ROM, RAM, timer, UART, input, and display blocks are validated.
- [ ] Four-bit and eight-bit reference CPUs execute their complete documented instruction sets.
- [ ] Assembler output, program loading, breakpoints, state inspection, timing, and deterministic replay pass.
- [ ] Users can switch between supported abstraction levels without changing logical behavior.

## RTL and full-computer gate

- [ ] Verilog/SystemVerilog validation, compilation, sandboxing, caching, and waveform import pass.
- [ ] RTL and event-driven reference models agree on declared boundaries.
- [ ] The educational full computer boots its documented monitor, firmware, or small operating environment.
- [ ] Checkpoint/resume preserves architectural state.

## Cloud and collaboration gate

- [ ] Authentication, authorization, project visibility, invitations, comments, version history, conflict resolution, and public-library moderation pass.
- [ ] Job submit, queue, stream, cancel, retry, checkpoint, resume, quota, and cost-accounting behavior pass.
- [ ] Worker containers have no outbound network by default, read-only base filesystems, and enforced CPU/memory/time limits.
- [ ] Tenant-isolation and object-authorization tests pass.

## Large analog and HPC gate (R11/G11)

- [ ] `PLAT-HPC-001` proves the accepted immutable G10 manifest and every named cross-epic dependency before any R11 execution task begins.
- [ ] `PLAT-HPC-002` pins the Xyce-class engine/build/image and official license/capability evidence, keeps GPL execution outside the Apache-2.0 core, and records a current distribution decision.
- [ ] `PLAT-HPC-003` and `PLAT-HPC-004` pass lease fencing, duplicate delivery, retry, cancellation, drain, rank/collective failure, scheduler-loss, and bounded resource tests without split-brain ownership or orphan descendants.
- [ ] `PLAT-HPC-005` proves Monte Carlo global sample identity and declared aggregates are invariant under pool size, batch size, retry, reassignment, and completion order for the same seed and immutable inputs.
- [ ] `PLAT-HPC-006` proves declared thermal partition convergence, boundary continuity, conservation, accuracy, and partial-failure behavior against approved references.
- [ ] `PLAT-HPC-007` proves deterministic merge order, bounded raw/derived retention, backpressure, approximation/error disclosure, and no unbounded browser, worker, or storage growth.
- [ ] `PLAT-HPC-008` accepts only compatible checkpoints and proves restart lineage across engine, model, input, numerical, partition, MPI/runtime, image, and environment revisions.
- [ ] `PLAT-HPC-009` passes tenant authorization, encryption/integrity, lifecycle, retention/legal-hold, export, deletion, regional, corruption, and retrieval evidence for large artifacts.
- [ ] `PLAT-HPC-010` reconciles admission, reservation, quota, cost estimate, usage ledger, telemetry, privacy, alerts, cancellation, capacity, and recovery evidence.
- [ ] `PLAT-HPC-011` independently audits all R11 evidence and publishes an immutable accepted `G11AcceptanceManifest` and `G11ReleaseDecision`; any mandatory open finding fails G11 closed.
- [ ] Every R11 technical claim resolves to a pinned official/primary source or approved independent/physical evidence plus current project test evidence; Source PDF context cannot satisfy this gate.

## Architecture, GPU, and research gates

- [ ] Engine adapters pin versions and reproduce reference workloads.
- [ ] Functional, timing, and architecture results are visibly distinguished.
- [ ] Full-transistor claims are not made for modern CPUs, GPUs, or full memory systems.
- [ ] Research model accuracy is bounded by a declared validation dataset and operating envelope.
- [ ] Downstream research results retain configuration, workload, model, engine, partition, MPI/runtime, checkpoint, artifact, and environment provenance and consume only an accepted G11 decision where G11 is a predecessor.
