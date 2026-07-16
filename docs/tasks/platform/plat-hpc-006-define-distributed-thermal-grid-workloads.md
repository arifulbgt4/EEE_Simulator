# PLAT-HPC-006 - Define distributed thermal-grid workloads

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-HPC-001](../epics/epic-hpc-001.md) |
| Release | R11 |
| Requirements | REQ-010, REQ-015, REQ-017, REQ-030, REQ-043, REQ-045, REQ-053, REQ-059 |
| Concern | `distributed_thermal_grid_workloads` |
| Effort | S |
| Depends on | PLAT-HPC-004; PLAT-REAL-006; PLAT-REAL-021 |
| Blocks | PLAT-HPC-007, PLAT-HPC-011 |

## Objective

Define one distributed thermal-grid workload contract that partitions an immutable thermal problem, exchanges boundary state in deterministic phases, preserves units and physical lineage, and validates convergence and energy balance against an accepted single-domain or independent reference within a declared envelope.

## Context to read

- [Applied Physics and Real-World Fidelity](../../architecture/APPLIED_PHYSICS_AND_REAL_WORLD_FIDELITY.md), thermal/environment coupling
- [Multi-Fidelity and Co-Simulation](../../architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md), fidelity boundaries
- [Simulation Engine](../../architecture/SIMULATION_ENGINE.md), electrothermal scheduling
- [Numerical Accuracy Targets](../../quality/NUMERICAL_ACCURACY_TARGETS.md)
- [Physical Benchmark and Correlation Contract](../../quality/PHYSICAL_BENCHMARK_AND_CORRELATION_CONTRACT.md)

## Exact prerequisites

- Completed `PLAT-REAL-006` ambient/thermal-boundary and coupling contracts.
- Completed `PLAT-REAL-021` uncertainty/correlation and physical-lineage contracts.
- Accepted MPI/HPC profile and rank-failure rules from `PLAT-HPC-004`.

## Public contracts

- `ThermalGridWorkload`
- `ThermalDomainPartitionPlan`
- `ThermalCellIdentity`
- `ThermalBoundaryExchange`
- `ThermalCouplingIteration`
- `ThermalConvergenceReport`
- `ThermalGridResultManifest`

All quantities use canonical SI dimensions. A partition fixes global cell/element IDs, ownership, ghost/interface entities, material and boundary revisions, source mapping, time integration/numerical method, exchange order, convergence norm, absolute/relative tolerance, maximum iterations, conservation tolerance, and result probes.

## Exact inputs, equations, and reference data

- Immutable geometry/grid/mesh and coordinate revision; materials; density `rho`, heat capacity `c_p`, conductivity tensor/scalar `k`; heat sources `q`; initial `T`; ambient/environment; Dirichlet/Neumann/Robin/contact/radiative boundaries when supported; electrical-power coupling; timestep/schedule; solver/preconditioner; partition revision; rank mapping; convergence and conservation tolerances; checkpoint/retry policy; expected outputs; accuracy/uncertainty envelope.
- Governing basis for supported conduction is declared in the model contract, for example `rho*c_p*dT/dt = div(k*grad(T)) + q`, with every term's dimension, discretization, validity, and omitted physics explicit. This card does not claim support for a boundary type or multiphysics term unless the exact model revision does.
- Energy-balance evidence reports input energy, stored-energy change, boundary exchange/loss, and residual in joules; accepted residual thresholds are fixture-specific and never inferred from mesh size.
- Nominal fixtures: homogeneous steady conduction and transient heating with a partition boundary. Boundary fixtures: one cell/domain, minimum/maximum declared timestep/grid size, partition through material interface, zero source, insulating boundary, exact convergence threshold, and electrical/thermal exchange timestamp.
- Failure fixtures: dimensional mismatch, nonphysical material value, invalid/overlapping/gapped ownership, missing neighbor, inconsistent interface orientation/area, non-finite state, divergence, iteration/timestep underflow, rank loss, stale exchange, changed partition at restart, and conservation failure.
- Reference must be an independently reproducible analytical solution, accepted single-domain implementation, physical benchmark where applicable, or pinned primary dataset/software; simulation-to-simulation agreement alone is not physical correlation. Source PDF prose is not reference data.

## Allowed files

