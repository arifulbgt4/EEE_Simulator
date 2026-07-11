# Project Charter

## Mission

Build an open, browser-based virtual electronics laboratory that lets learners, engineers, and researchers understand how behavior changes across component, transistor, gate, RTL, processor, memory, architecture, and complete-system abstractions. The product must expose the right fidelity for the question instead of treating all scales as one impossible SPICE problem. [Source PDF, pp. 1-3, 13-16, 41-44]

## Problem statement

Existing tools usually specialize in one layer: analog circuit solving, interactive educational circuits, RTL compilation, processor architecture, machine emulation, or GPU analysis. The intended platform connects these layers in a single hierarchical project, with interactive visualization and an explicit accuracy model. [Source PDF, pp. 16, 21-22, 42]

Users should be able to begin with a power source, resistor, LED, and ground; observe voltage, current, power, temperature, waveform, and failure risk; construct transistor logic and memory; and later substitute gate, RTL, timing, architecture, or functional models for larger systems. [Source PDF, pp. 2, 16-21]

## Product principles

1. **Fidelity must be explicit.** Every model declares its fidelity, supported analyses, limits, validation reference, and provenance. [Source PDF, pp. 3-4, 13-16, 27, 40]
2. **Scale determines abstraction.** Detailed electrical models serve small circuits and selected blocks; event, RTL, architecture, and ISA models serve larger systems. [Source PDF, pp. 12-21, 43-44]
3. **Realistic electronics comes first.** Non-ideal components, temperature, leakage, tolerance, parasitics, and failure are required before CPU and GPU expansion. [Source PDF, pp. 5-11, 33, 37, 44]
4. **The browser remains responsive.** Simulation work runs outside the main UI thread, and heavy jobs can move to cloud workers. [Source PDF, pp. 23-26]
5. **Results must teach and explain.** Waveforms are complemented by voltage/current overlays, heat maps, logic state, timing, failure, memory, CPU, cache, and GPU views with honest educational labeling. [Source PDF, pp. 30-31]
6. **Determinism and evidence beat appearance.** A realistic-looking result is not acceptable without deterministic scheduling, validated models, diagnostics, and reference comparisons. [Source PDF, pp. 27-29, 39-40]
7. **Open core, explicit boundaries.** The core remains Apache-2.0; external engines and imported models retain their own licenses and run across documented isolation boundaries.

## Initial success outcome

The first production outcome is the **Realistic Electronics MVP**. A user can create and simulate the ten canonical demonstrations - LED circuit, RC charging circuit, transistor switch, CMOS inverter, ring oscillator, NAND gate, SR latch, one-bit memory, half adder, and full adder - with measurement, waveform, non-ideal, thermal, and failure behavior appropriate to the selected model. [Source PDF, p. 37]

Passing this outcome is a prerequisite for CPU-stage work. The exact criteria live in [Release Gates](planning/RELEASE_GATES.md) and [Release Acceptance Checklists](quality/RELEASE_ACCEPTANCE_CHECKLISTS.md).

## Stakeholders

- learners and educators in electronics and computer architecture;
- circuit, embedded, and mixed-signal engineers;
- hardware, CPU, memory, and GPU researchers;
- component-model authors and validators;
- open-source contributors and maintainers;
- hosted-service operators and organizational administrators.

Their responsibilities and workflows are defined in [User Roles and Use Cases](USER_ROLES_AND_USE_CASES.md). The source study identifies education, engineering, architecture research, fault analysis, and collaborative design as the main use areas. [Source PDF, pp. 41-42]

## Governance and authority

- Accepted ADRs lock architectural and policy decisions.
- `REQ-001` through `REQ-036` are the stable product requirement identifiers.
- The component registry is the canonical catalog inventory.
- Release gates decide whether capability may advance to the next stage.
- Atomic tasks are the only executable planning units.
- Accuracy and performance claims require current validation evidence.

Changes to mission, fidelity semantics, project format compatibility, engine isolation, collaboration consistency, or licensing require an ADR. Changes to a requirement keep the existing ID and record the revision; IDs are never reused.

## Constraints

- Full-transistor, full-physics simulation of modern CPUs, GPUs, or gigabyte-scale memory in a browser is outside feasible scope. [Source PDF, pp. 12-13, 18-21, 42-44]
- The implementation must remain useful without cloud connectivity for supported small projects and editing workflows. [Source PDF, pp. 25-26, 31-32]
- Browser and worker resource use must be bounded; large matrices and waveforms cannot grow without limits. [Source PDF, pp. 29, 39]
- The project must not imply that animated current particles represent actual electron speed. [Source PDF, p. 31]
- Built-in catalog completeness means the versioned family and preset baseline, not every commercial SKU.

## Related documents

- [Product Requirements](PRODUCT_REQUIREMENTS.md)
- [Scope, Success, and Non-Goals](SCOPE_SUCCESS_AND_NON_GOALS.md)
- [System Architecture](architecture/SYSTEM_ARCHITECTURE.md)
- [Master Roadmap](planning/MASTER_ROADMAP.md)
- [Risk Register](planning/RISK_REGISTER.md)
