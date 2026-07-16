# Product Requirements

## Status and conventions

This document defines the stable product requirements for the documentation baseline. The words **MUST**, **MUST NOT**, **SHOULD**, and **MAY** are normative.

- Requirement IDs `REQ-001` through `REQ-063` are permanent and must not be renumbered or reused.
- Each requirement preserves its planning-origin annotation. `[Source PDF, p. N]` refers to *Web-based Electronics and Computer Simulation Platform*, 44 pages, and is classified as unverified source-brief context rather than technical evidence.
- Architecture details are delegated to linked contracts and accepted ADRs.
- Verification links are maintained in [Requirements Traceability Matrix](quality/REQUIREMENTS_TRACEABILITY_MATRIX.md).

The normative [Source and Evidence Policy](SOURCE_AND_EVIDENCE_POLICY.md) applies to every requirement. Repository approval makes these statements product requirements, but neither `[Source PDF]` nor a user/repository architecture brief confirms an equation, standard, accuracy claim, license, security property, implementation state, test result, or release status. Before applicable technical work becomes `Ready`, its task must name verified official/primary sources or approved physical/reference artifacts. Before `Validated` or `Released`, current evidence must demonstrate the requirement inside its declared envelope.

## Vision and fidelity

### REQ-001 - Hierarchical multi-fidelity product

The platform MUST support one hierarchical project spanning component-level physics, circuit models, transistor switching, gate-level logic, RTL, microarchitecture, and functional or ISA-level simulation. It MUST NOT imply that all layers run at the same physical fidelity. [Source PDF, pp. 1-4, 13-16, 43-44]

### REQ-002 - Abstraction selection and substitution

Users MUST be able to select an appropriate model fidelity for a component or subsystem and replace a higher-level model with a more detailed model for a selected block while preserving explicit interface contracts. Fast, balanced, accurate, and research-oriented experiences MAY map to supported fidelity tiers, but the actual tier MUST remain visible. [Source PDF, pp. 16, 20-21, 27]

### REQ-003 - Audience modes and honest explanations

The product MUST provide progressive beginner, intermediate, advanced, and research experiences without changing the underlying physical meaning of results. Educational visualization MUST identify simplifications and MUST NOT portray animated current particles as literal electron speed. [Source PDF, pp. 30-31]

## Editor and project lifecycle

### REQ-004 - Visual schematic editor

The browser client MUST provide component placement, movement, rotation, pin connection, wire routing, property editing, hierarchy navigation, simulation control, and clear invalid-circuit diagnostics. [Source PDF, pp. 22-23, 32]

### REQ-005 - Hierarchy and reusable subcircuits

Projects MUST support named hierarchical blocks, reusable subcircuits, stable component identities, explicit ports, and navigation from a system block to its internal implementation. [Source PDF, pp. 2, 16, 29, 31-32, 37]

### REQ-006 - Portable, versioned project persistence

Projects MUST round-trip through the versioned `.eesim` format without losing schematic hierarchy, models, stimuli, testbenches, measurements, documentation, or assets. Supported small projects MUST be editable and simulatable offline, and the format MUST have deterministic migration and a Git-friendly unpacked representation. [Source PDF, pp. 25-26, 31-32]

### REQ-007 - Measurement and visualization

Users MUST be able to probe voltage, current, power, temperature, logic state, and supported timing or architecture state; view waveforms and timing diagrams; and receive non-color-only overlays or summaries for voltage, current direction, heat, failure, and digital state. [Source PDF, pp. 2, 30-31, 37]

## Analog simulation and analyses

### REQ-008 - Netlist and numerical circuit foundation

The simulation core MUST derive a deterministic electrical netlist, identify nodes and branches, construct a sparse Modified Nodal Analysis system, support nonlinear device iteration, and report convergence diagnostics. [Source PDF, pp. 9-10, 29, 39]

### REQ-009 - DC operating point

The platform MUST compute DC node voltages, branch currents, and component power for supported models, including clear errors for floating nodes, shorts, singular systems, invalid parameters, and non-convergence. [Source PDF, pp. 9-10, 32]

### REQ-010 - Transient analysis

