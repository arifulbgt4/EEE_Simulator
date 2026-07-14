# Security, Privacy, and Sandboxing

Status: Normative  
Related: [System Architecture](./SYSTEM_ARCHITECTURE.md), [API and Worker Protocols](./API_AND_WORKER_PROTOCOLS.md), [Open Source and Third-Party Licenses](./OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md)

## 1. Security objectives

The platform accepts schematics, archives, custom component/package definitions, SPICE models, HDL, firmware, media, and external-engine inputs. All are untrusted even when uploaded by an authenticated user. The source PDF requires browser and server execution across resource-intensive engines and identifies browser memory, numerical failure, UI performance, and excessive workloads as core risks. [Source PDF, pp. 25-26, 36, 39-40]

Security objectives are:

- preserve tenant confidentiality and authorization;
- prevent imported content or simulation engines from escaping their execution boundary;
- maintain project/result integrity and provenance;
- keep local and cloud services available under bounded abusive or accidental workloads;
- collect the minimum operational data needed;
- make security and privacy failures explicit and auditable.

## 2. Trust zones

~~~mermaid
flowchart LR
    U["Untrusted user content"]
    B["Browser sandbox"]
    C["Authenticated control plane"]
    E["Isolated execution plane"]
    S["Trusted storage and operations"]
    X["External engines and toolchains"]

    U --> B
    B -->|"validated HTTPS/WSS"| C
    C -->|"signed immutable job envelope"| E
    E --> X
    C --> S
    E -->|"checksummed outputs"| S
    X -. no direct trust .-> C
~~~

Cross-zone messages MUST be authenticated where applicable, authorized, schema-validated, size-bounded, correlated, and safe to retry. A lower-trust zone never supplies the final tenant ID, resource profile, executable path, object key, or authorization decision.

## 3. Threat model

Required threat cases include:

- cross-tenant access through guessed IDs, stale signed URLs, cache keys, collaboration channels, or object references;
- archive traversal, decompression bombs, parser abuse, malicious media, or duplicate/case-colliding paths;
- model, HDL, firmware, custom equation, or external-engine escape;
- arbitrary script or remote-resource execution through symbols, physical views, IC packages, Markdown, SVG, or labels;
- denial of service through huge circuits, event storms, delta-cycle loops, matrix pathologies, waveforms, logs, or compilation;
- dependency, model, container, or compiler supply-chain compromise;
- result tampering, stale worker publication, replay, or nondeterministic provenance loss;
- WebSocket/SSE authorization drift and cross-site request attacks;
- secrets in projects, logs, telemetry, crash dumps, exports, or results;
- malicious public-library assets and license/provenance laundering.

## 4. Identity, session, and authorization

- Cloud identity uses a standards-based external identity/OIDC-compatible boundary; the project stores no password-equivalent material in portable files.
- Browser sessions use secure, HttpOnly, SameSite cookies or an equivalently reviewed mechanism; state-changing requests require origin/CSRF protection.
- Session rotation follows sign-in, privilege change, sensitive recovery, and suspected compromise.
- Authorization is deny-by-default and checked server-side on every project, version, object, package, comment, job, event stream, and collaboration operation.
- Tenant/project scope comes from the authorized resource lookup, never a client body.
- Role changes and revocation terminate or reauthorize long-lived WebSocket/SSE sessions.
- Public links are opaque, revocable, scope-limited, optionally version-pinned, and expiring by default for private projects.
- Sensitive owner actions require recent authentication and auditable confirmation.

Cross-tenant not-found behavior MUST avoid confirming resource existence.

## 5. Input and content safety

### 5.1 Portable archives

Archive readers enforce the limits and atomic import rules in [Project File Format](./PROJECT_FILE_FORMAT.md). Extraction uses a private temporary directory, never follows links, and never writes outside the import root.

### 5.2 Structured records

JSON/YAML-equivalent records use strict schemas, depth/length/count/numeric limits, known units, and finite values. Unknown required semantic fields fail closed. HTML is not accepted in labels.

### 5.3 Symbols, physical views, and packages

Component art and custom IC packages are declarative:

