# Start Here

This is the canonical navigation page for contributors, reviewers, maintainers, and AI agents.

## What this project is

The product is a browser-based, **Applied Physics-driven, hierarchical, multi-fidelity electronics and computer simulation platform**. It is planned to combine validated physical principles, mathematical models, engineering equations, numerical algorithms, reusable models, devices, circuits, boards, and systems with switch, event, RTL, architecture, and ISA abstractions. Users can move from a component to a complete educational computer without pretending that a modern processor can be simulated transistor-by-transistor in a browser. The legacy citation records planning origin only; it is not confirmation that the technical claims are correct or implemented. [Source PDF, pp. 1-4, 12-16, 42-44]

The [Source and Evidence Policy](SOURCE_AND_EVIDENCE_POLICY.md) is normative for classifying every citation and release claim. In particular, all `[Source PDF]` references are unverified source-brief context, never confirmed technical evidence.

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
3. [Source and Evidence Policy](SOURCE_AND_EVIDENCE_POLICY.md)
4. [Product Requirements](PRODUCT_REQUIREMENTS.md)
5. [System Architecture](architecture/SYSTEM_ARCHITECTURE.md)
6. [Applied Physics and Real-World Fidelity](architecture/APPLIED_PHYSICS_AND_REAL_WORLD_FIDELITY.md)
7. [Hierarchical Model and Library Architecture](architecture/HIERARCHICAL_MODEL_AND_LIBRARY_ARCHITECTURE.md)
8. [Data-Driven Library and Storage Architecture](architecture/DATA_DRIVEN_LIBRARY_AND_STORAGE_ARCHITECTURE.md)
9. [Component Taxonomy](catalog/COMPONENT_TAXONOMY.md)
10. [Master Roadmap](planning/MASTER_ROADMAP.md)
11. [Release Gates](planning/RELEASE_GATES.md)
12. [Test and Validation Strategy](quality/TEST_AND_VALIDATION_STRATEGY.md)
13. [Atomic Task Index](tasks/TASK_INDEX.md)

The repository-adopted delivery order is to establish the editor and basic solver, add semiconductor and non-ideal behavior, add event-driven digital and mixed-signal simulation, pass the realistic-electronics MVP, then progress to educational CPUs, RTL, full computers, architecture, GPU, and cloud/HPC capability. The cited source-brief pages record its planning origin but do not validate the sequence's technical assumptions or any release result. [Source PDF, pp. 32-37, 43-44]

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
| [ADR-0011](decisions/ADR-0011.md) | Applied Physics First |
| [ADR-0012](decisions/ADR-0012.md) | R4 Applied Physics and Real-World Fidelity gate |
| [ADR-0013](decisions/ADR-0013.md) | Hierarchical reusable model and library taxonomy |
| [ADR-0014](decisions/ADR-0014.md) | Model, symbol, package, pin, board, and system orthogonality |
| [ADR-0015](decisions/ADR-0015.md) | Data-driven Library Service boundary |
| [ADR-0016](decisions/ADR-0016.md) | Mixed storage responsibilities |
| [ADR-0017](decisions/ADR-0017.md) | Minimal Google OIDC and personal project persistence |
| [ADR-0018](decisions/ADR-0018.md) | Immutable revisions and dependency-safe operations |
| [ADR-0019](decisions/ADR-0019.md) | Declarative model and executable-kernel boundary |
| [ADR-0020](decisions/ADR-0020.md) | Generic-device and vendor-variant inheritance |

## Contract index

