# EPIC-PHY-001 - Applied Physics model framework and evidence

## Outcome

Deliver **Applied Physics model framework and evidence** as a bounded, versioned capability with explicit scientific, security, compatibility, lifecycle, and validation evidence.

## Requirements and release

- Requirements: REQ-039, REQ-040, REQ-041, REQ-042, REQ-043, REQ-044, REQ-045, REQ-046, REQ-047
- Release: R4
- Entry: Gate G3 nonlinear analog.
- Normative contract: `docs/architecture/APPLIED_PHYSICS_AND_REAL_WORLD_FIDELITY.md`.

## Atomic tasks

| Task | Single outcome | Depends on | Status |
|---|---|---|---|
| [PLAT-PHY-001](../platform/plat-phy-001-define-the-applied-physics-model-contract.md) | Define the Applied Physics model contract | Gate G3 nonlinear analog | Planned |
| [PLAT-PHY-002](../platform/plat-phy-002-define-the-scientific-model-registry-schema.md) | Define the scientific model registry schema | PLAT-PHY-001 | Planned |
| [PLAT-PHY-003](../platform/plat-phy-003-define-units-and-dimensional-schema.md) | Define units and dimensional schema | PLAT-PHY-002 | Planned |
| [PLAT-PHY-004](../platform/plat-phy-004-define-model-provenance-and-trust-schema.md) | Define model provenance and trust schema | PLAT-PHY-003 | Planned |
| [PLAT-PHY-005](../platform/plat-phy-005-define-validity-and-limitation-schema.md) | Define validity and limitation schema | PLAT-PHY-004 | Planned |
| [PLAT-PHY-006](../platform/plat-phy-006-define-accuracy-and-uncertainty-schema.md) | Define accuracy and uncertainty schema | PLAT-PHY-005 | Planned |
| [PLAT-PHY-007](../platform/plat-phy-007-define-physical-benchmark-fixture-contracts.md) | Define physical benchmark fixture contracts | PLAT-PHY-006 | Planned |
| [PLAT-PHY-008](../platform/plat-phy-008-define-experimental-correlation-workflow.md) | Define experimental correlation workflow | PLAT-PHY-007 | Planned |
| [PLAT-PHY-009](../platform/plat-phy-009-define-bounded-accuracy-reporting.md) | Define bounded accuracy reporting | PLAT-PHY-008 | Planned |
| [PLAT-PHY-010](../platform/plat-phy-010-define-declarative-and-executable-kernel-boundary.md) | Define declarative and executable kernel boundary | PLAT-PHY-009 | Planned |
| [PLAT-PHY-011](../platform/plat-phy-011-expand-the-r4-release-gate-and-evidence-audit.md) | Expand the R4 release gate and evidence audit | PLAT-PHY-010 | Planned |

## Exit criteria

- [ ] Every listed task is `Done` with linked current evidence.
- [ ] Requirements, ADRs, schemas, immutable revisions, tests, risks, and release evidence resolve bidirectionally.
- [ ] Nominal, boundary, invalid, compatibility, security, and resource behavior is explicit.
- [ ] Provenance, license, trust, validity, accuracy/uncertainty, lineage, and limitations are complete where applicable.
- [ ] No runtime capability is claimed merely because its documentation exists.
