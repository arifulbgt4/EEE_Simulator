# Package and Physical Appearance Contract

Status: **Normative baseline 1.0**  
Requirements: **REQ-037 and REQ-038**  
Registry: [package-registry.yaml](package-registry.yaml)

## Product intent

Basic components must be recognizable in a physical view: a resistor should look like a resistor, a polarized capacitor should expose its polarity stripe and lead relationship, a diode should show its cathode band, an LED should show lens and polarity cues, and a transistor or IC should expose its package silhouette, leads/contacts, pin numbering, orientation mark, and printed marking area. This is an educational and interaction view, not a photorealistic rendering requirement or a manufacturing guarantee.

Integrated circuits are not a single appearance. Electrical function, schematic symbol, simulation model, physical package, and optional PCB footprint are separate, so the same function may use DIP, SIP, SOIC, SSOP, TSSOP, QFP, QFN, DFN, PLCC, LGA, BGA, CSP, SOT, TO, module, or a custom package with a validated pin map.

## Five independent layers

| Layer | Owns | Must not silently own |
|---|---|---|
| Function/family | Logical purpose, pins, parameters, capabilities | Package geometry or vendor footprint |
| Schematic symbol | Connectivity-oriented original artwork | Physical dimensions |
| Electrical model | Equations, events, engine binding, accuracy | Visual body or pin placement |
| Physical package | Body/lead geometry, materials, markings, orientation, pin numbers | Electrical pin meaning |
| Footprint | Sourced pads/holes/courtyard and manufacturing rules | Simulation behavior |

`DevicePackageBinding` is the only bridge: it maps logical pins to package pins explicitly and optionally selects reviewed package parasitics.

## Required physical representation

Every released `basic-component` variant has original scalable vector or procedural geometry containing:

- body shape and material regions;
- leads, contacts, terminals, lens/window, tab, shield, or other defining geometry;
- visible polarity, cathode, positive terminal, pin-one, keyed corner, or direction cue where applicable;
- readable reference, value, device-code, rating, and applicable safety-marking areas without unlicensed protected vendor or certification marks;
- realistic default proportions and colors, while maintaining non-color cues;
- three LOD levels: silhouette, orientation-and-pins, and markings/material detail;
- selected, hovered, energized, failed, and disabled states that do not obscure identity;
- a declared accuracy claim: `illustrative`, `generic-dimensioned`, or `manufacturer-verified`.

The editor must not imply that an illustrative body is a verified footprint, enclosure fit, creepage/clearance solution, thermal model, or manufacturer part.

## View switching and interaction

Schematic, physical, and package views are renderings of the same component instance. Switching view preserves instance ID, project hierarchy, connectivity, logical-to-physical pin map, parameters, model and fidelity binding, simulation state, failures, selection, labels, rotation, and undo/redo history. Wiring remains attached to logical pins; the renderer resolves their current visible anchors.

Rotation uses the package orientation contract. Mirroring changes presentation only and cannot renumber electrical pins. The user can inspect logical name, package number, electrical type, and mapping from either view. Any incomplete or ambiguous map blocks release/export and is shown as a diagnostic.

## Package taxonomy

- **Axial/radial passives:** cylindrical, can, disc, bead, chip, polarized and non-polarized forms.
- **Optoelectronic:** round/rectangular through-hole and SMD LEDs with lens and polarity cues.
- **Transistor/power:** SOT-23/SOT-89/SOT-223, TO-92/TO-126/TO-220/TO-247, DPAK/D2PAK, and modules.
- **Through-hole IC:** DIP, SIP, and ZIP.
- **Gull-wing/J-lead IC:** SOIC, SSOP, TSSOP, QFP, and PLCC.
- **Leadless IC:** QFN and DFN, including exposed pads.
- **Grid-array/scale:** LGA, BGA, and CSP with row/column naming and A1 orientation.
- **Modules/interfaces:** sensor, RF, display, electromechanical, connector, and cable profiles.
- **Custom:** constrained parametric body/contact generator plus explicit pin mapping.

## Parametric IC package designer

The designer creates a new immutable `PackageDefinition` revision; it never edits a shared package in place. Required inputs are:

