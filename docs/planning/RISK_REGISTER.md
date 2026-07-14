# Risk Register

## Scoring

Likelihood and impact use `Low`, `Medium`, `High`, and `Critical`. Owners are workstream roles rather than named people. A risk is closed only when evidence demonstrates that the exit condition holds.

| ID | Risk | Likelihood | Impact | Mitigation and trigger |
|---|---|---|---|---|
| RSK-001 | Nonlinear convergence failure | High | Critical | Continuation methods, adaptive steps, diagnostics, golden stiff circuits; trigger: non-convergence rate exceeds baseline |
| RSK-002 | Incorrect but plausible model result | Medium | Critical | Independent references, provenance, accuracy envelopes, differential tests |
| RSK-003 | Scope expands to modern transistor-level CPU/GPU | High | Critical | Enforce F0-F5 policy and roadmap non-goals; trigger: task bypasses abstraction gate |
| RSK-004 | Component catalog appears complete but lacks models/tests | High | High | Separate symbol/connectivity/model/validated/released states |
| RSK-005 | Browser memory exhaustion | High | High | Probe selection, chunking, ring buffers, decimation, cloud routing |
| RSK-006 | Main-thread UI freezes | Medium | High | Workers, OffscreenCanvas where supported, no blocking waits, performance gates |
| RSK-007 | Sparse solver does not scale | Medium | High | Sparse formats, symbolic reuse, profiling, server/HPC adapters |
| RSK-008 | Analog/digital event ordering is nondeterministic | Medium | Critical | Integer timebase, deterministic tie-breaking, replay fixtures |
| RSK-009 | Thermal coupling destabilizes electrical solve | Medium | High | Multirate scheduler, bounded iteration, explicit convergence contract |
| RSK-010 | External model is malicious or malformed | High | Critical | Parser limits, no-network sandbox, read-only filesystem, quotas |
| RSK-011 | Vendor model cannot be redistributed | High | High | Provenance/license metadata, user-supplied references, no bundled redistribution by default |
| RSK-012 | Copyleft engine contaminates core distribution | Medium | Critical | Process/API isolation, dependency matrix, legal gate |
| RSK-013 | IEC/third-party symbol artwork is copied unlawfully | Medium | High | Original symbol artwork and reference-only standards mapping |
| RSK-014 | Project schema breaks old projects | Medium | High | Semantic schema versions, migrations, fixtures, round-trip tests |
| RSK-015 | Offline storage quota loses work | Medium | High | Usage warnings, export, recovery snapshots, transactional saves |
| RSK-016 | CRDT merge creates electrically invalid topology | Medium | High | Operation validation, deterministic repair/diagnostics, snapshots |
| RSK-017 | Cross-tenant project/result exposure | Medium | Critical | Object-level authorization, tenant-scoped storage, security tests |
| RSK-018 | Compute abuse causes cost overrun | High | High | Quotas, admission estimation, usage ledger, cancellation, spend controls |
| RSK-019 | Worker crash loses long simulation | Medium | High | Checkpoints, idempotent jobs, leases, retry policy |
| RSK-020 | Results are not reproducible after engine update | Medium | High | Version pinning, immutable provenance, retained compatibility workers where required |
| RSK-021 | Accessibility is bolted on too late | Medium | High | Keyboard/nonvisual contracts from editor foundation, WCAG gates |
| RSK-022 | WebGPU optimization adds complexity without benefit | High | Medium | Benchmark-gated ADR; retain CPU/WASM default |
| RSK-023 | Browser cross-origin isolation unavailable | Medium | Medium | Single-threaded WASM fallback and visible capability status |
| RSK-024 | Public library spreads unsafe or misleading models | Medium | High | Moderation, trust status, provenance, reporting and quarantine |
| RSK-025 | Small task cards omit cross-cutting work | Medium | High | Epic dependencies, traceability audit, task templates, integration tasks |
| RSK-026 | Documentation drifts from implementation | High | High | Docs-as-code gates and Definition of Done requiring simultaneous updates |
| RSK-027 | External engine project becomes unavailable | Low | High | Adapter boundary, exportable formats, version archives, replacement plan |
| RSK-028 | RF/TCAD fidelity is overclaimed | Medium | High | Research-only classification, external datasets, visible limitations |
| RSK-029 | Security headers break embedding/integrations | Medium | Medium | Document cross-origin policy, fallback build, integration tests |
| RSK-030 | Team lacks multidisciplinary review capacity | High | High | Required reviewer roles, staged scope, explicit evidence and external review |
| RSK-031 | Realistic-looking component uses the wrong electrical pin map | Medium | Critical | Separate package from model, stable pin IDs, symbol/package equivalence tests, golden fixtures |
| RSK-032 | Photorealistic detail harms editor performance or accessibility | Medium | High | Parametric vector/Canvas bodies, level of detail, nonvisual labels, performance gates |
| RSK-033 | Package drawing or vendor marking is copied without rights | Medium | High | Original parametric geometry, generic markings, provenance review and no copied protected artwork |
| RSK-034 | Sibling variant IDs exist but resolve to the same behavior | High | Critical | One-to-one semantic profiles, explicit behavior selectors/pin profiles/overrides, sibling-distinguishability audit, and variant-specific CAT evidence; trigger: behavior is inferred from display text |
| RSK-035 | Compact catalog normalization invents unresolved executable fields | High | Critical | Distinguish planning records from releaseable normalized entities, use deterministic parameter/pin/semantic sidecars, and emit blocking unresolved-field diagnostics instead of defaults |
| RSK-036 | Package candidate metadata is mistaken for a verified device binding | High | Critical | Candidate/binding separation, immutable `DevicePackageBinding`, complete contact disposition, candidate-only rejection, and GRC-049..054 binding evidence |

## Review cadence

- Review at every release gate and after a security, accuracy, data-loss, or cost incident.
- High/Critical risks must link to active tasks and test evidence.
- A new component domain or external engine requires a new risk review before tasks become `Ready`.
