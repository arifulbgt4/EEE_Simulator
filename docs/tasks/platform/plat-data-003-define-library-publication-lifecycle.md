# PLAT-DATA-003 - Define library publication lifecycle

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-DATA-001](../epics/epic-data-001.md) |
| Release | R1 |
| Requirements | REQ-054, REQ-055, REQ-056, REQ-059, REQ-060, REQ-061, REQ-062, REQ-063 |
| Concern | `library_publication_lifecycle` |
| Effort | S |
| Depends on | PLAT-DATA-002 |

## Objective

Move drafts through validation review immutable publication and retirement. This card owns exactly one public concern and no implementation is authorized while its status is `Planned`.

## Context to read

- [Primary architecture contract](../../architecture/DATA_DRIVEN_LIBRARY_AND_STORAGE_ARCHITECTURE.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)
- [Accepted decisions](../../decisions/)
- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)

## Exact prerequisites

- `PLAT-DATA-002`

The named task or gate must be complete with immutable evidence before this card can become `Ready`. Epic membership, a later gate, or an unversioned draft is not a substitute.

## Public contracts

- `docs/architecture/DATA_DRIVEN_LIBRARY_AND_STORAGE_ARCHITECTURE.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`
- `docs/quality/test-registry.yaml`

## Exact inputs

- The accepted clauses for REQ-054, REQ-055, REQ-056, REQ-059, REQ-060, REQ-061, REQ-062, REQ-063, ADR-0011 through ADR-0020 where applicable, and exact predecessor evidence from `PLAT-DATA-002`.
- Stable logical IDs, immutable revision IDs, schema versions, content hashes, dimensions, provenance, trust/validation state, and limitations for every referenced record.
- One minimal valid fixture, one exact boundary fixture, and every invalid/failure case named below.

No numerical equation is introduced by this planning card unless the primary contract explicitly names it. Any later equation or algorithm artifact must declare dimensions, validity domain, approximation, numerical method, source, and evidence before this task is promoted.

## Allowed files

- `docs/tasks/platform/plat-data-003-define-library-publication-lifecycle.md`
- `docs/tasks/epics/epic-data-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/DATA_DRIVEN_LIBRARY_AND_STORAGE_ARCHITECTURE.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

No application source, package configuration, database migration, identity-provider configuration, deployment asset, or runtime test path is authorized while this card is `Planned`. Exact source/test paths may be appended only under completed `PLAT-GOV-001` without widening this concern.

## Expected outputs and diagnostics

- A versioned, schema-valid deliverable for `library_publication_lifecycle` with exact inputs, outputs, defaults, dimensions, limits, state ownership, compatibility, provenance, and known limitations.
- `PLAT_DATA_003_NOMINAL`: the valid fixture resolves deterministically to the specified outcome and retains complete lineage.
- `PLAT_DATA_003_BOUNDARY`: every inclusive/exclusive limit and unsupported case returns its declared state or diagnostic.
- `PUBLICATION_TRANSITION_INVALID`: invalid input is rejected before authoritative publication or execution; the diagnostic names the entity, field/reference, rejected value, and remediation.
- `PLAT_DATA_003_PREREQUISITE_MISMATCH`: incompatible or missing predecessor/schema revision is rejected without implicit migration.

## Forbidden scope

- Do not combine an adjacent concern, mutate an accepted ID, relax a gate, hard-delete a referenced revision, infer missing units or provenance, execute arbitrary stored content, couple the engine to a storage technology, or claim unevidenced market/accuracy coverage.
- Do not mark this or dependent implementation work `Ready` or `Done` from documentation existence alone.

## Acceptance tests

1. `TEST-PLAT-DATA-003-ACCEPTANCE` validates the nominal and exact boundary fixtures against REQ-054, REQ-055, REQ-056, REQ-059, REQ-060, REQ-061, REQ-062, REQ-063, the primary contract, schema version, revision IDs, hashes, dimensions, provenance, and expected outcome.
2. `TEST-PLAT-DATA-003-FAILURE` exercises `PUBLICATION_TRANSITION_INVALID` and the prerequisite mismatch path; no partial authoritative state, silent fallback, unsafe execution, broken historical reference, or lost audit record is allowed.
3. Repeating the same fixture with the same revisions, configuration, seed or explicit no-seed declaration produces the same deterministic classification and evidence digest.
4. The task card, epic, requirement rows, stable tests, risk, release checklist, and affected coverage/registry records resolve bidirectionally with no count or link drift.

## Documentation and evidence updates

- Update this card, its epic, both task indexes, requirement traceability, test registry/evidence, risk record, and the R1 release checklist together.
- Record exact commands, fixture identities, expected/actual results, evidence digests, residual limitations, migration impact, and release disposition.

## Definition of Done

- [ ] The single deliverable and every diagnostic match the normative contracts.
- [ ] Nominal, boundary, invalid, compatibility, security, and applicable accessibility/performance evidence is reproducible.
- [ ] Immutable references, provenance, dimensions, accuracy/uncertainty, and limitations are complete where applicable.
- [ ] Documentation, tests, traceability, risks, counts, and release evidence are synchronized.
- [ ] No forbidden scope or unsupported claim was introduced.
