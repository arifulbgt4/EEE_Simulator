# Requirements Traceability Matrix

## Reading the matrix

This matrix is the authoritative bridge from product intent to implementation evidence. Task ranges refer to individually linked cards in [`TASK_INDEX.md`](../tasks/TASK_INDEX.md). `CMP-*` means the applicable component-family and variant cards generated from the frozen registry. A requirement is not complete until its tasks are `Done`, its tests have current evidence, and its release checklist passes.

| Requirement | Source/decision | Normative documentation | Primary epic and atomic tasks | Required tests/evidence | Gate |
|---|---|---|---|---|---|
| REQ-001 | PDF pp. 1-4, 13-16, 43-44 | `SYSTEM_ARCHITECTURE`, `MULTI_FIDELITY_AND_CO_SIMULATION` | `EPIC-MIX-001`, `EPIC-ARCH-001`; `PLAT-MIX-*`, `PLAT-ARCH-*` | GRC-034, GRC-045, GRC-047 | G5/G12 |
| REQ-002 | PDF pp. 16, 20-21, 27 | `MULTI_FIDELITY_AND_CO_SIMULATION` | `EPIC-MIX-001`, `EPIC-CPU-001`; fidelity tasks and `CMP-*-F#-*` | Cross-fidelity equivalence suite | G5/G8 |
| REQ-003 | PDF pp. 30-31 | `USER_ROLES_AND_USE_CASES`, editor UX | `EPIC-UX-001`; `PLAT-UX-001..008` | Mode capability and explanation review | G1/G6 |
| REQ-004 | PDF pp. 22-23, 32 | `SCHEMATIC_EDITOR_AND_VISUALIZATION` | `EPIC-EDT-001`; `PLAT-EDT-*` | Editor operation, keyboard, invalid-circuit and visual regression suites | G1 |
| REQ-005 | PDF pp. 2, 16, 29, 31-32, 37 | Editor and project-format contracts | `EPIC-EDT-001`, `EPIC-PROJ-001`; hierarchy tasks | Hierarchy round trip and stable-port suite | G1 |
| REQ-006 | PDF pp. 25-26, 31-32 | `PROJECT_FILE_FORMAT`, storage contract | `EPIC-PROJ-001`, `EPIC-OFF-001`; `PLAT-PROJ-*`, `PLAT-OFF-*` | `.eesim` conformance, migration, corruption and offline-recovery suites | G1 |
| REQ-007 | PDF pp. 2, 30-31, 37 | Editor visualization and result contracts | `EPIC-VIZ-001`; `PLAT-VIZ-*` | Probe/instrument GRC assertions and accessible waveform review | G2/G6 |
| REQ-008 | PDF pp. 9-10, 29, 39 | `SIMULATION_ENGINE` | `EPIC-NET-001`, `EPIC-ANA-001`, `EPIC-NON-001` | GRC-001..013, conservation and topology diagnostics | G2/G3 |
| REQ-009 | PDF pp. 9-10, 32 | `SIMULATION_ENGINE` | `EPIC-ANA-001`; DC tasks | GRC-001..005, GRC-011..018 DC assertions | G2/G3 |
| REQ-010 | PDF pp. 9-10, 27-30, 32-33 | `SIMULATION_ENGINE` | `EPIC-ANA-001`; transient tasks | GRC-006..010 and transient semiconductor fixtures | G2/G3 |
| REQ-011 | PDF pp. 3, 10-11, 30 | `SIMULATION_ENGINE` | `EPIC-ANL-001`; AC tasks | GRC-008..010, GRC-018 and GRC-040 | G3/G7 |
| REQ-012 | PDF pp. 1, 5, 11 | Simulation and model contracts | `EPIC-ANL-001`; noise tasks plus `CMP-*-MODEL` | Noise density, integration and source-attribution suite | G4/G7 |
| REQ-013 | PDF pp. 11, 24, 30-31, 33 | Analysis and provenance contracts | `EPIC-ANL-001`; sweep/Monte Carlo tasks | GRC-026 and deterministic-seed suite | G4 |
| REQ-014 | PDF pp. 1, 3, 5-8, 33 | Component model contract | `EPIC-REAL-001`; `PLAT-REAL-*`, applicable `CMP-*` | Family golden fixtures and ngspice/reference comparisons | G4/G7 |
| REQ-015 | PDF pp. 5, 8-11, 33 | Model and co-simulation contracts | `EPIC-REAL-001`; thermal tasks and applicable `CMP-*-F4-*` | GRC-021..024, thermal balance and runaway suite | G4 |
| REQ-016 | PDF pp. 8-9, 31, 33, 41 | Model contract and editor diagnostics | `EPIC-REAL-001`; failure tasks and applicable `CMP-*-FAILURE` | GRC-021..025 and all documented failure-state tests | G4 |
| REQ-017 | PDF pp. 9-10, 12, 39 | `SIMULATION_ENGINE`, accuracy targets | `EPIC-NON-001`, `EPIC-QA-001`; convergence tasks | Singular, non-convergent, timestep-underflow, NaN and resource suites | G3/G6 |
| REQ-018 | PDF pp. 14-15, 29, 33-34 | Multi-fidelity/co-simulation contract | `EPIC-DIG-001`; `PLAT-DIG-*` | GRC-027..032 and exhaustive logic/timing suite | G5 |
| REQ-019 | PDF pp. 27-28, 40 | Multi-fidelity scheduler contract | `EPIC-MIX-001`; scheduler/timebase tasks | Same-timestamp ordering, checkpoint and deterministic replay suite | G5 |
| REQ-020 | PDF p. 28 | Boundary adapter contracts | `EPIC-MIX-001`; analog/digital adapter tasks | GRC-033, GRC-034 and load/threshold edge suite | G5 |
| REQ-021 | PDF pp. 15, 30-31, 33-35 | Digital and visualization contracts | `EPIC-DIG-001`, `EPIC-VIZ-001` | GRC-027..035 and instrument-loading tests | G5/G6 |
| REQ-022 | PDF pp. 1-8, 14-15, 18-21, 30, 32-36; baseline decision | Catalog taxonomy and registry | `EPIC-SYM-001`, `EPIC-QA-001`; all `CMP-*` catalog tasks | Registry count audit: 162 families/502 variants | G0/G7 |
| REQ-023 | PDF pp. 5-9, 20, 26-28, 40 | Component model contract | `EPIC-SYM-001`, `EPIC-QA-001`; family concern tasks | Required-field, lifecycle and family golden-evidence audit | G0/G7 |
| REQ-024 | PDF pp. 14-18, 21-23, 30, 33-36 | Model import/export contract | `EPIC-IMP-001`; `PLAT-IMP-*`, applicable `CMP-*-IMPORT` | Format conformance, malformed input, security and round-trip suites | G7/G9 |
| REQ-025 | PDF pp. 13, 17-19, 34-35, 37 | CPU and memory specifications | `EPIC-CPU-001`, `EPIC-MEM-001` | GRC-035, GRC-041..043 and ISA/memory suites | G8 |
| REQ-026 | PDF pp. 15, 18, 30, 35 | HDL/import and worker contracts | `EPIC-HDL-001`; `PLAT-HDL-*` | GRC-045, HDL conformance, sandbox and differential suites | G9 |
| REQ-027 | PDF pp. 21, 35 | Product and architecture contracts | `EPIC-COMP-001`; `PLAT-COMP-*` | GRC-044 and complete boot/application suite | G9 |
| REQ-028 | PDF pp. 15-21, 36, 42-44 | System architecture and non-goals | `EPIC-ARCH-001`, `EPIC-GPU-001`, `EPIC-RF-001` | GRC-046..048 and research reproducibility datasets | G12/G13 |
| REQ-029 | PDF pp. 25-26, 31-32 | Local/cloud/worker architecture | `EPIC-OFF-001`, `EPIC-WASM-001`, `EPIC-API-001` | Browser capability, offline, routing and worker-fallback suites | G2/G10 |
| REQ-030 | PDF pp. 25-26, 36, 39 | Job API and operations contracts | `EPIC-API-001`, `EPIC-OPS-001` | Queue, stream, cancel, retry, checkpoint, worker-loss and quota suites | G10/G11 |
| REQ-031 | PDF pp. 31-32, 41-42; CRDT decision | Storage/collaboration contract | `EPIC-AUTH-001`, `EPIC-COL-001` | Convergence, reconnect, authorization, history and moderation suites | G10 |
| REQ-032 | PDF pp. 25-26, 36, 39-40; security decision | Security and sandboxing contract | `EPIC-SEC-001`, `EPIC-AUTH-001`, `EPIC-IMP-001` | Malicious archive/model/HDL, quota and tenant-isolation suites | G1/G10 |
| REQ-033 | PDF pp. 23-25, 29-30, 39-40 | Performance/browser/worker contracts | `EPIC-PERF-001`, `EPIC-WASM-001` | Published benchmark matrix and threaded/single-thread fallback | G2/G6 |
| REQ-034 | PDF pp. 22-25, 30-32, 37; WCAG/browser decision | Accessibility/browser/i18n contract | `EPIC-A11Y-001`, `EPIC-UX-001` | WCAG 2.2 AA manual/automated and supported-browser suites | G1/G6 |
| REQ-035 | PDF pp. 21-26, 35-36, 43; Apache/process decision | License and dependency documents | `EPIC-GOV-001`, `EPIC-SEC-001` | License/notice inventory, boundary review and release audit | G0/every release |
| REQ-036 | PDF p. 37 | MVP release checklist and roadmap | `EPIC-QA-001` plus G2-G5 epics | Required MVP demos, benchmarks, security, browser and accessibility evidence | G6 |
| REQ-037 | User decision, 2026-07-11; PDF pp. 30-31 visual basis | Physical-appearance/package and editor contracts | `EPIC-SYM-001`, `EPIC-EDT-001`, `EPIC-VIZ-001` | GRC-049, GRC-050, GRC-054 and visual-performance suite | G1/G6 |
| REQ-038 | User decision, 2026-07-11 | Package registry, package designer, project format | `EPIC-SYM-001`, `EPIC-PROJ-001`, `EPIC-EDT-001`, `EPIC-QA-001` | GRC-051..054, pin-equivalence and custom-package conformance suites | G1/G7 |

## Audit rules

1. Stable IDs are never reused or silently renumbered.
2. Every `Done` task must link current evidence; a task title alone is not evidence.
3. Every released component and package must identify the exact golden fixture/assertions it passes.
4. A requirement may have several release gates; later gates cannot invalidate evidence retained by an earlier compatible schema/model version.
5. Any accepted ADR that changes a row must update this matrix in the same change.