- `docs/tasks/platform/plat-hpc-006-define-distributed-thermal-grid-workloads.md`
- `docs/tasks/epics/epic-hpc-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/APPLIED_PHYSICS_AND_REAL_WORLD_FIDELITY.md`
- `docs/architecture/MULTI_FIDELITY_AND_CO_SIMULATION.md`
- `docs/architecture/SIMULATION_ENGINE.md`
- `docs/quality/NUMERICAL_ACCURACY_TARGETS.md`
- `docs/quality/PHYSICAL_BENCHMARK_AND_CORRELATION_CONTRACT.md`
- `docs/quality/PERFORMANCE_BENCHMARKS.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No mesh/grid solver, electrothermal runtime, MPI exchange, benchmark execution, source/test path, or cluster run is authorized while `Planned`.

## Expected outputs and known limitations

- Versioned workload/partition/cell/exchange/iteration/convergence/result schemas, dimensionally checked reference fixtures, diagnostics catalog, and single/distributed comparison evidence.
- Human-readable, non-color-only hot-spot/convergence/conservation/failure summaries with accessible tables. Only declared conduction, boundary, coupling, material, geometry, and fidelity subsets are covered.

## Required behavior and diagnostics

- `PLAT_HPC_006_NOMINAL`: partitioned and accepted reference runs preserve global identity, deterministic exchange phases, convergence classification, and declared temperature/flux/energy envelope.
- `PLAT_HPC_006_BOUNDARY`: exact grid, timestep, material, interface, iteration, convergence, temperature, power, and result-retention limits are tested with units.
- `PLAT_HPC_006_PARTITION_INVALID`: reject duplicate/gapped cell ownership, unknown neighbor, inconsistent interface, unsupported topology, or dimension mismatch before execution.
- `PLAT_HPC_006_STATE_INVALID`: reject non-finite temperature/source, nonphysical or out-of-validity material/environment values, unsupported boundary, or stale coupling timestamp.
- `PLAT_HPC_006_NON_CONVERGENT`: stop at the declared iteration/timestep boundary, retain residual history and last valid state, and never publish a converged label.
- `PLAT_HPC_006_CONSERVATION_FAILED`: publish a failed evidence state when the declared balance residual is exceeded, even if local solver residuals pass.
- `PLAT_HPC_006_RANK_OR_EXCHANGE_FAILED`: checkpoint-restart the complete compatible phase or fail it; never omit a domain or reuse stale interface state.
- `PLAT_HPC_006_REFERENCE_MISMATCH`: report metric, location/time, expected/actual, tolerance, model/numerical/reference revisions, and uncertainty without widening the accepted envelope.

## Acceptance tests and evidence

1. `TEST-PLAT-HPC-006-ACCEPTANCE` compares one-domain and multiple partition counts/orderings for the declared deterministic/tolerance class and verifies temperature, heat flux, interface continuity, convergence, and energy balance.
2. `TEST-PLAT-HPC-006-FAILURE` exercises every diagnostic plus cancellation, checkpoint boundary, corrupt exchange, rank loss, and out-of-validity environment.
3. Evidence includes grid/geometry/material/source/boundary hashes, units/dimensions, partition/rank maps, exchange/event order, solver/profile revisions, residual histories, energy budget, reference/uncertainty, resource telemetry, and limitations.
4. Physical-correlation labels require the complete benchmark contract; otherwise evidence is analytical, numerical-reference, or estimated as appropriate.

## Documentation updates on completion

- Synchronize this card/epic, indexes, physics/co-simulation/solver contracts, numerical/physical/performance evidence, tests, RTM, risks, and G11 checklist.
- Add distributed energy-balance, partition-interface, and rank-loss risk links if existing records do not cover them explicitly.

## Forbidden scope

- Do not add unsupported CFD, radiation, phase change, stress, fluid, EM, or geometry claims; each requires a separate governed model/task.
- Do not change R4 thermal physics, ignore unit/validity checks, silently relax convergence/conservation, or label numerical agreement as physical correlation.
- Do not own streaming reduction/retention, checkpoint format, storage, quota, or cost behavior defined later.

## Definition of Done

- [ ] Workload/partition/exchange/iteration/result contracts specify exact identities, SI dimensions, equations, limits, methods, and diagnostics.
- [ ] Analytical/single-domain, multi-partition, interface, convergence, conservation, boundary, rank-loss, restart, and invalid-input evidence passes.
- [ ] Accuracy, uncertainty, validity, omitted physics, and physical-correlation state are explicit.
- [ ] Central records and G11 evidence are synchronized before status advances.
- [ ] No distributed thermal implementation or run was performed by this documentation task.
