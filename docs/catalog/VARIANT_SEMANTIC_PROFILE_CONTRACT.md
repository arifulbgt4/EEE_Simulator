# Variant Semantic Profile Contract

Status: **Normative documentation baseline 1.0**  
Requirements: **REQ-009, REQ-010, REQ-014, REQ-015, REQ-016, REQ-018, REQ-020, REQ-022, REQ-023, REQ-037, REQ-038**

## Purpose

A component variant is a meaningful built-in electrical, digital, physical-stimulus, architectural, or research preset. A stable variant ID identifies the preset, but its spelling and display name do not define behavior. This contract provides the explicit dispatch record that connects every canonical variant to its pin topology, parameter changes, planned model tiers, allowed analyses, validation identities, provenance, and lifecycle. It prevents sibling variants from collapsing to the same family defaults while preserving the frozen 162-family and 502-variant counts. [Source PDF, pp. 6-35]

The machine-readable registry is [variant-semantic-profiles.yaml](variant-semantic-profiles.yaml). Exact logical pins are owned by [variant-pin-profiles.yaml](variant-pin-profiles.yaml). The general entity and fidelity rules remain in [COMPONENT_MODEL_CONTRACT.md](COMPONENT_MODEL_CONTRACT.md).

## Planning record versus executable entity

`VariantSemanticProfile` is a documentation and implementation-planning record. It is not an executable component model and does not prove that a referenced solver, model artifact, physical representation, package binding, or golden result exists.

The compact component catalog plus this profile may generate atomic work. Validation, project persistence, simulation, or release may consume a normalized `ComponentVariant` only after every required reference for the selected release profile resolves to a schema-valid record. Missing information is never invented by normalization. An unresolved item returns a structured diagnostic and remains release-blocking.

Permitted inheritance is field-specific:

- aliases, provenance, limitations, and golden obligations may inherit an existing family record and then append or narrow explicit variant data;
- a parameter keeps its family default only when the profile explicitly omits that declared parameter from `parameter_overrides`;
- pins, behavior dispatch, model bindings, analysis support, physical representation, and package pin maps do not materialize from absence;
- a display name, ID suffix, category, package, or neighboring variant must never be parsed to guess behavior.

## Required record

Every record in `profiles` contains:

| Field | Contract |
|---|---|
| `id` | Stable `vsp-<variant-suffix>` profile ID. It is immutable after publication. |
| `revision` | Semantic revision of this profile. Changing pin meaning, selector meaning, defaults, or behavior requires a new revision and migration review. |
| `variant_id` | Exact canonical variant ID from `component-registry.yaml`; one profile per variant. |
| `family_id` | Exact containing canonical family ID. |
| `release_target` | Copied release profile for synchronization checks; it does not itself release the variant. |
| `behavior_selector` | Opaque, stable dispatch key. Engines resolve it by exact registry lookup and must not interpret its text. |
| `behavior_contract` | Normative variant-specific operation, transfer, state, topology, or abstraction selected by `behavior_selector`. |
| `parameter_overrides` | Explicit map over parameters declared by the family. An empty map is valid only when the behavior selector, pin profile, or model plan still gives the variant a meaningful semantic identity. |
| `pin_profile_ref` | Exact `PinProfile.id` from `variant-pin-profiles.yaml`. Logical pins are never inferred from the family display table. |
| `model_profile_plan` | One planned reference for every tier declared by the component variant. Each entry records resolution status and whether absence blocks release. |
| `analysis_restrictions` | Closed allowed-analysis set after variant narrowing. Anything not listed is denied by default. |
| `golden_tests` | Unique nominal, boundary, and failure IDs for this variant. These are obligations, not pass claims. |
| `provenance` | Source identity, authorship basis, license expression, and review state for the semantic planning record. |
| `limitations` | Explicit unsupported or unverified behavior. |
| `lifecycle` | Variant-profile lifecycle; it does not advance from family status. |

Additional fields may be introduced only by a schema revision. A consumer must retain unknown additive fields or reject an unsupported schema version; it must not silently discard semantic data.

## Stable identifiers

For canonical variant `var-digital-logic-logic-gate-nand`:

```text
semantic profile: vsp-digital-logic-logic-gate-nand
pin profile:      pinprof-digital-logic-logic-gate-nand
model plan F2:    modelplan-digital-logic-logic-gate-nand-f2
golden nominal:   GOLD-VAR-DIGITAL-LOGIC-LOGIC-GATE-NAND-NOMINAL
```

These strings are lookup keys, not a grammar for deriving semantics. The registry stores every mapping explicitly. A renamed display label cannot change any key.

## Behavior dispatch

`behavior_selector` is globally unique and resolves to exactly one `behavior_contract` revision. Selectors use readable project-owned text for review, but consumers compare the complete selector as an opaque value. They must not split it, title-case it, derive a truth function from it, or fall back to a family default when lookup fails.

Within a multi-variant family, each sibling must be distinguishable by at least one of:

1. a different behavior selector and contract;
2. a different resolved pin profile;
3. a non-empty parameter override that changes declared behavior;
4. a different resolved model profile with an explicitly documented semantic boundary.

The current baseline assigns a distinct behavior selector to every canonical variant. Equal family equations are allowed, but the contract must state the selected polarity, material, waveform, topology, protocol, transfer mode, state machine, instrument mode, architecture abstraction, or research boundary.

## Parameter overrides