The platform MUST support deterministic transient analysis with adaptive timestep control for supported capacitive, inductive, switching, oscillator, startup, digital-pulse, and electrothermal behavior. [Source PDF, pp. 9-10, 27-30, 32-33]

### REQ-011 - AC analysis

The platform MUST support small-signal AC analysis for gain, phase, impedance, bandwidth, and resonance where the selected models declare AC capability. [Source PDF, pp. 3, 10-11, 30]

### REQ-012 - Noise analysis

The platform MUST support declared noise models and analyses for resistor thermal noise, transistor shot and flicker noise, and power-supply noise, with the included noise sources and assumptions reported in results. [Source PDF, pp. 1, 5, 11]

### REQ-013 - Statistical and parameter analyses

The platform MUST support seeded Monte Carlo analysis for declared tolerances and SHOULD support parameter sweeps. Every stochastic result MUST store its seed, distributions, sample count, model versions, and execution engine. [Source PDF, pp. 11, 24, 30-31, 33]

## Non-ideal, thermal, and failure behavior

### REQ-014 - Non-ideal component behavior

Production models MUST declare applicable tolerance, leakage, parasitic resistance/capacitance/inductance, saturation, breakdown, delay, frequency behavior, and temperature coefficients rather than presenting ideal behavior as realistic. [Source PDF, pp. 1, 3, 5-8, 33]

### REQ-015 - Electrothermal coupling

Supported models MUST calculate power and temperature using declared thermal resistance, thermal mass, ambient conditions, and neighbor coupling where applicable. Temperature-dependent electrical behavior MUST feed back into the simulation at the declared fidelity. [Source PDF, pp. 5, 8-11, 33]

### REQ-016 - Failure modeling and injection

Supported models MUST declare ratings and failure modes, including applicable open, short, drift, leakage, intermittent, breakdown, and thermal-runaway behavior. Educational workflows MUST support controlled failure injection and results MUST distinguish warning, reversible stress, and permanent failure. [Source PDF, pp. 8-9, 31, 33, 41]

### REQ-017 - Numerical robustness and diagnostics

The solver MUST detect and diagnose convergence failure, timestep underflow, singular matrices, invalid numeric values, and resource exhaustion. It SHOULD provide documented remedies such as initial conditions, source stepping, conductance stepping, and timestep reduction without silently changing the requested model. [Source PDF, pp. 9-10, 12, 39]

## Digital and mixed-signal simulation

### REQ-018 - Event-driven digital semantics

The digital engine MUST be event-driven and deterministic; support logic `0`, `1`, `X`, and `Z`; model declared propagation delays and drive strengths; and diagnose contention, floating state, glitches, and setup/hold violations. [Source PDF, pp. 14-15, 29, 33-34]

### REQ-019 - Global deterministic scheduler

A global scheduler MUST coordinate analog timesteps, digital and clock events, thermal steps, RTL or external engines, and checkpoints using a deterministic integer timebase and timestamped boundary events. Identical inputs, configuration, seed, and engine versions MUST produce identical logical ordering. [Source PDF, pp. 27-28, 40]

### REQ-020 - Analog/digital boundary adapters

Analog-to-digital adapters MUST declare voltage thresholds, hysteresis, and unknown regions. Digital-to-analog adapters MUST support declared output resistance, rise/fall time, maximum current, and supply-dependent voltage so loading and signal integrity are observable. [Source PDF, p. 28]

### REQ-021 - Digital buses, clocks, and instruments

The platform MUST support clocks, buses, counters, registers, memories, and reusable digital blocks, with logic-analyzer and timing-diagram views that expose delays, violations, unknowns, and high-impedance state. [Source PDF, pp. 15, 30-31, 33-35]

## Component catalog and model exchange

### REQ-022 - Complete tracked component baseline

The canonical registry MUST track exactly 162 component families and 502 built-in variants or presets for the frozen baseline: 157 production families with 494 variants and 5 explicitly deferred research families with 8 variants. Every entry MUST have a stable ID and lifecycle state. Completeness refers to this family/preset baseline, not every manufacturer SKU. [Source basis for broad component domains: PDF, pp. 1-8, 14-15, 18-21, 30, 32-36; baseline counts are a repository decision.]

