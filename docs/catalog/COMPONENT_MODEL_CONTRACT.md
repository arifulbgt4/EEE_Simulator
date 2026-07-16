# Component Model Contract

Status: **Normative baseline 1.2**
Requirements: **REQ-009, REQ-010, REQ-014, REQ-015, REQ-016, REQ-018, REQ-020, REQ-022, REQ-023, REQ-024, REQ-037, REQ-038, REQ-039, REQ-040, REQ-041, REQ-042, REQ-043, REQ-048, REQ-049, REQ-050, REQ-053, REQ-054, REQ-056, REQ-059, REQ-063**

## Purpose

This contract separates physical/scientific models, electrical meaning, simulation behavior, schematic appearance, physical appearance, package geometry, boards/systems, and optional manufacturing metadata. All engines, editors, importers, Library Service operations, project files, and catalog tools must preserve these boundaries. [Source PDF, pp. 6-35]

It is read with the [Applied Physics contract](../architecture/APPLIED_PHYSICS_AND_REAL_WORLD_FIDELITY.md), [hierarchical library architecture](../architecture/HIERARCHICAL_MODEL_AND_LIBRARY_ARCHITECTURE.md), [data-driven library architecture](../architecture/DATA_DRIVEN_LIBRARY_AND_STORAGE_ARCHITECTURE.md), [scientific model registry](model-registry.yaml), [variant semantic profiles](variant-semantic-profiles.yaml), and [parameter-definition catalog](PARAMETER_DEFINITION_CATALOG.md). Registry presence is planning evidence only; unresolved executable bindings remain release-blocking.

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

The [variant semantic profile](VARIANT_SEMANTIC_PROFILE_CONTRACT.md) selects the exact behavior selector, PinProfile, fidelity-specific model-plan references, parameter overrides, and nominal/boundary/failure obligations for each built-in variant. A semantic profile never creates an executable model by implication. Every unresolved `model-plan-*` reference blocks `Model Ready` and must later resolve through the Library Service to an immutable model revision in [model-registry.yaml](model-registry.yaml) or a validated imported model.

### PinProfile

`PinProfile` is the normative topology selected by one built-in variant. Required fields are `id`, `revision`, `familyId`, `variantId`, `topologyStatus`, `pins`, `resolvedOrderRule`, `packageBindingRule`, and `limitations`. Every built-in variant resolves exactly one profile; profile IDs use `pinprof-<category>-<family>-<variant>` and are not derived from display names at runtime.

Each ordered `pins` entry is either a scalar, a logical bus, or a bounded parameterized group. A bus declares its exact fixed width or a finite `parameter`, `default`, `minimum`, and `maximum`. A group declares the same finite cardinality contract, member ID/name pattern, members per index, suffix order where applicable, and expansion order. `parameter_scope: family` means the controlling parameter is declared by the family; `parameter_scope: profile` is a topology parameter owned by the profile. All parameterized directions, widths, and groups MUST resolve before netlist generation. The resolved ordered list and parameter values are persisted with project provenance.

The family role vocabulary in the profile registry is the stable semantic namespace shared by its variants. It may contain roles unused by a particular variant. A profile selects exact roles and may vary pole count, winding count, sensor interface, protocol bus, supply exposure, or optional terminals without changing the family identity. A role does not imply a package contact number.

An optional pin has `required: false` and a named `optional_group`. It is absent unless that group is explicitly enabled by the instance or `DevicePackageBinding`. Implementations must never infer optional terminals from package pin count. Changing a released profile's pin identity, order, role, direction, domain, width, group expansion, or required state is a breaking change requiring a new revision and migration.

### PinDefinition

Required fields: `id`, `name`, `aliases`, `electricalType`, `domains`, `direction`, `required`, `busWidth`, `referenceRole`, `acceptedPackageRoles`, and `description`. A normalized `PinDefinition` is materialized from the selected `PinProfile`; the compact family pin preview is never authoritative for variant connectivity. Pin IDs are immutable. Bus ordering and endian convention are explicit. Optional, exposed-pad, shield, chassis, and no-connect semantics are never inferred.

### ParameterDefinition

