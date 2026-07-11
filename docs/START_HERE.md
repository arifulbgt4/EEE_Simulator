# Start Here

This is the canonical navigation page for contributors, reviewers, maintainers, and AI agents.

## What this project is

The product is a browser-based, hierarchical, multi-fidelity electronics and computer simulation platform. It combines detailed circuit physics with switch, event, RTL, architecture, and ISA abstractions so users can move from a component to a complete educational computer without pretending that a modern processor can be simulated transistor-by-transistor in a browser. [Source PDF, pp. 1-4, 12-16, 42-44]

The documentation foundation is normative. When documents disagree, use this precedence order:

1. Accepted Architecture Decision Records (ADRs)
2. [Product requirements](PRODUCT_REQUIREMENTS.md)
3. Public architecture, format, API, and component-model contracts
4. Release gates and acceptance checklists
5. Atomic task cards
6. Explanatory guides and examples

A later ADR may explicitly supersede an earlier ADR. Otherwise, do not resolve contradictions by silently choosing a preferred document.

## First reading path

Read these documents before selecting implementation work:

1. [Project Charter](PROJECT_CHARTER.md)
2. [Scope, Success, and Non-Goals](SCOPE_SUCCESS_AND_NON_GOALS.md)
3. [Product Requirements](PRODUCT_REQUIREMENTS.md)
4. [System Architecture](architecture/SYSTEM_ARCHITECTURE.md)
5. [Component Taxonomy](catalog/COMPONENT_TAXONOMY.md)
6. [Master Roadmap](planning/MASTER_ROADMAP.md)
7. [Release Gates](planning/RELEASE_GATES.md)
8. [Test and Validation Strategy](quality/TEST_AND_VALIDATION_STRATEGY.md)
9. [Atomic Task Index](tasks/TASK_INDEX.md)

The delivery order follows the source study: establish the editor and basic solver, add semiconductor and non-ideal behavior, add event-driven digital and mixed-signal simulation, pass the realistic-electronics MVP, then progress to educational CPUs, RTL, full computers, architecture, GPU, and cloud/HPC capability. [Source PDF, pp. 32-37, 43-44]

## Decision index

| ADR | Locked decision |
|---|---|
| [ADR-0001](decisions/ADR-0001.md) | Hierarchical multi-fidelity product vision |
| [ADR-0002](decisions/ADR-0002.md) | Next.js/React, TypeScript, and Rust/WebAssembly core |
| [ADR-0003](decisions/ADR-0003.md) | Local-first execution and cloud worker split |
| [ADR-0004](decisions/ADR-0004.md) | Versioned `.eesim` project format |
| [ADR-0005](decisions/ADR-0005.md) | Fidelity levels F0 through F5 |
| [ADR-0006](decisions/ADR-0006.md) | Deterministic timestamped scheduler |
| [ADR-0007](decisions/ADR-0007.md) | Canvas/WebGL2 rendering and benchmark-gated WebGPU |
| [ADR-0008](decisions/ADR-0008.md) | External engine process isolation |
| [ADR-0009](decisions/ADR-0009.md) | CRDT-based collaboration |
| [ADR-0010](decisions/ADR-0010.md) | Apache-2.0 open-source core |

## Contract index

- Architecture: [system](architecture/SYSTEM_ARCHITECTURE.md), [simulation engine](architecture/SIMULATION_ENGINE.md), [co-simulation](architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md), [workers](architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md)
- Public data: [project format](architecture/PROJECT_FILE_FORMAT.md), [API and worker protocols](architecture/API_AND_WORKER_PROTOCOLS.md), [storage and collaboration](architecture/STORAGE_VERSIONING_AND_COLLABORATION.md)
- Components: [registry](catalog/component-registry.yaml), [coverage matrix](catalog/COMPONENT_COVERAGE_MATRIX.md), [model contract](catalog/COMPONENT_MODEL_CONTRACT.md), [import/export](catalog/MODEL_IMPORT_EXPORT_FORMATS.md), and [physical representation and package requirements](PRODUCT_REQUIREMENTS.md#physical-representation-and-integrated-circuit-packages)
- Quality: [validation](quality/TEST_AND_VALIDATION_STRATEGY.md), [golden circuits](quality/GOLDEN_REFERENCE_CIRCUITS.md), [accuracy](quality/NUMERICAL_ACCURACY_TARGETS.md), [performance](quality/PERFORMANCE_BENCHMARKS.md), [traceability](quality/REQUIREMENTS_TRACEABILITY_MATRIX.md)
- Governance: [contributing](../CONTRIBUTING.md), [agent contract](../AGENTS.md), [security](../SECURITY.md), [license policy](architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md)

## Selecting work

Open [tasks/TASK_INDEX.md](tasks/TASK_INDEX.md) and select one `Ready` task. Confirm dependencies, permitted files, public contracts, acceptance tests, and required documentation updates. Complete the work according to [AGENTS.md](../AGENTS.md); do not take a broad epic as an executable task.

## Source citation convention

The principal brief is *Web-based Electronics and Computer Simulation Platform*, 44 pages. `[Source PDF, p. N]` and `[Source PDF, pp. N-M]` refer to its numbered PDF pages. Requirements derived from that brief include page references. Product decisions added during documentation planning are labeled as repository decisions rather than attributed to the brief.
