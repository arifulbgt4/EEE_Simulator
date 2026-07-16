# Master Roadmap

## Roadmap policy

The platform advances from component to circuit to logic to computer. The unverified source brief suggests this feasibility sequence (PDF pp. 32-36 and 40-44); accepted repository decisions adopt it as product planning, not as confirmed technical evidence. A later phase may begin discovery work early, but no release may bypass its prerequisite gate. See the [Source and Evidence Policy](../SOURCE_AND_EVIDENCE_POLICY.md).

Each phase has four parallel tracks:

- Product and user experience.
- Simulation and component capability.
- Platform, security, and operations.
- Validation, documentation, and release evidence.

## R0 - Documentation baseline

**Outcome:** A decision-complete source of truth suitable for contributors and small AI agents.

- Freeze product scope, Applied Physics First, architecture, public contracts, 162-family/502-variant component registry, scientific model registry, separate package registry, realistic physical-appearance contract, fidelity policy, accuracy/uncertainty targets, physical benchmark contract, and open-source boundary.
- Create requirement, epic, atomic task, validation, risk, dependency, and release traceability.
- Exit only when the R0 checklist has no missing required document, family, variant, task, or traceability link.

## R1 - Repository and editor foundation

**Outcome:** A local-first visual project can be created and safely stored.

- Establish the open-source repository, quality gates, release/version policy, and documentation checks.
- Build the React/TypeScript application shell, Canvas editor, selection, placement, rotation, deletion, undo/redo, keyboard navigation, and accessible property editing.
- Implement original schematic symbols, recognizable physical/breadboard component views, reusable IC packages, symbol-to-package pin mapping, wire/junction/net rules, hierarchy, and subcircuits.
- Define axial/radial, LED, transistor/power and IC package primitives plus a constrained parametric custom-package designer.
- Implement `.eesim` manifest, local IndexedDB storage, autosave, import/export, schema validation, and migrations.
- Establish the versioned Library Service contract, immutable revision/dependency foundation, declarative model ingestion, and exact model/device/package/board/system references.
- Add optional provider-neutral Google OIDC, private personal cloud projects, explicit guest-to-account migration, and IndexedDB cache/outbox sync while preserving unauthenticated offline use. Organizations, team RBAC, invitations, collaboration, and public moderation remain R10.

## R2 - Linear analog foundation

**Outcome:** Small ideal circuits run locally in a responsive browser.

- Implement SI units, topology validation, netlist generation, sparse MNA, DC operating point, and transient integration.
- Release core sources, controlled sources, resistor, capacitor, inductor, switch, ground, probes, multimeter, oscilloscope, and waveform viewer.
- Run the simulation core in a Rust/WASM worker with structured progress, result, cancellation, and diagnostic messages.
- Validate GRC-001 through GRC-008.

## R3 - Nonlinear semiconductors and realistic analog

**Outcome:** Nonlinear circuits and core semiconductor demonstrations are trustworthy.

- Implement nonlinear stamping, Newton iteration, adaptive timestep, damping, source stepping, conductance stepping, and convergence reporting.
- Release diode families required by MVP, LED, NPN/PNP BJT, NMOS/PMOS, and op-amp tiers.
- Add AC analysis, compact-model import foundation, and reference-engine differential tests.
- Complete the versioned `EngineAdapter` lifecycle and the isolated ngspice reference path through `PLAT-EXT-001`..`PLAT-EXT-018`, including capability discovery, validation, preparation, run/stream, pause/checkpoint/resume negotiation, cancellation, disposal, sandboxing, provenance, and analytical/differential evidence. Unsupported operations must fail closed; documentation does not imply that ngspice is installed or distributable.
- Validate GRC-011 through GRC-020.

## R4 - Applied Physics and Real-World Fidelity

**Outcome:** The product connects validated physical principles and evidence to real-world circuit behavior and explains why a mathematically functioning circuit may perform differently, disturb its measurement, age, or fail physically.

- Preserve tolerance distributions, Monte Carlo, leakage, ESR/ESL, parasitic R/C/L, noise, power limits, thermal resistance/capacitance, derating, aging, open/short/degraded/leakage/intermittent/breakdown failures, heat maps, power indicators, diagnostics, injection, and deterministic seeds.
- Govern formal physics-model specifications, canonical SI dimensions, operating/validity ranges, approximation limits, provenance, trust, accuracy envelopes, uncertainty budgets, dependency lineage, and reproducibility manifests.
- Add electrical/thermal/environmental coupling; manufacturing variation and mismatch; aging and stress history; wire/contact/connector/package interconnect; source impedance/regulation/ripple/capacity; and instrument loading/bandwidth/noise/resolution physics at declared fidelity.
- Correlate the declared envelopes with versioned physical benchmark fixtures containing calibrated equipment, raw data, environment, procedure, specimen, uncertainty, model revision, and processing evidence.
- Validate GRC-021, GRC-022, GRC-026, and GRC-055 through GRC-066 at G4. Preserve the specifications and dependencies for catalog-bound power/protection fixtures GRC-023 through GRC-025, whose execution evidence remains scheduled for R7. G5 and G6 cannot bypass applicable G4 behavior.

## R5 - Event-driven digital and mixed-signal

**Outcome:** Transistor-to-logic learning and analog/digital co-simulation work in one project.

- Implement deterministic event queue, 0/1/X/Z logic, drive strength, delay, fan-out, buses, contention, setup/hold, and metastability indication.
- Release basic gates, latch, flip-flop, mux/demux, encoder/decoder, counter, register, adder, and comparator.
- Implement timestamped analog/digital boundaries, threshold bands, hysteresis, non-ideal output drive, and global scheduler ordering.
- Validate GRC-027 through GRC-034; the transistor-level SRAM fixture GRC-035 remains scheduled for R8 with the educational memory milestone.

