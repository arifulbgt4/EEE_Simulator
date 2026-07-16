# Agent Operating Contract

This file is the mandatory workflow for human-directed AI agents working in this repository.

## Start here

1. Read [docs/START_HERE.md](docs/START_HERE.md).
2. Read the normative [Source and Evidence Policy](docs/SOURCE_AND_EVIDENCE_POLICY.md).
3. Read the relevant accepted decisions in [docs/decisions](docs/decisions).
4. Read [docs/PRODUCT_REQUIREMENTS.md](docs/PRODUCT_REQUIREMENTS.md), the applicable release gate, and the applicable architecture or model contract.
5. Select exactly one task whose status is `Ready` in [docs/tasks/TASK_INDEX.md](docs/tasks/TASK_INDEX.md).
6. Confirm that all dependencies listed by the task are complete before changing anything.

The repository has adopted staged delivery from components to circuits, logic, CPU blocks, small computers, and only then architecture-level systems. The legacy citation records that this sequence appeared in the unverified source brief; it does not prove the technical assumptions or completion of any gate. Do not skip those gates or silently widen the selected task. [Source PDF, pp. 32-41]

For model or library work, also read [Applied Physics and Real-World Fidelity](docs/architecture/APPLIED_PHYSICS_AND_REAL_WORLD_FIDELITY.md), [Hierarchical Model and Library Architecture](docs/architecture/HIERARCHICAL_MODEL_AND_LIBRARY_ARCHITECTURE.md), and [Data-Driven Library and Storage Architecture](docs/architecture/DATA_DRIVEN_LIBRARY_AND_STORAGE_ARCHITECTURE.md). Preserve the complete principle-to-result lineage.

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

The repository risk program includes model accuracy, numerical convergence, mixed-engine synchronization, browser memory, UI performance, and uncontrolled scope. The legacy citation is source-brief context only; current primary references, tests, benchmarks, and physical evidence must establish the applicable risk and its control. Every task must make its validation and failure behavior explicit. [Source PDF, pp. 39-41]

## Documentation rules

- Repository documentation and public identifiers are English-only.
- Use stable IDs; never renumber an existing requirement, ADR, component family, variant, task, test, or release gate.
- Preserve explicit PDF page references for source-brief lineage, but classify every `[Source PDF]` citation as unverified context under [Source and Evidence Policy](docs/SOURCE_AND_EVIDENCE_POLICY.md).
- Never use the Source PDF alone to support an equation, standard, accuracy target, license, security property, implementation fact, test result, or release decision.
- Before a technical task becomes `Ready`, name and verify the applicable official/primary source or approved physical/reference artifact, its version and exact location, applicability, license status, and expected evidence. If this is not possible, keep the task `Planned` or record it as blocked.
- Use SI base units internally in normative examples; presentation prefixes are display concerns.
- State assumptions, limits, provenance, fidelity, and unsupported analyses directly.
- Store normative quantities in unprefixed SI units with explicit dimensions; reject incompatible units rather than guessing.
- Reference immutable published revisions and content hashes; never hard-delete a referenced or published record.
- Treat `behavioral` as the canonical public enum; `behavioural` is an import/display alias only.
- Do not claim unenumerated model counts, market-wide coverage, or experimental accuracy without evidence.
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
- Applied Physics First and the hard R4 Applied Physics and Real-World Fidelity gate;
- hierarchical, acyclic model/device/board/system taxonomy with exact revision lineage;
- orthogonal model, symbol, package, pin-profile, binding, board, and system records;
- Library Service resolution into an engine-ready bundle with no direct engine-to-storage dependency;
- PostgreSQL plus validated JSONB, object storage, and IndexedDB responsibilities;
- declarative stored models and allowlisted, sandboxed executable kernels;
- guest/offline access plus provider-neutral Google OIDC planning, with organization/RBAC scope retained in R10;
- immutable publication and dependency-safe soft deletion.

## Verification and handoff

Before marking a task complete:

1. Run every acceptance check named by the task.
2. Add or update positive, boundary, and failure-path tests.
3. Verify deterministic output with the same project, configuration, seed, and engine versions where applicable.
4. Verify documentation links and identifier references.
5. Verify that technical claims resolve to applicable official/primary sources or physical evidence and that no acceptance decision depends only on a legacy Source PDF citation.
6. Record commands, results, source/evidence identities, known limitations, and remaining risks in the task card.
7. Change task status only after the evidence exists.

Do not claim that a build, simulation, benchmark, accessibility check, security check, or numerical comparison passed without current evidence.
