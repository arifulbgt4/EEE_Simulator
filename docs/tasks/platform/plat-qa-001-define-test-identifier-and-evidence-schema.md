# PLAT-QA-001 - Define test identifier and evidence schema

## Metadata

| Field | Value |
|---|---|
| Status | Ready |
| Epic | [EPIC-QA-001](../epics/epic-qa-001.md) |
| Release | R0 |
| Requirements | REQ-017, REQ-022, REQ-023, REQ-034, REQ-035, REQ-036, REQ-037, REQ-038 |
| Concern | `define_test_identifier_and_evidence_schema` |
| Effort | S |
| Depends on | None - R0 root task; G0 is this epic's exit gate |

## Objective

Define test identifier and evidence schema. Deliver one reviewable outcome that satisfies the named requirements without expanding into adjacent concerns.

## Context to read

- [Test and validation strategy](../../quality/TEST_AND_VALIDATION_STRATEGY.md)
- [Source and Evidence Policy](../../SOURCE_AND_EVIDENCE_POLICY.md)
- [Product requirements](../../PRODUCT_REQUIREMENTS.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)
- [Relevant accepted ADRs](../../decisions/)

## Exact prerequisites

- `None - R0 root task; G0 is this epic's exit gate`

This is the sole R0 root task: it has no predecessor task, gate, versioned artifact, or completion record. Its `Ready` state comes only from the documentation-only root exception in `docs/tasks/ATOMIC_TASK_CONTRACT.md`; G0 is an output of this epic and MUST NOT be treated as an input prerequisite.

## Public contracts

- `docs/quality/TEST_AND_VALIDATION_STRATEGY.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/tasks/ATOMIC_TASK_CONTRACT.md`

## Inputs

- Normative input: `docs/quality/TEST_AND_VALIDATION_STRATEGY.md` clauses governing **test identifier and evidence schema**, together with every acceptance obligation in REQ-017, REQ-022, REQ-023, REQ-034, REQ-035, REQ-036, REQ-037, REQ-038.
- Root-task input: `None - R0 root task; G0 is this epic's exit gate` declares that no completed predecessor artifact is required or permitted. The accepted R0 documentation inventory, registry snapshots, and requirement set are the only baseline inputs; `PLAT_QA_001_BASELINE_INCOMPLETE` is raised if one is missing.
- Domain input for `define_test_identifier_and_evidence_schema`: stable requirement, task, test and gate IDs, registry records, fixtures, expected envelopes, evidence manifests, and release policies; the fixture manifest enumerates the consumed fields and pins each value to the immutable project/task revision used by PLAT-QA-001.
- Evidence input: `TEST-PLAT-QA-001-ACCEPTANCE` receives one minimal valid and one declared boundary fixture, while `TEST-PLAT-QA-001-FAILURE` receives every named invalid/failure case in this card.

## Allowed files

- `docs/tasks/platform/plat-qa-001-define-test-identifier-and-evidence-schema.md`
- `docs/tasks/epics/epic-qa-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/quality/TEST_AND_VALIDATION_STRATEGY.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/RISK_REGISTER.md`

This documentation-only R0 root is `Ready` under the explicit exception in the Atomic Task Contract: the paths above are its complete documentation/evidence allowlist, and no application source or runtime-test path is required before G0. This card does not authorize application code, package configuration, migrations, or deployment assets.

## Reference data and test IDs

- Normative reference: `docs/quality/TEST_AND_VALIDATION_STRATEGY.md` plus the exact requirements listed in metadata.
- `TEST-PLAT-QA-001-ACCEPTANCE`
- `TEST-PLAT-QA-001-FAILURE`

## Technical source qualification

- External technical source requirement: `not_applicable` for this documentation-governance concern.
- Rationale: this task defines only the repository's internal stable-ID and evidence-record schema from already accepted repository documents. It asserts no governing equation, material/device property, external standard content, engine/browser behavior, numerical accuracy, license right, security guarantee, or physical result.
- Technical examples are opaque schema fixtures and cannot be used as evidence that their subject matter is true. Any future change that introduces an external technical assertion must return this card to `Planned` until the exact applicable official/primary or approved reference evidence is recorded. Source PDF citations never satisfy that requirement.

## Deliverables

- A versioned normative contract named `define_test_identifier_and_evidence_schema` for **test identifier and evidence schema**, with explicit inputs, outputs, state ownership, units, defaults, limits, version/compatibility rules, and stable diagnostics.
- Observable outcome: the valid `PLAT-QA-001` fixture resolves every required field, default, invariant, version rule, and public input/output without ambiguity; the published outcome is machine-auditable test evidence and release disposition.
- Failure outcome: `PLAT_QA_001_SCHEMA_INVALID` and `PLAT_QA_001_COMPATIBILITY_CONFLICT` terminate or reject at the documented boundary without silent fallback, partial authoritative state, or lost provenance.
- Evidence artifact: `TEST-PLAT-QA-001-ACCEPTANCE` and `TEST-PLAT-QA-001-FAILURE` record root baseline identity, exact fixture input, expected and actual output, diagnostic codes, limits/tolerances, requirement set REQ-017, REQ-022, REQ-023, REQ-034, REQ-035, REQ-036, REQ-037, REQ-038, and release disposition.

