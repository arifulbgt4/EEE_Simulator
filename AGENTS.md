# Agent Operating Contract

This file is the mandatory workflow for human-directed AI agents working in this repository.

## Start here

1. Read [docs/START_HERE.md](docs/START_HERE.md).
2. Read the relevant accepted decisions in [docs/decisions](docs/decisions).
3. Read [docs/PRODUCT_REQUIREMENTS.md](docs/PRODUCT_REQUIREMENTS.md), the applicable release gate, and the applicable architecture or model contract.
4. Select exactly one task whose status is `Ready` in [docs/tasks/TASK_INDEX.md](docs/tasks/TASK_INDEX.md).
5. Confirm that all dependencies listed by the task are complete before changing anything.

The source brief recommends staged delivery from components to circuits, logic, CPU blocks, small computers, and only then architecture-level systems. Do not skip those gates or silently widen the selected task. [Source PDF, pp. 32-41]

## One-task rule

- Work on one atomic task at a time.
- Do not expand scope beyond the task's allowed files, public contracts, concern, model tier, and component variant.
- Do not combine cleanup, redesign, dependency upgrades, or adjacent backlog items unless the task explicitly requires them.
- If the task is blocked, record the blocking evidence and dependency; do not invent a substitute requirement.
- Never mark a component `Released` before every required lifecycle state and validation gate is complete.

Component task IDs use:

```text
CMP-<category>-<family>-<variant>-<tier>-<concern>
```

Platform task IDs use:

```text
PLAT-<subsystem>-<concern>
```

Standard component concerns are `CAT`, `SYM`, `MODEL`, `THERMAL`, `FAILURE`, `IMPORT`, `VALIDATION`, and `DOCS`.

## Required synchronization

A task is not complete until the same change is reflected in all applicable records:

- the task card and [task index](docs/tasks/TASK_INDEX.md);
- the relevant requirement in [PRODUCT_REQUIREMENTS.md](docs/PRODUCT_REQUIREMENTS.md);
- the [component registry](docs/catalog/component-registry.yaml) and [coverage matrix](docs/catalog/COMPONENT_COVERAGE_MATRIX.md), when applicable;
- the relevant test or golden circuit in [docs/quality](docs/quality);
- the [requirements traceability matrix](docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md);
- the applicable [release acceptance checklist](docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md);
- architecture, API, file-format, or model documentation when a public contract changes.

The source brief identifies model accuracy, numerical convergence, mixed-engine synchronization, browser memory, UI performance, and uncontrolled scope as primary risks. Every task must make its validation and failure behavior explicit. [Source PDF, pp. 39-41]

## Documentation rules

- Repository documentation and public identifiers are English-only.
- Use stable IDs; never renumber an existing requirement, ADR, component family, variant, task, test, or release gate.
- Cite derived source requirements with an explicit PDF page reference.
- Use SI base units internally in normative examples; presentation prefixes are display concerns.
- State assumptions, limits, provenance, fidelity, and unsupported analyses directly.
- Keep links relative and update inbound references when a document moves.
- Mermaid diagrams must render in standard GitHub Markdown.
- Do not copy IEC symbol artwork. Create original IEC/ANSI-aligned symbols and document provenance.

## Architecture invariants

Agents must not contradict accepted ADRs without first adding a superseding ADR:

- hierarchical multi-fidelity simulation;
- Next.js/React plus TypeScript and a Rust/WebAssembly simulation core;
- local-first execution with isolated cloud workers for heavy jobs;
- the versioned `.eesim` project format;
- fidelity levels F0 through F5;
- deterministic timestamped co-simulation;
- Canvas/WebGL2 rendering with benchmark-gated WebGPU;
- process isolation for external engines;
- CRDT-based collaboration;
- Apache-2.0 open-source core licensing.

## Verification and handoff

Before marking a task complete:

1. Run every acceptance check named by the task.
2. Add or update positive, boundary, and failure-path tests.
3. Verify deterministic output with the same project, configuration, seed, and engine versions where applicable.
4. Verify documentation links and identifier references.
5. Record commands, results, known limitations, and remaining risks in the task card.
6. Change task status only after the evidence exists.

Do not claim that a build, simulation, benchmark, accessibility check, security check, or numerical comparison passed without current evidence.
