# Component Model Contract

Status: **Normative baseline 1.1**
Requirements: **REQ-009, REQ-010, REQ-014, REQ-015, REQ-016, REQ-018, REQ-020, REQ-022, REQ-023, REQ-024, REQ-037, REQ-038**

## Purpose

This contract separates electrical meaning, simulation behavior, schematic appearance, physical appearance, package geometry, and optional manufacturing metadata. All engines, editors, importers, project files, and catalog tools must preserve these boundaries. [Source PDF, pp. 6-35]

## Normative entities

### ComponentDefinition

Required fields: `id`, `schemaVersion`, `name`, `aliases`, `categoryId`, `symbol`, `pins`, `parameters`, `domains`, `analysisCapabilities`, `modelBindings`, `fidelityTiers`, `nonIdealBehavior`, `thermalBehavior`, `failureDefinitions`, `variants`, `provenance`, `goldenTests`, `limitations`, and `lifecycle`.

The definition owns function and a stable logical pin-role vocabulary. It does not own one topology for every variant and it does not own a single mandatory package. Exact logical topology is selected through a `PinProfile`.

### ComponentVariant

Required fields: `id`, `familyId`, `name`, `aliases`, `releaseTarget`, `classTags`, `pinProfileRef`, `parameterOverrides`, `modelBindingRefs`, `supportedAnalyses`, `fidelityTiers`, `packageCompatibility`, `physicalRepresentation`, `provenance`, `goldenTests`, `limitations`, and `lifecycle`.

`classTags` contains `basic-component` when REQ-037 applies. For that tag, `physicalRepresentation.required` is true and release validation rejects missing body, lead/contact, orientation/polarity, marking, LOD, or non-color metadata.

The compact registry stores family-owned defaults once and variant-owned overrides on each variant node. Before validation, persistence, task generation, or execution, a deterministic normalization step MUST materialize the complete `ComponentVariant` entity:

- `familyId` is the containing stable family ID; it is never inferred from display text.
- `aliases` is the stable-order unique union of family aliases, variant name, and explicit variant aliases.
- `pinProfileRef` resolves the compact registry's `pin_profile` through [variant-pin-profiles.yaml](variant-pin-profiles.yaml). It is mandatory, immutable for a released variant revision, and materializes the exact ordered logical pins before ERC, netlisting, model binding, package binding, persistence, or execution.
- absent `parameterOverrides` becomes an empty map and cannot change family defaults implicitly.
- `modelBindingRefs` contains only family bindings compatible with the variant's declared tiers and explicit overrides; a required unresolved binding blocks release.
- `supportedAnalyses` is the intersection of family analyses, selected model capabilities, and variant restrictions; inheritance cannot widen support.
- `fidelityTiers`, `packageCompatibility`, and `physicalRepresentation` are materialized from the variant node and validated against family/package policy.
- `provenance`, `goldenTests`, and `limitations` inherit the family records and append or narrow explicit variant records; a variant cannot erase a family limitation.
- `lifecycle` is the variant's own status and never advances merely because the family advances.

The normalized form MUST contain every required field named above. Missing compact fields mean “inherit by this rule,” never `null`, wildcard support, or implementer discretion. Normalized output and the source family/variant digests are recorded in project and result provenance.

### PinProfile

`PinProfile` is the normative topology selected by one built-in variant. Required fields are `id`, `revision`, `familyId`, `variantId`, `topologyStatus`, `pins`, `resolvedOrderRule`, `packageBindingRule`, and `limitations`. Every built-in variant resolves exactly one profile; profile IDs use `pinprof-<category>-<family>-<variant>` and are not derived from display names at runtime.