## Documentation updates

- This task card, `docs/tasks/epics/epic-qa-001.md`, `docs/tasks/platform/INDEX.md`, and `docs/tasks/TASK_INDEX.md`.
- `docs/quality/TEST_AND_VALIDATION_STRATEGY.md` and `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md` when public behavior changes.
- The named test evidence, risk record, and applicable release checklist.

## Allowed scope

- Only the contract, behavior, tests, and documentation directly necessary for this task title.

## Forbidden scope

- Do not redesign accepted public contracts, combine another independent concern, silently relax accuracy/security/accessibility budgets, or mark dependent tasks complete.

## Required behavior and edge cases

- `PLAT_QA_001_NOMINAL`: processing a minimal valid **test identifier and evidence schema** fixture resolves every required field, default, invariant, version rule, and public input/output without ambiguity; rerunning the same revision, configuration, seed, and dependency versions produces the same declared outcome.
- `PLAT_QA_001_BOUNDARY`: the **test identifier and evidence schema** fixture matrix covers empty corpus, first/last registry entry, tolerance edge, expected failure, deferred model, and release-blocking severity boundary; it records each exact inclusive/exclusive limit and expected state or diagnostic, and marks a contract-declared unsupported case explicitly instead of skipping it.
- `PLAT_QA_001_SCHEMA_INVALID`: reject a duplicate or orphan ID, missing expected result, stale digest, undocumented tolerance, absent provenance, or ambiguous pass criterion before authoritative state is published; the diagnostic identifies the field/entity, rejected value, and remediation.
- `PLAT_QA_001_BASELINE_INCOMPLETE`: reject the root task when a required R0 document, registry snapshot, stable-ID namespace, or requirement record is absent or internally inconsistent; no predecessor artifact is invented and no later gate is treated as complete.
- `PLAT_QA_001_COMPATIBILITY_CONFLICT`: contain false pass, untested released model, traceability gap, reference-engine divergence, evidence tampering, or incomplete release bundle with bounded time/memory/output, deterministic cleanup or rollback, retained correlation/provenance, and no main-thread blocking or sandbox escape.

## Acceptance tests

1. `TEST-PLAT-QA-001-ACCEPTANCE` proves that **Define test identifier and evidence schema** resolves every required field, default, invariant, version rule, and public input/output without ambiguity, produces machine-auditable test evidence and release disposition, and satisfies every metadata requirement: REQ-017, REQ-022, REQ-023, REQ-034, REQ-035, REQ-036, REQ-037, REQ-038.
2. `TEST-PLAT-QA-001-FAILURE` executes `PLAT_QA_001_SCHEMA_INVALID`, `PLAT_QA_001_BASELINE_INCOMPLETE`, and `PLAT_QA_001_COMPATIBILITY_CONFLICT` and observes the exact rejection, rollback/cleanup, diagnostic target, and provenance behavior specified above.
3. The evidence names `docs/quality/TEST_AND_VALIDATION_STRATEGY.md` and root declaration `None - R0 root task; G0 is this epic's exit gate`; it records immutable R0 document and registry digests, configuration plus seed or an explicit no-seed declaration, expected/actual output, known limitations, and the fact that no predecessor artifact exists. An identical rerun meets the declared determinism or tolerance class.
4. The PLAT-QA-001 card, its epic, test registry entries `TEST-PLAT-QA-001-ACCEPTANCE` and `TEST-PLAT-QA-001-FAILURE`, requirement links REQ-017, REQ-022, REQ-023, REQ-034, REQ-035, REQ-036, REQ-037, REQ-038, risk record, and release checklist resolve bidirectionally with no unrelated scope or lifecycle metadata change.

## Known limitations

- `Ready` authorizes only the documentation/evidence-schema work in the allowlist. It does not prove that any stable test has executed or passed, that any technical source has been verified, that any implementation exists, or that G0 or a later release has passed.
- The schema can classify and retain evidence but cannot by itself establish numerical correctness, physical accuracy, security, accessibility, performance, license rights, or reproducibility.

## Definition of Done

- [ ] Deliverable and failure behavior match the normative documents.
- [ ] Acceptance evidence is reproducible and linked.
- [ ] No unrelated concern was implemented or silently deferred.
- [ ] Documentation, traceability, risks, and release evidence are current.
