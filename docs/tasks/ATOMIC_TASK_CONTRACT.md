# Atomic Task Contract

Status: **Normative planning contract 1.0**

This contract makes every future task safe for a small implementation model. It complements [AGENTS.md](../../AGENTS.md), the [task index](TASK_INDEX.md), and the card templates. A card cannot become `Ready` unless every field below is concrete and mechanically verifiable.

## One outcome and stable identity

- A platform card owns one subsystem concern.
- A component card owns one family or variant, one fidelity tier, and one concern.
- A package card owns one package revision, one F0 concern, and no electrical-model behavior.
- A validation card owns one golden fixture and cannot modify the implementation under test.
- IDs, release IDs, requirement IDs, dependency IDs, public contracts, and test IDs are immutable after publication.

Canonical release values are `R0` through `R13`. Descriptive aliases such as `MVP` and composite values such as `R1/R7` are forbidden in task metadata; the Realistic Electronics MVP is `R6`.

## Required card fields

Every card MUST state:

1. purpose and one observable outcome;
2. exact prerequisite task or gate IDs;
3. exact normative inputs and reference data;
4. expected outputs and named public contracts;
5. an exact documentation allowlist and, when `Ready`, exact implementation/test paths unless the task is one of the documentation-only readiness exceptions defined below;
6. forbidden scope;
7. equations, event rules, external references, or an explicit statement that the concern has no numerical equation;
8. nominal, boundary, invalid, failure, cancellation, compatibility, security, performance, and accessibility behavior where applicable;
9. stable acceptance-test IDs and expected evidence;
10. exact documentation, coverage, traceability, risk, and release records to update;
11. known limitations and Definition of Done.

“Applicable dependencies,” “relevant files,” or similar implementer-selected scope is not valid readiness evidence.

## Allowed-file readiness rule

The documentation baseline can authorize exact documentation records, but application source paths do not exist until `PLAT-GOV-001` defines repository layout and ownership. Therefore:

- every `Planned` model, package, validation, or platform card lists its current exact documentation allowlist;
- no application/source path is authorized while that restriction is present;
- every documentation-only R0 card is an explicit exception: it may be `Ready` with a complete documentation/evidence allowlist and no application source or runtime-test path, and it grants no permission to create application code;
- `PLAT-QA-001` is the only initial `Ready` card; later R0 quality cards are promoted sequentially only after their exact predecessor is `Done`;
- `PLAT-GOV-001` remains `Planned` until G0 is accepted, may then be promoted using its exact documentation/output allowlist, and establishes the source/test layout required by later implementation tasks;
- outside the documentation-only exceptions above, promotion to `Ready` MUST append exact implementation and test paths defined by completed `PLAT-GOV-001` without changing the task's component, tier, concern, contracts, or documentation allowlist;

This is a stage gate, not permission for an implementer to choose files.

## Dependency rules

### Component/model cards

- Variant `CAT` depends on `PLAT-GOV-001` and freezes that variant's exact `PinProfile`, parameter/profile selection, package candidates, release target, provenance, and limitations. A package candidate is never a concrete pin map or release artifact.
- Family `SYM` depends on the `CAT` cards inside its exact release scope, `PLAT-SYM-007`, and validation of every package template used by that scope. It produces profile-specific symbol anchors and, for every variant claimed by the release, at least one concrete `DevicePackageBinding` with exact profile/package revisions, resolved contacts, logical-to-contact map, realistic accessible views, provenance, and binding-specific evidence.
- The first family `MODEL` tier depends on the gate-required variant `CAT` cards and the canonical netlist contract; each later tier depends on the preceding declared tier. A shared model must enumerate the exact `PinProfile` revisions it accepts and reject every incompatible topology.
- Tier `VALIDATION` depends on the same-tier `MODEL` card and `PLAT-QA-001`.
- `THERMAL` and `FAILURE` depend on the F4 model and their named realism platform tasks.
- `IMPORT` depends on the highest declared model tier and each exact format-policy task implied by the family import mappings.
- `DOCS` depends on every gate-required `CAT`, `SYM`, `MODEL`, `VALIDATION`, `THERMAL`, and `FAILURE` card in the component's core release profile; it does not depend on a later optional `IMPORT` extension.
- A later `IMPORT` card owns the documentation, provenance, security limits, compatibility statement, validation evidence, and release record for that format extension. Until that card is `Done`, the released component must report the format as unavailable and cannot claim it through inheritance or a family-wide capability flag.
- Optional-extension treatment can never defer a model tier, package binding, physical representation, analysis, failure behavior, or import format that the applicable release gate explicitly requires.
- A shared family task may finish for an explicitly listed early-release variant subset while later variants remain unavailable. The card must name the excluded variant IDs and their unfinished `CAT`/validation obligations; completion never promotes those later variants through family inheritance.

### Package cards

`CAT -> SYM -> VALIDATION -> DOCS` is the required package chain. Platform package schema/designer and pin-equivalence tasks are named explicitly on the applicable cards.

### Platform and validation cards

The first task of an epic depends on the predecessor release gate; later tasks name the preceding task. R0 quality work treats G0 as its exit gate and does not depend on G0. Each golden validation card depends on `PLAT-QA-001`, the predecessor gate, and exact target component/platform/package task IDs.

## Stable test IDs

- Requirement acceptance: `TEST-REQ-<NNN>`.
- Golden fixture: `TEST-GRC-<NNN>`.
- Atomic task nominal path: `TEST-<TASK-ID>-NOMINAL`.
- Atomic task boundary path: `TEST-<TASK-ID>-BOUNDARY`.
- Atomic task failure path: `TEST-<TASK-ID>-FAILURE`.
- Platform tasks may use `TEST-<TASK-ID>-ACCEPTANCE` and `TEST-<TASK-ID>-FAILURE` when a three-vector component form is not applicable.

The machine-readable registry is [test-registry.yaml](../quality/test-registry.yaml). Evidence does not exist merely because an ID exists; task completion still requires current reproducible results.

## Promotion audit

Before changing a card to `Ready`, automation MUST reject:

- unresolved or non-terminal dependencies;
- a noncanonical release value;
- missing exact implementation/test paths, unless the task satisfies a documentation-only readiness exception above;
- missing public contracts or reference/equation basis;
- missing stable test IDs;
- a dependency cycle;
- requirement, coverage, registry, golden-test, risk, or release links that disagree;
- scope that combines another variant, tier, package, or concern.
