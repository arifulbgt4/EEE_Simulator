# Deployment, Operations, and Observability

Status: Normative  
Related: [Local, Cloud, and Worker Architecture](./LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md), [Security, Privacy, and Sandboxing](./SECURITY_PRIVACY_AND_SANDBOXING.md), [Open Source and Third-Party Licenses](./OPEN_SOURCE_AND_THIRD_PARTY_LICENSES.md)

## 1. Purpose

This document defines deployment units, environments, release/rollback, migrations, capacity, backups, observability, alerting, and incident operations. The source brief requires a hybrid browser/server architecture, CPU and GPU/HPC Workers, distributed jobs, progress streaming, result storage, checkpoint/resume, and a multidisciplinary operational boundary. [Source brief, pp. 25-26, 36, 38-40]

## 2. Deployment topology

~~~mermaid
flowchart TB
    CDN["CDN/static web delivery"]
    Web["Next.js web application"]
    API["Project, collaboration, and job APIs"]
    PG["PostgreSQL"]
    Obj["S3-compatible object storage"]
    Redis["Redis Streams"]
    CPU["Isolated CPU worker pools"]
    GPU["Isolated GPU/HPC pools"]
    Obs["Metrics, logs, traces, audit"]

    CDN --> Web
    Web --> API
    API --> PG
    API --> Obj
    API --> Redis
    Redis --> CPU
    Redis --> GPU
    CPU --> Obj
    GPU --> Obj
    API --> Obs
    CPU --> Obs
    GPU --> Obs
~~~

Deployment units are independently versioned:

- public browser shell and immutable static assets;
- authenticated project/job API;
- collaboration gateway;
- import/asset-validation service;
- queue reconciliation and scheduler service;
- engine-specific CPU workers;
- GPU/HPC workers;
- migration/maintenance jobs;
- telemetry and audit sinks.

The API MUST NOT contain external-engine binaries or execute imported content.

## 3. Environments

| Environment | Purpose | Data rule | External engines |
|---|---|---|---|
| Local development | implementation and unit fixtures | synthetic/local only | optional explicitly installed test versions |
| CI | deterministic validation, schemas, builds, tests | generated fixtures only | digest-pinned test images |
| Preview | review one change | no production copies or credentials | minimal allowlist |
| Staging | production-like integration, load, migration, recovery | synthetic or separately approved sanitized data | same boundaries and representative versions |
| Production | authorized users and published releases | policy-controlled | only release-approved digests |

No production secret, private project, or unrestricted database copy enters preview/CI. Staging parity includes headers, authorization, queues, storage policies, sandbox, and observability, not user data.

## 4. Browser delivery and WASM headers

- Static assets are content-hashed and immutable; HTML and service-worker updates use short cache lifetimes and explicit version activation.
- Threaded-WASM pages require Cross-Origin-Opener-Policy and Cross-Origin-Embedder-Policy plus compatible cross-origin resource policy. All embedded resources are inventoried and tested.
- A separate single-threaded WASM artifact is mandatory. Capability detection selects it when isolation is unavailable.
- Content Security Policy, MIME types, source maps, integrity metadata, and compression are release-tested.
- Source maps containing first-party source are access-controlled in production diagnostics or omitted according to policy.
- Service-worker rollout MUST avoid mixing an incompatible shell, protocol, and Worker/WASM build. Activation is version-coordinated and rollback-tested.

## 5. Release artifact identity

Every deployable artifact records:

- source revision and clean/dirty state;
- reproducible build identifier and timestamp;
- dependency lock/SBOM and license report;
- container or asset digest;
- schema/protocol compatibility ranges;
- catalog, component, package, and pin-map registry digest;
- engine/toolchain version and adapter capability digest;
- security scan and required test evidence;
- release approver and rollout record.

Mutable tags such as latest are not production identity. Workers and APIs communicate using immutable digests and negotiated protocols.

## 6. Release flow

~~~mermaid
flowchart LR
    Build --> Verify["Tests, docs, security, licenses, benchmarks"]
    Verify --> Stage["Deploy staging"]
    Stage --> Migrate["Dry-run and compatible migrations"]
    Migrate --> Canary["Production canary"]
    Canary --> Observe["Observe SLOs and correctness"]
    Observe --> Rollout["Progressive rollout"]
    Canary --> Rollback["Rollback on gate failure"]
    Rollout --> Record["Finalize evidence and changelog"]
