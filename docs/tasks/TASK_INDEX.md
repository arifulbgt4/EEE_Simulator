# Task Index

## Operating rule

Select exactly one task whose card status is `Ready`, verify every dependency, and keep the work inside that card. `Planned` tasks are not authorized for implementation. Component/package tasks remain `Planned` until their platform dependencies and release gate are complete.

## Current ready queue

- [`PLAT-GOV-001`](platform/plat-gov-001-define-repository-layout-and-ownership-boundaries.md) - define repository layout and ownership boundaries. This is the only initial `Ready` task after the documentation baseline is accepted.

## Baseline proof

| Controlled artifact | Count | Evidence |
|---|---:|---|
| Product requirements | 38 | `REQ-001` through `REQ-038` in `docs/PRODUCT_REQUIREMENTS.md` |
| Accepted ADRs | 10 | `ADR-0001` through `ADR-0010` |
| Component families | 162 | `docs/catalog/component-registry.yaml` and model task manifest |
| Component variants with individual CAT cards | 502 | `docs/tasks/models/task-manifest.yaml` |
| Reusable package templates | 38 | `docs/catalog/package-registry.yaml` |
| Platform epics | 31 | `docs/tasks/epics/` |
| Platform atomic tasks | 400 | [Platform index](platform/INDEX.md) |
| Component/package atomic tasks | 2636 | [Component/package index](models/INDEX.md) |
| Golden validation tasks | 54 | [Validation index](validation/INDEX.md) |
| Total atomic tasks | 3090 | Sum of the three task collections |

The baseline count distinguishes reusable physical packages from electrical component families. Package templates do not alter the 162-family/502-variant component baseline.

## Epic queue

| Epic | Outcome | Release | Requirements | Tasks |
|---|---|---|---|---:|
| [EPIC-A11Y-001](epics/epic-a11y-001.md) | Accessibility browser support and localization | R1 | REQ-034 | 10 |
| [EPIC-ANA-001](epics/epic-ana-001.md) | Linear analog simulation | R2 | REQ-008, REQ-009, REQ-010, REQ-029, REQ-033 | 15 |
| [EPIC-ANL-001](epics/epic-anl-001.md) | Analysis modes and parameter studies | R3 | REQ-011, REQ-012, REQ-013 | 12 |
| [EPIC-API-001](epics/epic-api-001.md) | Cloud simulation jobs | R10 | REQ-029, REQ-030 | 14 |
| [EPIC-ARCH-001](epics/epic-arch-001.md) | Computer architecture and functional emulation | R12 | REQ-028 | 14 |
| [EPIC-AUTH-001](epics/epic-auth-001.md) | Identity organizations and authorization | R10 | REQ-031, REQ-032 | 10 |
| [EPIC-COL-001](epics/epic-col-001.md) | Collaboration versioning and public library | R10 | REQ-031 | 12 |
| [EPIC-COMP-001](epics/epic-comp-001.md) | Educational full computer | R9 | REQ-027 | 16 |
| [EPIC-CPU-001](epics/epic-cpu-001.md) | Educational CPU hierarchy | R8 | REQ-025 | 16 |
| [EPIC-DIG-001](epics/epic-dig-001.md) | Event-driven digital simulation | R5 | REQ-018, REQ-021 | 15 |
| [EPIC-EDT-001](epics/epic-edt-001.md) | Schematic editor | R1 | REQ-004, REQ-005, REQ-037, REQ-038 | 20 |
| [EPIC-GOV-001](epics/epic-gov-001.md) | Open-source repository and governance | R1 | REQ-034, REQ-035 | 8 |
| [EPIC-GPU-001](epics/epic-gpu-001.md) | GPU and accelerator simulation | R13 | REQ-028 | 12 |
| [EPIC-HDL-001](epics/epic-hdl-001.md) | RTL FPGA and Verilator integration | R9 | REQ-026 | 14 |
| [EPIC-IMP-001](epics/epic-imp-001.md) | Model data and firmware interchange | R7 | REQ-024, REQ-032 | 12 |
| [EPIC-MEM-001](epics/epic-mem-001.md) | Memory hierarchy | R8 | REQ-025 | 12 |
| [EPIC-MIX-001](epics/epic-mix-001.md) | Mixed-signal scheduler and boundaries | R5 | REQ-019, REQ-020 | 12 |
| [EPIC-NET-001](epics/epic-net-001.md) | Units topology and netlist | R2 | REQ-008, REQ-023 | 10 |
| [EPIC-NON-001](epics/epic-non-001.md) | Nonlinear simulation and convergence | R3 | REQ-008, REQ-017 | 12 |
| [EPIC-OFF-001](epics/epic-off-001.md) | Offline storage and PWA behavior | R1 | REQ-006 | 8 |
| [EPIC-OPS-001](epics/epic-ops-001.md) | Deployment operations and observability | R10 | REQ-030 | 14 |
| [EPIC-PERF-001](epics/epic-perf-001.md) | Performance and scale engineering | R2 | REQ-033 | 12 |
| [EPIC-PROJ-001](epics/epic-proj-001.md) | Project format and lifecycle | R1 | REQ-006, REQ-023, REQ-038 | 14 |
| [EPIC-QA-001](epics/epic-qa-001.md) | Quality traceability and release evidence | R0 | REQ-023, REQ-034, REQ-035, REQ-036, REQ-037, REQ-038 | 16 |
| [EPIC-REAL-001](epics/epic-real-001.md) | Non-ideal thermal and failure behavior | R4 | REQ-014, REQ-015, REQ-016 | 14 |
| [EPIC-RF-001](epics/epic-rf-001.md) | RF communications and distributed models | R7 | REQ-024, REQ-028 | 12 |
| [EPIC-SEC-001](epics/epic-sec-001.md) | Security privacy and sandboxing | R1 | REQ-032, REQ-035 | 15 |
| [EPIC-SYM-001](epics/epic-sym-001.md) | Symbols physical appearance and package system | R1 | REQ-022, REQ-023, REQ-037, REQ-038 | 15 |
| [EPIC-UX-001](epics/epic-ux-001.md) | Application shell and user modes | R1 | REQ-003, REQ-034 | 8 |
| [EPIC-VIZ-001](epics/epic-viz-001.md) | Visualization and virtual instruments | R2 | REQ-007, REQ-021, REQ-034, REQ-037 | 16 |
| [EPIC-WASM-001](epics/epic-wasm-001.md) | Rust WASM and worker runtime | R2 | REQ-029, REQ-033 | 10 |

## Status meanings

- `Planned`: scoped but not yet dependency-complete.
- `Ready`: decision-complete, dependencies satisfied, and eligible to select.
- `In Progress`: actively owned; no parallel agent may take it.
- `Review`: implementation and evidence are awaiting review.
- `Done`: all acceptance evidence and synchronized records are complete.
- `Blocked`: named external evidence or dependency prevents progress.
- `Deferred`: intentionally outside active delivery with an entry criterion.

## Promotion to Ready

A maintainer may promote one task only when its requirement and ADRs are accepted, every dependency is `Done`, inputs and allowed files exist, acceptance tests are executable, and no unresolved design choice is delegated to the implementer. Promote the card, its epic table row, and this ready queue in the same change.

## Completion synchronization

A completed task updates its card, this index, its epic, requirement traceability, applicable registry/coverage row, tests/golden evidence, release checklist, public contracts, risks, and limitations. A code or document change without these records is incomplete.
