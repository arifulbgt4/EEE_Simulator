# Performance Benchmarks

## Reference classes

Performance claims must name a reproducible reference machine and browser. The first benchmark publication will define:

- `Desktop-Baseline`: 4 physical CPU cores, 8 GB available memory, integrated graphics, current supported desktop browser.
- `Desktop-Recommended`: 8 physical CPU cores, 16 GB available memory, discrete or modern integrated graphics.
- `Cloud-Worker-S`: 4 vCPU and 8 GB memory.
- `Cloud-Worker-L`: 16 vCPU and 64 GB memory.

Exact hardware, OS, browser, power mode, engine build, and dataset commit are stored with every result.

## MVP budgets

| Benchmark | Desktop-Baseline target |
|---|---:|
| Open a 500-component/1,000-net project | <= 2 s |
| DC operating point for reference suite | <= 1 s |
| Reference transient with 100,000 retained samples | <= 5 s |
| Pan/zoom while not simulating | >= 50 FPS p95 |
| Main-thread simulation stall | No task > 100 ms |
| Property edit to visual acknowledgment | <= 100 ms p95 |
| Local autosave acknowledgment | <= 250 ms p95 |
| Waveform interaction with 100,000 points | >= 45 FPS p95 |
| Project archive round trip | <= 3 s and exact semantic equality |
| Render 500 realistic physical component bodies | >= 45 FPS p95 during pan/zoom |
| Toggle schematic/physical view for 500 components | <= 500 ms p95 without changing topology |

## Scale tiers

| Tier | Intended execution | Circuit/system scale |
|---|---|---|
| S | Browser interactive | Up to 500 components and 1,000 nets |
| M | Browser background or small cloud worker | Up to 10,000 event-driven digital elements or 2,000 moderate analog elements, subject to memory |
| L | Cloud CPU worker | Large SPICE, RTL compilation, Monte Carlo, educational full system |
| XL | Cloud/HPC | Xyce-class parallel runs, architecture sweeps, GPU studies, research workloads |

Scale figures are routing thresholds, not unconditional performance promises. The estimator may route a smaller numerically stiff problem to cloud execution.

## Required benchmark suites

- Editor: sparse, dense, hierarchical, long-wire, high-selection-count, realistic physical/package, dual-view switching, and large-waveform scenes.
- Analog: linear sparse solve, stiff RC, oscillator startup, nonlinear diode/MOSFET sweep, and convergence failure.
- Digital: low activity, high fan-out, clock-heavy, contention, and burst-event circuits.
- Mixed signal: frequent analog/digital crossings and synchronized thermal steps.
- Analysis: AC sweep, Monte Carlo 1/100/1,000 runs, thermal grid, and waveform decimation.
- Storage: IndexedDB load/save, migration, archive import/export, checkpoint, and quota failure.
- Cloud: queue wait, cold start, streaming, cancellation, retry, checkpoint/resume, and worker loss.

## Measurement rules

- Report median, p95, maximum, peak resident memory, transferred bytes, retained samples, and thermal throttling indicators.
- Warm and cold measurements are separate.
- Run at least 20 interactive trials or enough batch trials to produce stable confidence intervals.
- Do not exclude failures or timeouts from latency reports.
- A benchmark regression greater than 10% blocks release unless an accepted ADR explains the tradeoff.

## Browser and fallback matrix

The latest two stable desktop releases of Chrome, Edge, Firefox, and Safari are supported. Both single-threaded and threaded WASM builds are tested. Lack of cross-origin isolation must select the single-threaded build with a visible capability status, not break the application.

Mobile editing is outside the MVP. Mobile may open read-only shared projects and static result summaries after a separate release gate.
