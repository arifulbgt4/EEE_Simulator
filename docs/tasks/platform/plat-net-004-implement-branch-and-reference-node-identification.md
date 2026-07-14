# PLAT-NET-004 - Implement branch and reference-node identification

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-NET-001](../epics/epic-net-001.md) |
| Release | R2 |
| Requirements | REQ-008, REQ-023 |
| Concern | `implement_branch_and_reference_node_identification` |
| Effort | S |
| Depends on | PLAT-NET-003 |

## Objective

Implement branch and reference-node identification. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [docs/architecture/SIMULATION_ENGINE.md](../../architecture/SIMULATION_ENGINE.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `PLAT-NET-003`

The named task or gate must be complete before this card may become `Ready`; a later sequential task cannot use an epic title as a substitute dependency.

## Public contracts

- `docs/architecture/SIMULATION_ENGINE.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/architecture/SIMULATION_ENGINE.md` clauses governing **branch and reference-node identification**, together with every acceptance obligation in REQ-008, REQ-023.
- Prerequisite input: the completion evidence for `PLAT-NET-003`, including its artifact versions, digests, unresolved limitations, and compatibility range; `PLAT_NET_004_PREREQUISITE_MISSING` is raised if that evidence is absent.
- Domain input for `implement_branch_and_reference_node_identification`: component and pin IDs, net segments, junctions, labels, reference domains, hierarchy ports, adapters, and topology rules; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-NET-004.
- Evidence input: `TEST-PLAT-NET-004-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-NET-004-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-net-004-implement-branch-and-reference-node-identification.md`
- `docs/tasks/epics/epic-net-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/SIMULATION_ENGINE.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application/source path is authorized while this card is `Planned`. Promotion to `Ready` must append exact source and test paths from completed `PLAT-GOV-001` without widening this concern.

## Reference data and test IDs

- Normative reference: `docs/architecture/SIMULATION_ENGINE.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-NET-004-ACCEPTANCE`
- `TEST-PLAT-NET-004-FAILURE`

## Deliverables

- An implementation behavior and public-interface record named `implement_branch_and_reference_node_identification` for **branch and reference-node identification**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-NET-004` fixture accepts the minimal valid input and produces the documented deterministic state transition or output; the published outcome is canonical deterministic topology, netlist projection, and structural diagnostics.
- Failure outcome: `PLAT_NET_004_INVALID_INPUT` and `PLAT_NET_004_EXECUTION_FAILURE` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-NET-004-ACCEPTANCE` and `TEST-PLAT-NET-004-FAILURE` record prerequisite identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-008, REQ-023, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-net-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/architecture/SIMULATION_ENGINE.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_NET_004_NOMINAL`: processing a minimal valid **branch and reference-node identification** fixture accepts the minimal valid input and produces the documented deterministic state transition or output; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_NET_004_BOUNDARY`: the **branch and reference-node identification** fixture matrix covers wire crossing, dangling optional pin, one-pin net, net tie, scoped label edge, and hierarchy boundary; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_NET_004_INVALID_INPUT`: reject a duplicate stable ID, incompatible domain connection, unresolved label, missing reference, illegal junction, or hierarchy cycle before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_NET_004_PREREQUISITE_MISMATCH`: reject a prerequisite artifact, schema, model, engine, or contract version outside the range declared by `PLAT-NET-003`; no implicit migration or downgrade is allowed.
- `PLAT_NET_004_EXECUTION_FAILURE`: contain unintended net merge or split, floating required node, direct source short, non-deterministic ordering, or origin-map loss with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-NET-004-ACCEPTANCE` proves that **Implement branch and reference-node identification** accepts the minimal valid input and produces the documented deterministic state transition or output, produces canonical deterministic topology, netlist projection, and structural diagnostics, and satisfies every metadata requirement: REQ-008, REQ-023.
2. `TEST-PLAT-NET-004-FAILURE` executes `PLAT_NET_004_INVALID_INPUT`, `PLAT_NET_004_PREREQUISITE_MISMATCH`, and `PLAT_NET_004_EXECUTION_FAILURE` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/architecture/SIMULATION_ENGINE.md`, prerequisite `PLAT-NET-003`, immutable fixture and dependency digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, and known limitations; an identical rerun meets the declared determinism or tolerance class.
4. The PLAT-NET-004 card, its epic, test registry entries `TEST-PLAT-NET-004-ACCEPTANCE` and `TEST-PLAT-NET-004-FAILURE`, requirement links REQ-008, REQ-023, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
