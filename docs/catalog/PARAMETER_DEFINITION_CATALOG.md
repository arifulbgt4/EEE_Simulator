# Parameter Definition Catalog

Status: **Normative documentation baseline 1.0**  
Requirements: **REQ-009, REQ-010, REQ-041, REQ-042**  
Machine-readable catalog: [parameter-definitions.yaml](parameter-definitions.yaml)

## Purpose

The compact [component registry](component-registry.yaml) declares a parameter as five source fields: local `id`, `name`, `unit`, `default`, and `limits`. Those local IDs are not globally unique, and several source constraints require contextual or domain-specific validation. This catalog materializes one stable, family-scoped `ParameterDefinition` for every source occurrence without inventing missing physics, units, values, or validation evidence.

It is a planning and normalization artifact. It does not implement a parser, solver, component model, database, or UI, and it does not prove that any component is accurate or released.

## Exact frozen inventory

The catalog was derived from component-registry schema `1.1.0` and contains:

| Record class | Exact count | Meaning |
|---|---:|---|
| Source component families | 162 | Every frozen production and research family was inspected. |
| Family-scoped parameter definitions | 801 | Exactly one record for every family `parameters[]` occurrence. |
| Unique source-local parameter IDs | 463 | Reuse across families is expected; local IDs are never treated as global IDs. |
| Unit definitions | 60 | Exactly one entry for every distinct source `unit` token. |
| Physical-dimension definitions | 46 | Reused SI-base exponent vectors, including explicit dimensionless semantics. |

No variant override was added by inference. Variant overrides, when explicitly authored, must resolve to one of these family-scoped IDs and then pass its type, unit, limit, and model-binding checks. Model-registry parameters are a separate inventory owned by [model-registry.yaml](model-registry.yaml); they may bind to these component parameters only through an explicit, dimension-compatible mapping.

## Stable identity and scope

An ID has this form:

```text
pdef-<family-id-without-fam-prefix>-<source-parameter-id>
```

For example, `resistance` in `fam-passives-resistor` becomes `pdef-passives-resistor-resistance`. The same local word in a different family is a different definition. IDs and published revisions are immutable. Changing a meaning, canonical unit, dimension, default, range, or expression policy requires a new revision and migration review; a display-label change alone does not.

Each record preserves a stable family ID plus an audit pointer to the original registry location. A consumer must resolve by exact ID. It must not reconstruct semantics from a display name, neighboring family, model name, or unit spelling.

## Normative record

Every `parameter_definitions[]` entry contains:

| Field | Contract |
|---|---|
| `id`, `revision`, `family_id`, `source_parameter_id` | Stable family-scoped identity and source ownership. |
| `name`, `description` | Source name plus a scope statement; neither changes electrical meaning. |
| `quantity_kind`, `dimension_ref`, `unit_semantics_ref` | Typed quantity and exact physical-dimension resolution. A null dimension is an explicit unresolved diagnostic, not dimensionless. |
| `source_unit`, `internal_unit`, `display_unit_hints` | Original token, canonical unprefixed coherent-SI or explicit dimensionless storage unit, and presentation hints. |
| `value_type`, `scalar_kind` | Number, boolean, string/reference, or bounded expression AST. The baseline contains scalar definitions only. |
| `default` | Original literal, normalized decimal text/boolean where justified, and normalization status. Decimal text preserves exact source spelling before a consumer chooses a bounded numeric representation. |
| `minimum`, `maximum`, inclusivity flags | Structured numeric bounds only when the source expression is unambiguous. Unknown or symbolic bounds remain null. |
| `enum_values` | Closed values only when the source text declares a finite closed set. Open registries and schema-dependent sets are not converted into enums. |
| `limits` | Unmodified source expression, normalization status, and exact same-family dependency references where resolvable. |
| `expression_allowed` | `true` only where the source explicitly permits a validated expression AST; otherwise the value is null and status is `not_evidenced`. |
| `temperature_dependency` | Explicitly `not_declared_by_source_parameter_record` until reviewed evidence supplies a dependency. |
| `display_guidance` | Unit- and semantic-specific presentation rule; display conversion never alters storage. |
| `provenance` | Source registry version and pointer, preserved source fields, normalization contracts, license, and review status. |
| `validation` | Planning status, release-blocking flag, unit/default/limit status, and structured diagnostics. |
| `limitations` | No implementation, vendor-accuracy, correlation, or release claim. |

The `dimensions[]` records use this ordered SI-base basis:

```text
mass, length, time, electric_current, thermodynamic_temperature,
amount_of_substance, luminous_intensity
```

Integer or rational exponents are explicit. Plane angle, state, count, ratio, coefficient, bit count, and byte count use a zero dimension vector while retaining their semantic `quantity_kind`. A null vector is never silently interpreted as zero.

## Unit normalization

- Numerical storage uses unprefixed coherent SI or explicit dimensionless values. Coherent derived units such as `V`, `A`, `ohm`, `F`, `H`, `S`, `W`, and `J` are allowed by the simulation-engine contract.
- Prefixes are presentation choices. The original lexical value remains available for editing, but calculations use normalized values.
- `rad` and `mol/mol` are dimensionless with explicit angle or amount-fraction semantics.
- `bit` and `byte` are dimensionless information counts. Their meaning remains in `quantity_kind`; the catalog does not guess decimal-versus-binary capacity prefixes.
- `bit/s` is stored as the dimensionally equivalent unprefixed rate `s^-1` while retaining its information-rate meaning.
- `tick` has time dimension and canonical unit `s`, but conversion requires the exact project time quantum. The nine tick-valued definitions therefore carry `PROJECT_TIME_QUANTUM_REQUIRED` rather than a fabricated number of seconds.
- The legacy `FNU` turbidity token has no approved SI conversion or dimension contract in the source. It remains null and release-blocking under `UNRESOLVED_LEGACY_UNIT_FNU`.
- Absolute temperature uses kelvin. No Celsius offset conversion was introduced because the source parameters already use `K`.

