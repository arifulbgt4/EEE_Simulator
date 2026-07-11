# Scope, Success, and Non-Goals

## In scope

### Realistic electronics foundation

- Hierarchical schematic capture, reusable subcircuits, offline projects, measurement, waveforms, and educational overlays. [Source PDF, pp. 2, 22-23, 30-32]
- DC, transient, AC, noise, Monte Carlo, thermal, and applicable parameter analyses. [Source PDF, pp. 9-11, 30]
- Ideal, non-ideal, nonlinear, parasitic, tolerance, leakage, thermal, rating, and failure behavior at declared fidelity. [Source PDF, pp. 3, 5-9, 33]
- Analog, event-driven digital, and mixed-signal co-simulation with deterministic boundary exchange. [Source PDF, pp. 14-15, 27-28, 33-34, 40]
- A versioned catalog baseline of 162 families and 502 built-in variants or presets, plus safely imported vendor models. The counts are a repository baseline; the source brief supplies the required component domains and progression. [Source PDF, pp. 1-8, 13-15, 18-21, 30, 32-36]
- Original, scalable physical representations for released basic components, linked to but distinct from their schematic symbols and electrical models. Recognizable body geometry, polarity, orientation, leads, and value markings are required where applicable. [Source basis: PDF, pp. 22-23, 30-31; physical-view specifics are a repository decision.]
- A reusable, versioned IC package library and parametric package designer that separates package appearance and pin geometry from device function, model, symbol, and optional footprint metadata. [Source basis: PDF, pp. 26-27, 31-32; package-system specifics are a repository decision.]

### Staged computer systems

- Gate and selected transistor views of logic, registers, ALUs, control, and small memories. [Source PDF, pp. 13-19]
- One-bit, four-bit, and small eight-bit educational CPU progression, then an eight-bit or sixteen-bit educational computer. [Source PDF, pp. 13, 17-21, 34-35]
- Verilog/SystemVerilog and isolated RTL compilation with testbenches, waveforms, hierarchy, and reusable IP. [Source PDF, pp. 15, 18, 35]
- Later, gated architecture, functional machine, memory timing, and GPU cycle/trace abstractions. [Source PDF, pp. 15-21, 36]

### Platform and operations

- Next.js/React plus TypeScript UI, Canvas/WebGL2 visualization, Rust/WebAssembly core, and Worker-separated computation. [Source basis: PDF, pp. 22-25; exact stack selections are accepted repository decisions.]
- Local-first small simulation and isolated cloud workers for large or specialized jobs. [Source PDF, pp. 25-26, 36]
- Versioning, comments, controlled sharing, reusable libraries, and real-time collaboration. [Source PDF, pp. 31-32, 42]
- Accessibility, localization readiness, security isolation, provenance, open-core licensing, observability, and bounded resource use.

## Release boundaries

1. Documentation and registry foundation.
2. Editor, format, offline persistence, and linear circuit foundation.
3. Nonlinear semiconductor and SPICE interoperability.
4. Non-ideal, electrothermal, failure, AC, and statistical analyses.
5. Event-driven digital and analog/digital co-simulation.
6. **Realistic Electronics MVP** with all ten canonical demonstrations. [Source PDF, p. 37]
7. Remaining production component domains.
8. Educational CPU and memory.
9. RTL/FPGA integration and complete educational computer.
10. Collaboration, public library, and larger cloud workers.
11. Architecture, full-system, GPU, advanced RF, TCAD, and other research extensions.

The exact ordering and entry/exit criteria are defined in [Master Roadmap](planning/MASTER_ROADMAP.md) and [Release Gates](planning/RELEASE_GATES.md). The source brief explicitly warns that beginning with CPU, GPU, RAM, and a complete computer makes completion unlikely. [Source PDF, pp. 40-41]

## Success criteria

### Documentation foundation

- All planned canonical documents exist and cross-links resolve.
- `REQ-001` through `REQ-038` trace to at least one ADR, epic, atomic task, test, and release gate as applicable.
- The registry validates at exactly 162 families and 502 variants, with no missing required contract field.
- Every external dependency has source, version policy, license, isolation decision, and distribution status.

### Realistic Electronics MVP

