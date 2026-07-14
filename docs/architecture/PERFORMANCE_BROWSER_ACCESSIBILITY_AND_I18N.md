# Performance, Browser, Accessibility, and Internationalization

Status: Normative  
Related: [Schematic Editor and Visualization](./SCHEMATIC_EDITOR_AND_VISUALIZATION.md), [Local, Cloud, and Worker Architecture](./LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md), [Performance Benchmarks](../quality/PERFORMANCE_BENCHMARKS.md)

## 1. Purpose

This document defines measurable browser responsiveness, capacity, compatibility, accessible interaction, and localization requirements. The source PDF requires a browser schematic editor, separated Workers, Canvas/WebGL rendering, waveform/heat visualization, large-diagram optimization, and progressive user modes; it explicitly identifies browser memory and UI performance as risks. [Source PDF, pp. 22-25, 29-31, 38-40]

## 2. Reference workloads and evidence

Performance claims MUST name:

- benchmark fixture and immutable project/catalog/package digest;
- hardware, available memory, OS, browser and exact browser version;
- cold or warm state, power mode, device-pixel ratio, viewport, renderer, and theme;
- single-threaded or threaded WASM artifact and build digest;
- sample count, trial count, median, p95, maximum, peak memory, and failures;
- whether the run was local, cloud, or hybrid.

The reference desktop classes and benchmark methodology live in [Performance Benchmarks](../quality/PERFORMANCE_BENCHMARKS.md). Results from a faster development machine MUST NOT be represented as the baseline.

## 3. MVP budgets

| Interaction or workload | Desktop-Baseline requirement |
|---|---:|
| Open 500 components and 1,000 nets | at most 2 seconds |
| Reference DC operating point | at most 1 second |
| Reference transient with 100,000 retained samples | at most 5 seconds |
| Schematic pan/zoom while idle | at least 50 FPS p95 |
| Render/pan 500 realistic physical component bodies | at least 45 FPS p95 |
| Toggle schematic/physical view for 500 components | at most 500 ms p95; unchanged topology |
| Waveform interaction with 100,000 points | at least 45 FPS p95 |
| Property edit to visible acknowledgement | at most 100 ms p95 |
| Local autosave acknowledgement | at most 250 ms p95 |
| Canonical project archive round trip | at most 3 seconds and semantic equality |
| Simulation-caused main-thread task | no task over 100 ms |

The product targets 50 FPS for normal interaction. The 45 FPS physical/waveform floors acknowledge heavier visual scenes and are release minimums, not optimization ceilings.

## 4. Main-thread and Worker budgets

~~~mermaid
flowchart LR
    Input["Pointer/keyboard input"] --> Main["Main thread: command and accessible feedback"]
    Main --> Domain["Domain/render projection Worker"]
    Domain --> Frame["Canvas/WebGL frame data"]
    Main --> Solver["Analog/digital Workers"]
    Solver --> Wave["Waveform Worker"]
    Wave --> Summary["Decimated display and semantic summary"]
    Frame --> Main
    Summary --> Main
~~~

- The main thread owns input, focus, accessible DOM, and frame submission; it MUST NOT solve circuits, parse large archives, compile models, or generate unbounded package geometry.
- Interaction feedback SHOULD begin in the next animation frame and MUST meet the property-edit budget.
- Worker command batches, transfer buffers, and update frequencies are bounded. Large arrays are transferred, not cloned.
- Expensive domain validation MAY be incremental; stale diagnostics MUST be visibly marked until the corresponding revision completes.
- Cancellation and memory-pressure messages have priority over ordinary progress.
- Background tabs MAY throttle presentation but MUST preserve simulation correctness or pause at a declared safe point with visible status.

## 5. Rendering and level of detail

The renderer uses viewport culling, spatial indexing, cached geometry/glyphs, batched draw submission, and level of detail. [Source PDF, pp. 29-30, 39-40]

### 5.1 Schematic view

- At distant zoom, preserve components, net continuity, junctions, selection, and blocking diagnostics before decorative detail.
- Pin names and values appear only when legible or focused.
- Hit testing uses a screen-space tolerance and stable IDs.

### 5.2 Realistic physical and breadboard view