- no JavaScript, event handlers, remote URLs, embedded HTML, shader code, fonts, or unrestricted SVG;
- geometry primitives, labels, colors, materials, orientation marks, and dimensions are allowlisted;
- labels are escaped and length-bounded;
- raster media, if allowed for non-electrical documentation, is decoded in a bounded safe path and never becomes an electrical hit target;
- package designer parameters are finite and constrained by family rules;
- generated geometry is clipped to bounded extents and complexity;
- pin maps are schema-validated and electrically checked before placement or simulation.

These controls preserve REQ-037/REQ-038 without creating a scriptable drawing or PCB-manufacturing environment.

### 5.4 Models, HDL, and firmware

Import parses metadata and syntax separately from execution. Antivirus/malware scanning where available does not replace sandboxing. External includes, filesystem paths, system tasks, dynamic libraries, foreign-function calls, and network retrieval are rejected unless an adapter explicitly normalizes them under a reviewed policy.

## 6. Browser security

- The application uses a restrictive Content Security Policy with no unsafe inline/eval path in production.
- Trusted Types SHOULD protect DOM injection sinks where supported.
- Cross-origin resources are minimized and must satisfy COOP/COEP/CORP requirements on threaded-WASM pages.
- The threaded build is selected only after cross-origin isolation checks; otherwise the single-threaded Worker build is used.
- Untrusted parsing, netlisting, simulation, waveform processing, and expensive package geometry generation run outside the main thread with memory/time/message limits.
- IndexedDB records are origin-private but not treated as encrypted secret storage.
- Private API responses are never placed in a shared Service Worker cache.
- Exports use safe content types and attachment disposition; user-supplied filenames are normalized.
- PostMessage accepts only expected origins, sources, schemas, and transfer sizes.

No secret may be embedded in a project, Worker message, client bundle, or service-worker cache.

## 7. Server execution sandbox

Every untrusted simulation, compilation, or external-engine attempt runs in a fresh container or stronger isolation boundary with:

- digest-pinned minimal image and recorded software bill of materials;
- non-root user, dropped Linux capabilities, no privilege escalation, and no host device access;
- read-only root filesystem and private size-limited scratch volume;
- no outbound network and no inbound listener;
- only job-scoped, read-only input credentials and write-only temporary output authorization;
- CPU, memory, wall-time, process, file-descriptor, file-count, output-byte, diagnostic-count, and scratch limits;
- syscall, mount, namespace, and runtime policy appropriate to the engine;
- supervisor-enforced cancellation and termination grace;
- complete destruction and scratch cleanup after publication or failure.

GPU/HPC jobs use an explicitly reviewed profile; device access is never inherited from a general worker. Nested containers, package managers, interactive shells, and dynamic network downloads are prohibited during a job.

## 8. Artifact and result integrity

- Inputs, engine images, models, packages, compiled artifacts, checkpoints, and result chunks use cryptographic digests.
- Workers receive an immutable execution plan and fencing token.
- Output remains quarantined until media/schema validation, checksum verification, and current-fence authorization pass.
- Only one attempt can publish authoritative completion.
- Checkpoints verify engine build, plan, partition, scheduler, and random-state compatibility.
- User-visible results retain source project, model, package-registry, engine, seed, and determinism provenance.
- Digital signatures MAY be added for releases or shared libraries but do not replace authorization and digest verification.

## 9. Secrets and cryptography

- Secrets live in a managed secret store and are delivered only to the service that needs them.
- Workers do not receive control-plane database credentials or broad object-store credentials.
- Transport uses currently approved TLS; stored cloud data and backups use platform-managed encryption at rest.
- Key rotation and revocation are documented and tested.
- Passwords, API keys, tokens, signing material, and private model-repository credentials are redacted from logs and diagnostics.
- Users are warned and uploads may be blocked when secret scanning finds likely credentials; raw secret values MUST NOT be echoed.

## 10. Privacy and data governance

Data classes include public library data, ordinary private project data, organization-restricted data, and operational security data. Each deployment declares retention, region, export, sharing, and deletion policy per class.