### REQ-023 - Normative component model contract

Every registry entry MUST declare aliases, an original IEC/ANSI-aligned symbol, pins, domains, SI units, defaults, limits, variants, supported analyses, fidelity/model tiers, temperature/parasitic/failure behavior, import mappings, provenance/license, golden tests, and known limitations. [Source PDF, pp. 5-9, 20, 26-28, 40]

### REQ-024 - Model and result interchange

The platform MUST define safe, versioned import/export behavior for SPICE `.model` and `.subckt`, Verilog/SystemVerilog, Verilog-A/AMS, IBIS, Touchstone, CSV/PWL, VCD/FST, and HEX/ELF. Unsupported syntax MUST fail with diagnostics rather than be ignored silently. [Source basis for SPICE, Verilog, waveforms, firmware, and external engines: PDF, pp. 14-18, 21-23, 30, 33-36; the complete format list is a repository decision.]

## CPU, RTL, memory, and complete systems

### REQ-025 - Educational CPU and memory progression

After the realistic-electronics gate, the product MUST support gate-level and selected transistor-level construction of registers, ALUs, program counters, decoders, control logic, ROM, RAM, and a one-bit, four-bit, or small eight-bit educational CPU. [Source PDF, pp. 13, 17-19, 34-35, 37]

### REQ-026 - HDL and RTL integration

The platform MUST support a staged Verilog/SystemVerilog workflow with source editing or import, syntax diagnostics, testbenches, hierarchy, compiled-model caching, waveform output, and reusable IP. Compilation MUST run in an isolated environment and MAY produce a WebAssembly model for supported designs. [Source PDF, pp. 15, 18, 30, 35]

### REQ-027 - Complete educational computer

The product MUST support a staged eight-bit or sixteen-bit educational computer comprising CPU, RAM, ROM, bus, timer, UART or equivalent I/O, keyboard, display, storage, assembler, bootloader, and a simple software execution path. It MUST NOT be marketed as a transistor-accurate modern PC. [Source PDF, pp. 21, 35]

### REQ-028 - Architecture and GPU abstractions

Later release gates MAY add CPU microarchitecture, cache, DRAM timing, multicore, functional machine emulation, and GPU SIMT, raster, compute, memory, and power models. Complete modern CPU/GPU simulation MUST use architecture, cycle, trace, RTL, or ISA abstractions, not simultaneous full-transistor physics. [Source PDF, pp. 15-21, 36, 42-44]

## Local, cloud, and collaboration

### REQ-029 - Local-first execution routing

Supported small analog circuits, educational digital circuits, selected transistor blocks, editing, and visualization MUST work locally where browser capabilities permit. The system MUST route unsupported or oversized work to an eligible server worker only with a clear explanation and user action or policy. [Source PDF, pp. 25-26, 31-32]

### REQ-030 - Heavy-job lifecycle

Cloud simulation MUST expose validation, queueing, progress streaming, bounded execution, checkpoint/resume where supported, cancellation, result storage, and terminal diagnostics for large SPICE, RTL, Monte Carlo, thermal, architecture, and GPU jobs. [Source PDF, pp. 25-26, 36, 39]

### REQ-031 - Versioning and real-time collaboration

Cloud projects MUST support durable versions, access-controlled sharing, comments, reusable libraries, and CRDT-based concurrent editing. Reconnect and conflict handling MUST converge without silently discarding accepted edits; simulation runs MUST bind to an immutable project revision. [Source basis for version history, comments, team collaboration, and public sharing: PDF, pp. 31-32, 41-42; CRDT selection is a repository decision.]

## Security, performance, accessibility, and licensing

### REQ-032 - Untrusted workload isolation

Imported archives, SPICE models, HDL, firmware, custom equations, and external-engine inputs MUST be treated as untrusted. Server execution MUST use no outbound network by default, read-only runtime filesystems, isolated scratch storage, and CPU, memory, time, process, and output limits. [Source basis for server workers and resource risks: PDF, pp. 25-26, 36, 39-40; specific controls are a repository security decision.]