Each ordered `pins` entry is either a scalar, a logical bus, or a bounded parameterized group. A bus declares its exact fixed width or a finite `parameter`, `default`, `minimum`, and `maximum`. A group declares the same finite cardinality contract, member ID/name pattern, members per index, suffix order where applicable, and expansion order. `parameter_scope: family` means the controlling parameter is declared by the family; `parameter_scope: profile` is a topology parameter owned by the profile. All parameterized directions, widths, and groups MUST resolve before netlist generation. The resolved ordered list and parameter values are persisted with project provenance.

The family role vocabulary in the profile registry is the stable semantic namespace shared by its variants. It may contain roles unused by a particular variant. A profile selects exact roles and may vary pole count, winding count, sensor interface, protocol bus, supply exposure, or optional terminals without changing the family identity. A role does not imply a package contact number.

An optional pin has `required: false` and a named `optional_group`. It is absent unless that group is explicitly enabled by the instance or `DevicePackageBinding`. Implementations must never infer optional terminals from package pin count. Changing a released profile's pin identity, order, role, direction, domain, width, group expansion, or required state is a breaking change requiring a new revision and migration.

### PinDefinition

Required fields: `id`, `name`, `aliases`, `electricalType`, `domains`, `direction`, `required`, `busWidth`, `referenceRole`, `acceptedPackageRoles`, and `description`. A normalized `PinDefinition` is materialized from the selected `PinProfile`; the compact family pin preview is never authoritative for variant connectivity. Pin IDs are immutable. Bus ordering and endian convention are explicit. Optional, exposed-pad, shield, chassis, and no-connect semantics are never inferred.

### ParameterDefinition

Required fields: `id`, `name`, `quantityKind`, `internalUnit`, `displayUnitHints`, `valueType`, `default`, `minimum`, `maximum`, `enumValues`, `expressionAllowed`, `temperatureDependency`, `validation`, and `description`. Numerical storage uses SI base units. Display prefixes do not alter stored values.

### ModelBinding

Required fields: `id`, `engineAdapter`, `format`, `formatVersion`, `artifactDigest`, `entryPoint`, `logicalPinOrder`, `normalizedPinMap`, `parameterMap`, `supportedAnalyses`, `fidelityTier`, `determinism`, `engineVersionConstraint`, `provenance`, `license`, `sandboxPolicy`, and `limitations`.

### AnalysisCapability

Required fields: `analysis`, `fidelityTier`, `status`, `parameterEnvelope`, `requiredEngineFeatures`, `accuracyTarget`, `referenceMethod`, `unsupportedBehavior`, and `diagnostics`. Status is `supported`, `partial`, `unsupported`, or `research`; no implicit support is allowed.

### FailureDefinition

Required fields: `id`, `trigger`, `threshold`, `duration`, `transition`, `resultingParameters`, `recoverability`, `diagnostic`, `deterministicSeedPolicy`, and `supportedTiers`. Minimum considered modes are open circuit, short circuit, parameter drift, and overstress/saturation; inapplicable modes carry rationale.

### ModelProvenance

Required fields: `sourceType`, `sourceIdentity`, `sourceVersion`, `retrievedAt`, `contentDigest`, `authorsOrOrganization`, `licenseExpression`, `redistributionAllowed`, `modifications`, `reviewStatus`, and `reviewEvidence`. Personal paths and credentials are prohibited.

### PhysicalRepresentation

Required fields: `id`, `variantId`, `artworkRevision`, `geometryType`, `body`, `leadsOrContacts`, `polarityOrPinOne`, `markings`, `materials`, `lodLevels`, `accessibilityCues`, `defaultPackageRef`, `availablePackageRefs`, `accuracyClaim`, `provenance`, and `license`. Applicable value, rating, and safety markings require text equivalents; protected marks require documented permission. Geometry must be original scalable vector or procedural metadata.

### PackageDefinition and DevicePackageBinding

`PackageDefinition` owns reusable physical form: stable ID and immutable semantic `revision`, classification, mounting, body and contact dimensions in metres, lead form, parameterized pin-count rule, numbering, markings, materials, orientation, LOD, provenance, one primary golden fixture, limitations, and optional footprint reference. A binding identifies both package ID and revision; registry schema version alone is not a package revision.