- Architecture: [system](architecture/SYSTEM_ARCHITECTURE.md), [Applied Physics and real-world fidelity](architecture/APPLIED_PHYSICS_AND_REAL_WORLD_FIDELITY.md), [hierarchical model and library](architecture/HIERARCHICAL_MODEL_AND_LIBRARY_ARCHITECTURE.md), [data-driven library and storage](architecture/DATA_DRIVEN_LIBRARY_AND_STORAGE_ARCHITECTURE.md), [editor and visualization](architecture/SCHEMATIC_EDITOR_AND_VISUALIZATION.md), [simulation engine](architecture/SIMULATION_ENGINE.md), [co-simulation](architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md), [local/cloud workers](architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md)
- Public data: [project format](architecture/PROJECT_FILE_FORMAT.md), [API and worker protocols](architecture/API_AND_WORKER_PROTOCOLS.md), [storage and collaboration](architecture/STORAGE_VERSIONING_AND_COLLABORATION.md)
- Cross-cutting architecture: [security and sandboxing](architecture/SECURITY_PRIVACY_AND_SANDBOXING.md), [performance/browser/accessibility/i18n](architecture/PERFORMANCE_BROWSER_ACCESSIBILITY_AND_I18N.md), [deployment/operations/observability](architecture/DEPLOYMENT_OPERATIONS_AND_OBSERVABILITY.md), [open-source and third-party licenses](architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md)
- Components and models: [component registry](catalog/component-registry.yaml), [scientific model registry](catalog/model-registry.yaml), [pin-profile guide](catalog/PIN_PROFILE_CATALOG.md), [normative variant pin profiles](catalog/variant-pin-profiles.yaml), [variant semantic contract](catalog/VARIANT_SEMANTIC_PROFILE_CONTRACT.md), [normative variant semantic profiles](catalog/variant-semantic-profiles.yaml), [parameter-definition guide](catalog/PARAMETER_DEFINITION_CATALOG.md), [normalized parameters](catalog/parameter-definitions.yaml), [coverage matrix](catalog/COMPONENT_COVERAGE_MATRIX.md), [model contract](catalog/COMPONENT_MODEL_CONTRACT.md), [import/export](catalog/MODEL_IMPORT_EXPORT_FORMATS.md), [physical appearance and package contract](catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md), [device/package binding contract](catalog/DEVICE_PACKAGE_BINDING_CONTRACT.md), [package registry](catalog/package-registry.yaml), and [product requirements](PRODUCT_REQUIREMENTS.md#physical-representation-and-integrated-circuit-packages)
- Quality: [validation](quality/TEST_AND_VALIDATION_STRATEGY.md), [physical benchmark/correlation contract](quality/PHYSICAL_BENCHMARK_AND_CORRELATION_CONTRACT.md), [test catalog](quality/TEST_CATALOG.md), [golden circuits](quality/GOLDEN_REFERENCE_CIRCUITS.md), [accuracy](quality/NUMERICAL_ACCURACY_TARGETS.md), [performance](quality/PERFORMANCE_BENCHMARKS.md), [traceability](quality/REQUIREMENTS_TRACEABILITY_MATRIX.md)
- Work planning: [atomic task contract](tasks/ATOMIC_TASK_CONTRACT.md), [task index](tasks/TASK_INDEX.md), and [release gates](planning/RELEASE_GATES.md)
- Governance: [source and evidence policy](SOURCE_AND_EVIDENCE_POLICY.md), [contributing](../CONTRIBUTING.md), [agent contract](../AGENTS.md), [security](../SECURITY.md), [license policy](architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md)

## Selecting work

Open [tasks/TASK_INDEX.md](tasks/TASK_INDEX.md) and select one `Ready` task. Confirm dependencies, permitted files, public contracts, acceptance tests, and required documentation updates. Complete the work according to [AGENTS.md](../AGENTS.md); do not take a broad epic as an executable task.

## Source citation convention

The principal planning brief is *Web-based Electronics and Computer Simulation Platform*, 44 pages. `[Source PDF, p. N]`, `[Source PDF, pp. N-M]`, and `[Source basis: PDF, ...]` refer to its numbered pages only as legacy origin/scope metadata. These citations are classified as `source_brief_unverified` by the [Source and Evidence Policy](SOURCE_AND_EVIDENCE_POLICY.md). They are never sufficient support for equations, standards, accuracy, licenses, security, implementation truth, test results, or release decisions. Requirements become normative through repository adoption, not through the PDF. Applicable official/primary technical sources or physical evidence and current project results are required before technical tasks become `Ready` and artifacts become `Validated` or `Released`.