## R6 - Realistic Electronics MVP

**Outcome:** The first public production release.

- Complete guest/offline workflow, tutorials, reference projects, error guidance, accessibility, browser compatibility, performance, and security hardening.
- Demonstrate LED, RC, rectifier, transistor switch, CMOS inverter, ring oscillator, NAND, SR latch, one-bit memory, half/full adder, and thermal failure.
- Publish accuracy envelopes, known limitations, component coverage, release evidence, and migration policy.
- Production-harden the optional personal account/cloud path, guest migration, private-project authorization, cache synchronization, quota behavior, export, and account unlinking without making sign-in mandatory.

## R7 - Complete production component catalog

**Outcome:** All 157 production families and 494 production variants are covered.

- Complete passives/magnetics, protection/isolation, power electronics, sensors, actuators, connectors/cables, instruments, digital logic, memory, MCU/FPGA peripherals, and RF/communications, including their required physical/package representations.
- Complete SPICE, Verilog/SystemVerilog, Verilog-A/AMS, IBIS, Touchstone, CSV/PWL, VCD/FST, and HEX/ELF format work scheduled for this phase.
- Complete `PLAT-EXT-019`..`PLAT-EXT-021` so only reviewed, immutable SPICE bundles reach the R3 adapter path and imported F3 macro-models retain pin, trust, license, sandbox, provenance, limitation, and differential evidence.
- Validate GRC-023 through GRC-025, GRC-036 through GRC-040, plus every family-specific fixture.
- Ingest market devices through generic-model inheritance, dimensionally valid bounded overrides, exact package/pin bindings, provenance, license, trust, and validation evidence; do not duplicate an internal circuit per ordering code or claim complete SKU coverage.

## R8 - Educational CPU

**Outcome:** Users can build and understand a complete 1/4/8-bit processor hierarchy.

- Release register file, ALU, program counter, decoder, control, flags, bus, ROM/RAM, clock, interrupt, timer, UART, assembler, loader, debugger, and instruction/state views.
- Provide transistor or gate detail only for selected small blocks; use event/behavioral levels for the complete CPU.
- Validate GRC-035 and GRC-041 through GRC-043.

## R9 - RTL, FPGA, and educational full computer

**Outcome:** HDL blocks and an 8/16-bit educational machine run within the platform.

- Add sandboxed HDL validation, Verilator compilation, model caching, testbenches, waveforms, hierarchy, reusable IP, FPGA primitives, and differential validation.
- Complete CPU, RAM, ROM, bus, storage, input, display, network/serial devices, boot flow, and a documented firmware/monitor environment.
- Validate GRC-044 and GRC-045.

## R10 - Cloud collaboration and compute

**Outcome:** Teams share projects and safely run heavy simulations.

- Add OIDC-compatible identity, organizations, projects, RBAC, invitations, comments, CRDT collaboration, snapshots, branches, public library, and moderation.
- Add REST job API, Redis Streams queue, container workers, SSE progress/results, cancellation, retry, checkpoint/resume, quotas, usage accounting, and S3-compatible result storage.
- Operationalize accepted external adapters such as ngspice and Verilator in isolated workers without redefining their lifecycle contracts. The ngspice worker requires the accepted R3 `PLAT-EXT-018` evidence; imported SPICE execution also requires the accepted R7 `PLAT-EXT-021` evidence. Hosted dispatch, leases, tenancy, quotas, and recovery remain R10 responsibilities.

## R11 - Large analog and HPC

**Outcome:** Large SPICE-compatible and parameter-sweep workloads use isolated scalable workers.

- Execute `PLAT-HPC-001`..`PLAT-HPC-011`: freeze G11 entry evidence; define the Xyce-class isolated adapter and license boundary; define scalable worker pools and MPI/HPC profiles; preserve deterministic Monte Carlo identities; distribute thermal-grid workloads with explicit convergence/conservation rules; perform deterministic streaming reduction; provide compatible checkpoint/restart; archive and retrieve large artifacts; enforce quotas, cost controls, and observability; and independently audit the complete evidence bundle.
- Keep GPL components outside the Apache-licensed core process and distribution unless a current legal review explicitly approves a different arrangement. Engine capability, MPI/runtime, scheduler, container image, model set, and environment revisions must be pinned; Source PDF citations cannot establish any of those facts.
- Exit only when `PLAT-HPC-011` publishes an accepted immutable `G11AcceptanceManifest` and `G11ReleaseDecision`; missing isolation, reproducibility, license, security, performance, artifact, quota, or traceability evidence fails the gate closed.

## R12 - Architecture and full-system research

**Outcome:** Functional and timing-oriented computer research is possible without false transistor-level claims.

- Add gem5-style CPU/cache/DRAM models, QEMU functional execution, RISC-V reference systems, checkpoints, workloads, pipeline/cache visualization, and power/performance studies.
- Validate GRC-046 and GRC-047.

## R13 - GPU and advanced research

**Outcome:** GPU, accelerator, advanced RF, and optional physical-device research are available through explicit research fidelity.

- Add simple raster/compute GPU, SIMD/SIMT, memory hierarchy, shader/kernel workflows, and Accel-Sim-class adapters.
- Add advanced S-parameter/RF workflows and explicitly approved F5 TCAD, electromagnetic, MEMS, superconducting, or emerging-device services.
- Validate GRC-048 and published research datasets.

## Completion definition

The project is complete only when every non-deferred requirement is released, all 157 production families and 494 production variants meet their required fidelity, every release checklist passes, and every deferred item remains visible with a reason and entry criterion.
