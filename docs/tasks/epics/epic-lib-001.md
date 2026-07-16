# EPIC-LIB-001 - Hierarchical reusable model and device library

## Outcome

Deliver **Hierarchical reusable model and device library** as a bounded, versioned capability with explicit scientific, security, compatibility, lifecycle, and validation evidence.

## Requirements and release

- Requirements: REQ-040, REQ-042, REQ-048, REQ-049, REQ-050, REQ-051, REQ-052, REQ-053, REQ-059, REQ-063
- Release: R1
- Entry: Gate G0 documentation baseline.
- Normative contract: `docs/architecture/HIERARCHICAL_MODEL_AND_LIBRARY_ARCHITECTURE.md`.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-LIB-001](../platform/plat-lib-001-define-primitive-and-composite-taxonomy.md) | Define primitive and composite taxonomy | Gate G0 documentation baseline | Planned |
| [PLAT-LIB-002](../platform/plat-lib-002-validate-composite-dependency-graphs.md) | Validate composite dependency graphs | PLAT-LIB-001 | Planned |
| [PLAT-LIB-003](../platform/plat-lib-003-define-generic-device-model-binding.md) | Define generic device model binding | PLAT-LIB-002 | Planned |
| [PLAT-LIB-004](../platform/plat-lib-004-define-vendor-variant-inheritance.md) | Define vendor variant inheritance | PLAT-LIB-003 | Planned |
| [PLAT-LIB-005](../platform/plat-lib-005-separate-schematic-symbols-from-devices.md) | Separate schematic symbols from devices | PLAT-LIB-004 | Planned |
| [PLAT-LIB-006](../platform/plat-lib-006-enforce-package-orthogonality.md) | Enforce package orthogonality | PLAT-LIB-005 | Planned |
| [PLAT-LIB-007](../platform/plat-lib-007-validate-device-package-bindings.md) | Validate device package bindings | PLAT-LIB-006 | Planned |
| [PLAT-LIB-008](../platform/plat-lib-008-define-board-and-module-schema.md) | Define board and module schema | PLAT-LIB-007 | Planned |
| [PLAT-LIB-009](../platform/plat-lib-009-define-system-composition-schema.md) | Define system composition schema | PLAT-LIB-008 | Planned |
| [PLAT-LIB-010](../platform/plat-lib-010-implement-bidirectional-model-lineage-contract.md) | Implement bidirectional model lineage contract | PLAT-LIB-009 | Planned |
| [PLAT-LIB-011](../platform/plat-lib-011-define-immutable-model-revision-identities.md) | Define immutable model revision identities | PLAT-LIB-010 | Planned |
| [PLAT-LIB-012](../platform/plat-lib-012-define-deprecation-and-replacement-semantics.md) | Define deprecation and replacement semantics | PLAT-LIB-011 | Planned |
| [PLAT-LIB-013](../platform/plat-lib-013-validate-actual-registry-counts-and-references.md) | Validate actual registry counts and references | PLAT-LIB-012 | Planned |
| [PLAT-LIB-014](../platform/plat-lib-014-govern-imported-model-trust-and-licensing.md) | Govern imported model trust and licensing | PLAT-LIB-013 | Planned |

## Exit criteria

- [ ] Every listed task is `Done` with linked current evidence.
- [ ] Requirements, ADRs, schemas, immutable revisions, tests, risks, and release evidence resolve bidirectionally.
- [ ] Nominal, boundary, invalid, compatibility, security, and resource behavior is explicit.
- [ ] Provenance, license, trust, validity, accuracy/uncertainty, lineage, and limitations are complete where applicable.
- [ ] No runtime capability is claimed merely because its documentation exists.
