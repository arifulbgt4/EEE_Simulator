# Requirements Traceability Matrix

## Reading the matrix

This matrix is the authoritative bridge from product intent to implementation evidence. Task ranges refer to individually linked cards in [`TASK_INDEX.md`](../tasks/TASK_INDEX.md). `CMP-*` means the applicable component-family and variant cards generated from the frozen registry. A requirement is not complete until its tasks are `Done`, its tests have current evidence, and its release checklist passes.

Every `PDF` page reference in the `Source/decision` column is **unverified source-brief context only** under the [Source and Evidence Policy](../SOURCE_AND_EVIDENCE_POLICY.md). It locates planning intent; it is not confirmed technical evidence and cannot validate an equation, standard, device model, numerical method, accuracy claim, license, security control, or release result. Those claims require the primary technical or measured evidence named by the task and acceptance contract.

| Requirement | Source/decision | Normative documentation | Primary epic and atomic tasks | Required tests/evidence | Gate |
|---|---|---|---|---|---|
| REQ-001 | PDF pp. 1-4, 13-16, 43-44 | `SYSTEM_ARCHITECTURE`, `MULTI_FIDELITY_AND_CO_SIMULATION` | `EPIC-MIX-001`, `EPIC-ARCH-001`; `PLAT-MIX-*`, `PLAT-ARCH-*` | `TEST-REQ-001`; GRC-034, GRC-045, GRC-047 | G5/G12 |
| REQ-002 | PDF pp. 16, 20-21, 27 | `MULTI_FIDELITY_AND_CO_SIMULATION` | `EPIC-MIX-001`, `EPIC-CPU-001`; fidelity tasks and `CMP-*-F#-*` | `TEST-REQ-002`; Cross-fidelity equivalence suite | G5/G8 |
| REQ-003 | PDF pp. 30-31 | `USER_ROLES_AND_USE_CASES`, editor UX | `EPIC-UX-001`; `PLAT-UX-001..008` | `TEST-REQ-003`; Mode capability and explanation review | G1/G6 |
| REQ-004 | PDF pp. 22-23, 32 | `SCHEMATIC_EDITOR_AND_VISUALIZATION` | `EPIC-EDT-001`; `PLAT-EDT-*` | `TEST-REQ-004`; Editor operation, keyboard, invalid-circuit and visual regression suites | G1 |
| REQ-005 | PDF pp. 2, 16, 29, 31-32, 37 | Editor and project-format contracts | `EPIC-EDT-001`, `EPIC-PROJ-001`; hierarchy tasks | `TEST-REQ-005`; Hierarchy round trip and stable-port suite | G1 |
| REQ-006 | PDF pp. 25-26, 31-32 | `PROJECT_FILE_FORMAT`, storage contract | `EPIC-PROJ-001`, `EPIC-OFF-001`; `PLAT-PROJ-*`, `PLAT-OFF-*` | `TEST-REQ-006`; `.eesim` conformance, migration, corruption and offline-recovery suites | G1 |
| REQ-007 | PDF pp. 2, 30-31, 37 | Editor visualization and result contracts | `EPIC-VIZ-001`; `PLAT-VIZ-*` | `TEST-REQ-007`; Probe/instrument GRC assertions and accessible waveform review | G2/G6 |
| REQ-008 | PDF pp. 9-10, 29, 39 | `SIMULATION_ENGINE` | `EPIC-NET-001`, `EPIC-ANA-001`, `EPIC-NON-001` | `TEST-REQ-008`; GRC-001..013, conservation and topology diagnostics | G2/G3 |
| REQ-009 | PDF pp. 9-10, 32 | `SIMULATION_ENGINE` | `EPIC-ANA-001`; DC tasks | `TEST-REQ-009`; GRC-001..005, GRC-011..018 DC assertions | G2/G3 |
| REQ-010 | PDF pp. 9-10, 27-30, 32-33 | `SIMULATION_ENGINE` | `EPIC-ANA-001`; transient tasks | `TEST-REQ-010`; GRC-006..010 and transient semiconductor fixtures | G2/G3 |
| REQ-011 | PDF pp. 3, 10-11, 30 | `SIMULATION_ENGINE` | `EPIC-ANL-001`; AC tasks | `TEST-REQ-011`; GRC-008..010, GRC-018 and GRC-040 | G3/G7 |
| REQ-012 | PDF pp. 1, 5, 11 | Simulation and model contracts | `EPIC-ANL-001`; noise tasks plus `CMP-*-MODEL` | `TEST-REQ-012`; Noise density, integration and source-attribution suite | G4/G7 |
| REQ-013 | PDF pp. 11, 24, 30-31, 33 | Analysis and provenance contracts | `EPIC-ANL-001`; sweep/Monte Carlo tasks | `TEST-REQ-013`; GRC-026 and deterministic-seed suite | G4 |
| REQ-014 | PDF pp. 1, 3, 5-8, 33 | Component model contract | `EPIC-REAL-001`, `EPIC-EXT-001`; `PLAT-REAL-*`, `PLAT-EXT-017`, `PLAT-EXT-020..021`, applicable `CMP-*` | `TEST-REQ-014`; Family golden fixtures and ngspice/reference comparisons | G3/G4/G7 |
| REQ-015 | PDF pp. 5, 8-11, 33 | Model and co-simulation contracts | `EPIC-REAL-001`; thermal tasks and applicable `CMP-*-F4-*` | `TEST-REQ-015`; GRC-021..022 at G4, GRC-023..024 at G7, thermal balance and runaway suite | G4/G7 |
| REQ-016 | PDF pp. 8-9, 31, 33, 41 | Model contract and editor diagnostics | `EPIC-REAL-001`; failure tasks and applicable `CMP-*-FAILURE` | `TEST-REQ-016`; GRC-021..022 at G4, GRC-023..025 at G7, and all documented failure-state tests | G4/G7 |
| REQ-017 | PDF pp. 9-10, 12, 39 | `SIMULATION_ENGINE`, accuracy targets | `EPIC-NON-001`, `EPIC-QA-001`; convergence tasks | `TEST-REQ-017`; Singular, non-convergent, timestep-underflow, NaN and resource suites | G3/G6 |
| REQ-018 | PDF pp. 14-15, 29, 33-34 | Multi-fidelity/co-simulation contract | `EPIC-DIG-001`; `PLAT-DIG-*` | `TEST-REQ-018`; GRC-027..032 and exhaustive logic/timing suite | G5 |
| REQ-019 | PDF pp. 27-28, 40 | Multi-fidelity scheduler contract | `EPIC-MIX-001`; scheduler/timebase tasks | `TEST-REQ-019`; Same-timestamp ordering, checkpoint and deterministic replay suite | G5 |
| REQ-020 | PDF p. 28 | Boundary adapter contracts | `EPIC-MIX-001`; analog/digital adapter tasks | `TEST-REQ-020`; GRC-033, GRC-034 and load/threshold edge suite | G5 |
| REQ-021 | PDF pp. 15, 30-31, 33-35 | Digital and visualization contracts | `EPIC-DIG-001`, `EPIC-VIZ-001` | `TEST-REQ-021`; GRC-027..034 at G5/G6, GRC-035 at G8, and instrument-loading tests | G5/G6/G8 |
| REQ-022 | PDF pp. 1-8, 14-15, 18-21, 30, 32-36; baseline decision | Catalog taxonomy and registry | `EPIC-SYM-001`, `EPIC-QA-001`; all `CMP-*` catalog tasks | `TEST-REQ-022`; Registry count audit: 162 families/502 variants | G0/G7 |
| REQ-023 | PDF pp. 5-9, 20, 26-28, 40 | Component model contract | `EPIC-SYM-001`, `EPIC-QA-001`; family concern tasks | `TEST-REQ-023`; Required-field, lifecycle and family golden-evidence audit | G0/G7 |
| REQ-024 | PDF pp. 14-18, 21-23, 30, 33-36 | Model import/export contract | `EPIC-IMP-001`, `EPIC-EXT-001`, `EPIC-HPC-001`; `PLAT-IMP-*`, `PLAT-EXT-*`, `PLAT-HPC-002`, `PLAT-HPC-011`, applicable `CMP-*-IMPORT` | `TEST-REQ-024`; Format conformance, malformed input, security, adapter handoff and round-trip suites | G3/G7/G9/G11 |
| REQ-025 | PDF pp. 13, 17-19, 34-35, 37 | CPU and memory specifications | `EPIC-CPU-001`, `EPIC-MEM-001` | `TEST-REQ-025`; GRC-035, GRC-041..043 and ISA/memory suites | G8 |
| REQ-026 | PDF pp. 15, 18, 30, 35 | HDL/import and worker contracts | `EPIC-HDL-001`; `PLAT-HDL-*` | `TEST-REQ-026`; GRC-045, HDL conformance, sandbox and differential suites | G9 |
| REQ-027 | PDF pp. 21, 35 | Product and architecture contracts | `EPIC-COMP-001`; `PLAT-COMP-*` | `TEST-REQ-027`; GRC-044 and complete boot/application suite | G9 |
| REQ-028 | PDF pp. 15-21, 36, 42-44 | System architecture and non-goals | `EPIC-ARCH-001`, `EPIC-GPU-001`, `EPIC-RF-001` | `TEST-REQ-028`; GRC-046..048 and research reproducibility datasets | G12/G13 |
| REQ-029 | PDF pp. 25-26, 31-32 | Local/cloud/worker architecture | `EPIC-OFF-001`, `EPIC-WASM-001`, `EPIC-API-001`, `EPIC-EXT-001`, `EPIC-HPC-001` | `TEST-REQ-029`; Browser capability, offline, routing, external-adapter placement and worker-fallback suites | G2/G3/G10/G11 |
| REQ-030 | PDF pp. 25-26, 36, 39 | Job API and operations contracts | `EPIC-API-001`, `EPIC-OPS-001`, `EPIC-EXT-001`, `EPIC-HPC-001`; `PLAT-EXT-013`, `PLAT-HPC-001..011` | `TEST-REQ-030`; Queue, stream, cancel, retry, checkpoint, worker-loss, MPI/pool, reduction, artifact and quota suites | G10/G11 |
| REQ-031 | PDF pp. 31-32, 41-42; CRDT decision | Storage/collaboration contract | `EPIC-AUTH-001`, `EPIC-COL-001` | `TEST-REQ-031`; Convergence, reconnect, authorization, history and moderation suites | G10 |
| REQ-032 | PDF pp. 25-26, 36, 39-40; security decision | Security and sandboxing contract | `EPIC-SEC-001`, `EPIC-AUTH-001`, `EPIC-IMP-001`, `EPIC-EXT-001`, `EPIC-HPC-001` | `TEST-REQ-032`; Malicious archive/model/HDL, adapter sandbox, MPI/HPC isolation, quota and tenant-isolation suites | G1/G3/G10/G11 |
| REQ-033 | PDF pp. 23-25, 29-30, 39-40 | Performance/browser/worker contracts | `EPIC-PERF-001`, `EPIC-WASM-001` | `TEST-REQ-033`; Published benchmark matrix and threaded/single-thread fallback | G2/G6 |
| REQ-034 | PDF pp. 22-25, 30-32, 37; WCAG/browser decision | Accessibility/browser/i18n contract | `EPIC-A11Y-001`, `EPIC-UX-001` | `TEST-REQ-034`; WCAG 2.2 AA manual/automated and supported-browser suites | G1/G6 |
| REQ-035 | PDF pp. 21-26, 35-36, 43; Apache/process decision | License and dependency documents | `EPIC-GOV-001`, `EPIC-SEC-001`, `EPIC-EXT-001`, `EPIC-HPC-001` | `TEST-REQ-035`; License/notice inventory, ngspice/Xyce process boundary review and release audit | G0/every release |
| REQ-036 | PDF p. 37 | MVP release checklist and roadmap | `EPIC-QA-001` plus G2-G5 epics | `TEST-REQ-036`; Required MVP demos, benchmarks, security, browser and accessibility evidence | G6 |
| REQ-037 | User decision, 2026-07-11; PDF pp. 30-31 visual basis | Physical-appearance/package and editor contracts | `EPIC-SYM-001`, `EPIC-EDT-001`, `EPIC-VIZ-001` | `TEST-REQ-037`; GRC-049, GRC-050, GRC-054 and visual-performance suite | G1/G6 |
| REQ-038 | User decision, 2026-07-11 | Package registry, package designer, project format | `EPIC-SYM-001`, `EPIC-PROJ-001`, `EPIC-EDT-001`, `EPIC-QA-001` | `TEST-REQ-038`; GRC-051..054, pin-equivalence and custom-package conformance suites | G1/G7 |
| REQ-039 | User architecture brief, 2026-07-16; PDF pp. 1-12, 27-30, 39-41 | `ADR-0011`; `APPLIED_PHYSICS_AND_REAL_WORLD_FIDELITY` | `EPIC-PHY-001`, `EPIC-REAL-001`; `PLAT-PHY-001..011`, `PLAT-REAL-015..022` | `TEST-REQ-039`; project-description/principle and exact R0-R13 audit | G0/G4 |
| REQ-040 | User architecture brief; PDF pp. 5-12, 20-21, 26-28, 40 | `ADR-0011`, `ADR-0013`; Applied Physics contract, `model-registry.yaml` | `EPIC-PHY-001`, `EPIC-LIB-001`; `PLAT-PHY-001..002`, `PLAT-LIB-001` | `TEST-REQ-040`; schema/kind/required-field conformance | G0/G4 |
| REQ-041 | User architecture brief; PDF pp. 5-11, 27-30 | `ADR-0011`; Applied Physics and component-model contracts, parameter catalog | `EPIC-PHY-001`; `PLAT-PHY-003`; normalized parameter tasks | `TEST-REQ-041`; valid SI and invalid/missing/incompatible-dimension suite | G0/G4 |
| REQ-042 | User architecture brief; PDF pp. 5-9, 20-21, 26-28, 40-41 | `ADR-0011`, `ADR-0020`; model/component/import contracts | `EPIC-PHY-001`, `EPIC-LIB-001`; `PLAT-PHY-004..005`, `PLAT-LIB-014` | `TEST-REQ-042`; incomplete validity/provenance/trust publication rejection | G0/G4 |
| REQ-043 | User architecture brief; PDF pp. 9-12, 39-41 | `ADR-0011`, `ADR-0012`; Applied Physics and accuracy contracts | `EPIC-PHY-001`, `EPIC-REAL-001`; `PLAT-PHY-006`, `PLAT-PHY-009`, `PLAT-REAL-021` | `TEST-REQ-043`; category envelope, uncertainty, and false-precision review | G4 |
| REQ-044 | User architecture brief; PDF pp. 30-31, 37, 39-41 | `ADR-0011`, `ADR-0012`; physical benchmark contract | `EPIC-PHY-001`, `EPIC-REAL-001`; `PLAT-PHY-007..008`, `VAL-GRC-055..066` | `TEST-REQ-044`, `TEST-GRC-055..066`; calibrated evidence/metadata audit | G4 |
| REQ-045 | User architecture brief; unverified source-brief context, PDF pp. 1, 3, 5-12, 33, 39-41 | `ADR-0012`; Applied Physics, simulation, co-simulation contracts | `EPIC-REAL-001`, `EPIC-PHY-001`; `PLAT-REAL-001..022` | `TEST-REQ-045`; GRC-021, GRC-022, GRC-026, and GRC-055..066 at G4; preserved GRC-023..025 specifications at G7 | G4/G7 |
| REQ-046 | User architecture brief; PDF pp. 8-11, 24, 30-31, 33 | `ADR-0012`; Applied Physics and simulation contracts | `EPIC-REAL-001`; `PLAT-REAL-001`, `PLAT-REAL-016..017`, `PLAT-REAL-021` | `TEST-REQ-046`; seeded variation/correlation/stress-history suite | G4 |
| REQ-047 | User architecture brief; PDF pp. 5-11, 22-23, 30-31, 33, 37 | `ADR-0012`; Applied Physics, model and instrument contracts | `EPIC-REAL-001`; `PLAT-REAL-010..013`, `PLAT-REAL-018..020` | `TEST-REQ-047`; threshold failure/interconnect/source/instrument evidence | G4 |
| REQ-048 | User architecture brief; PDF pp. 2, 13-21, 26-29, 31-37 | `ADR-0013`; `HIERARCHICAL_MODEL_AND_LIBRARY_ARCHITECTURE` | `EPIC-LIB-001`; `PLAT-LIB-001..002` | `TEST-REQ-048`; kind/DAG/exact-revision/cycle suite | G1/G4 |
| REQ-049 | User architecture brief; PDF pp. 6-8, 20, 26-27, 32-36 | `ADR-0020`; hierarchy and import contracts | `EPIC-LIB-001`, `EPIC-IMP-001`; `PLAT-LIB-003..004`, `PLAT-LIB-014` | `TEST-REQ-049`; bounded inheritance and ingestion suite | G1/G7 |
| REQ-050 | User architecture brief; PDF pp. 22-23, 26-32 | `ADR-0014`; hierarchy, package, pin and binding contracts | `EPIC-LIB-001`, `EPIC-SYM-001`; `PLAT-LIB-005..007` plus applicable package tasks | `TEST-REQ-050`; type separation/package-content/pin-equivalence suite | G1 |
| REQ-051 | User architecture brief; PDF pp. 16, 21, 26-27, 29, 31-37 | `ADR-0013`, `ADR-0014`; hierarchy and project-format contracts | `EPIC-LIB-001`, `EPIC-PROJ-001`; `PLAT-LIB-008` | `TEST-REQ-051`; exact board composition and board-not-package suite | G1 |
| REQ-052 | User architecture brief; PDF pp. 16-21, 25-29, 35-37, 40 | `ADR-0013`, `ADR-0018`; hierarchy/project-format contracts | `EPIC-LIB-001`, `EPIC-PROJ-001`; `PLAT-LIB-009`, `PLAT-LIB-011` | `TEST-REQ-052`; immutable system/project composition and round trip | G1/G9 |
| REQ-053 | User architecture brief; PDF pp. 20-21, 26-28, 35-37, 40-41 | `ADR-0013`, `ADR-0020`; hierarchy, model and result contracts | `EPIC-LIB-001`, `EPIC-QA-001`; `PLAT-LIB-010` | `TEST-REQ-053`; bidirectional lineage and missing-lineage rejection | G1/every release |
| REQ-054 | User architecture brief; PDF pp. 25-29, 31-32, 39-40 | `ADR-0015`; `DATA_DRIVEN_LIBRARY_AND_STORAGE_ARCHITECTURE`, system/API contracts | `EPIC-DATA-001`; `PLAT-DATA-002`, `PLAT-DATA-008` | `TEST-REQ-054`; resolved-bundle and engine/database independence audit | G1 |
| REQ-055 | User architecture brief; PDF pp. 25-26, 31-32, 39 | `ADR-0016`; data/storage architecture | `EPIC-DATA-001`, `EPIC-OFF-001`; `PLAT-DATA-001` | `TEST-REQ-055`; PostgreSQL/JSONB/object/IndexedDB responsibility audit | G1/G10 |
| REQ-056 | User architecture brief; PDF pp. 21-29, 35-36, 39-40 | `ADR-0019`; data, security, engine and import contracts | `EPIC-PHY-001`, `EPIC-DATA-001`, `EPIC-SEC-001`; `PLAT-PHY-010`, `PLAT-LIB-014` | `TEST-REQ-056`; arbitrary-execution rejection/allowlist sandbox suite | G1/G7 |
| REQ-057 | User architecture brief; PDF pp. 31-32, 41-42 | `ADR-0017`; data/security/local-cloud contracts | `EPIC-IDP-001`; `PLAT-IDP-001` | `TEST-REQ-057`; OIDC security contract plus guest/offline preservation | G1/G6 |
| REQ-058 | User architecture brief; PDF pp. 25-26, 31-32, 41-42 | `ADR-0017`; data, project and offline contracts | `EPIC-IDP-001`, `EPIC-OFF-001`; `PLAT-IDP-002..004` | `TEST-REQ-058`; non-destructive migration/conflict/quota/offline suite | G1/G6 |
| REQ-059 | User architecture brief; PDF pp. 26-28, 31-32, 40-41 | `ADR-0018`; hierarchy, data and project contracts | `EPIC-LIB-001`, `EPIC-DATA-001`; `PLAT-LIB-011..012`, `PLAT-DATA-003` | `TEST-REQ-059`; published mutation rejection/content identity/supersession | G1 |
| REQ-060 | User architecture brief; PDF pp. 26-27, 31-32, 40-42 | `ADR-0018`; data/security contracts | `EPIC-DATA-001`; `PLAT-DATA-003..005` | `TEST-REQ-060`; system steward and private-user permission matrix | G1/G10 |
| REQ-061 | User architecture brief; PDF pp. 26-28, 31-32, 40-42 | `ADR-0018`; data/library lifecycle contract | `EPIC-DATA-001`, `EPIC-LIB-001`; `PLAT-DATA-006..007`, `PLAT-LIB-012` | `TEST-REQ-061`; hard-delete rejection/soft-delete/reverse dependencies | G1 |
| REQ-062 | User architecture brief; PDF pp. 25-29, 31-32, 39-42 | `ADR-0015`, `ADR-0018`; data and API contracts | `EPIC-DATA-001`; `PLAT-DATA-002..007` | `TEST-REQ-062`; operation/schema/auth/concurrency/idempotency/audit suite | G1/G10 |
| REQ-063 | User architecture brief; PDF pp. 20-21, 26-28, 35-36, 39-40 | `ADR-0010`, `ADR-0019`, `ADR-0020`; import/security/license contracts | `EPIC-LIB-001`, `EPIC-IMP-001`, `EPIC-SEC-001`; `PLAT-LIB-014` | `TEST-REQ-063`; source/hash/license/trust/parser/sandbox quarantine suite | G1/G7 |