1. package classification and mounting style;
2. body shape, length, width, height, corner/chamfer, standoff, and optional thermal slug;
3. lead/contact form, row count, per-row distribution, pitch, span, width, length, thickness, and excluded positions;
4. numbering direction, pin-one/A1 location, zero-rotation orientation, keyed features, and mirror policy;
5. marking fields, material regions, realistic color hints, and non-color orientation cues;
6. optional sourced tolerance/drawing reference and optional footprint link;
7. explicit device logical-pin to package-pin map, NC/reserved pins, exposed pads, shields, and duplicate electrical connections;
8. optional package parasitics that are separately versioned and visible to the simulation user.

Designer outputs include previewable LOD geometry, a package contact table, orientation diagrams, validation report, provenance, accuracy claim, and stable revision ID. Custom packages are project-local until engineering, accessibility, and license review approves catalog publication.

## Designer validation

- Dimensions are finite, positive where applicable, in SI base units, and within platform safety limits.
- Pin/contact count is an integer within 1..4096; no duplicate contact identifiers or geometric collisions.
- Numbering covers every present contact exactly once; intentionally absent and NC positions are explicit.
- Every required logical pin maps exactly once; multi-bonded pins require an explicit allowed multiplicity.
- Power, ground, shield, exposed/thermal pad, and mechanical-only roles remain distinct.
- Pin-one/polarity is visible at every LOD where pin identity is actionable and after all allowed rotations.
- Duplicate, missing, out-of-range, and unmapped pins are hard validation errors; package-specific limits are enforced.
- Text and markings do not overlap contacts at the validation zoom.
- Shape and text identify orientation without relying on color.
- A footprint or dimensional-accuracy claim is blocked without a cited source and review evidence.

## Rendering and performance

Geometry is authored in normalized package coordinates and rendered through the platform Canvas/WebGL2 pipeline; SVG export is generated from the same semantic geometry. WebGPU remains optional and benchmark-gated. Repeated bodies use instancing and cached LOD meshes. Physical rendering must not block the main UI thread or change simulation state.

At distant zoom the silhouette and polarity/pin-one cue remain; at medium zoom contacts and numbering appear; at close zoom markings and material details appear. Decorative details are omitted before identity, connectivity, or accessibility cues.

## Accessibility

Every physical representation exposes an accessible name, family/variant, package, orientation, polarity, pin count, selected pin, value/marking, and fault state. Keyboard navigation follows logical pin order. Tooltips and the inspector repeat color-band or LED-color meaning as text. High-contrast and monochrome modes retain shape and label cues.

## Provenance and licensing

Project package geometry and symbol artwork are original Apache-2.0 assets. IEC/ANSI conventions may guide familiar semantics, but IEC 60617 artwork is not copied. Manufacturer drawings may supply reviewed dimensions and pinouts when citation and redistribution terms permit; logos, trade dress, and proprietary 3D models are not copied by default.

## Physical QA matrix

| Case | Required result |
|---|---|
| Resistor | Body, leads, readable value/color-band text equivalent, axial/SMD choices. |
| Polarized capacitor | Positive/negative cue remains after rotation and in monochrome. |
| Diode/LED | Cathode/polarity cue, lens/body, lead/contact relationship. |
| Transistor | Correct SOT/TO silhouette, numbered pins, tab/flat-face orientation. |
| DIP/SOIC/TSSOP | Notch/dot, pin-one, counterclockwise numbering, validated logical map. |
| QFP/QFN/DFN | Four/dual side contact placement, chamfer/dot, exposed pad handling. |
| BGA/LGA/CSP | A1 cue, row/column labels, hidden-contact inspection, explicit map. |
| Custom IC | Validated geometry, numbering, marking, orientation, and immutable revision. |
| View switch | No loss/change of identity, wiring, parameters, model, or state. |
| Accuracy claim | Illustrative and verified geometry are visually and textually distinguished. |

## Release gate

A `basic-component` variant cannot advance to `Released` until its schematic symbol, physical representation, package compatibility, explicit pin maps, orientation/polarity behavior, LOD behavior, accessibility metadata, provenance/license, and visual regression evidence are complete. Package entries remain outside the 162-family/502-variant counts.