- Package bodies are generated once per package-version/parameter/render-profile key and reused as immutable geometry.
- At distant zoom, leads/pins, body outline, orientation, polarity, selection, and electrical connections remain recognizable; fine texture, material shading, and printed secondary text may be omitted.
- Resistor color bands, diode cathode bands, capacitor/LED polarity, transistor face/orientation, package pin 1/A1/notch, and connector keys MUST have non-color and textual equivalents.
- Nominal physical dimensions determine placement/collision. Any render exaggeration is presentation metadata and MUST NOT alter scale, electrical attachment, or package pin coordinates.
- Switching views reuses domain/net state and package caches; it MUST NOT rebuild the simulation graph.

### 5.3 Renderer fallback

Canvas 2D is required. WebGL2 is the scale path after feature detection. Loss of a WebGL context falls back to Canvas 2D or a recreated context without project loss. SVG is deterministic export/accessibility representation. WebGPU is never a correctness dependency.

## 6. Waveform and memory policy

- Retention is explicitly bounded by channels, samples/events, bytes, and time span.
- Raw samples are chunked and immutable; display levels use multiresolution decimation.
- Ring buffers MAY discard old non-retained interactive data only after showing the policy.
- Selective probing is the default for large projects.
- Data may spill to IndexedDB or object storage by policy; the UI displays storage and completeness.
- A gap, dropped chunk, non-finite value, or partial result remains visible.
- Measurements use raw or declared derived data, never an undisclosed display decimation.
- Approaching memory limits triggers reduction/export/cloud choices before failure.

## 7. WebGPU admission

A workload may use WebGPU only when:

1. it has a CPU/WASM correctness reference;
2. supported browsers produce results within declared numeric tolerance;
3. end-to-end median and p95 improve after transfer/compilation overhead;
4. peak memory and energy/thermal behavior are recorded;
5. device loss and unsupported hardware fall back cleanly;
6. the benchmark is repeatable in the release evidence.

Candidates include independent Monte Carlo runs, thermal grids, waveform filtering, visualization, and batched component evaluation. Frequently changing sparse matrices, branch-heavy Newton iteration, and small sequential circuits are not presumed suitable. [Source PDF, pp. 24-25]

## 8. Supported browsers

Production supports the latest two stable desktop releases of Chrome, Edge, Firefox, and Safari at release test time.

Required matrix:

- Canvas 2D baseline on every browser;
- WebGL2 path where available and conformant;
- single-threaded WASM Worker path everywhere in the supported matrix;
- threaded WASM path only where SharedArrayBuffer and cross-origin isolation pass;
- IndexedDB persistence, Service Worker/offline shell, file import/export, SSE, WebSocket, and accessibility tests;
- reduced-motion, forced-colors/high-contrast where the platform exposes it, zoom, and common screen readers.

Unsupported capabilities produce a specific fallback/status, not a blank or broken editor. Mobile editing is outside the MVP. A later read-only mobile view requires its own release evidence.

## 9. Accessibility architecture

The target is WCAG 2.2 AA for all production user-facing paths.

### 9.1 Semantic model

The visual canvas has a synchronized, virtualized semantic tree:

~~~mermaid
flowchart TD
    Project --> Sheet
    Sheet --> Block
    Block --> Component
    Component --> Symbol["Schematic representation"]
    Component --> Physical["Physical/package representation"]
    Component --> Pin
    Pin --> Net
    Component --> Diagnostic
    Sheet --> Instrument
~~~

Both views expose the same component, pin, net, parameter, model, and simulation identity. A physical representation adds package name, nominal body dimensions, orientation mark, package-pin number, and pin-map relation; it MUST NOT create duplicate focus objects for the same domain component unless the user explicitly opens both views side by side.

### 9.2 Keyboard and focus

- Every placement, selection, move, rotate, connect, disconnect, property, hierarchy, package selection, custom-package parameter, simulation, probe, measurement, export, and collaboration action is keyboard-operable.
- Focus is stable by entity ID across rerenders, view switching, Worker results, and remote edits.
- The package designer offers logical field order, numeric text entry, step controls, validation summary, and an orientation/pin-order preview describable without vision.
- Canvas shortcuts have discoverable command-search equivalents and do not trap keyboard focus.
- Deleting a focused entity moves focus deterministically and announces the change.