~~~

Release gates require:

1. schema/link/traceability and visual/package golden checks;
2. unit, integration, numerical, determinism, security, accessibility, browser, and performance evidence appropriate to the change;
3. migration dry run plus rollback/forward-fix decision;
4. dependency/license/SBOM review;
5. canary health and correctness observation;
6. explicit completion or rollback.

Web, API, Worker, catalog/package registry, and protocol releases are independently rollable only within documented compatibility windows.

## 7. Database, object, and schema migrations

- Migrations are versioned, reviewed, idempotent where practical, observable, and tested against production-scale synthetic data.
- Expand-contract is the default: add backward-compatible structures, deploy dual-read/write where required, backfill with checkpoints, verify, switch reads, then remove only after the compatibility window.
- Destructive database changes require backup evidence, impact estimate, maintenance/online plan, and rollback or forward-restoration procedure.
- Object format changes create new immutable objects and update references transactionally; objects are never rewritten in place.
- .eesim and custom-package migrations are deterministic application migrations and never run implicitly against published source bytes.
- CRDT schema migration pauses publication for affected drafts, creates a verified snapshot, migrates, and resumes under a declared protocol version.
- Engine checkpoint formats are not migrated unless the adapter declares an exact compatible transformation.

## 8. Queue and worker operations

- Queue depth, age, lease expiry, retries, cancellations, per-engine saturation, and quota rejection are monitored by profile.
- Reconciliation finds durable queued jobs missing dispatch entries and republishes idempotently.
- Worker images are engine-specific and digest-pinned.
- Autoscaling considers oldest eligible job age, profile capacity, warm-up time, tenant fairness, and budget.
- Scale-down drains leases; it never kills a running job without checkpoint/cancellation policy.
- A worker version is removed only after no compatible queued/running/checkpointed job requires it or an explicit retirement policy handles those jobs.
- GPU/HPC pools have separate admission, capacity, cost, driver, and license controls.

## 9. Service objectives

Initial hosted-service objectives, measured monthly after GA, are:

| Signal | Objective |
|---|---:|
| Authenticated control-plane availability | at least 99.9% |
| Successful authorized project-version reads | at least 99.9%, excluding invalid requests |
| Accepted job commands reaching durable state | at least 99.9% |
| SSE state/diagnostic delivery after durable publication | p95 at most 2 seconds |
| Collaboration accepted-operation acknowledgement | p95 at most 500 ms in-region |
| Worker cancellation to terminal state | p95 at most 30 seconds for cooperative engines; hard supervisor bound documented per profile |
| Local editor availability during cloud outage | supported cached shell/draft paths continue without cloud writes |

Simulation runtime is workload-dependent and is not an availability SLO. Queue estimates MUST distinguish queue delay from execution and carry confidence, not a false deadline.

The default recovery objectives for hosted metadata and referenced object manifests are RPO at most 15 minutes and RTO at most 4 hours. Immutable object durability depends on the selected storage class and replication policy and MUST be documented per deployment.

## 10. Backups and disaster recovery

- PostgreSQL uses encrypted automated backups plus point-in-time recovery where supported.
- Object storage uses versioning/replication or equivalent protection for authoritative immutable objects.
- Redis is reconstructable dispatch state and is not the only copy of any job.
- Backup credentials and recovery roles are separate from normal application roles.
- Restore tests occur at least quarterly before GA claims, using an isolated environment and representative scale.
- Recovery verifies tenant ACLs, version/object referential integrity, package/model digests, queued/running job reconciliation, and audit continuity.
- Running jobs at disaster time become explicitly interrupted; resume occurs only from compatible verified checkpoints.
- Recovery exercises record achieved RPO/RTO, gaps, owners, and corrective tasks.

## 11. Observability model

~~~mermaid
flowchart LR
    Request["Browser/API request"] --> Correlation["Correlation ID"]
    Correlation --> Trace["Distributed trace"]
    Correlation --> Logs["Structured logs"]
    Correlation --> Metrics["Metrics and SLO events"]
    Correlation --> Audit["Security/audit event when applicable"]
    Job["Job/attempt/fence IDs"] --> Trace
    Job --> Logs
    Job --> Metrics
