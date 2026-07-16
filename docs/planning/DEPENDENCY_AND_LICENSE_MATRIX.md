# Dependency and License Matrix

## Policy

The Apache-2.0 core must not assume that an external executable, generated model, manufacturer library, or standard document can be redistributed. Each adapter pins a version, records its source and license, and passes a release-time review. This matrix is planning evidence, not legal advice.

| Dependency/specification | Intended role | Boundary | License/status | Release rule |
|---|---|---|---|---|
| Next.js/React/TypeScript | Web application and contracts | Core | Verify pinned releases | Include notices required by pinned packages |
| Rust/WebAssembly | First-party local simulation | Core | Toolchain licenses verified when pinned | Apache-compatible dependencies only unless reviewed |
| Emscripten | C/C++ adapter builds where needed | Build/worker | Open source; verify pinned release | Do not assume a single threaded/unthreaded binary; test both modes |
| ngspice | SPICE-compatible reference/heavy adapter | Separate adapter process/service | Verify exact pinned source/build and bundled models | `PLAT-EXT-005`..`PLAT-EXT-018` must establish the shared-library/control boundary, capability, isolation, provenance, differential, and R3 audit evidence; imported models additionally require `PLAT-EXT-019`..`PLAT-EXT-021`; no model redistribution without rights and the API remains engine-neutral |
| Verilator | Verilog/SystemVerilog compilation | Sandboxed compiler worker | LGPL-3.0 or Artistic-2.0 for the tool; generated design rights remain separately reviewed | Pin compiler and runtime; sandbox user HDL |
| Xyce | Large parallel analog workloads | Separate GPL worker/service | GPLv3 target; verify the exact pinned release and license files | `PLAT-HPC-002` and `PLAT-HPC-011` must retain exact engine/build/image, official capability/license review, process isolation, and final distribution disposition; never link into the Apache core and fail closed without current legal evidence |
| gem5 | Microarchitecture/full-system timing research | Separate research worker | BSD-style with source-specific notices | Pin resources/workloads and preserve provenance |
| QEMU | Functional machine/ISA execution | Separate worker | Per-component license matrix | Review each distributed build and device component |
| Accel-Sim/GPGPU-Sim | GPU/accelerator research | Separate research worker | Verify exact repositories/components | User traces and vendor dependencies require separate review |
| PostgreSQL and JSONB | Identity/ownership, library/project metadata, immutable revisions, dependencies, publication/audit/search, validated evolving definitions | Infrastructure behind Library Service | PostgreSQL License; verify pinned distribution | No engine dependency or public contract on vendor-only extensions; separate document database requires ADR evidence |
| S3-compatible storage | Assets, results, checkpoints | Infrastructure API | Provider-independent contract | Encryption, retention, and tenant isolation required |
| Redis Streams | Job dispatch | Infrastructure | Verify pinned release | Jobs remain portable through the documented queue contract |
| Google OpenID Connect | Initial optional personal identity provider | Standards-based provider adapter | Google service terms plus OpenID Connect/OAuth standards; no bundled proprietary SDK assumed | Guest/offline remains available; provider-neutral subject mapping; organizations/RBAC stay R10 |
| IEC 60617 | Symbol naming/reference | Reference only | Subscription/copyrighted database | Create original artwork; do not copy database assets |
| IEEE 315 | Symbol/reference guidance | Reference only | Standards access required | Record reference mapping; do not redistribute protected text/artwork |
| Verilog-AMS 2023 | Analog/mixed-signal language target | Format specification | Accellera specification | Implement only documented supported subset until full conformance |
| IBIS 8.0 | I/O buffer model target | Import format | IBIS Open Forum specification | Preserve model licenses and unsupported-key diagnostics |
| Touchstone 2.1 | S-parameter import target | Import format | IBIS Open Forum specification | Preserve port/reference metadata and source license |
| Manufacturer datasheets and models | Device-specific parameters, validation, bounded generic-device overrides | User/project asset, reference-only record, or approved library | Vendor-specific copyright/license/terms | Default to citation/user-provided reference; no redistribution without rights; ordering code does not imply validation |

## Primary reference targets

These official/upstream locators are planning targets, not retained proof that a future pinned version, license, capability, or distribution was reviewed. The owning task must re-open the applicable source, pin its exact revision and digest where possible, record retrieval and applicability, and retain review evidence before becoming `Ready` or supporting a release. Legacy Source PDF citations are not substitutes; see the [Source and Evidence Policy](../SOURCE_AND_EVIDENCE_POLICY.md).

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

Before an adapter is released, its task must record exact version/hash, build source, license files, included models/resources, process boundary, network/filesystem policy, supported request capabilities and lifecycle operations, request/result/diagnostic mapping, timeout/cancellation/checkpoint/disposal behavior, reproducibility limits, and replacement/export path. The ngspice path is governed by `EPIC-EXT-001`; the Xyce-class R11 path is governed by `EPIC-HPC-001`. Execution success never substitutes for a separate redistribution decision, and an unverified Source PDF citation never substitutes for pinned upstream/license evidence.