### 9.3 Non-visual and non-color information

- Voltage, temperature, current direction/magnitude, logic, warnings, failures, and selection use text, shape/pattern, and accessible summaries in addition to color.
- Resistor color bands expose decoded resistance/tolerance text.
- Polarity and pin-1/A1 indicators use geometry and explicit labels, not color alone.
- Waveforms expose trace names, units, extrema, transitions, cursor values, gaps, and diagnostics.
- Physical realism never overrides readable contrast or minimum target sizes; a high-contrast semantic style remains available.
- Motion honors reduced-motion preferences; flashing stays within safe thresholds.

## 10. Internationalization and units

Repository identifiers and documentation are English. The product launches with English UI and is localization-ready.

- All user-facing prose uses localization keys, not string concatenation.
- Messages separate stable machine codes, localization keys, and typed parameters.
- Plural, list, date/time, number, and unit display use locale-aware formatters.
- Internal physical values remain SI base units; locale affects display only.
- Decimal parsing follows the active locale but stores an unambiguous normalized value and shows the interpreted unit before commit.
- Technical identifiers, reference designators, net names, model names, and file paths are not translated.
- Layout supports text expansion and bidirectional scripts; diagrams and pin numbering retain defined electrical orientation semantics.
- Search indexes canonical English names, stable IDs, aliases, and localized names without changing identity.
- Export may include selected localized labels, but the canonical project remains language-neutral through keys and values.

## 11. Performance-accessibility interaction

Virtualization MUST NOT remove the focused object, active diagnostic, live-region announcement, or search result from the semantic tree. Frame-rate optimization cannot hide electrically meaningful pins or rely on color. Accessible summaries MAY be computed in a Worker, but urgent state changes and errors are announced promptly and in bounded form.

A reduced-effects mode may disable shadows, textures, particles, and heat animation while preserving bodies, leads, orientation, values, connectivity, and simulation data.

## 12. Failure behavior

| Failure | Required behavior |
|---|---|
| Out-of-memory risk | stop growth, preserve project, offer retention/cache/cloud choices |
| WebGL/WebGPU device loss | fall back without semantic or project loss |
| Package geometry too complex | reject/bound geometry and show validation; do not freeze UI |
| Font unavailable | use measured fallback and mark visual-regression environment mismatch |
| Worker crash | UI remains operable, announces failed operation, offers safe restart |
| IndexedDB quota | preserve unsynchronized state in memory where possible and prompt export/cleanup |
| Unsupported browser capability | select documented fallback and state limitation |
| Localization key missing | safe English fallback plus development diagnostic; never show raw unsafe payload |
| Accessibility projection stale | mark busy, retain focus, then atomically replace with matching revision |

## 13. Acceptance criteria

1. Every supported browser passes the required editor, persistence, Worker, SSE, WebSocket, and export matrix.
2. Reference workloads meet the published budgets with current reproducible evidence.
3. Threaded and single-threaded WASM paths produce equivalent logical results.
4. Keyboard-only and screen-reader users can build, inspect, simulate, measure, switch views, bind a package, and correct a pin-map error.
5. Axial/radial basics, LED/diode/transistor bodies, and DIP/SOIC/QFP/QFN/BGA fixtures remain recognizable at declared scales and in high contrast.
6. View switching preserves focus, component identity, topology, parameters, model state, and results.
7. Every color/polarity/orientation/logic/heat signal has a non-color textual or geometric equivalent.
8. WebGPU remains disabled until its workload-specific evidence passes.

## 14. Source record

Frontend rendering and Workers are grounded in the feasibility source. [Source PDF, pp. 22-25] Optimization and large-diagram controls address its performance plan and recorded risks. [Source PDF, pp. 29-30, 39-40] User modes and visualizations follow its interaction plan. [Source PDF, pp. 30-31] Exact budgets, browser matrix, WCAG target, localization contract, realistic physical/package performance, and dual-view accessibility are repository decisions supporting REQ-033, REQ-034, REQ-037, and REQ-038.
