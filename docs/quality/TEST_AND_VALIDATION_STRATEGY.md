# Test and Validation Strategy

## Purpose

This document defines the evidence required before any component, solver, interface, or release can be called correct. It turns the feasibility brief into a repeatable validation program rather than relying on visually plausible waveforms. The source brief explicitly identifies model accuracy, nonlinear convergence, browser memory, UI performance, and mixed-simulator synchronization as primary risks. [Source PDF, pp. 39-40]

Stable identifiers and the requirement/fixture test inventory are defined by the [Test Catalog](TEST_CATALOG.md) and [machine-readable test registry](test-registry.yaml). Atomic task test IDs follow the [Atomic Task Contract](../tasks/ATOMIC_TASK_CONTRACT.md).

## Quality principles

1. Applied Physics evidence follows principle -> equation -> numerical method -> model -> composed artifact -> physical validation; a plausible display is not evidence.
2. A symbol is not a simulation model, and a package is not a device, board, or system.
3. A converged answer is not automatically a correct answer.
4. Every result must identify its engine, engine version, exact model/dependency revisions, fidelity level, settings, seed, environment, evidence status, and limitations.
5. Every released component must have a golden circuit, expected results, tolerance, failure cases, provenance, validity range, and accuracy/uncertainty envelope.
6. Local and cloud execution must use the same normative request, resolved-definition, and result contracts.
7. Randomized analyses must be reproducible from a stored seed.
8. Accuracy claims apply only inside a documented operating envelope and cannot show false precision.
9. Differential simulator agreement is not a substitute for physical correlation when a physical claim is made.

## Evidence layers

| Layer | Purpose | Required evidence |
|---|---|---|
| Documentation conformance | Ensure the specification is complete | Links, schema examples, requirement/task/test traceability, registry counts |
| Unit and property testing | Verify equations and invariants | Analytical values, dimensional consistency, conservation checks, truth tables |
| Golden-circuit testing | Verify models in known topologies | Expected voltages, currents, timing, power, and temperature |
| Differential testing | Compare independent engines | Rust/WASM versus ngspice or another declared reference |
| Import conformance | Verify external formats | Valid, invalid, edge, and round-trip fixtures |
| Integration testing | Verify editor-to-engine behavior | Schematic -> netlist -> engine -> stream -> visualization |
| System testing | Verify complete workflows | Local, offline, cloud, collaboration, cancellation, and recovery |
| Performance testing | Enforce budgets | Latency, throughput, memory, frame rate, and main-thread responsiveness |
| Security testing | Contain untrusted content | Sandbox, quotas, parser abuse, authorization, and tenant isolation |
| Accessibility testing | Make the laboratory operable without pointer/color dependence | Keyboard, focus, screen-reader, contrast, and nonvisual waveform summaries |
| Visual/package conformance | Keep physical views recognizable and electrically correct | Golden renders, resolved package revision/parameters, concrete `DevicePackageBinding`, dimensions, orientation marks, color/label rules, and symbol-to-package pin equivalence |
| Schema and lineage conformance | Keep data-driven definitions scientifically and historically resolvable | Kinds, dimensions, immutable revisions, hashes, dependency DAG, reverse dependencies, provenance, trust, license, publication state, and principle-to-result lineage |
| Physical benchmark correlation | Bound real-world claims against measurements | Exact specimen/BOM, calibrated equipment, environment, procedure, immutable raw data, model revisions, error calculation, uncertainty budget, envelope, and limitations |

## Component release workflow

Every family and variant follows this state machine:

```mermaid
stateDiagram-v2
    [*] --> Planned
    Planned --> SymbolReady: symbol and pins reviewed
    SymbolReady --> ConnectivityReady: domain and net rules pass
    ConnectivityReady --> ModelReady: required fidelity model implemented
    ModelReady --> Validated: golden and differential tests pass
    Validated --> Released: documentation and provenance complete
    ModelReady --> Planned: model contract changes
    Validated --> ModelReady: regression or reference change
```

`Released` requires all fields in the component registry, coverage matrix, family specification, task cards, and validation records. Deferred research families remain visible but cannot be marked released.

## Model validation matrix