## External-engine and R11 extension traceability

These rows supplement the primary requirement rows above and prove that the external analog and R11 work is neither orphaned nor hidden inside generic cloud tasks.

| Epic | Requirements covered by card metadata | Atomic tasks | Stable and derived tests | Gate |
|---|---|---|---|---|
| `EPIC-EXT-001` | REQ-007..011, REQ-014, REQ-017, REQ-024, REQ-029, REQ-030, REQ-032, REQ-033, REQ-035, REQ-041..043, REQ-049, REQ-053, REQ-056, REQ-063 | `PLAT-EXT-001..018` at R3; `PLAT-EXT-019..021` at R7 | Applicable `TEST-REQ-*`; `TEST-PLAT-EXT-001..021-ACCEPTANCE/FAILURE` | G3/G7 |
| `EPIC-HPC-001` | REQ-006, REQ-007, REQ-010, REQ-013, REQ-015, REQ-017, REQ-019, REQ-024, REQ-029, REQ-030, REQ-032, REQ-033, REQ-035, REQ-042, REQ-043, REQ-045, REQ-046, REQ-053, REQ-055, REQ-056, REQ-059, REQ-061, REQ-063 | `PLAT-HPC-001..011` | Applicable `TEST-REQ-*`; `TEST-PLAT-HPC-001..011-ACCEPTANCE/FAILURE` | G11 |

