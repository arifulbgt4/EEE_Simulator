# PLAT-GOV-001 - Define repository layout and ownership boundaries

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-GOV-001](../epics/epic-gov-001.md) |
| Release | R1 |
| Requirements | REQ-034, REQ-035 |
| Concern | `define_repository_layout_and_ownership_boundaries` |
| Effort | S |
| Depends on | Gate G0 documentation baseline |

## Objective

Publish one normative repository-layout and ownership document that assigns every planned source, test, schema, generated-artifact, documentation, third-party, and operations area to a clear owner and change-review boundary.

## Context to read

- [docs/START_HERE.md](../../START_HERE.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `Gate G0 documentation baseline`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md` clauses governing **repository layout and ownership boundaries**, together with every acceptance obligation in REQ-034 and REQ-035.
- Prerequisite input: the completion evidence for `Gate G0 documentation baseline`, including its accepted document inventory and unresolved exceptions; `PLAT_GOV_001_PREREQUISITE_MISSING` is raised when that evidence is absent.
- Repository input for `define_repository_layout_and_ownership_boundaries`: `README.md`, `AGENTS.md`, `CONTRIBUTING.md`, `docs/START_HERE.md`, ADR-0002, ADR-0003, ADR-0008, ADR-0010, and the architecture deliverable tree at one immutable repository revision.
- Ownership input: every planned frontend, Rust/WASM, Worker, schema/catalog, test/evidence, cloud-service, external-adapter, infrastructure, generated-artifact, and third-party area, with one proposed canonical path, owner, reviewer, dependency direction, and authored/generated classification.

## Allowed files

- `docs/tasks/platform/plat-gov-001-define-repository-layout-and-ownership-boundaries.md`
- `docs/tasks/epics/epic-gov-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`
- `README.md`
- `AGENTS.md`
- `CONTRIBUTING.md`
- `docs/START_HERE.md`
- `docs/architecture/REPOSITORY_LAYOUT_AND_OWNERSHIP.md`

Only the paths above are authorized; this documentation task does not authorize application code, package configuration, migrations, or deployment assets.

## Reference data and test IDs

- Normative reference: `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-GOV-001-ACCEPTANCE`
- `TEST-PLAT-GOV-001-FAILURE`

## Deliverables

- Create the `define_repository_layout_and_ownership_boundaries` normative artifact at `docs/architecture/REPOSITORY_LAYOUT_AND_OWNERSHIP.md` with a canonical directory tree, purpose of every top-level area, package/module boundaries, allowed dependency directions, generated-versus-authored rules, test/evidence locations, public/private artifact rules, secret exclusions, external-engine/process boundaries, and ownership/reviewer matrix.
- Update `README.md`, `docs/START_HERE.md`, `AGENTS.md`, and `CONTRIBUTING.md` so contributors reach that document and do not invent a competing layout.
- Update this card, both task indexes, its epic, requirement traceability, release evidence, and risk record without creating application code, package configuration, migrations, or deployment assets.

## Documentation updates

- This task card, `docs/tasks/epics/epic-gov-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_GOV_001_NOMINAL`: every planned subsystem has exactly one authoritative home and named ownership/review responsibility; cross-cutting contracts identify one canonical owner plus named consumers.
- `PLAT_GOV_001_BOUNDARY`: generated files, vendored dependencies, imported models, large fixture data, secrets, local caches, build output, and user projects each have an explicit allowed or forbidden location at the authored/generated and public/private boundaries.
- `PLAT_GOV_001_DEPENDENCY_BOUNDARY`: the dependency rules prevent UI code from owning solver semantics, core code from importing React/cloud clients, and Apache-2.0 core code from absorbing isolated GPL/mixed-license engines.
- `PLAT_GOV_001_SCHEMA_INVALID`: ambiguous ownership, duplicate canonical locations, writable generated sources, or undocumented secret storage is rejected as a release-blocking documentation error with the conflicting paths and owners named.
- `PLAT_GOV_001_PREREQUISITE_MISMATCH`: a layout derived from an incomplete or different `Gate G0 documentation baseline` is rejected before publication; no missing baseline document is silently assigned a path.
- `PLAT_GOV_001_COMPATIBILITY_CONFLICT`: a proposed path that violates ADR-0002/0003/0008/0010 dependency or external-engine boundaries is rejected without changing the accepted architecture.

## Acceptance tests

1. `TEST-PLAT-GOV-001-ACCEPTANCE` proves that **Define repository layout and ownership boundaries** maps every planned area to exactly one documented repository location, owner, and reviewer with no broken navigation link and satisfies every metadata requirement: REQ-034, REQ-035.
2. `TEST-PLAT-GOV-001-FAILURE` executes `PLAT_GOV_001_SCHEMA_INVALID`, `PLAT_GOV_001_PREREQUISITE_MISMATCH`, and `PLAT_GOV_001_COMPATIBILITY_CONFLICT`; duplicate ownership, secret placement, generated-source editing, and GPL-engine-in-core fixtures are each rejected by the named rule.
3. The evidence names `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`, prerequisite `Gate G0 documentation baseline`, the immutable repository revision, ADR-0002/0003/0008/0010, and every audited path; it introduces no application code, package configuration, migration, or deployment artifact.
4. Requirement -> epic -> task -> test -> release traceability and the R0/R1 handoff records agree with no unrelated scope change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
