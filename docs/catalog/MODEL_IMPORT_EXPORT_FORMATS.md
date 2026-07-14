# Model Import and Export Formats

Status: **Normative interchange plan 1.0**  
Related contracts: [COMPONENT_MODEL_CONTRACT.md](COMPONENT_MODEL_CONTRACT.md), [variant-pin-profiles.yaml](variant-pin-profiles.yaml), [package-registry.yaml](package-registry.yaml)

## Supported targets

| Format | Direction | Primary use | Required metadata | Boundary |
|---|---|---|---|---|
| SPICE `.model` / `.subckt` | Import/export subset | Analog and compact models | dialect, ordered pins, parameters, analyses, temperature assumptions | External engine adapter |
| Verilog/SystemVerilog | Import; source-preserving export | Digital, RTL, FPGA, mixed wrappers | language version, top module, parameters, clocks/resets, timescale | Sandboxed Verilator adapter |
| Verilog-A/AMS 2023 | Import; source-preserving export | Analog behavioral and mixed signal | standard version, disciplines, terminals, parameters | Isolated compatible adapter |
| IBIS 8.0 | Import | I/O buffers and interconnect | component/model selector, package parasitics, pin map, voltage range | Validated IBIS adapter |
| Touchstone 2.1 | Import/export | N-port RF/network data | port count/order, reference impedance, frequency unit, data representation | RF adapter |
| CSV/PWL | Import/export | Stimuli, tables, calibration, waveforms | column schema, units, interpolation, extrapolation | Core parser |
| VCD/FST | Import/export | Digital traces | timescale, signal hierarchy, widths, logic states | Waveform subsystem |
| HEX/ELF | Import | Firmware and memory images | address base, architecture, endianness, entry point, segments | Sandboxed MCU/CPU adapter |

Format support is capability-scoped. Listing a format does not imply full language or dialect coverage. Each importer publishes its accepted subset and rejects or diagnoses unsupported constructs.

Unless an applicable release gate explicitly requires a format, import support is an independently versioned component extension under the lifecycle rules in `COMPONENT_MODEL_CONTRACT.md`. A core component release may precede that extension, but the UI, API, registry normalization, and documentation must report the format as unavailable until its import task and evidence are complete. A required gate format is never optional.

## Import pipeline

1. **Acquire:** read a user-selected artifact without executing it; compute a cryptographic digest.
2. **Identify:** determine format and version from content plus user confirmation, never from filename alone.
3. **License review:** capture source, authors/organization, SPDX expression, redistribution permission, and modifications.
4. **Parse in isolation:** apply size, depth, token, time, CPU, and memory limits; no outbound network.
5. **Normalize:** convert units to SI, preserve original text/artifact, and create stable internal names.
6. **Map:** select or create a reviewed variant `PinProfile`; require explicit logical pins, buses/endianness, parameterized group resolution, package contacts where present, parameters, domains, and supported analyses.
7. **Validate:** run syntax, semantic, nominal, boundary, failure, and determinism checks against declared references.
8. **Quarantine or publish:** unreviewed artifacts remain project-local and cannot enter the public catalog.

## Pin and package mapping

Original ordered pins are immutable provenance. Normalized logical pins map explicitly to the selected variant `PinProfile`, never to the family's compact preview. The importer records profile ID/revision, resolved bus widths and group cardinalities, and a complete model-pin-to-logical-pin map. An incompatible topology requires a new reviewed variant/profile or a project-local custom profile; it cannot silently mutate a published profile.

If an imported model includes package data, that data becomes a separate package revision or package-parasitic profile; it does not rewrite the component family or `PinProfile`. Every physical pin map validates pin existence, uniqueness, NC/reserved/exposed pads, orientation, and round-trip export.

## Units, time, and logic

All normalized numerical values use SI base units. Importers preserve original scale tokens for round-trip diagnostics. Verilog timescale is converted to the project integer timebase with an explicit rounding/error policy. Digital values preserve `0`, `1`, `X`, `Z`, width, signedness, drive strength when supported, and unknown-state loss warnings when not.

## Format-specific rules

### SPICE

Record the dialect and engine version. Preserve `.model`/`.subckt` source, ordered node list, default parameters, expressions, temperature, and analysis limitations. Reject unsafe file inclusion, shell escapes, uncontrolled plugins, and path traversal. Convergence in one engine does not prove portability.

### Verilog/SystemVerilog and Verilog-A/AMS

Declare the supported syntax subset, top entity, parameters, timescale, disciplines, and foreign interfaces. Compilation/execution occurs without network access under CPU/memory/time limits and read-only inputs. DPI, PLI, system commands, unrestricted file I/O, and undeclared external modules are prohibited by default.

### IBIS and Touchstone

Preserve case-sensitive identifiers, port/pin order, reference impedance, frequency units, matrix/data representation, and package/parasitic sections. Validate dimensions, monotonic frequency axes, finite values, and declared reference planes. Extrapolation is opt-in and recorded.

### CSV/PWL and waveform formats

A sidecar schema or import wizard records column names, quantity kinds, units, time basis, delimiter, missing-value rule, interpolation, and extrapolation. Duplicate or non-monotonic time points require an explicit resolution policy.

### HEX/ELF

Firmware images bind to an architecture/profile, address space, endianness, memory map, and entry point. Segments outside declared memory, overlapping segments, malformed records, and architecture mismatch are hard errors. Imported firmware never runs outside the selected sandboxed simulator.

## Export rules

- Export only information representable by the target format; emit a loss report for omitted fidelity, failures, package metadata, or state.
- Include registry IDs, schema versions, engine/version provenance, seeds, and source digests in a sidecar manifest when the format cannot hold them.
- Never export third-party models when redistribution is not allowed.
- Preserve explicit profile ID/revision, resolved logical pin order, bus/group shape, model pin order, and units; do not guess a vendor pinout.
- Waveform export states sampling/decimation and whether values are raw or display-derived.

## Security and resource limits

Imports use content-size, expanded-size, nesting, symbol-count, pin-count, waveform-sample, compile-time, runtime, CPU, and memory quotas. Archives reject absolute paths, symlinks, duplicate ambiguous names, and traversal. External engines run as isolated processes/containers without outbound network, with read-only inputs and disposable writable scratch space.

## Acceptance cases

- Valid minimal artifact for every supported format.
- Boundary pin count, bus width, parameter count, waveform size, and frequency range.
- Malformed syntax, unknown dialect/version, nonfinite values, unit mismatch, duplicate pins, and unsupported construct.
- License missing or redistribution forbidden.
- Timeout, memory limit, cancellation, engine crash, and deterministic retry.
- Import-export-import round trip with a documented semantic loss report.

## Limitations

Format standards evolve. Exact supported versions are pinned by adapter releases and dependency/license review. Source-preserving export is not a promise of semantic portability across engines.