### REQ-033 - Responsive and scalable browser execution

The browser MUST keep simulation off the main UI thread, provide threaded and single-threaded WebAssembly paths where supported, bound waveform retention, and apply viewport culling, level of detail, streaming, sparse storage, and selective probing as applicable. WebGPU compute MUST be enabled only for workloads that pass reproducible benchmarks. [Source PDF, pp. 23-25, 29-30, 39-40]

### REQ-034 - Browser compatibility, accessibility, and localization

The production UI MUST support the latest two stable desktop versions of Chrome, Edge, Firefox, and Safari; meet WCAG 2.2 AA; provide complete keyboard operation and non-color-only diagnostics; and keep user-facing text localization-ready. Mobile editing is outside the first MVP. [Source basis for a browser product and visualization: PDF, pp. 22-25, 30-32, 37; exact browser, accessibility, and localization targets are repository decisions.]

### REQ-035 - Open-source and third-party license boundary

The public core MUST be Apache-2.0. Every external engine, model, dataset, and symbol source MUST have recorded provenance and license. GPL or mixed-license engines MUST remain behind an executable or process boundary and MUST NOT be distributed with the core until a documented license review approves that distribution. [Repository decision informed by the external-engine integration strategy in Source PDF, pp. 21-26, 35-36, 43.]

### REQ-036 - Realistic Electronics MVP release gate

The first production gate MUST demonstrate the LED, RC charging, rectifier, transistor switch, CMOS inverter, ring oscillator, NAND, SR latch, one-bit memory, half-adder, and full-adder circuits with the required measurement, waveform, non-ideal, thermal, failure, reusable-subcircuit, WebAssembly, and Worker behaviors. CPU, GPU, and complete-computer release work MUST remain gated until this acceptance suite passes. [Source PDF, p. 37]

## Physical representation and integrated-circuit packages

### REQ-037 - Realistic physical component appearance

Every released basic component variant MUST provide an original, scalable physical representation that is recognizably similar to the corresponding real component while retaining an electrically unambiguous schematic symbol. The same component instance MUST be switchable between schematic and physical views without changing its stable identity, connectivity, parameters, model binding, or simulation state. Physical representations MUST show applicable body shape, lead or terminal geometry, polarity, pin-one orientation, value or color coding, and safety markings; they MUST provide zoom-level simplification, non-color-only identification, and a clear statement that visual realism does not establish dimensional, manufacturing, or simulation accuracy. [Source basis for drag-and-drop components, visual interaction, beginner components, and educational visualization: PDF, pp. 22-23, 30-31; the linked schematic/physical representation contract is a repository decision.]

### REQ-038 - Reusable IC package library and parametric package designer

Integrated-circuit function, schematic symbol, electrical model, physical package, and optional PCB-footprint metadata MUST be separate, versioned definitions joined by stable bindings. The platform MUST provide a reusable package library and a parametric package designer capable of defining a distinct visual package for each IC variant, including body dimensions and style, lead or pad geometry, pin count and numbering, pin names, spacing or pitch, orientation marker, notch or pin-one dot, exposed or thermal pad, labels, colors, and package-specific limits. A device MAY bind to several packages and a package MAY be reused by several devices; changing appearance MUST NOT silently alter electrical pin mapping. Package validation MUST diagnose duplicate, missing, out-of-range, or unmapped pins, and the initial package taxonomy MUST cover through-hole, gull-wing, leadless, grid-array, and transistor or power-package forms without claiming a PCB-layout editor. [Source basis for component records, custom models, hierarchy, and reusable component libraries: PDF, pp. 26-27, 29-32; the package-definition separation, parametric designer, and validation rules are repository decisions.]

## Applied Physics and scientific model governance

### REQ-039 - Applied Physics First

The platform MUST follow the normative progression **Physical Principles -> Mathematical Models -> Engineering Equations -> Numerical Algorithms -> Primitive Models -> Composite Models -> Library Devices -> Circuits and Boards -> Complete Systems -> Experimental Validation**. Physics MUST inform every fidelity tier; R4 applies the real-world effects that are intentionally simplified in earlier tiers and MUST NOT be treated as the first point at which physics exists. [User architecture brief, 2026-07-16; Source PDF, pp. 1-12, 27-30, 39-41]

