# Task Index

## Operating rule

Select exactly one task whose card status is `Ready`, verify every dependency, and keep the work inside that card. `Planned` tasks are not authorized for implementation. Component/package tasks remain `Planned` until their platform dependencies and release gate are complete.

Every card and promotion decision MUST conform to the [Atomic Task Contract](ATOMIC_TASK_CONTRACT.md), including exact dependencies, public contracts, allowed files, reference data, and stable test IDs.

## Current ready queue

- [`PLAT-QA-001`](platform/plat-qa-001-define-test-identifier-and-evidence-schema.md) - define the test identifier and evidence schema. This documentation-only R0 root is the sole initial `Ready` task and does not authorize application source files.

## Baseline proof

| Controlled artifact | Count | Evidence |
|---|---:|---|
| Product requirements | 63 | `REQ-001` through `REQ-063` in `docs/PRODUCT_REQUIREMENTS.md` |
| Accepted ADRs | 20 | `ADR-0001` through `ADR-0020` |
| Enumerated stable acceptance tests | 129 | `TEST-REQ-001..063` and `TEST-GRC-001..066` in `docs/quality/test-registry.yaml` |
| Component families | 162 | `docs/catalog/component-registry.yaml` and model task manifest |
| Component variants with individual CAT cards | 502 | `docs/tasks/models/task-manifest.yaml` |
| Scientific model seed records | 9 | `docs/catalog/model-registry.yaml`; all are `Planned`, not executable or validated |
| Variant semantic profiles | 502 | `docs/catalog/variant-semantic-profiles.yaml`; unresolved model plans remain release-blocking |
| Normalized parameter definitions | 801 | `docs/catalog/parameter-definitions.yaml`; 23 release-blocking unresolved/placeholder records remain explicit |
| Reusable package templates | 38 | `docs/catalog/package-registry.yaml` |
| Platform epics | 35 | `docs/tasks/epics/` |
| Platform atomic tasks | 445 | [Platform index](platform/INDEX.md) |
| Component/package atomic tasks | 2636 | [Component/package index](models/INDEX.md) |
| Golden validation tasks | 66 | [Validation index](validation/INDEX.md) |
| Total atomic tasks | 3147 | Sum of the three task collections |

The baseline count distinguishes reusable physical packages from electrical component families. Package templates do not alter the 162-family/502-variant component baseline.

## Epic queue

