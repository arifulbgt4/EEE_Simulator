# PLAT-HPC-001 - Define G11 entry and evidence contract

## Metadata

| Field | Value |
|---|---|
| Status | Planned |
| Epic | [EPIC-HPC-001](../epics/epic-hpc-001.md) |
| Release | R11 |
| Requirements | REQ-029, REQ-030, REQ-032, REQ-035, REQ-042, REQ-053, REQ-059 |
| Concern | `g11_entry_and_evidence_contract` |
| Effort | S |
| Depends on | Gate G10 Cloud/collaboration; PLAT-API-014; PLAT-OPS-014; PLAT-SEC-015; PLAT-IMP-012 |
| Blocks | PLAT-HPC-002 through PLAT-HPC-011 |

## Objective

Define one machine-auditable G11 entry contract that accepts only complete, immutable G10, cloud-job, operations, sandbox, and SPICE-import evidence and fixes the required evidence identities for every R11 concern.

## Context to read

- [Release gates](../../planning/RELEASE_GATES.md), G10 and G11
- [Local, Cloud, and Worker Architecture](../../architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md), sections 6-12
- [API and Worker Protocols](../../architecture/API_AND_WORKER_PROTOCOLS.md)
- [Security, Privacy, and Sandboxing](../../architecture/SECURITY_PRIVACY_AND_SANDBOXING.md)
- [Atomic Task Contract](../ATOMIC_TASK_CONTRACT.md)

## Exact prerequisites

- Accepted immutable Gate G10 release decision and evidence manifest.
- `PLAT-API-014` worker-loss and duplicate-delivery recovery evidence.
- `PLAT-OPS-014` recovery and rollback game-day evidence.
- `PLAT-SEC-015` malicious archive/model/HDL corpus evidence.
- `PLAT-IMP-012` unsupported-syntax and security-diagnostic evidence for SPICE-compatible inputs.

Every prerequisite must record its stable ID, immutable revision, schema version, content hash, environment, evidence timestamp, disposition, and unresolved limitation list. A gate label without its manifest is not a prerequisite.

## Public contracts

- `G11EntryEvidence`
- `G11EvidenceRequirement`
- `G11EvidenceMatrix`
- `HpcCapabilityBaseline`
- `G11EntryDecision`

`G11EntryEvidence` contains the G10 decision reference; exact predecessor task evidence; accepted architecture, security, job-protocol, operations, license, and test contract revisions; compatibility ranges; artifact hashes; owners; expiration/review dates; open findings; and a deterministic evidence-set digest.

## Exact inputs and reference basis

- The exact G10, task, requirement, ADR, architecture, security, dependency/license, test, risk, and release-record revisions named above.
- One valid evidence fixture, one evidence-at-expiry boundary fixture, and invalid fixtures for missing hash, superseded schema, rejected license disposition, incomplete sandbox proof, open Critical finding, broken reference, and mismatched environment.
- Technical claims must come from accepted repository contracts, pinned primary engine/tool documentation, or reproducible evidence. Source PDF references are contextual provenance only and never satisfy this contract.
- This concern has no numerical equation. Its deterministic rule is: canonicalize the ordered tuple `(evidence_type, stable_id, revision_id, content_hash, disposition)` by the accepted manifest schema, sort by `(evidence_type, stable_id, revision_id)`, and hash the canonical bytes using the repository-approved digest revision. The digest algorithm/revision must be explicit; an unspecified algorithm is invalid.

## Allowed files

- `docs/tasks/platform/plat-hpc-001-define-g11-entry-and-evidence-contract.md`
- `docs/tasks/epics/epic-hpc-001.md`
- `docs/tasks/platform/INDEX.md`
- `docs/tasks/TASK_INDEX.md`
- `docs/architecture/LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md`
- `docs/architecture/API_AND_WORKER_PROTOCOLS.md`
- `docs/architecture/SECURITY_PRIVACY_AND_SANDBOXING.md`
- `docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md`
- `docs/PRODUCT_REQUIREMENTS.md`
- `docs/quality/test-registry.yaml`
- `docs/quality/REQUIREMENTS_TRACEABILITY_MATRIX.md`
- `docs/quality/RELEASE_ACCEPTANCE_CHECKLISTS.md`
- `docs/planning/DEPENDENCY_AND_LICENSE_MATRIX.md`
- `docs/planning/RISK_REGISTER.md`