### REQ-040 - Formal physics model contract and registry

Every governed model MUST have a stable ID, immutable revision identity, model kind, governing principles, equations or algorithm reference, parameters, dimensions, dependencies, supported analyses, fidelity, validity domain, provenance, accuracy statement, uncertainty statement, limitations, and validation status. The versioned model registry MUST distinguish `physics`, `primitive`, `composite`, `behavioral`, and `external_adapter` kinds without claiming unenumerated model inventory. [User architecture brief, 2026-07-16; Source PDF, pp. 5-12, 20-21, 26-28, 40]

### REQ-041 - Units and dimensional validation

Normative numeric model parameters, equations, ports, stimuli, measurements, and benchmark assertions MUST declare dimensions and canonical unprefixed SI units. Import and authoring workflows MUST reject incompatible dimensions, preserve an explicit unit-conversion record, and keep display prefixes separate from internal values. Dimensionless quantities MUST be marked explicitly rather than represented by an absent unit. [User architecture brief, 2026-07-16; Source PDF, pp. 5-11, 27-30]

### REQ-042 - Validity, provenance, trust, and limitations

Every model revision MUST declare its applicable operating ranges, unsupported conditions, source type, source locator and version, license or redistribution status, author or steward, trust level, validation state, and known limitations. Missing, expired, contradictory, or unverifiable provenance MUST prevent system-library publication and MUST remain visible for user-library imports. [User architecture brief, 2026-07-16; Source PDF, pp. 5-9, 20-21, 26-28, 40-41]

### REQ-043 - Model accuracy and uncertainty

Every released model MUST state what reference it was compared with, the metrics and operating envelope used, observed error, numerical tolerance, parameter or measurement uncertainty, and whether the result is verified, correlated, estimated, or unknown. The product MUST NOT present more significant precision or a broader accuracy claim than its evidence supports. [User architecture brief, 2026-07-16; Source PDF, pp. 9-12, 39-41]

### REQ-044 - Experimental correlation and physical benchmarks

The quality system MUST define reproducible physical benchmark fixtures with device identity, specimen count, equipment, calibration status, wiring and environment, stimulus, procedure, raw-data location, processing method, expected envelope, uncertainty budget, model revision, and reproducibility manifest. Correlation evidence MUST be versioned and MUST NOT be inferred from a simulation-to-simulation comparison alone. [User architecture brief, 2026-07-16; Source PDF, pp. 30-31, 37, 39-41]

### REQ-045 - Real-world electrical, thermal, and environmental behavior

R4 MUST preserve the existing tolerance, non-ideal, parasitic, noise, electrothermal, derating, aging, and failure scope and expand it with explicit environment inputs, coupled heat flow, ambient and enclosure assumptions, humidity or pressure where applicable, and declared approximation limits. Models MUST couple these effects only at a documented fidelity and timestep policy. [User architecture brief, 2026-07-16; Source PDF, pp. 1, 3, 5-12, 33, 39-41]

### REQ-046 - Manufacturing variation, statistics, and aging

Applicable model revisions MUST define manufacturing distributions, correlations, lot or process assumptions, tolerance truncation, mismatch, deterministic seeds, sample counts, aging mechanisms, stress history, drift, and end-of-life criteria. Statistical results MUST retain the exact model and parameter revisions used. [User architecture brief, 2026-07-16; Source PDF, pp. 8-11, 24, 30-31, 33]

### REQ-047 - Failure, interconnection, source, and instrument physics

R4 MUST specify applicable overstress and failure transitions; wires, contacts, connectors, cables, breadboards, and package interconnect parasitics; source impedance, regulation, ripple, capacity, and transient limits; and instrument input impedance, bandwidth, loading, noise, resolution, and clipping. Ideal sources, wires, and instruments MAY exist only when their idealization is explicit. [User architecture brief, 2026-07-16; Source PDF, pp. 5-11, 22-23, 30-31, 33, 37]

