# Release Acceptance Checklists

## Universal release gate

- [ ] Scope and non-goals match the approved release gate.
- [ ] Every included requirement has an owner, task, test, and evidence link.
- [ ] No `Ready` or `In Progress` task is silently included as completed scope.
- [ ] Registry counts and coverage states are internally consistent.
- [ ] All released components have model, validation, provenance, limitations, and user documentation.
- [ ] All normative schemas are versioned and compatibility behavior is documented.
- [ ] Golden, differential, integration, failure, security, performance, browser, and accessibility suites pass.
- [ ] Known limitations and deferred work are visible in release notes.
- [ ] Third-party licenses, notices, model redistribution rights, and process isolation have been reviewed.
- [ ] Rollback, migration, backup, and incident procedures are current.

## Documentation baseline gate (R0)

- [ ] Root governance and contributor documents exist.
- [ ] Product, architecture, catalog, quality, planning, ADR, and task documents are cross-linked.
- [ ] The baseline contains exactly 162 families and 502 variants.
- [ ] Every variant has an atomic task card.
- [ ] Every production family has a family specification and applicable model/validation tasks.
- [ ] REQ-037/REQ-038 are traced to physical-appearance, package-registry, package-designer, pin-map and visual-regression tasks.
- [ ] Requirement traceability has no orphan row.
- [ ] All source-brief-derived requirements cite PDF pages.
- [ ] No executable application code or runtime configuration is introduced by the documentation-only milestone.

## Realistic Electronics MVP gate

- [ ] Guest users can create, save offline, export, import, and reopen a project.
- [ ] Core connectivity, sources, RLC, diode/LED, BJT, MOSFET, op-amp, basic gates, and instruments are released.
- [ ] Basic components have recognizable physical views, and released ICs have reusable package definitions with verified symbol/package pin equivalence.
- [ ] DC and transient analyses pass; AC, tolerance/Monte Carlo, power, temperature, leakage, and failure behavior meet the MVP scope.
- [ ] LED, RC, rectifier, transistor switch, CMOS inverter, ring oscillator, NAND, SR latch, one-bit memory, half adder, full adder, and thermal-failure demonstrations pass.
- [ ] Invalid circuits produce actionable diagnostics.
- [ ] UI remains responsive while simulations run in workers.
- [ ] Local result provenance and deterministic seeds are preserved.
- [ ] MVP performance, browser, and WCAG 2.2 AA gates pass.

## Complete catalog gate

- [ ] All 157 production families and 494 production variants are released or explicitly moved through an approved scope-change ADR.
- [ ] Deferred research families remain listed with rationale and entry criteria.
- [ ] SPICE, HDL, IBIS, Touchstone, waveform, stimulus, and firmware import policies are implemented and tested as scheduled.
- [ ] Vendor models retain provenance and redistribution restrictions.

## Educational computer gate

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

## Architecture, GPU, and research gates

- [ ] Engine adapters pin versions and reproduce reference workloads.
- [ ] Functional, timing, and architecture results are visibly distinguished.
- [ ] Full-transistor claims are not made for modern CPUs, GPUs, or full memory systems.
- [ ] Research model accuracy is bounded by a declared validation dataset and operating envelope.
- [ ] HPC results retain configuration, workload, model, engine, checkpoint, and environment provenance.
