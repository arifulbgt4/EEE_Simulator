# Component Model Contract

Status: **Normative baseline 1.0**  
Requirements: **REQ-003, REQ-004, REQ-006, REQ-009, REQ-010, REQ-037, REQ-038**

## Purpose

This contract separates electrical meaning, simulation behavior, schematic appearance, physical appearance, package geometry, and optional manufacturing metadata. All engines, editors, importers, project files, and catalog tools must preserve these boundaries. [Source PDF, pp. 6-35]

## Normative entities

### ComponentDefinition

Required fields: `id`, `schemaVersion`, `name`, `aliases`, `categoryId`, `symbol`, `pins`, `parameters`, `domains`, `analysisCapabilities`, `modelBindings`, `fidelityTiers`, `nonIdealBehavior`, `thermalBehavior`, `failureDefinitions`, `variants`, `provenance`, `goldenTests`, `limitations`, and `lifecycle`.

The definition owns function and stable logical pins. It does not own a single mandatory package.

### ComponentVariant

Required fields: `id`, `familyId`, `name`, `aliases`, `releaseTarget`, `classTags`, `parameterOverrides`, `modelBindingRefs`, `supportedAnalyses`, `fidelityTiers`, `packageCompatibility`, `physicalRepresentation`, `provenance`, `goldenTests`, `limitations`, and `lifecycle`.

`classTags` contains `basic-component` when REQ-037 applies. For that tag, `physicalRepresentation.required` is true and release validation rejects missing body, lead/contact, orientation/polarity, marking, LOD, or non-color metadata.

### PinDefinition

Required fields: `id`, `name`, `aliases`, `electricalType`, `domains`, `direction`, `required`, `busWidth`, `referenceRole`, `acceptedPackageRoles`, and `description`. Pin IDs are immutable. Bus ordering and endian convention are explicit. Optional, exposed-pad, shield, chassis, and no-connect semantics are never inferred.

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

`PackageDefinition` owns reusable physical form: stable ID/revision, classification, mounting, body and contact dimensions in metres, lead form, parameterized pin-count rule, numbering, markings, materials, orientation, LOD, provenance, limitations, and optional footprint reference.

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
2. Every required logical pin exists and maps at most once to a physical pin.
3. All required logical pins map exactly once for a releasable device-package binding.
4. Package pins not used by the device are explicit NC, reserved, shield, or exposed-pad roles.
5. Defaults satisfy type, unit, and range constraints.
6. Supported analyses resolve to a compatible tier and engine binding.
7. Imported artifacts have digest, provenance, license, and sandbox metadata.
8. A `basic-component` release has physical-view and package evidence.
9. Nominal, boundary, and failure golden tests resolve.
10. Unsupported behavior produces a diagnostic rather than a silent approximation.

## Lifecycle and compatibility

`Planned -> Symbol Ready -> Connectivity Ready -> Model Ready -> Validated -> Released`. Schema revisions use semantic versioning. Additive optional fields may be minor; changing pin meaning, units, defaults, or behavior requires a new stable revision and project migration. Old IDs remain resolvable.

## Canonical limitations

A family model cannot claim manufacturer accuracy without a validated vendor artifact. A physical package cannot claim manufacturability without sourced footprint evidence. A behavioral CPU/GPU block cannot claim transistor-level fidelity. Deferred models cannot satisfy production gates.