~~~

### 11.1 Metrics

Required metrics include:

- API request rate, latency, status, authorization denial, and rate limiting;
- WebSocket connections, operation acknowledgement, reconnect, snapshot, and fan-out lag;
- SSE connections, replay, delivery lag, backpressure, and expired retention;
- queue depth/age, dispatch reconciliation, leases, retries, attempts, cancellations, timeouts, and terminal states;
- Worker startup, engine phase, resource use, exit reason, checkpoint and result publication;
- object upload/download/checksum/quarantine and PostgreSQL pool/transaction/replication health;
- browser performance, Worker crash, memory pressure, renderer fallback, and view-switch/package-render timing through privacy-safe aggregates;
- schema, package pin-map, migration, and visual-regression failures in CI/release evidence.

Cardinality is bounded: component IDs, net IDs, filenames, model text, labels, waveform values, and raw user IDs are not metric labels.

### 11.2 Logs

Logs are structured with timestamp, service/build, severity, stable event code, correlation ID, tenant-safe opaque resource IDs, job/attempt where relevant, and bounded typed context. Schematic/model/HDL/firmware/package-label/waveform contents and secrets are excluded by default.

### 11.3 Traces

Traces cover control-plane and job lifecycle boundaries but do not ingest simulation samples or user source. Sampling preserves errors, security events, and slow-path evidence under a bounded policy.

### 11.4 Audit

Audit records are logically separate, access-controlled, tamper-evident to the deployment policy, and retained according to governance. Operational logs are not a substitute.

## 12. Alerts and runbooks

Release-blocking production runbooks are required for:

- control-plane or collaboration outage;
- PostgreSQL saturation/replication or object-store failure;
- queue age growth, dispatch loss, lease storm, or Worker crash loop;
- cross-tenant authorization anomaly;
- untrusted execution/sandbox alert;
- checksum, stale-fence, or result-publication integrity failure;
- runaway cost, GPU/HPC capacity, or quota-policy failure;
- COOP/COEP, service-worker, WASM, browser, or renderer regression;
- package-registry/pin-map incompatibility affecting projects;
- restore, region evacuation, key rotation, dependency/model quarantine, and public-library takedown.

Each alert has owner, severity, user impact, evidence queries, immediate containment, recovery, communication, escalation, and post-incident requirements. Alerts based only on noisy symptoms without an action are not release-ready.

## 13. Rollback and compatibility

- Browser deployment can roll back only to a version compatible with active service-worker cache, API, Worker protocol, and project schema.
- API rollback must understand all data written during the canary; otherwise use forward fix.
- Worker rollback keeps old images available for active compatible attempts and checkpoints.
- Catalog/package rollback changes the default pointer; immutable versions remain addressable.
- A bad package definition is quarantined by digest and replaced through a new version; published projects are not rewritten.
- Database rollback is never assumed after destructive writes; the migration plan chooses restore, compensating migration, or forward repair in advance.

## 14. Acceptance criteria

1. Staging proves production-equivalent headers, sandbox, authorization, storage, queue, protocol, and observability boundaries.
2. Canary and rollback preserve .eesim compatibility, dual-view identity, package pin maps, job state, and collaboration data.
3. Duplicate dispatch, stale Worker, queue loss, database outage, object failure, and region recovery drills produce the documented outcome.
4. Quarterly restore evidence meets or reports variance from RPO/RTO before GA claims.
5. SLO dashboards derive from durable state and privacy-safe telemetry.
6. Logs/traces/metrics contain no project payloads or secrets by default.
7. A registry or renderer release runs realistic-component/package visual regression and pin-equivalence evidence.
8. Every shipped external engine digest has current security and license approval.

## 15. Source record

Hybrid placement and Worker pools are grounded in the source brief, pp. 25-26. Cloud queues, progress, storage, checkpoint/resume, and HPC are grounded in p. 36. Browser memory, UI, synchronization, and model risks are grounded in pp. 39-40. Exact environments, SLO/RPO/RTO targets, release mechanics, observability, package-registry operations, and disaster-recovery procedures are repository operational decisions.