## Hierarchical model and device library

### REQ-048 - Hierarchical model taxonomy and acyclic dependencies

The library MUST distinguish physics models, primitive models, composite models, behavioral models, external-engine adapters, generic devices, vendor devices or variants, symbols, packages, pin profiles, bindings, boards or modules, systems, user projects, and validation artifacts. Composite dependency graphs MUST use exact immutable revisions and MUST reject cycles, missing nodes, incompatible ports, and unsupported fidelity transitions. [User architecture brief, 2026-07-16; Source PDF, pp. 2, 13-21, 26-29, 31-37]

### REQ-049 - Generic-device and vendor-variant inheritance

Market-scale ingestion MUST reuse a validated generic device or family model and create vendor or ordering-code variants through bounded parameter overrides, package and pin bindings, metadata, and evidence. Every override MUST name its source and validation state; inheritance MUST reject unknown, dimensionally incompatible, out-of-range, or contract-changing overrides. Complete internal circuits MUST NOT be duplicated solely for vendor ordering codes. [User architecture brief, 2026-07-16; Source PDF, pp. 6-8, 20, 26-27, 32-36]

### REQ-050 - Symbol, package, pin-profile, and binding orthogonality

Electrical or functional models, schematic symbols, physical packages, pin profiles, device-package bindings, boards, and systems MUST remain independently versioned records. A package MUST describe mechanical appearance and terminals only; it MUST NOT contain a device, board, module, or system. A binding MUST prove complete, one-to-one or explicitly aliased pin mapping and MUST diagnose every missing, duplicate, incompatible, or out-of-range mapping. [User architecture brief, 2026-07-16; Source PDF, pp. 22-23, 26-32]

### REQ-051 - Board and module schema

A board or module revision MUST compose exact device, binding, connector, subcircuit, asset, and firmware references with explicit ports and configuration. A board is not a package; for example, an Arduino Uno-class artifact is a board that may contain an ATmega328P-class device and other devices, packages, and interconnects. [User architecture brief, 2026-07-16; Source PDF, pp. 16, 21, 26-27, 29, 31-37]

### REQ-052 - System and project revision composition

A system revision MUST compose exact board, device, subsystem, stimulus, environment, and software revisions through declared interfaces. Every saved simulation and user project MUST resolve all mutable aliases to immutable revision IDs and content hashes so later library publication cannot silently change prior results. [User architecture brief, 2026-07-16; Source PDF, pp. 16-21, 25-29, 35-37, 40]

### REQ-053 - End-to-end model lineage

For every simulation result, the platform MUST be able to traverse from physical principle and governing model through primitive or composite dependencies, generic and vendor devices, symbol/package/pin binding, board or system composition, project revision, execution engine, benchmark evidence, and result artifact. Missing lineage MUST be reported as a publication or reproducibility failure. [User architecture brief, 2026-07-16; Source PDF, pp. 20-21, 26-28, 35-37, 40-41]

## Data-driven library, persistence, and identity

### REQ-054 - Library Service and storage-independent engine

Clients, importers, administrative tools, and simulation preparation MUST access governed library records through a versioned Library Service contract. The simulation engine MUST consume a validated, resolved `ComponentDefinitionPlan` or equivalent execution bundle and MUST NOT depend directly on PostgreSQL, a document database, object storage, or IndexedDB. Storage is a source of governed data, not a simulation engine. [User architecture brief, 2026-07-16; Source PDF, pp. 25-29, 31-32, 39-40]

### REQ-055 - Mixed storage responsibility

The hosted architecture MUST initially use PostgreSQL for identities, ownership, permissions, stable metadata, revisions, dependency edges, publication state, audit records, and searchable indexes; PostgreSQL `JSONB` MAY store validated evolving definitions when indexed query and transaction requirements are met. S3-compatible storage MUST hold large immutable archives, assets, raw datasets, and waveforms; IndexedDB MUST support local projects, cache, and offline outbox state. A separate document database requires a superseding ADR proving that PostgreSQL `JSONB` is insufficient. [User architecture brief, 2026-07-16; Source PDF, pp. 25-26, 31-32, 39]

