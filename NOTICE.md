# Notices

Web-Based Electronics and Computer Simulation Platform

Copyright 2026 Web-Based Electronics and Computer Simulation Platform contributors.

The open-source core is distributed under the Apache License, Version 2.0. See [LICENSE](LICENSE).

This repository may reference, interoperate with, or accept files associated with third-party projects and standards. Those names remain the property of their respective owners. Reference does not imply that third-party code, models, symbol artwork, datasets, or trademarks are included in or relicensed by this project.

Third-party artifacts must retain their own attribution, provenance, version, and license information. In particular:

- imported manufacturer and community component models remain subject to their source terms;
- IEC 60617 symbol artwork is not bundled merely because the project uses original IEC-aligned symbols;
- ngspice, Xyce, Verilator, gem5, QEMU, GPGPU-Sim, Accel-Sim, Emscripten, and other external engines or tools are not automatically part of the Apache-2.0 core;
- GPL or mixed-license engines must remain behind the process boundary defined by [ADR-0008](docs/decisions/ADR-0008-external-engine-process-isolation.md) and require distribution review;
- hosted-service deployment does not change the license of an imported model or external engine.

The authoritative dependency and attribution records are [docs/planning/DEPENDENCY_AND_LICENSE_MATRIX.md](docs/planning/DEPENDENCY_AND_LICENSE_MATRIX.md) and [docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md](docs/architecture/OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md).