- Keys must resolve to family `ParameterDefinition.id` values; unknown keys are errors.
- Values must satisfy the family type, SI-unit, and range contract after normalization.
- A value may select a registered enum/profile only when that profile exists and the selected meaning is stated in `behavior_contract`.
- An override cannot widen a family limit, analysis claim, fidelity tier, or license permission.
- A variant-specific required value cannot be left to display-name inference.
- Empty maps are explicit and are audited against sibling distinguishability.

## Pin profile

`pin_profile_ref` resolves to one exact entry in `variant-pin-profiles.yaml` whose `variant_id` and `family_id` match this record. The selected profile owns exact pin IDs, direction, domain, optional/required state, bus/cardinality rules, and package-role constraints. A family may expose a stable role vocabulary, but a variant's topology comes only from its selected pin profile.

Missing, duplicate, family-mismatched, or variant-mismatched references produce `UNRESOLVED_PIN_PROFILE` or `PIN_PROFILE_IDENTITY_MISMATCH` and block F0 connectivity release.

## Model profile plan

Each declared fidelity tier has exactly one entry:

```yaml
- tier: "F2"
  ref: "modelplan-digital-logic-logic-gate-nand-f2"
  status: "unresolved"
  release_blocking: true
  resolution_rule: "Replace the plan with a validated ModelBinding or built-in model-profile record before the tier is claimable."
```

Allowed status values are:

- `unresolved`: a stable plan exists, but no validated implementation record is claimed;
- `resolved-planned`: a schema-valid model profile exists but implementation/validation remains incomplete;
- `validated`: current evidence resolves the exact model, version, analysis envelope, provenance, license, and tests.

This documentation baseline uses `unresolved`. It makes no implementation or validation claim. Any selected tier with `release_blocking: true` cannot be `Released` until its plan resolves and the applicable task and gate evidence are complete.

## Analysis restrictions

`allowed` is a closed set copied or narrowed from the family capability labels for planning. `denied_by_default` is always true. At execution time, the normalized supported set is the intersection of this closed set, a resolved model profile's capabilities, engine capabilities, parameter envelope, and release profile. An unresolved model plan means no executable analysis support is claimed even when an analysis is listed as planned.

## Golden obligations

Every profile owns unique `nominal`, `boundary`, and `failure` IDs. IDs establish traceability only. A test passes only when a fixture, expected result, actual result, versions, seed where applicable, tolerance, provenance, and evidence digest exist under the quality contracts.

Sibling variants must not rely solely on one family-generic expected vector. Variant evidence must exercise the selected behavior contract, parameter overrides, pin profile, unsupported-analysis diagnostics, and invalid model/pin/profile references.

## Provenance, limitations, and lifecycle

The baseline semantics are project-authored planning decisions derived from the named family specification and source scope. `review_status: planned` means engineering review is still required. Apache-2.0 applies to project-authored documentation; it does not grant rights to imported vendor models, marks, symbol artwork, or third-party data.

Lifecycle values are `Planned`, `Specified`, `Validated`, and `Released` for this semantic profile. `Specified` requires complete contract review and resolved pin identity. `Validated` requires resolved model profiles and current golden evidence for the claimed tiers. `Released` additionally requires every applicable component, physical, package, security, license, accessibility, and release-gate obligation.

## Validation invariants

1. Exactly 502 profiles exist, one for each canonical variant and no extra record.
2. Profile IDs, behavior selectors, model-plan refs, and golden IDs are globally unique.
3. `family_id`, `release_target`, and declared tiers agree with the component registry.
4. Every `pin_profile_ref` resolves to the same family and variant.
5. Every declared variant tier has exactly one model-plan entry; undeclared tiers have none.
6. Every override key exists in the selected family and every value passes the family parameter contract.
7. Every allowed analysis is declared by the family; the profile cannot widen support.
8. Every multi-variant sibling is normatively distinguishable without parsing ID or display text.
9. Nominal, boundary, and failure IDs are present and variant-specific.
10. Unresolved plans, missing evidence, or planned lifecycle records never produce implementation, accuracy, or release claims.

## Required diagnostics

Minimum structured diagnostics are:

- `DUPLICATE_VARIANT_SEMANTIC_PROFILE`
- `MISSING_VARIANT_SEMANTIC_PROFILE`
- `VARIANT_FAMILY_MISMATCH`
- `RELEASE_TARGET_MISMATCH`
- `UNRESOLVED_BEHAVIOR_SELECTOR`
- `AMBIGUOUS_SIBLING_SEMANTICS`
- `INVALID_PARAMETER_OVERRIDE`
- `UNRESOLVED_PIN_PROFILE`
- `PIN_PROFILE_IDENTITY_MISMATCH`
- `MODEL_PROFILE_PLAN_MISSING`
- `MODEL_PROFILE_UNRESOLVED`
- `ANALYSIS_RESTRICTION_WIDENS_FAMILY`
- `GOLDEN_ID_NOT_VARIANT_SPECIFIC`
- `PROFILE_NOT_RELEASEABLE`

## Atomic-task use

A component CAT task reads exactly one semantic profile. Its normative inputs must include the resolved behavior selector and contract, exact pin profile, explicit overrides, planned analysis set, tier-specific model-plan reference, and variant-specific golden IDs. A small model must not be asked to invent any of these from a family name. Model, symbol, validation, import, thermal, failure, physical, and package tasks may refine only their named concern and must preserve the profile identity unless an approved semantic revision changes it.

## Canonical limitations

This registry specifies planned variant meaning; it does not implement a solver, model, renderer, physical asset, package binding, imported vendor artifact, or golden fixture. Every model-plan reference remains release-blocking until independently resolved and validated. Readable selector names aid review but never authorize string-based inference.