### REQ-056 - Declarative models and executable-kernel boundary

Database- and archive-resident model content MUST be declarative, schema-validated, dimensionally validated, resource-bounded, and compiled into approved execution plans. Native, WASM, HDL, SPICE, equation, or external-adapter kernels MUST be selected from an allowlisted capability registry and run under the applicable sandbox. Arbitrary executable database content MUST be prohibited. [User architecture brief, 2026-07-16; Source PDF, pp. 21-29, 35-36, 39-40]

### REQ-057 - Minimal Google OIDC with guest preservation

An early personal-account release MUST support Google OIDC through a provider-neutral identity interface while preserving a fully usable guest/offline path. Authentication MUST use standards-based issuer, audience, nonce, state, PKCE where applicable, verified email claims, session rotation, logout, and account-linking rules; it MUST NOT move organization, enterprise RBAC, or advanced collaboration scope out of R10. [User architecture brief, 2026-07-16; Source PDF, pp. 31-32, 41-42]

### REQ-058 - Guest migration and personal cloud persistence

Users MUST be able to keep projects only on their device, opt into a personal cloud account, and transactionally migrate selected guest projects without duplicate ownership, silent overwrite, or loss of local data. Sync MUST define revision comparison, conflict copies or explicit resolution, retry and idempotency, quota failure, account unlinking, export, and continued offline access. [User architecture brief, 2026-07-16; Source PDF, pp. 25-26, 31-32, 41-42]

### REQ-059 - Immutable revisions and publication lifecycle

Published model, device, package, binding, board, system, and benchmark revisions MUST be immutable, content-addressable, auditable, and replaceable only through a new revision with explicit supersession or deprecation metadata. Drafts MAY change until publication, but project and result references MUST resolve to an immutable revision. [User architecture brief, 2026-07-16; Source PDF, pp. 26-28, 31-32, 40-41]

### REQ-060 - System- and user-library permissions

System-library publication MUST require authorized stewardship, schema and dimensional conformance, provenance and license review, dependency closure, validation evidence, and audit records. User libraries MUST support private drafts, duplication, validation, publication where policy permits, archive, restore, and export without granting clients unrestricted database access. [User architecture brief, 2026-07-16; Source PDF, pp. 26-27, 31-32, 40-42]

### REQ-061 - Safe CRUD and dependency-aware retirement

Library operations MUST provide validated create, read, revise, compare, publish, deprecate, supersede, archive, soft-delete, restore, duplicate, dependency resolution, reverse-dependency resolution, reference migration, import, and export. Referenced or published records MUST NOT be hard-deleted; retirement MUST preserve historical resolution and identify compatible replacements where available. [User architecture brief, 2026-07-16; Source PDF, pp. 26-28, 31-32, 40-42]

### REQ-062 - Versioned Library Service API

The Library Service MUST specify versioned endpoints or messages for search, exact-revision retrieval, dependency and reverse-dependency traversal, draft creation, validation, comparison, publication, deprecation, supersession, archive, soft deletion, restore, import, export, and resolution into an engine-ready bundle. Every write MUST enforce authorization, schema, dimensions, dependency closure, provenance, license policy, publication policy, optimistic concurrency, and audit logging. [User architecture brief, 2026-07-16; Source PDF, pp. 25-29, 31-32, 39-42]

### REQ-063 - Imported-model trust and licensing

Every imported model MUST retain source, content hash, declared and detected format, license or unknown-license state, redistribution permission, trust level, validation status, parser diagnostics, executable-mode classification, dependency closure, and sandbox policy. Untrusted, unlicensed, or unvalidated imports MUST NOT enter the system library or execute outside the declared isolation boundary. [User architecture brief, 2026-07-16; Source PDF, pp. 20-21, 26-28, 35-36, 39-40]

## Change control

Changing a requirement's meaning requires:

1. an issue or decision record explaining the motivation;
2. an ADR when an accepted architectural decision changes;
3. updates to tasks, tests, release gates, and traceability;
4. compatibility and migration analysis for public contracts;
5. preservation of the existing requirement ID and a dated revision note.