No source path, test-runtime path, cluster configuration, engine binary, container image, package file, database migration, or cloud resource is authorized while this card is `Planned`.

## Expected outputs and known limitations

- Versioned schemas and examples for all five public contracts, plus one immutable evidence matrix and deterministic entry-decision digest covering every prerequisite and finding.
- A human-readable, non-color-only decision summary and machine-readable diagnostics. This card proves readiness evidence only; it neither proves R11 runtime behavior nor authorizes implementation.

## Required behavior and diagnostics

- `PLAT_HPC_001_NOMINAL`: all exact prerequisites resolve, are accepted and current, and produce one stable `G11EntryDecision: accepted` plus evidence-set digest.
- `PLAT_HPC_001_BOUNDARY`: evidence at a declared inclusive review deadline is handled exactly as specified; one tick after expiry is rejected.
- `PLAT_HPC_001_EVIDENCE_MISSING`: report every missing stable ID and expected evidence type; do not accept a partial matrix.
- `PLAT_HPC_001_EVIDENCE_STALE`: reject superseded, expired, hash-mismatched, or incompatible evidence and name the current required revision.
- `PLAT_HPC_001_LICENSE_BLOCKED`: reject an unknown, incompatible, expired, or explicitly denied external-engine license/distribution decision.
- `PLAT_HPC_001_SECURITY_BLOCKED`: reject open Critical/High mandatory findings, missing isolation proof, or a test environment weaker than the declared R11 profile.
- `PLAT_HPC_001_SOURCE_UNCONFIRMED`: reject a technical acceptance claim supported only by the Source PDF, informal prose, or an unpinned secondary source.
- Cancellation during audit publishes no accepted decision; rerun from immutable inputs yields the same classification and evidence digest.

## Acceptance tests and evidence

1. `TEST-PLAT-HPC-001-ACCEPTANCE` exercises the valid and deadline-boundary fixtures and proves exact prerequisite resolution, canonical ordering, stable digest, and accepted decision.
2. `TEST-PLAT-HPC-001-FAILURE` exercises every diagnostic above, cancellation, duplicate evidence, conflicting dispositions, and an unknown evidence type; no partial acceptance is published.
3. Evidence records fixture IDs and hashes, prerequisite revisions, canonicalizer and digest revisions, expected/actual matrix, diagnostics, environment, timestamp, owner, limitations, and G11 disposition.
4. The same immutable evidence set in different input order produces the same digest; changing any disposition or hash changes it.

## Documentation updates on completion

- Update this card and epic, both task indexes, the proposed requirement mappings, atomic test registrations, RTM rows, G11 checklist, dependency/license decisions, and linked risks together.
- Record exact verification commands, actual results, evidence archive identifiers, residual findings, and next-review dates.

## Forbidden scope

- Do not implement a worker, engine adapter, queue, scheduler, checkpoint, storage, billing, or observability feature.
- Do not waive G10 evidence, infer missing revisions, convert an open finding to accepted, or treat documentation existence as test evidence.
- Do not treat Source PDF page references as confirmed technical requirements or engine behavior.

## Definition of Done

- [ ] All five public contracts are versioned, schema-valid, immutable, and unambiguous.
- [ ] Nominal, boundary, invalid, stale, license, security, source-quality, and cancellation evidence passes.
- [ ] All prerequisite identities and the evidence digest reproduce independently.
- [ ] Central task/test/traceability/risk/license/release records are synchronized before status advances.
- [ ] No R11 implementation or external distribution was authorized by this documentation task.