- The ten canonical circuits - LED, RC charging, transistor switch, CMOS inverter, ring oscillator, NAND, SR latch, one-bit memory, half adder, and full adder - pass declared functional, numerical, deterministic, thermal/failure, and visualization checks. [Source PDF, p. 37]
- A supported reference project of 500 components and 1,000 nets can retain 100,000 selected waveform samples within documented browser limits.
- The declared reference suite reaches DC result in under one second and transient result in under five seconds on the documented reference desktop.
- Schematic pan and zoom target 50 FPS, and simulation causes no main-thread stall longer than 100 ms.
- Latest two stable desktop Chrome, Edge, Firefox, and Safari releases pass the supported capability matrix.
- WCAG 2.2 AA checks pass, including keyboard operation, focus behavior, non-color-only diagnostics, and accessible waveform summaries.
- Every released basic component in the MVP has a validated schematic-to-physical representation binding; switching views preserves identity, pin connectivity, parameter values, and simulation state.
- Every released MVP IC has a validated device-to-package pin map, and at least one through-hole and one surface-mount package demonstrate safe package reuse and per-device customization.

The numeric performance and accessibility thresholds are repository acceptance decisions. They implement the source study's requirements for Worker execution, bounded waveform memory, culling/level of detail, and responsive Canvas/WebGL rendering. [Source PDF, pp. 23-25, 29-31, 39-40]

### Numerical and deterministic quality

- F1 analytical circuits meet relative error `<= 1e-6`.
- F2 truth tables are exact, and configured timing ticks are deterministic.
- F3 models remain within the declared `<= 1%` DC and `<= 2%` transient/AC comparison envelope against their named reference unless a stricter or model-specific limit is documented.
- F4 electrothermal models remain within the declared default `<= 5%` reference envelope.
- Same project revision, configuration, seed, model versions, and engine versions reproduce the same logical event ordering and declared deterministic outputs.

Detailed criteria and exceptions belong in [Numerical Accuracy Targets](quality/NUMERICAL_ACCURACY_TARGETS.md).

## Non-goals

- Simulating every transistor in a modern CPU, GPU, or gigabyte-scale RAM simultaneously at full analog, thermal, or semiconductor-device fidelity in a browser. [Source PDF, pp. 12-13, 18-21, 42-44]
- Replacing mature SPICE, RTL, architecture, emulator, or GPU research engines in the first releases. The recommended strategy is a small educational solver plus adapters to specialized engines. [Source PDF, pp. 43-44]
- Shipping a modern-PC implementation in the Realistic Electronics MVP. [Source PDF, pp. 35, 37]
- Guaranteeing sign-off accuracy for safety-critical, medical, aerospace, mains, grid, automotive, or production semiconductor design without independent qualified verification.
- Bundling every manufacturer SKU. The built-in promise is the canonical family and preset baseline; vendor parts enter through imported models.
- Copying IEC 60617 artwork or redistributing proprietary models without permission.
- Treating visual animation as measured physical truth when it is an explanatory abstraction. [Source PDF, p. 31]
- Treating a realistic component body or IC package rendering as proof of electrical, dimensional, thermal, manufacturing, or regulatory accuracy.
- Delivering a complete PCB layout, manufacturing, or mechanical-CAD suite as part of the initial package designer; optional footprint metadata is an interoperability contract, not a PCB-editor commitment.
- Requiring cloud connectivity for supported small projects or basic editing. [Source PDF, pp. 25-26, 31-32]
- Mobile schematic editing in the first MVP; mobile viewing MAY be added later.
- Allowing arbitrary user HDL, model code, firmware, or external tools to execute without isolation and resource limits.

## Deferred research scope

Vacuum tubes, memristors, Josephson junctions, TCAD device physics, and detailed electromagnetic or MEMS models remain visible in the registry as `Deferred/Research`. Physical-device simulation is appropriate for individual devices and backend/HPC research, not the initial browser goal. [Source PDF, pp. 3-4, 14]

## Scope change rule

A proposal that bypasses a release gate, changes fidelity semantics, modifies `.eesim` compatibility, embeds an external engine, changes collaboration convergence, or changes the core license requires an ADR and updates to requirements, roadmap, risks, tests, and traceability before implementation begins.
