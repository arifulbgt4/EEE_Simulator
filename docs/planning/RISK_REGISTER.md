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
| RSK-037 | Model explosion from copying every vendor ordering code | High | High | Generic-device inheritance, bounded overrides, exact package/pin bindings, actual-count audits, and no duplicated internal circuit per SKU |
| RSK-038 | Invalid inheritance changes units, interface, or validity silently | Medium | Critical | Schema-authorized overrides, dimensional/range checks, immutable base revision, override provenance, and rejection tests |
| RSK-039 | Composite or library dependency cycle | Medium | Critical | Typed DAG validation, exact revision edges, cycle detection, dependency closure, and reverse traversal before publication |
| RSK-040 | Inconsistent package or pin binding | Medium | Critical | Orthogonal records, exact PinProfile/package revisions, complete contact disposition, equivalence evidence, and no inferred pin order |
| RSK-041 | Simulation engine becomes coupled to a database or deployment | Medium | High | Library Service resolution to immutable `ComponentDefinitionPlan`, repository interfaces, and architecture tests forbidding direct engine storage dependencies |
| RSK-042 | Arbitrary database content executes as model code | Medium | Critical | Declarative schema/expression subset, dimension/resource validation, allowlisted kernels, sandboxing, no dynamic host/network access |
| RSK-043 | Imported model is unsafe, malformed, or misleading | High | Critical | Quarantine, parser limits, hashes, trust/validation state, dependency closure, sandbox policy, and explicit unsupported diagnostics |
| RSK-044 | Model or dependency license is incompatible | High | High | SPDX/source records, redistribution flags, legal review, isolation, system-publication block, and replacement plan |
| RSK-045 | Vendor datasheet or model redistribution is restricted | High | High | Store citations/extracted facts only as permitted, user-supplied references, no protected asset redistribution, and license audit |
| RSK-046 | Unsupported scientific or multiphysics claim | Medium | Critical | Applied Physics lineage, evidence-state labels, explicit approximation/limits, category envelope, and review before publication |
| RSK-047 | Model is used outside unsupported validity ranges | High | Critical | Machine-readable ranges, environment/analysis checks, out-of-validity status, no silent extrapolation, and boundary fixtures |
| RSK-048 | False precision hides model or measurement uncertainty | High | High | Uncertainty budget, category-specific metrics, significant-digit policy, evidence state, and user-visible interval/limitations |
| RSK-049 | Unvalidated user model is treated as system-trusted | High | Critical | Separate user/system lifecycle, trust badges, private draft default, validation/publication workflow, and sandbox restrictions |
| RSK-050 | Large waveform and raw measurement storage cost grows without bound | High | High | Probe selection, chunks, decimation copies, lifecycle/tier policy, immutable object storage, quotas, retention and export |
| RSK-051 | Offline and cloud revisions conflict or overwrite data | Medium | High | Immutable revisions, outbox/idempotency, explicit conflict copies/resolution, local retention until acknowledgement, and export |
| RSK-052 | Deleted dependency breaks historical projects or results | Medium | Critical | No hard delete of referenced/published revisions, reverse-dependency checks, soft deletion, archive, supersession, and exact historical resolution |
| RSK-053 | Search and indexing cannot scale with market library growth | Medium | High | PostgreSQL indexed metadata/JSONB policy, measured query budgets, pagination, derived indexes, and evidence before adding another database |
| RSK-054 | Revision migration complexity strands old projects | High | High | Stable logical/revision IDs, content hashes, compatibility metadata, explicit migration plans, retained resolvers, and round-trip fixtures |
| RSK-055 | Physical validation is slow or costly | High | High | Small staged benchmark set, shared calibrated procedures, immutable raw data, uncertainty budgets, independent review, and no premature accuracy claim |
| RSK-056 | Unnecessary multi-database architecture adds inconsistency and operations cost | Medium | High | PostgreSQL plus validated JSONB first, bounded object/IndexedDB roles, storage abstraction, and ADR evidence before another document database |
| RSK-057 | Model provenance or lineage has gaps | High | Critical | Required source/hash/license/trust fields, principle-to-result lineage, publication block, reproducibility manifest, and audit |
| RSK-058 | Incompatible model revisions compose successfully but incorrectly | Medium | Critical | Exact revision/hash locks, typed ports, compatibility ranges, DAG closure, migration tests, and fail-closed resolution |
| RSK-059 | External engine results are nondeterministic or irreproducible | Medium | Critical | Version/image pinning, deterministic seed/time policy, adapter capability declaration, reproducibility manifest, tolerance class, and differential replay |
| RSK-060 | Documentation, schemas, registries, tasks, and runtime drift apart | High | Critical | Stable IDs, schema/count/link validators, synchronized Definition of Done, release audits, and `PLAT-DATA-008` drift test |

## Review cadence

- Review at every release gate and after a security, accuracy, data-loss, or cost incident.
- High/Critical risks must link to active tasks and test evidence.
- A new component domain or external engine requires a new risk review before tasks become `Ready`.