| Fidelity | Minimum validation |
|---|---|
| F0 Connectivity | Pin count/order, legal domains, net merging, disconnected and incompatible-domain diagnostics |
| F1 Ideal/equation | Analytical result, dimensional check, limiting cases, zero/extreme parameter behavior |
| F2 Behavioral/timing | Truth table or transfer function, delay and state transition tests, X/Z/contention behavior where digital |
| F3 Compact/macro | DC sweep, transient, AC where applicable, reference-engine comparison, convergence envelope |
| F4 Applied Physics/real-world | Non-ideal electrical effects, power/thermal balance, environment, manufacturing variation, aging, interconnect/source/instrument loading, limit crossing, each documented failure state, category uncertainty, and physical correlation where claimed |
| F5 Physical/research | Published or independently reproduced reference dataset and explicit research-only limitations |

## Mandatory failure suites

The regression corpus must include:

- Missing reference ground, floating input, isolated subcircuit, ideal voltage-source loop, ideal current-source cut set, shorted source, singular matrix, and inconsistent initial conditions.
- Non-convergence, iteration limit, timestep underflow, rejected step loop, NaN, infinity, numeric overflow, and waveform storage exhaustion.
- Digital X and Z propagation, multiple drivers, contention, fan-out overload, glitches, setup/hold violations, metastability indication, and clock-domain boundary errors.
- Analog-to-digital threshold ambiguity, hysteresis, supply collapse, output-current limit, loading, and scheduler events occurring at the same timestamp.
- Over-power, over-voltage, over-current, breakdown, thermal runaway, open, short, degraded, leakage-increase, and intermittent failures.
- Malformed archives, unsupported schema versions, failed migrations, missing model assets, storage quota exhaustion, and corrupted checkpoints.
- Worker timeout, cancellation, retry, worker crash, duplicate event delivery, out-of-order stream chunk, expired authorization, and cross-tenant access attempts.
- Invalid or missing dimensions, ambiguous constants, inverted validity ranges, dependency cycles, missing revisions, incompatible inheritance overrides, incomplete pin bindings, package-as-board type errors, mutable published revisions, and hard deletion of referenced records.
- Missing/expired calibration, incomplete physical-fixture metadata, raw-data digest mismatch, result outside model validity, false-precision formatting, unsupported scientific claims, and incomplete principle-to-result lineage.
- Arbitrary executable stored content, unknown executable capability, imported-model trust/license quarantine, direct engine/database coupling, unsafe guest migration, offline/cloud conflict, and unauthorized system-library publication.

## Test artifact requirements

Each test case records:

- Stable `TEST-*` ID and linked requirement/task/component IDs.
- Circuit or system fixture and `.eesim` schema version.
- Engine, model, and reference versions.
- Analysis settings, probes, tolerances, initial conditions, environment, and seed.
- Expected scalar values, waveform features, event ordering, thermal/failure outcomes, and permitted error.
- Human-readable reason for the tolerance and the source of reference data.
- Result status, execution date, environment fingerprint, and regression owner.
- For physical correlation: specimen count/identity, manufacturer ordering codes and packages, equipment/calibration, ambient/enclosure/airflow, immutable raw-data references, processing revision, error calculation, uncertainty components, correlation status, and evidence reviewer.

## Review gates

- Numerical-model changes require electronics/numerical review and regenerated golden evidence.
- Public contract changes require schema compatibility review and migration documentation.
- Physical appearance or package changes require golden visual review at fixed scales and pin-map equivalence tests against the [Device Package Binding Contract](../catalog/DEVICE_PACKAGE_BINDING_CONTRACT.md); appearance alone may never change electrical identity. `package_refs` and compatibility metadata are candidate inputs, not binding evidence.
- Third-party model updates require provenance and license review.
- Security-boundary changes require threat-model and sandbox review.
- Release candidates require the checklist in [Release Acceptance Checklists](./RELEASE_ACCEPTANCE_CHECKLISTS.md).

## Source basis

- Circuit equation and non-ideal model discussion: PDF pp. 3-11.
- Hybrid fidelity and abstraction switching: PDF pp. 13-28.
- Performance and validation risks: PDF pp. 29-30 and 39-40.
- Staged demonstrations and roadmap: PDF pp. 32-37.