## Architecture-brief requirement-to-risk crosswalk

| Requirement | Governed risks |
|---|---|
| REQ-039 | RSK-046, RSK-048, RSK-057, RSK-060 |
| REQ-040 | RSK-039, RSK-046, RSK-057, RSK-058, RSK-059, RSK-060, RSK-067 |
| REQ-041 | RSK-038, RSK-047, RSK-057 |
| REQ-042 | RSK-043, RSK-044, RSK-045, RSK-047, RSK-049, RSK-057 |
| REQ-043 | RSK-002, RSK-046, RSK-047, RSK-048, RSK-057, RSK-059, RSK-063 |
| REQ-044 | RSK-002, RSK-048, RSK-055, RSK-057, RSK-060 |
| REQ-045 | RSK-009, RSK-046, RSK-047, RSK-048, RSK-055 |
| REQ-046 | RSK-046, RSK-047, RSK-048, RSK-055 |
| REQ-047 | RSK-009, RSK-046, RSK-047, RSK-048 |
| REQ-048 | RSK-039, RSK-057, RSK-058 |
| REQ-049 | RSK-037, RSK-038, RSK-045, RSK-058 |
| REQ-050 | RSK-031, RSK-036, RSK-040 |
| REQ-051 | RSK-031, RSK-036, RSK-039, RSK-040 |
| REQ-052 | RSK-052, RSK-054, RSK-058, RSK-064 |
| REQ-053 | RSK-020, RSK-052, RSK-057, RSK-058, RSK-059, RSK-064 |
| REQ-054 | RSK-041, RSK-053, RSK-056, RSK-060 |
| REQ-055 | RSK-015, RSK-050, RSK-051, RSK-056, RSK-060, RSK-065 |
| REQ-056 | RSK-010, RSK-042, RSK-043, RSK-059, RSK-067 |
| REQ-057 | RSK-017, RSK-051, RSK-060 |
| REQ-058 | RSK-015, RSK-051, RSK-054 |
| REQ-059 | RSK-052, RSK-054, RSK-058, RSK-064 |
| REQ-060 | RSK-017, RSK-024, RSK-049, RSK-052 |
| REQ-061 | RSK-039, RSK-052, RSK-054 |
| REQ-062 | RSK-041, RSK-052, RSK-053, RSK-060 |
| REQ-063 | RSK-010, RSK-011, RSK-043, RSK-044, RSK-045, RSK-049, RSK-059, RSK-067 |

## Audit rules

1. Stable IDs are never reused or silently renumbered.
2. Every `Done` task must link current evidence; a task title alone is not evidence.
3. Every released component and package must identify the exact golden fixture/assertions it passes.
4. A requirement may have several release gates; later gates cannot invalidate evidence retained by an earlier compatible schema/model version.
5. Any accepted ADR that changes a row must update this matrix in the same change.
