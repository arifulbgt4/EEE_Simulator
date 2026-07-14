# Variant Pin Profile Catalog

Status: **Normative catalog guide 1.0**
Requirements: **REQ-009, REQ-010, REQ-022, REQ-037, REQ-038**
Machine-readable source: [variant-pin-profiles.yaml](variant-pin-profiles.yaml)

## Purpose

Electrical families often contain valid variants with different topologies. A two-terminal family preview cannot describe an SPDT switch, center-tapped transformer, RGB LED, sensored BLDC motor, USB-C connector, dual-port SRAM, or N-port RF network. This catalog assigns every built-in variant one stable, explicit `PinProfile` without splitting the frozen 162-family/502-variant baseline.

## Coverage invariants

| Record | Count | Rule |
|---|---:|---|
| Component families | 162 | Every family has one stable role vocabulary. |
| Built-in variants | 502 | Every variant has exactly one `pin_profile` reference. |
| Pin profiles | 502 | Every profile resolves exactly one family and variant. |
| Dangling or duplicate mappings | 0 | Release validation treats either condition as an error. |

Profile IDs use `pinprof-<category>-<family>-<variant>`. They are stable public identifiers, not display strings. The registry records profile revision `1.0.0`; a semantic topology change requires a new revision and migration.

## Resolution model

1. Resolve the variant from [component-registry.yaml](component-registry.yaml).
2. Resolve its `pin_profile` in [variant-pin-profiles.yaml](variant-pin-profiles.yaml).
3. Expand each bounded bus or parameterized group using its declared family or profile parameter.
4. Preserve top-level order, then ascending group index and declared suffix order.
5. Materialize normalized `PinDefinition` records and run ERC/netlist validation.
6. Map logical pins to model terminals through `ModelBinding` and to physical contacts only through `DevicePackageBinding`.
7. Persist profile ID/revision, resolved parameters, and resolved ordered pin IDs in project/result provenance.

No editor, importer, engine, or package renderer may infer exact variant pins from the family preview, symbol geometry, display name, package count, or model filename.

## Profile shapes

- **Scalar:** one stable logical terminal such as an anode, clock, reference, or RF feed.
- **Bus:** one logical terminal with a fixed or finitely bounded width and explicit bit order.
- **Parameterized group:** a bounded ordered set such as connector contacts, resistor-array elements, subcircuit ports, transformer windings, display rows, or RF ports.
- **Optional group:** terminals absent by default and enabled explicitly, such as a MOSFET body, IGBT Kelvin emitter, shield, exposed phototransistor base, or flow-control pins.
- **Parameterized direction:** allowed only for a declared interface/profile parameter and resolved before netlisting.

## Representative topology corrections

| Variant or family | Normative topology example |
|---|---|
| Controlled sources | Separate `OUT+`/`OUT-` and voltage-control or current-sense terminals. |
| Potentiometer | End A, wiper, and end B. |
| Switches and relays | Exact SPST, SPDT, DPST, DPDT, coil, and latching-coil contacts. |
| RGB LED | Red, green, blue, and declared common electrode. |
| IGBT | Collector, gate, emitter, and optional Kelvin emitter; never MOSFET drain/source/body names. |
| Transformers | Two-winding, center-tapped, pulse, and autotransformer topologies. |
| BLDC/stepper/servo | Exact phase or winding terminals, sensor/control pins, supplies, and mechanical shaft output. |
| Displays and HMI | Segment/matrix groups or explicit LCD/OLED/e-paper protocol buses. |
| Connectors and cables | Protocol-specific USB/RJ45/BNC contacts or bounded parameterized contact groups. |
| Digital, memory, MCU, and computer blocks | Directional buses, clocks, resets, controls, interrupt/status lines, and explicit power references. |
| RF networks | One-port, two-port, four-port coupler, balun, splitter, mixer, antenna-array, and bounded N-port profiles. |

## Family, model, and package boundaries

The family owns semantic roles and behavior. The variant selects exact topology. A `ModelBinding` maps that topology to an engine artifact. A `PackageDefinition` owns reusable geometry. A `DevicePackageBinding` maps exact logical pins to package contacts and declares NC, shield, exposed, or thermal contacts. These records may reference one another, but none may silently rewrite another.

Candidate `package_refs` in the component registry are compatibility choices, not completed bindings. A released variant still requires an explicit, validated `DevicePackageBinding` for every claimed package revision.

## Validation failures

Normalization fails on a missing/dangling profile, duplicate variant mapping, duplicate pin ID, non-contiguous order, empty domain, unsupported direction, unbounded bus/group, unresolved topology parameter, enabled optional pin without its group, model-order mismatch, or implicit package contact. Unsupported or ambiguous imported topology remains quarantined until a reviewed project-local or catalog profile exists.
