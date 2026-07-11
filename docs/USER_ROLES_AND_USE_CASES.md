# User Roles and Use Cases

## Role model

Roles describe user intent, not fixed subscription tiers. One person may act in several roles. Authorization roles for hosted projects are separate from these product personas.

The source study identifies education, engineering, computer-architecture research, fault analysis, and collaborative design as the principal uses. [Source PDF, pp. 41-42]

## Learner

**Goal:** Build intuition from current, voltage, and component behavior through logic and a small computer.

Primary use cases:

- Build a guided battery/resistor/LED circuit and understand that a resistor dissipates energy rather than consuming current. [Source PDF, pp. 2, 4-5]
- Observe voltage, current, power, temperature, waveform, and failure risk with explanations appropriate to the selected fidelity. [Source PDF, p. 2]
- Switch between an electrically clear schematic symbol and a recognizable physical component view, using body shape, polarity, pin-one, and value markings to connect the diagram with real hardware. [Source basis: PDF, pp. 22-23, 30-31; dual representation is a repository decision.]
- Progress from MOSFETs to inverters, gates, latches, registers, ALUs, and an educational CPU. [Source PDF, pp. 2, 13-18]
- Inject an open, short, leakage, or thermal failure and compare the result. [Source PDF, pp. 8-9]
- Use animated overlays without confusing current direction with literal electron motion. [Source PDF, pp. 30-31]

Success means the learner can reproduce the ten realistic-electronics MVP demonstrations before entering the CPU track. [Source PDF, p. 37]

## Educator or laboratory author

**Goal:** Create repeatable lessons, demonstrations, and assessments for school, college, university, or self-directed study. [Source PDF, p. 41]

Primary use cases:

- Publish a versioned circuit with instructions, locked reference values, stimuli, expected measurements, and hidden or visible testbenches.
- Choose which model fidelity and controls learners may change.
- Compare student results with golden circuits and declared tolerances.
- Explain the same block at component, transistor, gate, and functional levels. [Source PDF, pp. 16-17]
- Fork and reuse a public circuit or component library. [Source PDF, pp. 31-32, 42]

## Electronics or embedded engineer

**Goal:** Prototype and inspect analog, power, sensor, actuator, and mixed-signal behavior before or alongside hardware work.

Primary use cases:

- Run DC, transient, AC, noise, tolerance, Monte Carlo, and thermal analyses supported by selected models. [Source PDF, pp. 10-11]
- Inspect ESR, ESL, leakage, parasitics, breakdown, saturation, delay, and temperature dependencies. [Source PDF, pp. 5-8]
- Evaluate sensor, power-supply, motor-driver, MCU GPIO, PWM, ADC, and DAC interactions. [Source PDF, pp. 13, 28, 34]
- Select the actual package variant of an IC, inspect its pin map and orientation, and confirm that package customization does not change the electrical model.
- Import a model, inspect provenance and supported analyses, and compare it with a reference circuit.
- Diagnose non-convergence and invalid circuits instead of receiving a plausible but unsupported result. [Source PDF, pp. 9-10, 39-40]

## Digital hardware or FPGA designer

**Goal:** Build event-driven and RTL designs with timing, waveform, and mixed-signal context.

Primary use cases:

- Construct combinational and sequential logic with delays, `X`, `Z`, contention, glitches, setup/hold checks, clocks, and buses. [Source PDF, pp. 14-15, 33-34]
- Edit or import Verilog/SystemVerilog, run syntax checks and testbenches, compile an isolated model, and inspect waveforms and hierarchy. [Source PDF, pp. 18, 35]
- Wrap an RTL block with analog power, clock, sensor, ADC/DAC, or driver models. [Source PDF, pp. 21, 28, 34]
- Cache and reuse a compiled model when source and toolchain identity have not changed. [Source PDF, p. 30]

## Computer architecture researcher

**Goal:** Explore processor, memory, and accelerator tradeoffs at a feasible abstraction.

Primary use cases:

- Compare pipeline depth, in-order/out-of-order execution, branch prediction, cache size, memory latency, multicore, and power/performance tradeoffs. [Source PDF, pp. 15-18]
- Explore SRAM cells in detail while using timing or behavioral models for full memory. [Source PDF, pp. 18-20]
- Compare CPU RTL/cycle behavior with functional execution and architecture simulation. [Source PDF, pp. 18, 21, 36]
- Explore GPU SIMT, shader, cache, bandwidth, trace, and power behavior without a false full-transistor claim. [Source PDF, pp. 20, 36]

## Component model author or validator

**Goal:** Add trustworthy component families, presets, and imported models.

Primary use cases:

- Define pins, parameters, units, symbol, domains, supported analyses, fidelity tiers, temperature and failure behavior, import mappings, provenance, and limits.
- Create or reuse a parametric IC package, bind device pins explicitly, and validate body geometry, numbering, orientation marks, exposed pads, labels, and package-specific limits. [Source basis for component records and reusable libraries: PDF, pp. 26-27, 31-32; package fields are a repository decision.]
- Implement one model tier and concern at a time under an atomic task.
- Compare the model against analytical results, source data, an accepted external engine, or a measured reference.
- Publish accuracy limits and prevent release when the model has no golden validation. [Source PDF, p. 40]

## Collaborator or reviewer

**Goal:** Review and evolve a shared design without losing history or accepted edits.

Primary use cases:

- Co-edit a schematic, properties, annotations, and documentation.
- Comment on a stable revision, fork a project, and compare versions.
- Run a simulation against an immutable revision and share its result.
- Reconnect after offline editing and converge changes with visible conflict handling. [Source basis: PDF, pp. 31-32, 42]

## Hosted-service operator or organization administrator

**Goal:** Operate bounded, auditable local and cloud simulation services.

Primary use cases:

- Set project access, quotas, job priorities, retention, and allowed engines.
- Observe queue, worker, result-stream, storage, and cancellation health.
- Isolate untrusted imports and external-engine processes.
- Review license, provenance, and distribution constraints before enabling an engine or model source.
- Investigate resource exhaustion, failed cleanup, or unauthorized access without exposing private project content.

The source study places large SPICE, RTL compilation, architecture, GPU, Monte Carlo, and long thermal work on server workers and calls for queueing, streaming, storage, and checkpoint/resume. [Source PDF, pp. 25-26, 36]

## Authorization roles for hosted projects

The collaboration contract will define at least `Owner`, `Editor`, `Commenter`, and `Viewer` permissions. Simulation service roles such as operator or administrator MUST be separate from project-content roles and follow least privilege. See [Storage, Versioning, and Collaboration](architecture/STORAGE_VERSIONING_AND_COLLABORATION.md) and [Security, Privacy, and Sandboxing](architecture/SECURITY_PRIVACY_AND_SANDBOXING.md).