- Telemetry is data-minimized and disabled for schematic contents, HDL/firmware contents, imported models, comments, package labels, waveform values, and user documentation by default.
- Product analytics use coarse event names and counts, not circuit payloads.
- Logs use opaque IDs and bounded error context.
- Cloud upload is explicit for local projects and lists included assets.
- Organization region and retention policy participate in object and worker placement.
- Public publication is explicit and previews exactly what becomes public.
- Data export and deletion are authorization-checked and auditable.

No claim of anonymity is made for identifiers that can be re-associated operationally.

## 11. Availability and abuse controls

- Request, import, compilation, collaboration, SSE, result, and job submission paths have separate actor, tenant, IP/risk, and resource-class limits.
- Complexity estimation occurs before queueing and is enforced again in the worker.
- Event count, matrix size, timestep work, delta cycles, waveform samples, package primitive count, and diagnostic/log volume are bounded.
- Fair scheduling and tenant quotas prevent one project from monopolizing Workers.
- Backpressure coalesces non-authoritative progress but never hides terminal states.
- Public library imports are scanned, rate-limited, version-pinned, and subject to takedown/quarantine.
- Abuse controls SHOULD degrade locally where safe and fail closed for cloud mutations.

## 12. Supply chain

- Dependencies, engine/toolchain versions, container base images, model sources, and package/symbol sources are pinned by version and digest where possible.
- Builds produce provenance and an SBOM; release artifacts are reproducible to the documented class.
- Automated vulnerability/license scans inform review but do not auto-approve distribution.
- Critical build and deployment identities use least privilege and protected review.
- Compiled-model caches are keyed by normalized source, toolchain digest, target, flags, and sandbox policy; cross-tenant cache reuse is disabled unless artifacts are proven content-independent and policy-approved.
- A compromised or withdrawn asset can be quarantined by digest without rewriting immutable project history.

## 13. Audit and incident response

Audit events include membership/role changes, public sharing, version publication, package/library publication, cloud job submission/cancellation, policy changes, export, deletion, security quarantine, and administrator access. Events contain actor, action, target, result, time, correlation ID, and policy basis without sensitive payloads.

Incident response MUST support:

1. detection and triage;
2. credential/session/key revocation;
3. job and artifact quarantine by digest;
4. affected tenant/version/result identification;
5. contained evidence preservation;
6. user/owner notification according to policy and law;
7. remediation, restoration, and post-incident review.

## 14. Mandatory security tests

- horizontal and vertical authorization across every resource and stream;
- CSRF, origin, session fixation/rotation, and long-lived connection revocation;
- archive traversal, duplicate paths, case collisions, bombs, malformed JSON, and unsafe media;
- malicious SPICE/HDL/firmware/compiler inputs and external-engine escape attempts;
- package-label injection, remote-resource attempts, excessive geometry, invalid pins, and custom-package fuzzing;
- CPU/memory/time/process/output limits, cancellation, event storms, and log amplification;
- stale worker fencing, object substitution, digest mismatch, and checkpoint tampering;
- secret leakage review for logs, diagnostics, exports, telemetry, and crash output;
- tenant cache isolation, signed-URL expiry/scope, backup/restore authorization, and deletion workflows.

## 15. Acceptance criteria

1. Untrusted execution has no outbound network, host filesystem, privileged process, or durable credential access.
2. A compromised/stale attempt cannot publish authoritative output.
3. Cross-tenant project, object, package, job, result, SSE, and WebSocket access is denied.
4. Unsafe archives and custom-package payloads fail atomically without main-thread or server-process execution.
5. Resource limits stop pathological analog, digital, waveform, compiler, and geometry workloads with canonical diagnostics.
6. Threaded-WASM headers do not weaken CSP or permit uncontrolled cross-origin resources.
7. Telemetry and ordinary logs contain no project payloads or secrets by default.
8. Audit, quarantine, revocation, backup recovery, and deletion procedures have current test evidence before production release.

## 16. Source record

The browser/server split, external engines, distributed Workers, and resource-heavy workloads are grounded in the feasibility source. [Source PDF, pp. 23-26, 36] Browser-memory, convergence, synchronization, model-accuracy, and UI controls address its recorded risks. [Source PDF, pp. 39-40] Exact sandbox, authorization, privacy, package-safety, supply-chain, and incident controls are repository security decisions supporting REQ-032, REQ-033, REQ-035, REQ-037, and REQ-038.
