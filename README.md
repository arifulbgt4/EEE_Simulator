# Web-Based Electronics and Computer Simulation Platform

EEE Simulator is a browser-based, **Applied Physics-driven, hierarchical, multi-fidelity electronics and computer simulation platform** that transforms validated physical principles into mathematical models, engineering equations, numerical algorithms, reusable component models, realistic circuit simulations, integrated devices, educational processors, and complete computer systems.

The platform is intentionally not a promise to simulate every transistor in a modern CPU, GPU, or RAM device at full electrical and thermal fidelity in one browser tab. It combines detailed circuit simulation where scale permits with switch-level, event-driven, RTL, architecture, and ISA-level models where higher abstraction is necessary. This is the core feasibility conclusion of the source study. [Source PDF, pp. 1-4, 12-16, 43-44]

## Product direction

The normative development chain is:

```text
Physical Principles -> Mathematical Models -> Engineering Equations -> Numerical Algorithms
-> Primitive Models -> Composite Models -> Library Devices -> Circuits and Boards
-> Complete Systems -> Experimental Validation
```

Applied Physics informs every fidelity tier. R4 does not introduce physics for the first time; it applies real-world non-ideal, electrothermal, environmental, manufacturing, parasitic, uncertainty, aging, interconnection, source, instrument, and failure behavior to the foundations established earlier.

The first production target is the **Realistic Electronics MVP**: a visual schematic editor with voltage/current measurement, transient waveforms, non-ideal component behavior, heating, tolerance, leakage, failure indication, basic logic, reusable subcircuits, a WebAssembly simulation engine, and Worker-based execution. Released basic components also receive recognizable physical representations, and ICs use reusable, independently customizable package definitions with explicit pin mappings. CPU, GPU, and full-computer capabilities follow only after this gate succeeds. [Source basis: PDF, pp. 22-23, 26-27, 30-37; the representation and package contracts are repository decisions.]

The long-term learning path is:

```text
Component -> Circuit -> Logic -> CPU block -> Small CPU -> Small computer -> Architecture platform
```

This staged path is the source study's recommended response to numerical scale, browser memory, UI performance, synchronization, model accuracy, and scope risk. [Source PDF, pp. 39-41]

## Locked technical direction

- Next.js/React and TypeScript for the web product.
- Canvas 2D as the default editor renderer, WebGL2 for scale and visualization, SVG for standards-friendly export, and WebGPU only for benchmark-proven workloads.
- A Rust simulation core compiled to WebAssembly, with simulation and waveform work off the main UI thread.
- Small and interactive work runs locally first; large SPICE, RTL compilation, Monte Carlo, thermal, architecture, and GPU jobs run in isolated server workers. [Source PDF, pp. 22-26]
- A deterministic, timestamped scheduler coordinates analog, digital, thermal, RTL, and external engines. [Source PDF, pp. 27-28, 40]
- Apache-2.0 for the open-source core. GPL or mixed-license engines remain behind executable or process boundaries pending distribution review.

These decisions are recorded in the complete [ADR-0001 through ADR-0020 decision index](docs/START_HERE.md#decision-index).

## Documentation map

Start with [docs/START_HERE.md](docs/START_HERE.md). The most important contracts are:

- [Product requirements](docs/PRODUCT_REQUIREMENTS.md)
- [Physical representation and IC package requirements](docs/PRODUCT_REQUIREMENTS.md#physical-representation-and-integrated-circuit-packages)
- [Physical appearance and reusable package contract](docs/catalog/PACKAGE_AND_PHYSICAL_APPEARANCE.md)
- [Device/package binding and pin-map contract](docs/catalog/DEVICE_PACKAGE_BINDING_CONTRACT.md)
- [Reusable package registry](docs/catalog/package-registry.yaml)
- [System architecture](docs/architecture/SYSTEM_ARCHITECTURE.md)
- [Applied Physics and real-world fidelity](docs/architecture/APPLIED_PHYSICS_AND_REAL_WORLD_FIDELITY.md)
- [Hierarchical model and library architecture](docs/architecture/HIERARCHICAL_MODEL_AND_LIBRARY_ARCHITECTURE.md)
- [Data-driven library and storage architecture](docs/architecture/DATA_DRIVEN_LIBRARY_AND_STORAGE_ARCHITECTURE.md)
- [Component registry](docs/catalog/component-registry.yaml)
- [Scientific model registry](docs/catalog/model-registry.yaml)
- [Variant pin-profile guide](docs/catalog/PIN_PROFILE_CATALOG.md)
- [Normative variant pin-profile registry](docs/catalog/variant-pin-profiles.yaml)
- [Normative variant semantic-profile registry](docs/catalog/variant-semantic-profiles.yaml)
- [Normalized parameter-definition catalog](docs/catalog/PARAMETER_DEFINITION_CATALOG.md)
- [Component model contract](docs/catalog/COMPONENT_MODEL_CONTRACT.md)
- [Master roadmap](docs/planning/MASTER_ROADMAP.md)
- [Atomic task index](docs/tasks/TASK_INDEX.md)
- [Atomic task contract](docs/tasks/ATOMIC_TASK_CONTRACT.md)
- [Stable test catalog](docs/quality/TEST_CATALOG.md)
- [Requirements traceability](docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md)
- [Release gates](docs/planning/RELEASE_GATES.md)

The baseline catalog tracks 162 canonical component families, 502 built-in variants/presets, 502 exact PinProfiles, 502 semantic profiles, 801 normalized planning parameter definitions, 38 reusable package templates, and nine planned scientific seed models. These are separate inventories and do not claim executable completion or every manufacturer SKU. Vendor parts are ingested through generic-device inheritance, bounded parameter overrides, exact package/pin bindings, provenance, license, and validation evidence. Scientific-model counts include only records actually enumerated in the model registry; the project makes no speculative claim of thousands of completed models.

## Project status

This repository currently contains the documentation foundation only. It does not yet contain application code, runtime configuration, migrations, or deployment assets.

## Contributing and security

Read [CONTRIBUTING.md](CONTRIBUTING.md) before taking work. Future contributors and AI agents must select one `Ready` atomic task and keep its tests, catalog coverage, and requirements traceability synchronized. See [AGENTS.md](AGENTS.md) for the exact workflow.

Please report vulnerabilities according to [SECURITY.md](SECURITY.md). Community participation is governed by [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md).

## Source basis

The principal feasibility brief is *Web-based Electronics and Computer Simulation Platform*, 44 pages. Page references in this repository use the notation `[Source PDF, p. N]` or `[Source PDF, pp. N-M]` and refer to the numbered PDF pages, which match the document's printed page numbers.

## License

The repository's open-source core is licensed under Apache License 2.0. See [LICENSE](LICENSE) and [NOTICE.md](NOTICE.md). Third-party models, datasets, symbols, tools, and engines retain their own terms and require provenance and compatibility review.
