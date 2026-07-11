# Dependency and License Matrix

## Policy

The Apache-2.0 core must not assume that an external executable, generated model, manufacturer library, or standard document can be redistributed. Each adapter pins a version, records its source and license, and passes a release-time review. This matrix is planning evidence, not legal advice.

| Dependency/specification | Intended role | Boundary | License/status | Release rule |
|---|---|---|---|---|
| Next.js/React/TypeScript | Web application and contracts | Core | Verify pinned releases | Include notices required by pinned packages |
| Rust/WebAssembly | First-party local simulation | Core | Toolchain licenses verified when pinned | Apache-compatible dependencies only unless reviewed |
| Emscripten | C/C++ adapter builds where needed | Build/worker | Open source; verify pinned release | Do not assume a single threaded/unthreaded binary; test both modes |
| ngspice | SPICE-compatible reference/heavy adapter | Separate adapter process/service | Verify exact source and bundled models | No model redistribution without provenance; API contract remains engine-neutral |
| Verilator | Verilog/SystemVerilog compilation | Sandboxed compiler worker | LGPL-3.0 or Artistic-2.0 for the tool; generated design rights remain separately reviewed | Pin compiler and runtime; sandbox user HDL |
| Xyce | Large parallel analog workloads | Separate GPL worker/service | GPLv3 | Never link into Apache core; distribution requires legal review |
| gem5 | Microarchitecture/full-system timing research | Separate research worker | BSD-style with source-specific notices | Pin resources/workloads and preserve provenance |
| QEMU | Functional machine/ISA execution | Separate worker | Per-component license matrix | Review each distributed build and device component |
| Accel-Sim/GPGPU-Sim | GPU/accelerator research | Separate research worker | Verify exact repositories/components | User traces and vendor dependencies require separate review |
| PostgreSQL | Cloud metadata | Infrastructure | Verify pinned distribution | No public contract may depend on vendor-only extensions |
| S3-compatible storage | Assets, results, checkpoints | Infrastructure API | Provider-independent contract | Encryption, retention, and tenant isolation required |
| Redis Streams | Job dispatch | Infrastructure | Verify pinned release | Jobs remain portable through the documented queue contract |
| IEC 60617 | Symbol naming/reference | Reference only | Subscription/copyrighted database | Create original artwork; do not copy database assets |
| IEEE 315 | Symbol/reference guidance | Reference only | Standards access required | Record reference mapping; do not redistribute protected text/artwork |
| Verilog-AMS 2023 | Analog/mixed-signal language target | Format specification | Accellera specification | Implement only documented supported subset until full conformance |
| IBIS 8.0 | I/O buffer model target | Import format | IBIS Open Forum specification | Preserve model licenses and unsupported-key diagnostics |
| Touchstone 2.1 | S-parameter import target | Import format | IBIS Open Forum specification | Preserve port/reference metadata and source license |
| Manufacturer models | Device-specific behavior | User/project asset or approved library | Vendor-specific | Default to user-provided reference; redistribution opt-in only after review |

## Verified primary references

- Apache License 2.0: <https://www.apache.org/licenses/LICENSE-2.0.txt>
- Emscripten pthreads and COOP/COEP: <https://emscripten.org/docs/porting/pthreads.html>
- ngspice shared-library control: <https://ngspice.sourceforge.io/shared.html>
- Verilator overview and licensing: <https://verilator.org/guide/latest/overview.html> and <https://verilator.org/guide/latest/copyright.html>
- Xyce role and GPLv3: <https://xyce.sandia.gov/about-xyce/>
- gem5 documentation and license summary: <https://www.gem5.org/documentation/> and <https://www.gem5.org/about/>
- QEMU license documentation: <https://www.qemu.org/docs/master/about/license.html>
- Accel-Sim framework: <https://accel-sim.github.io/>
- IEC 60617: <https://webstore.iec.ch/en/publication/2723>
- Accellera Verilog-AMS: <https://www.accellera.org/downloads/standards/v-ams>
- IBIS and Touchstone specifications: <https://ibis.org/specs/>

## Adapter acceptance

Before an adapter is released, its task must record exact version/hash, build source, license files, included models/resources, process boundary, network/filesystem policy, supported request capabilities, result mapping, cancellation behavior, reproducibility limits, and replacement/export path.

