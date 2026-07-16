# Glossary

Terms in this glossary are normative where they define project-specific semantics.

| Term | Definition |
|---|---|
| Abstraction switching | Replacing a block's model with a more or less detailed representation while preserving declared boundary semantics. The source brief calls the overall idea hierarchical adaptive-fidelity simulation. [Source PDF, p. 16] |
| AC analysis | Small-signal frequency-domain analysis of gain, phase, impedance, bandwidth, and resonance. [Source PDF, pp. 10-11] |
| Accuracy envelope | The declared analyses, parameter range, reference, and maximum error within which a model is validated. |
| Applied Physics First | The normative progression from physical principles through mathematical models, engineering equations, numerical algorithms, reusable models, devices, circuits/boards, complete systems, and experimental validation. Physics informs every fidelity tier. |
| Analog/digital adapter | A boundary model that maps analog voltage to digital logic using thresholds/hysteresis or maps a digital output to non-ideal analog drive. [Source PDF, p. 28] |
| Basic component | A production component variant explicitly classified in the registry for the beginner or Realistic Electronics MVP experience. Every released basic component requires both an electrically clear schematic symbol and a recognizable physical representation. |
| Canonical family | A stable component concept in the registry, independent of manufacturer SKU or visual preset. |
| Checkpoint | A versioned, engine-specific state from which a supported simulation job may resume. [Source PDF, pp. 27-28, 36] |
| Component variant | A built-in preset or structural variation of a canonical family with a stable ID and shared or specialized models. |
| Composite model | A versioned model whose behavior is composed from exact primitive, composite, behavioral, or adapter revisions through an acyclic dependency graph. |
| CRDT | Conflict-free Replicated Data Type; the selected foundation for convergent concurrent editing and offline merge. |
| DC operating point | A steady-state solution reporting supported node voltages, branch currents, and component power. [Source PDF, p. 10] |
| Deterministic scheduler | The global integer-time coordinator that orders analog steps, digital events, clocks, thermal updates, RTL/external boundaries, and checkpoints reproducibly. [Source PDF, pp. 27-28, 40] |
| Digital event | A timestamped change to digital state or timing condition processed by the event-driven engine. [Source PDF, pp. 15, 27-29] |
| Drive strength | A digital output's ability to drive a net, used with state and impedance to resolve contention and loading. |
| `.eesim` | The versioned, portable archive format for projects, including manifest, hierarchy, component references, models, stimuli, testbenches, documentation, and assets. |
| Electrothermal coupling | Bidirectional interaction in which electrical power changes temperature and temperature changes electrical behavior. [Source PDF, pp. 5, 8-11] |
| Engine adapter | A lifecycle boundary that discovers capabilities and validates, prepares, runs, streams, pauses, checkpoints, resumes, cancels, and disposes a simulation engine. |
| External engine | A simulator, compiler, emulator, or analyzer invoked outside the Apache core, normally in an isolated worker process. |
| Generic device | A reusable device or family definition that binds models, interfaces, and common parameters without claiming a specific manufacturer ordering code. |
| F0 | Connectivity-only fidelity: topology, pins, nets, domains, and structural checks without behavioral simulation. |
| F1 | Ideal/equation fidelity: analytical or simplified electrical behavior without full non-ideal effects. |
| F2 | Behavioral/digital-timing fidelity: event, switch, timing, or functional behavior with declared delays and states. |
| F3 | SPICE compact or macro-model fidelity: nonlinear circuit behavior validated against a declared SPICE/reference envelope. |
| F4 | Electrothermal, tolerance, and failure fidelity: coupled temperature, variation, ratings, degradation, or failure behavior. |
| F5 | Physical/TCAD research fidelity: device geometry, fields, carriers, doping, and related research physics, normally backend/HPC only. [Source PDF, pp. 3-4, 14] |
| Failure injection | A controlled educational or validation action that forces a declared failure mode such as open, short, drift, leakage, intermittent behavior, or breakdown. [Source PDF, p. 9] |
| Fidelity | The declared level of physical, electrical, timing, thermal, or functional detail used to answer a simulation question. [Source PDF, pp. 3-4, 13-16] |
| Golden circuit | A versioned reference project with known expected results, tolerances, and provenance used to validate a model or engine. |
| Heavy job | Work that exceeds local capability or policy and requires a bounded server worker, such as large SPICE, RTL compilation, long thermal/Monte Carlo, architecture, or GPU simulation. [Source PDF, pp. 25-26, 36] |
| Hierarchical project | A project composed of nested blocks with explicit ports, stable identity, and navigable internal implementations. [Source PDF, pp. 2, 16, 29] |
| ISA simulation | Functional instruction execution or machine emulation without claiming transistor-level physical fidelity. [Source PDF, p. 16] |
| Logic `X` | Unknown or indeterminate digital state, including unresolved threshold or conflicting uncertainty. [Source PDF, pp. 14, 28, 34] |
| Logic `Z` | High-impedance digital state in which a driver does not actively drive the net. [Source PDF, p. 34] |
| MNA | Modified Nodal Analysis; the matrix formulation used to solve node voltages and selected branch currents. [Source PDF, p. 9] |
| Model binding | The association between a component variant, fidelity tier, supported analysis, and executable model implementation. |
| Model lineage | The bidirectional, immutable chain from physical principle, model and dependencies through device/package/board/system/project/execution revisions to validation and result artifacts. |
| Model registry | The versioned inventory of actually enumerated physics, primitive, composite, behavioral, and external-adapter models; it is separate from the 162-family/502-variant component registry. |
| Model provenance | Source, author or organization, version, retrieval data, checksum, license, modifications, and validation evidence for a model. |
| Monte Carlo analysis | Repeated seeded simulation using declared parameter distributions to estimate variation or yield. [Source PDF, p. 11] |
| Non-ideal behavior | Real effects such as tolerance, leakage, parasitics, noise, saturation, breakdown, delay, and temperature dependence. [Source PDF, pp. 1, 3, 5-8] |
| Offline-capable | Editing and supported local simulation that do not require network connectivity after the required client assets are available. [Source PDF, pp. 25-26, 31-32] |
| Package definition | A reusable, versioned description of an IC or discrete-device body, leads or pads, pin numbering, pitch, orientation marks, labels, dimensions, and optional footprint metadata; it is separate from device function and electrical behavior. |
| Package designer | The parametric editor for creating and validating package definitions and explicit device-to-package pin mappings. |
| Board or module | A versioned composition of exact devices, bindings, connectors, interconnects, assets, and optional firmware with declared ports; it is not a package. |
| Library Service | The storage-independent domain boundary that validates, revisions, searches, publishes, resolves dependencies, and produces an immutable engine-ready definition bundle. |
| Primitive model | A smallest governed simulation behavior implemented by an approved equation or kernel and used directly or by composite models. |
| Physical representation | An original, scalable rendering that resembles a real component body and its observable markings while remaining separate from the schematic symbol, electrical model, and dimensional-accuracy claims. [Source basis: PDF, pp. 22-23, 30-31] |
| Project revision | An immutable content identity against which a simulation job, comment, comparison, or release result is bound. |
| System | A versioned composition of boards, devices, subsystems, software, stimuli, and environments through explicit interfaces. |
| Vendor device | A manufacturer or ordering-code revision that inherits an exact generic-device revision and adds bounded parameter overrides, package/pin binding, metadata, provenance, license, and validation evidence. |
| Realistic Electronics MVP | The first production gate containing realistic browser electronics and eleven canonical demonstrations; CPU and GPU stages remain blocked until it passes. [Source PDF, p. 37] |
| Release gate | A mandatory, evidence-based entry/exit checkpoint that prevents later product stages from beginning prematurely. |
| SI base units | Canonical internal quantities represented in unprefixed SI units; display prefixes are a presentation concern. |
| SPICE | A family of circuit simulation formats and engines used for detailed analog and transistor-level analysis. [Source PDF, pp. 3, 14, 21-22] |
| Stable ID | A permanent machine-readable identifier that is never reused for a different requirement, component, variant, task, test, gate, or decision. |
| Switch-level model | A transistor abstraction using switch states such as off, weak on, strong on, or unknown instead of solving full analog device equations. [Source PDF, pp. 14-15] |
| Transient analysis | Time-domain simulation of charging, oscillation, switching, pulses, startup, and related dynamic behavior. [Source PDF, p. 10] |
| Worker | A browser Worker or isolated server process that performs bounded work outside the main UI thread or API process. [Source PDF, pp. 23, 25-26] |
| Waveform chunk | A bounded, ordered segment of time-series result data suitable for streaming, storage, decimation, and selective retention. [Source basis: PDF, pp. 23, 31, 39] |
| WebGPU gate | The rule that a compute or rendering workload may use WebGPU only after a reproducible benchmark demonstrates a meaningful benefit without violating correctness or compatibility. [Source PDF, pp. 24-25] |

## Naming rules

- Use `component family` for the stable concept and `component variant` for a preset or variation.
- Use `model` for an executable behavior and `symbol` for its schematic representation.
- Use `physical representation` for the recognizable component body and `package definition` for reusable body and pin geometry; neither term means an electrical model.
- Use `project revision` for immutable content and `workspace` for a mutable collaboration context.
- Use `simulation result` only for a terminal, versioned output; in-progress data are events or waveform chunks.
- Do not use `realistic` without naming the fidelity, accuracy envelope, and known limitations.
