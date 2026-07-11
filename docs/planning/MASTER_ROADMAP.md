# Master Roadmap

## Roadmap policy

The platform advances from component to circuit to logic to computer, matching the feasibility sequence in the source brief (PDF pp. 32-36 and 40-44). A later phase may begin discovery work early, but no release may bypass its prerequisite gate.

Each phase has four parallel tracks:

- Product and user experience.
- Simulation and component capability.
- Platform, security, and operations.
- Validation, documentation, and release evidence.

## R0 - Documentation baseline

**Outcome:** A decision-complete source of truth suitable for contributors and small AI agents.

- Freeze product scope, architecture, public contracts, 162-family/502-variant registry, separate package registry, realistic physical-appearance contract, fidelity policy, accuracy targets, and open-source boundary.
- Create requirement, epic, atomic task, validation, risk, dependency, and release traceability.
- Exit only when the R0 checklist has no missing required document, family, variant, task, or traceability link.

## R1 - Repository and editor foundation

**Outcome:** A local-first visual project can be created and safely stored.

- Establish the open-source repository, quality gates, release/version policy, and documentation checks.
- Build the React/TypeScript application shell, Canvas editor, selection, placement, rotation, deletion, undo/redo, keyboard navigation, and accessible property editing.
- Implement original schematic symbols, recognizable physical/breadboard component views, reusable IC packages, symbol-to-package pin mapping, wire/junction/net rules, hierarchy, and subcircuits.
- Define axial/radial, LED, transistor/power and IC package primitives plus a constrained parametric custom-package designer.
- Implement `.eesim` manifest, local IndexedDB storage, autosave, import/export, schema validation, and migrations.

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
- Validate GRC-011 through GRC-020.

## R4 - Non-ideal, thermal, tolerance, and failure

**Outcome:** The product explains why a mathematically functioning circuit may fail physically.

- Add tolerance distributions, Monte Carlo, leakage, ESR/ESL, parasitic R/C/L, noise foundation, power limits, thermal resistance/capacitance, derating, and aging metadata.
- Add open, short, degraded, leakage-increase, intermittent, and breakdown failure behavior.
- Add heat maps, power indicators, limit diagnostics, failure injection, and deterministic seeds.
- Validate GRC-021 through GRC-026.

## R5 - Event-driven digital and mixed-signal

**Outcome:** Transistor-to-logic learning and analog/digital co-simulation work in one project.

- Implement deterministic event queue, 0/1/X/Z logic, drive strength, delay, fan-out, buses, contention, setup/hold, and metastability indication.
- Release basic gates, latch, flip-flop, mux/demux, encoder/decoder, counter, register, adder, and comparator.
- Implement timestamped analog/digital boundaries, threshold bands, hysteresis, non-ideal output drive, and global scheduler ordering.
- Validate GRC-027 through GRC-035.

## R6 - Realistic Electronics MVP

**Outcome:** The first public production release.

- Complete guest/offline workflow, tutorials, reference projects, error guidance, accessibility, browser compatibility, performance, and security hardening.
- Demonstrate LED, RC, rectifier, transistor switch, CMOS inverter, ring oscillator, NAND, SR latch, one-bit memory, half/full adder, and thermal failure.
- Publish accuracy envelopes, known limitations, component coverage, release evidence, and migration policy.

## R7 - Complete production component catalog

**Outcome:** All 157 production families and 494 production variants are covered.

- Complete passives/magnetics, protection/isolation, power electronics, sensors, actuators, connectors/cables, instruments, digital logic, memory, MCU/FPGA peripherals, and RF/communications, including their required physical/package representations.
- Complete SPICE, Verilog/SystemVerilog, Verilog-A/AMS, IBIS, Touchstone, CSV/PWL, VCD/FST, and HEX/ELF format work scheduled for this phase.
- Validate GRC-036 through GRC-040 plus every family-specific fixture.

## R8 - Educational CPU

**Outcome:** Users can build and understand a complete 1/4/8-bit processor hierarchy.

- Release register file, ALU, program counter, decoder, control, flags, bus, ROM/RAM, clock, interrupt, timer, UART, assembler, loader, debugger, and instruction/state views.
- Provide transistor or gate detail only for selected small blocks; use event/behavioral levels for the complete CPU.
- Validate GRC-041 through GRC-043.

## R9 - RTL, FPGA, and educational full computer

**Outcome:** HDL blocks and an 8/16-bit educational machine run within the platform.

- Add sandboxed HDL validation, Verilator compilation, model caching, testbenches, waveforms, hierarchy, reusable IP, FPGA primitives, and differential validation.
- Complete CPU, RAM, ROM, bus, storage, input, display, network/serial devices, boot flow, and a documented firmware/monitor environment.
- Validate GRC-044 and GRC-045.

## R10 - Cloud collaboration and compute

**Outcome:** Teams share projects and safely run heavy simulations.

- Add OIDC-compatible identity, organizations, projects, RBAC, invitations, comments, CRDT collaboration, snapshots, branches, public library, and moderation.
- Add REST job API, Redis Streams queue, container workers, SSE progress/results, cancellation, retry, checkpoint/resume, quotas, usage accounting, and S3-compatible result storage.
- Add initial ngspice, Verilator, and approved heavy-analysis workers.

## R11 - Large analog and HPC

**Outcome:** Large SPICE-compatible and parameter-sweep workloads use isolated scalable workers.

- Add Xyce-class worker integration, worker pools, MPI/HPC profiles, large Monte Carlo, thermal grid, result reduction, archival, and reproducibility bundles.
- Keep GPL components outside the Apache-licensed core process and distribution unless legal review approves a different arrangement.

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