Required fields: `id`, `name`, `quantityKind`, `internalUnit`, `displayUnitHints`, `valueType`, `default`, `minimum`, `maximum`, `enumValues`, `expressionAllowed`, `temperatureDependency`, `validation`, and `description`. Numerical storage uses SI base units. Display prefixes do not alter stored values.

Every compact-registry parameter occurrence resolves through [parameter-definitions.yaml](parameter-definitions.yaml). When legacy source data does not establish a dimension, unit, default, or limit, normalization records an explicit unresolved diagnostic and cannot invent a value. Ambiguous legacy tokens such as `FNU` remain quarantined until reviewed.

### ScientificModelRevision

Required fields are defined by [model-registry.yaml](model-registry.yaml): stable model ID, immutable revision ID and content digest, canonical `kind` (`physics`, `primitive`, `composite`, `behavioral`, or `external_adapter`), governing principles/equations or algorithm reference, assumptions, approximation, inputs/outputs/state, parameter references and dimensions, dependencies, analyses/fidelity, validity, numerical method, convergence expectations, failure conditions, provenance/license/trust, validation evidence, accuracy/uncertainty envelope, limitations, lifecycle, deprecation, and replacement. `behavioural` is accepted only as an import/display alias for canonical `behavioral`.

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

A package contains no device, MCU, circuit, board, module, system, firmware, or behavioral model. Boards and systems are separate composition revisions defined by the hierarchical library architecture.

### ComponentDefinitionPlan

The Library Service resolves a project/component reference into an immutable, storage-independent execution bundle. Required content includes project/component/variant IDs, exact semantic and pin-profile revisions, exact scientific-model revisions and dependency DAG, parameters normalized to canonical SI, logical pins and domains, model/analysis selection, package-parasitic binding when enabled, environment and stimulus inputs, executable capability IDs, engine/version constraints, deterministic seed/timebase policy, source content hashes, provenance/license/trust, validation and accuracy envelope, limitations, and a bundle digest.

Resolution fails before simulation with stable diagnostics for missing revision, hash mismatch, dependency cycle, incompatible port/fidelity/analysis, invalid dimension/range, incomplete package binding, untrusted executable capability, or unavailable model plan. The engine consumes only this bundle and never queries PostgreSQL, JSONB, object storage, or IndexedDB.

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
11. Composite/model/device/board/system dependency graphs are acyclic, exact-revision, hash-verified, and dependency-closed.
12. Published revisions are immutable; referenced revisions cannot be hard-deleted.
13. Stored model content is declarative unless it selects an allowlisted, versioned, sandboxed executable capability.
14. Physical/scientific claims remain inside their validity and accuracy/uncertainty envelope and identify their evidence state.

## Lifecycle and compatibility

`Planned -> Symbol Ready -> Connectivity Ready -> Model Ready -> Validated -> Released`. `Released` applies to an explicit gate-scoped core release profile: the exact model tiers, analyses, packages/physical views, non-ideal/failure behavior, golden evidence, and documentation required by that gate. Every item in that profile must be `Done`; a required item cannot be relabeled as an extension to pass a gate.

An import format or later capability not named by the core profile is an independently releasable extension. It does not block the already validated core profile, but it remains unavailable and unclaimable until its own task has completed parsing/security/provenance/round-trip validation and updated user documentation, compatibility, limitations, traceability, and release evidence. Project/result provenance identifies both the core component revision and every enabled extension revision.

Schema and profile revisions use semantic versioning. Additive optional fields may be minor; changing pin meaning, topology, order, group expansion, units, defaults, or behavior requires a new stable revision and project migration. Old IDs and the migration path remain resolvable.

## Canonical limitations

A family model cannot claim manufacturer accuracy without a validated vendor artifact. A vendor ordering code cannot widen the generic model's claim through metadata alone. A physical package cannot claim manufacturability without sourced footprint evidence. A behavioral CPU/GPU block cannot claim transistor-level fidelity. Differential agreement cannot claim physical correlation. Deferred or unresolved model-plan records cannot satisfy production gates. No database, imported record, visual representation, or model name is itself a simulation engine or evidence of physical accuracy.