| Epic | Outcome | Release | Requirements | Tasks |
|---|---|---|---|---:|
| [EPIC-A11Y-001](epics/epic-a11y-001.md) | Accessibility browser support and localization | R1 | REQ-034 | 10 |
| [EPIC-ANA-001](epics/epic-ana-001.md) | Linear analog simulation | R2 | REQ-008, REQ-009, REQ-010, REQ-029, REQ-033 | 15 |
| [EPIC-ANL-001](epics/epic-anl-001.md) | Analysis modes and parameter studies | R3 | REQ-011, REQ-012, REQ-013 | 12 |
| [EPIC-API-001](epics/epic-api-001.md) | Cloud simulation jobs | R10 | REQ-029, REQ-030 | 14 |
| [EPIC-ARCH-001](epics/epic-arch-001.md) | Computer architecture and functional emulation | R12 | REQ-001, REQ-028 | 14 |
| [EPIC-AUTH-001](epics/epic-auth-001.md) | Identity organizations and authorization | R10 | REQ-031, REQ-032, REQ-057, REQ-060 | 10 |
| [EPIC-COL-001](epics/epic-col-001.md) | Collaboration versioning and public library | R10 | REQ-031, REQ-053, REQ-059, REQ-060, REQ-061, REQ-062 | 12 |
| [EPIC-COMP-001](epics/epic-comp-001.md) | Educational full computer | R9 | REQ-027 | 16 |
| [EPIC-CPU-001](epics/epic-cpu-001.md) | Educational CPU hierarchy | R8 | REQ-002, REQ-025 | 16 |
| [EPIC-DATA-001](epics/epic-data-001.md) | Data-driven Library Service and lifecycle | R1 | REQ-054, REQ-055, REQ-056, REQ-059, REQ-060, REQ-061, REQ-062, REQ-063 | 8 |
| [EPIC-DIG-001](epics/epic-dig-001.md) | Event-driven digital simulation | R5 | REQ-018, REQ-021 | 15 |
| [EPIC-EDT-001](epics/epic-edt-001.md) | Schematic editor | R1 | REQ-004, REQ-005, REQ-037, REQ-038 | 20 |
| [EPIC-GOV-001](epics/epic-gov-001.md) | Open-source repository and governance | R1 | REQ-034, REQ-035 | 8 |
| [EPIC-GPU-001](epics/epic-gpu-001.md) | GPU and accelerator simulation | R13 | REQ-028 | 12 |
| [EPIC-HDL-001](epics/epic-hdl-001.md) | RTL FPGA and Verilator integration | R9 | REQ-026 | 14 |
| [EPIC-IDP-001](epics/epic-idp-001.md) | Minimal personal identity and project persistence | R1 | REQ-006, REQ-029, REQ-057, REQ-058 | 4 |
| [EPIC-IMP-001](epics/epic-imp-001.md) | Model data and firmware interchange | R7 | REQ-024, REQ-032, REQ-042, REQ-049, REQ-056, REQ-063 | 12 |
| [EPIC-LIB-001](epics/epic-lib-001.md) | Hierarchical reusable model and device library | R1 | REQ-040, REQ-042, REQ-048, REQ-049, REQ-050, REQ-051, REQ-052, REQ-053, REQ-059, REQ-063 | 14 |
| [EPIC-MEM-001](epics/epic-mem-001.md) | Memory hierarchy | R8 | REQ-025 | 12 |
| [EPIC-MIX-001](epics/epic-mix-001.md) | Mixed-signal scheduler and boundaries | R5 | REQ-001, REQ-002, REQ-019, REQ-020 | 12 |
| [EPIC-NET-001](epics/epic-net-001.md) | Units topology and netlist | R2 | REQ-008, REQ-023 | 10 |
| [EPIC-NON-001](epics/epic-non-001.md) | Nonlinear simulation and convergence | R3 | REQ-008, REQ-017 | 12 |
| [EPIC-OFF-001](epics/epic-off-001.md) | Offline storage and PWA behavior | R1 | REQ-006, REQ-029, REQ-055, REQ-057, REQ-058 | 8 |
| [EPIC-OPS-001](epics/epic-ops-001.md) | Deployment operations and observability | R10 | REQ-030 | 14 |
| [EPIC-PERF-001](epics/epic-perf-001.md) | Performance and scale engineering | R2 | REQ-033 | 12 |
| [EPIC-PHY-001](epics/epic-phy-001.md) | Applied Physics model framework and evidence | R4 | REQ-039, REQ-040, REQ-041, REQ-042, REQ-043, REQ-044, REQ-045, REQ-046, REQ-047 | 11 |
| [EPIC-PROJ-001](epics/epic-proj-001.md) | Project format and lifecycle | R1 | REQ-005, REQ-006, REQ-023, REQ-038, REQ-050, REQ-051, REQ-052, REQ-053, REQ-058, REQ-059 | 14 |
| [EPIC-QA-001](epics/epic-qa-001.md) | Quality traceability and release evidence | R0 | REQ-017, REQ-022, REQ-023, REQ-034, REQ-035, REQ-036, REQ-037, REQ-038 | 16 |
| [EPIC-REAL-001](epics/epic-real-001.md) | Applied Physics and real-world behavior | R4 | REQ-013, REQ-014, REQ-015, REQ-016, REQ-039, REQ-043, REQ-044, REQ-045, REQ-046, REQ-047 | 22 |
| [EPIC-RF-001](epics/epic-rf-001.md) | RF communications and distributed models | R7 | REQ-024, REQ-028 | 12 |
| [EPIC-SEC-001](epics/epic-sec-001.md) | Security privacy and sandboxing | R1 | REQ-032, REQ-035, REQ-056, REQ-057, REQ-060, REQ-062, REQ-063 | 15 |
| [EPIC-SYM-001](epics/epic-sym-001.md) | Symbols physical appearance and package system | R1 | REQ-022, REQ-023, REQ-037, REQ-038, REQ-048, REQ-050 | 15 |
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

A maintainer may promote one task only when its requirement and ADRs are accepted, every dependency is `Done`, inputs and allowed files exist, acceptance tests are executable, and no unresolved design choice is delegated to the implementer. The documentation-only R0 exception in the Atomic Task Contract uses exact documentation/evidence paths instead of nonexistent application source paths. Promote the card, its epic table row, and this ready queue in the same change.

## Completion synchronization

A completed task updates its card, this index, its epic, requirement traceability, applicable registry/coverage row, tests/golden evidence, release checklist, public contracts, risks, and limitations. A code or document change without these records is incomplete.
