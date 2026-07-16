# Release Gates

## Gate semantics

- `Planned`: scope and dependencies are documented.
- `Ready`: all decisions, inputs, and acceptance criteria are available.
- `In Progress`: implementation is active; scope is frozen.
- `Review`: deliverables and evidence exist.
- `Done`: evidence passes and traceability is updated.
- `Blocked`: a named external dependency or decision prevents progress.
- `Deferred`: intentionally outside the active roadmap with an entry criterion.

No phase is considered released because its feature list appears complete. Release requires the corresponding evidence checklist in `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`.

## Gate table

| Gate | Required predecessor | Required evidence | Product milestone |
|---|---|---|---|
| G0 Documentation | None | Complete documents, component/package/model registries, Applied Physics contracts, tasks, tests, and traceability | Implementation may begin |
| G1 Editor foundation | G0 | Accessible editing, dual schematic/physical views, reusable package pin mapping, and `.eesim` round trip | Internal alpha |
| G2 Linear analog | G1 | GRC-001..010 applicable subset and performance | Engineering preview |
| G3 Nonlinear analog | G2 | GRC-011..020 and convergence diagnostics | Closed alpha |
| G4 Applied Physics and Real-World Fidelity | G3 | Preserved GRC-021..026 scope; GRC-055..066 physical fixtures; model/units/validity/provenance/accuracy/uncertainty conformance; electrothermal/environment/manufacturing/aging/failure/interconnect/source/instrument evidence | Closed beta |
| G5 Digital/mixed | G4 | GRC-027..034 and deterministic scheduler; no bypass of applicable R4 loading, threshold, source, interconnect, or uncertainty behavior | Public beta candidate |
| G6 Electronics MVP | G5 | Full MVP checklist plus production-hardened optional personal persistence; guest/offline remains supported | First production release |
| G7 Complete catalog | G6 | GRC-023..025, GRC-036..040, family fixtures, and 157/494 production coverage | Electronics 1.0 |
| G8 Educational CPU | G7 | GRC-035, GRC-041..043, and ISA suite | Computer education preview |
| G9 RTL/full computer | G8 | GRC-044..045 and sandbox evidence | Computer education 1.0 |
| G10 Cloud/collaboration | G6 | Security, tenancy, operations and recovery | Hosted service GA |
| G11 HPC | G10 | Isolation, reproducibility, license review | Research compute GA |
| G12 Architecture | G9, G10 | GRC-046..047 | Architecture research preview |
| G13 GPU/research | G11, G12 | GRC-048 and research datasets | Research extension release |

## Change control

The roadmap contains exactly R0 through R13. `ADR-0012` renames and expands R4 without renumbering R5 through R13 or creating R14. G4 is a mandatory predecessor of G5 and G6 wherever realistic behavior is required.

- A gate may tighten acceptance criteria without an ADR when the change cannot invalidate existing users or models.
- Scope, public contracts, fidelity semantics, accuracy relaxation, license boundary, or compatibility changes require an ADR.
- A removed requirement or component remains in history with replacement/deprecation rationale; it is never silently deleted from traceability.
- Emergency security releases may bypass feature completeness but never security validation, authorization, or rollback evidence.