## Defaults and limits

Source decimal defaults are retained as exact decimal text. A consumer must parse them into its declared bounded representation, reject non-finite values, then check the normalized bounds and dimensions. The catalog does not turn a large integer literal into an imprecise floating-point value during documentation generation.

Limit normalization is deliberately conservative:

- direct numeric intervals and inequalities become structured bounds;
- `finite`, `non-zero`, and `finite non-zero` remain explicit numeric predicates;
- finite closed choices become `enum_values`;
- references such as `>lower_frequency` resolve to the exact same-family parameter definition where the token matches;
- expressions such as `2^width`, constants such as `pi`, schema-valid maps, registered profiles, width-matched vectors, and content digests retain their source expression and require the named validator;
- `unset` and `unassigned` are placeholders, not usable defaults.

No minimum, maximum, enum, identifier, digest, model reference, temperature dependency, or tolerance may be synthesized from prose, a parameter name, or common engineering practice.

## Baseline validation result

| Status | Count | Interpretation |
|---|---:|---|
| `normalized_planning_record` | 702 | Unit/default/constraint information was deterministically materialized from the source. This is not physical validation. |
| `normalized_with_deferred_validator` | 67 | A symbolic or semantic source constraint must be enforced by a reviewed validator. |
| `contextual_normalization_required` | 9 | A scheduler tick requires the project's exact time quantum before conversion to seconds. |
| `unresolved_release_blocking` | 23 | Twenty-two placeholder defaults and one unresolved `FNU` unit cannot support release until a reviewed revision resolves them. |

Diagnostics may overlap within one definition, so their counts are not a partition:

| Diagnostic | Occurrences | Required response |
|---|---:|---|
| `PROJECT_TIME_QUANTUM_REQUIRED` | 9 | Resolve the immutable project quantum and perform checked tick-to-second conversion. |
| `SEMANTIC_LIMIT_VALIDATOR_REQUIRED` | 63 | Use a registered enum/profile/schema/vector/digest validator; do not accept arbitrary text. |
| `SYMBOLIC_LIMIT_VALIDATOR_REQUIRED` | 26 | Resolve exact dependency revisions and dimension-check the expression. |
| `SOURCE_PLACEHOLDER_DEFAULT` | 22 | Supply reviewed explicit content before the affected definition becomes releaseable. |
| `UNRESOLVED_LEGACY_UNIT_FNU` | 1 | Add an approved turbidity quantity/unit contract and migration; never assume equivalence. |

## Resolution algorithm

Before a parameter reaches a model or solver, a consumer must:

1. resolve the exact family-scoped definition ID and immutable revision;
2. verify that the selected component variant is allowed to override that family parameter;
3. validate the source literal against `value_type`, expression policy, enum or external validator, and finite-value policy;
4. resolve every symbolic dependency without cycles and validate the expression dimension;
5. resolve contextual units such as `tick`, then convert to the canonical internal unit with checked overflow and rounding;
6. enforce minimum, maximum, and semantic constraints in canonical units;
7. map the parameter to an exact model/revision input only when quantity and dimension are compatible;
8. retain source literal, normalized value, definition revision, conversion policy, model mapping, and content digests in project/result lineage;
9. emit a structured diagnostic and stop the affected operation when any required record is unknown, ambiguous, incompatible, placeholder, or release-blocking.

A database or Library Service may store and resolve these records, but it does not define their physics and the simulation engine must not read storage directly.

## Worked records

### Resolved coherent-SI scalar

`pdef-passives-resistor-resistance` preserves source default `1000`, canonical unit `ohm`, and numeric constraint `>0`. Its status is `normalized_planning_record`; this does not assert a resistor model or measured accuracy.

### Closed dimensionless selector

`pdef-connectivity-ground-reference_kind` preserves default `signal` and the exact closed set `signal`, `analog`, `digital`, `power`, `chassis`, `earth`, and `protective-earth`. It stores no physical unit and applies no prefix.

### Contextual scheduler time

`pdef-analog-mixed-signal-data-converter-latency` preserves the source default of one `tick`, identifies time dimension and canonical `s`, and leaves the canonical value null until the project time quantum resolves.

### Explicit unresolved legacy unit

`pdef-sensors-environment-water-quality-sensor-turbidity` preserves source default `0` and token `FNU`, but its internal unit and dimension are null. It is release-blocking; neither zero nor the familiar unit label is evidence for an SI conversion.

## Publication and change control

A parameter definition may become publication-ready only when required units, dimensions, defaults, bounds, symbolic dependencies, expression policy, provenance, and validators resolve and the relevant component/model validation exists. A new revision is required when a published definition changes meaning. Existing project and result lineage must continue resolving the old revision.

Hard deletion is forbidden for a published or referenced definition. Deprecation must name a replacement when one exists, preserve reverse dependencies, and provide an explicit unit- and meaning-safe migration. A catalog count is an inventory fact only; it is not evidence of model coverage, vendor coverage, or product completeness.

## Canonical limitations

- The 801 definitions cover only parameters currently present in the frozen component registry; they do not enumerate every possible physical or vendor parameter.
- The catalog does not normalize independent parameters inside the nine-record seed model registry. Explicit model bindings must map those separately.
- Per-parameter temperature behavior is not supplied by the compact registry and remains unknown.
- Semantic constraints require future allowlisted validators; arbitrary database code or host-language expressions are prohibited.
- Source defaults and limits may be revised only through stable revision and migration governance; this baseline deliberately preserves rather than repairs unevidenced source data.