`DevicePackageBinding` owns `variantId`, `packageRevision`, explicit logical-to-package pin map, NC pins, exposed or thermal pads, package-parasitic profile, marking overrides, validation evidence, and effective date. Electrical function, symbol, model, package, and footprint are distinct records as required by REQ-038.

## Fidelity levels

| Tier | Contract |
|---|---|
| F0 | Connectivity, pin rules, hierarchy, and ERC only. |
| F1 | Ideal or closed-form/equation behavior. |
| F2 | Behavioral, event, timing, control, or functional abstraction. |
| F3 | Compact/macro/HDL/IBIS/S-parameter model validated against a declared reference. |
| F4 | Parasitic, tolerance, electrothermal, aging, and fault behavior. |
| F5 | Physical, TCAD, field, or multiphysics research model. |

A higher tier is not automatically more valid. Each analysis selects the lowest adequate validated tier. Switching tier preserves logical pins and project identity and records the active tier in results.

## Physical-view invariants

- Schematic-to-physical-to-package switching preserves instance ID, connectivity, parameters, model binding, live simulation state, selection, and undo history.
- Rotation and mirroring preserve the logical pin map; visual pin positions change through the package transform only.
- Body, leads/contacts, polarity or pin-one, value/part markings, material regions, and non-color cues are visible at the applicable LOD.
- Physical illustration is not a footprint or dimensional certificate. Verified dimensions require a cited package drawing and review evidence.
- A package-parasitic profile may affect the model only through an explicit user-visible binding and result provenance entry.

## Determinism, units, and expressions

Time is an integer multiple of the declared project time quantum. Logic uses `0`, `1`, `X`, and `Z`; thresholds, hysteresis, drive strength, and transition shape are explicit. Randomized tolerance/noise/fault analyses store their seed. Expressions are dimension-checked, bounded, side-effect free, and evaluated in a sandbox.

## Validation invariants

1. IDs are unique and stable; every reference resolves.
2. Every variant resolves exactly one profile, every profile resolves only its declared family and variant, and every required logical pin exists and maps at most once to a physical pin.
3. All required logical pins map exactly once for a releasable device-package binding.
4. Package pins not used by the device are explicit NC, reserved, shield, or exposed-pad roles.
5. Defaults satisfy type, unit, and range constraints.
6. Supported analyses resolve to a compatible tier and engine binding.
7. Imported artifacts have digest, provenance, license, and sandbox metadata.
8. A `basic-component` release has physical-view and package evidence.
9. Nominal, boundary, and failure golden tests resolve.
10. Unsupported behavior produces a diagnostic rather than a silent approximation.

## Lifecycle and compatibility

`Planned -> Symbol Ready -> Connectivity Ready -> Model Ready -> Validated -> Released`. `Released` applies to an explicit gate-scoped core release profile: the exact model tiers, analyses, packages/physical views, non-ideal/failure behavior, golden evidence, and documentation required by that gate. Every item in that profile must be `Done`; a required item cannot be relabeled as an extension to pass a gate.

An import format or later capability not named by the core profile is an independently releasable extension. It does not block the already validated core profile, but it remains unavailable and unclaimable until its own task has completed parsing/security/provenance/round-trip validation and updated user documentation, compatibility, limitations, traceability, and release evidence. Project/result provenance identifies both the core component revision and every enabled extension revision.

Schema and profile revisions use semantic versioning. Additive optional fields may be minor; changing pin meaning, topology, order, group expansion, units, defaults, or behavior requires a new stable revision and project migration. Old IDs and the migration path remain resolvable.

## Canonical limitations

A family model cannot claim manufacturer accuracy without a validated vendor artifact. A physical package cannot claim manufacturability without sourced footprint evidence. A behavioral CPU/GPU block cannot claim transistor-level fidelity. Deferred models cannot satisfy production gates.
