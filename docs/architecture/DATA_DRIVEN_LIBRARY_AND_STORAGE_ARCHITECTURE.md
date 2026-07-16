# Data-Driven Library and Storage Architecture

Status: Normative architecture contract  
Related: [System Architecture](./SYSTEM_ARCHITECTURE.md), [Storage, Versioning, and Collaboration](./STORAGE_VERSIONING_AND_COLLABORATION.md), [Project File Format](./PROJECT_FILE_FORMAT.md), [API and Worker Protocols](./API_AND_WORKER_PROTOCOLS.md), [Security, Privacy, and Sandboxing](./SECURITY_PRIVACY_AND_SANDBOXING.md), [Component Model Contract](../catalog/COMPONENT_MODEL_CONTRACT.md), [Device-Package Binding Contract](../catalog/DEVICE_PACKAGE_BINDING_CONTRACT.md), [Model Import and Export Formats](../catalog/MODEL_IMPORT_EXPORT_FORMATS.md), and [Product Requirements](../PRODUCT_REQUIREMENTS.md)

## 1. Purpose and normative language

This document defines how versioned scientific models, reusable library entities, user projects, and validation artifacts move from persistence into generic simulation and rendering engines. It also defines the initial mixed-storage boundary, Library Service lifecycle and API semantics, offline synchronization, and the minimal personal-account capability required before advanced collaboration.

This contract governs `REQ-054` through `REQ-063`: storage-independent engine input, mixed storage, declarative/executable separation, minimal Google OIDC, guest migration and personal persistence, immutable publication, system/user permissions, safe CRUD, the versioned Library Service API, and imported-model trust/licensing.

`MUST`, `MUST NOT`, `SHOULD`, `SHOULD NOT`, and `MAY` are normative. This is a documentation and architecture contract; it does not define a database migration, executable service implementation, authentication implementation, or deployment configuration.

The central invariant is:

> **The database is not the simulation engine.**

PostgreSQL, JSONB documents, S3-compatible objects, and IndexedDB persist or transport data. They MUST NOT define solver behavior by accident, and no simulation engine may query them directly while preparing or running an analysis.

## 2. Architectural boundary

The only allowed runtime dependency direction is:

```text
Storage
-> Library Service
-> Validated Immutable Model Bundle
-> Simulation Engine
-> Rendering and User Interface
```

~~~mermaid
flowchart LR
    PG["PostgreSQL relational metadata and JSONB documents"]
    S3["S3-compatible immutable objects"]
    IDB["IndexedDB drafts, cache, and pending sync"]
    Library["Library Service"]
    Resolve["Schema, unit, provenance, trust, dependency, and policy validation"]
    Bundle["Validated immutable model bundle"]
    Engine["Generic simulation engines and scheduler"]
    Render["Generic renderers and UI read models"]

    PG --> Library
    S3 --> Library
    IDB --> Library
    Library --> Resolve
    Resolve --> Bundle
    Bundle --> Engine
    Bundle --> Render
    Engine --> Render
    Engine -. "no storage query" .-> PG
    Engine -. "no storage query" .-> S3
    Engine -. "no storage query" .-> IDB
~~~

The dotted edges are prohibitions, not data flows. An engine receives a validated bundle through an engine-neutral port. It MUST NOT import a PostgreSQL client, object-storage SDK, browser storage API, Library Service client, authorization client, or persistence-specific identifier into its domain contract.

An object-store key, database row ID, JSONB path, IndexedDB key, provider subject, or signed URL MUST NOT become portable model identity. Portable identity uses stable logical IDs, immutable revision IDs, versions, and content hashes.

## 3. Responsibility split

### 3.1 Generic application and engine responsibilities

Application code and generic engines own behavior that must remain stable across library records and storage implementations:

- strict schema, reference, dimensional-unit, range, and compatibility validation;
- exact-revision resolution and dependency-graph traversal;
- numerical solvers, declarative-model interpreters, deterministic scheduling, convergence controls, and result production;
- rendering of allowlisted symbol, package, board, system, and physical-view primitives;
- import/export normalization, version migration, content hashing, and reproducibility manifests;
- compilation and external-engine adapters behind the accepted worker and sandbox boundary;
- authorization enforcement, safe caching, search/index projection, quotas, and audit emission in the service layer;
- deterministic diagnostic generation when data is missing, incompatible, untrusted, invalid, revoked, or outside its validity envelope.

An engine implementation may understand a versioned canonical model schema and approved kernel interfaces. It MUST NOT understand the tables, buckets, tenant layout, draft workflow, search index, or authentication provider used to obtain that model.

### 3.2 Data responsibilities

Versioned data describes what is simulated, rendered, composed, or validated:

- physics, primitive, behavioral, composite, and external-adapter model descriptors;
- equations and approved kernel bindings, parameters, state definitions, units, dimensions, ranges, validity, assumptions, accuracy, uncertainty, and limitations;
- generic devices, vendor devices, parameter overrides, symbols, packages, physical representations, pin profiles, and device-package bindings;
- composite graphs, boards/modules, systems, materials, environmental profiles, failure and aging rules, and simulation profiles;
- manufacturer and ordering metadata, provenance, license, redistribution restrictions, trust level, lifecycle, validation status, and evidence;
- user projects, project templates, exact library locks, testbenches, measurements, and retained result manifests.

Data MAY select an already approved implementation kind or kernel by stable capability ID. It MUST NOT introduce a new native behavior merely by naming an executable, dynamic library, script, SQL function, browser module, or server endpoint.

## 4. Validated immutable model bundle

### 4.1 Resolution input

The Library Service resolves a bundle from an explicit request containing:

- exact root logical ID and immutable revision ID;
- required entity kind and expected content hash;
- requested fidelity and analysis capabilities;
- project revision, catalog, package, pin-profile, device-binding, and model locks;
- permitted trust classes, license policy, and execution placement;
- canonical unit-system and schema versions;
- optional platform capability and approved kernel manifest digests.

Floating labels such as `latest`, display names, search aliases, or current publication pointers MAY help a user choose a revision. They MUST be resolved and frozen before validation and MUST NOT appear as an unresolved dependency in a bundle or project revision.

### 4.2 Bundle content

A validated bundle is an immutable, content-addressed execution and rendering input. Its manifest MUST include:

- bundle schema version, bundle ID, content hash, creation purpose, and deterministic canonicalization profile;
- every logical entity ID, immutable revision ID, version, kind, content hash, and dependency edge;
- normalized SI-valued parameters and dimensions, with original display metadata kept separate;
- equations or approved kernel capability bindings and their exact revisions;
- fidelity, supported analyses, validity ranges, assumptions, limitations, accuracy/uncertainty declarations, and expected diagnostics;
- model, symbol, package, pin-profile, pin-map, board, and system bindings needed by the requested projection;
- provenance, license, redistribution restrictions, trust level, validation status, and validation-evidence references;
- approved executable artifact or external-adapter digests when execution requires them;
- migration history for any source record read through an older supported schema;
- a complete dependency-order manifest and a reproducibility fingerprint.

The bundle MUST be self-consistent and immutable. It may contain small canonical records directly and digest-address large objects, but every referenced object MUST be authorized, checksum-verified, available to the selected placement, and frozen before execution starts. A server worker receives a signed or equivalently integrity-protected bundle envelope; a browser Worker receives the same canonical semantics through the versioned Worker protocol.

### 4.3 Validation pipeline

Bundle construction follows one fail-closed sequence:

1. authorize the root resource and intended operation;
2. load exact revisions without following floating pointers;
3. verify schemas, stable kinds, hashes, signatures where required, and migration compatibility;
4. resolve the complete directed dependency graph and reject missing edges or unsupported cycles;
5. validate units, dimensions, ranges, operating regions, package/pin equivalence, and model capabilities;
6. enforce provenance, license, redistribution, trust, quarantine, and execution-placement policy;
7. verify required validation evidence and approved executable-kernel digests;
8. canonicalize content, calculate the bundle hash, and emit an auditable resolution record;
9. transfer the immutable bundle to the engine or renderer.

Validation MUST distinguish malformed data, missing dependency, dependency cycle, incompatible revision, dimensional error, invalid operating range, package-pin mismatch, insufficient trust, license restriction, quarantined asset, unsupported kernel, and policy denial. The Library Service MUST NOT replace a rejected revision with another revision silently.

## 5. Declarative records and executable kernels

The platform has two extension modes. Their trust and release requirements are intentionally different.

### 5.1 Declarative extension mode

Validated CRUD operations MAY create or revise supported declarative entities, including:

- parameterized devices and approved primitive declarations;
- bounded equation parameters for an already approved interpreter or kernel;
- truth tables, state machines, composite graphs, subcircuits, and board/system graphs;
- symbols, physical representations, packages, pin profiles, and bindings;
- material tables, environmental profiles, failure thresholds, simulation profiles, and parameter overrides.

Declarative records MUST use allowlisted schemas, finite bounded values, known units and dimensions, acyclic dependency rules where required, deterministic interpretation, and declared resource limits. A declarative expression language, if supported, is an approved bounded interpreter with a versioned grammar and capability allowlist; it is not arbitrary JavaScript, WebAssembly, SQL, shell, Python, native code, dynamic loading, or a remote-resource hook.

### 5.2 Executable-kernel mode

A new executable or native behavior requires all of the following before release:

- reviewed source or an approved external binary with immutable provenance;
- an approved implementation and versioned kernel/adapter capability contract;
- deterministic-behavior declaration and validation evidence;
- signed artifacts where the release policy requires them;
- CPU, memory, process, file, output, and wall-time limits;
- security, supply-chain, provenance, license, and redistribution review;
- digest-pinned deployment and explicit compatibility ranges;
- browser Worker isolation for approved WASM or declarative interpreters, or process/container isolation for imported and native execution.

Arbitrary executable content stored in any database or object store MUST NOT run in the browser main process, API/control-plane process, Library Service, PostgreSQL process, or another trusted service. Imported SPICE, Verilog/SystemVerilog, Verilog-A, HDL, firmware, compiled models, native plugins, and external simulators remain subject to [Security, Privacy, and Sandboxing](./SECURITY_PRIVACY_AND_SANDBOXING.md) and the `EngineAdapter` lifecycle in [API and Worker Protocols](./API_AND_WORKER_PROTOCOLS.md).

## 6. Mixed-storage architecture

Storage is accessed through ports owned by the Library Service and project service. Storage implementations may optimize reads, indexes, and object transfer, but they MUST NOT change canonical entity meaning.

### 6.1 PostgreSQL relational metadata

PostgreSQL is the initial authoritative relational store for:

- users, external identity mappings, personal accounts, ownership, and authorization grants;
- projects, draft/branch metadata, immutable project-version records, retention, archive, and soft-deletion state;
- library logical items, revisions, kinds, publication state, aliases, tags, manufacturers, device families, and vendor variants;
- dependency and reverse-dependency edges, package/pin/binding metadata, compatibility, replacements, supersessions, and deprecations;
- provenance indexes, license/trust/validation status, content-object references, search metadata, quota/usage records, and audit indexes;
- idempotency records and durable workflow state that require transactional consistency.

Relational rows carry service metadata and references; they are not a substitute for canonical portable documents. Large binaries and waveforms do not belong in ordinary relational fields.

### 6.2 Initial document abstraction with PostgreSQL JSONB

The Library Service exposes a storage-neutral document port for hierarchical project graphs, composite-model graphs, boards, systems, declarative model documents, project snapshots, mutable draft snapshots, and revision manifests.

The initial hosted implementation MUST use PostgreSQL `JSONB` where it meets documented indexing, query, migration, schema-validation, scale, backup, and transactional-consistency needs. JSONB documents MUST still pass application-level canonical schemas; the database representation is not the public contract.

A separate document database MUST NOT be introduced merely for schema flexibility or anticipated scale. It requires measured evidence that PostgreSQL JSONB cannot satisfy a named workload, plus a focused ADR that extends or supersedes the canonical persistence decision in [ADR-0003](../decisions/ADR-0003.md), an operational-cost comparison, security and backup analysis, compatibility tests, and a migration/rollback plan. Any future replacement remains behind the document port and cannot change the simulation-engine interface.

### 6.3 S3-compatible object storage

S3-compatible object storage holds large or opaque immutable objects, including:

- SPICE, IBIS, Touchstone, HDL, firmware, imported vendor, and compiled artifacts;
- waveform/event chunks, large result sets, checkpoints, and reproducibility archives;
- physical measurement datasets, validation evidence, safe images, and approved 3D assets;
- canonical `.eesim` archives, immutable library bundles, and large project assets.

Objects are content-addressed or manifest-bound, checksum-verified, and unreferenced until an authorized metadata transaction publishes the reference. Signed URLs are short-lived transport authorizations, never identity. Quarantine, retention, legal/license withdrawal, and garbage collection MUST consult authoritative metadata and reverse references before removal.

### 6.4 IndexedDB browser-local storage

IndexedDB stores:

- guest and local-only projects, autosave journals, recovery snapshots, and view state;
- cached immutable library bundles and exact revision records;
- cached account-authorized project revisions selected for offline use;
- bounded local results and immutable object chunks;
- pending synchronization operations, upload manifests, base vectors, and migration state.

IndexedDB is authoritative for unsynchronized device-local work. It is not authoritative for cloud ownership, provider identity, permissions, publication state, quota, or another device's history. Service Worker caches MAY hold the public application shell and immutable public assets but MUST NOT contain private API responses in a shared cache.

## 7. Offline, migration, and synchronization contract

### 7.1 Local schema migration and cache invalidation

- Every IndexedDB database, object store, journal batch, cached bundle, and project snapshot carries a schema version.
- Migrations are ordered, deterministic, crash-safe, and non-destructive to the last verified snapshot until the migrated snapshot passes checksums and schema validation.
- An unsupported migration preserves an exportable last-good copy and opens read-only or blocks the affected feature with a diagnostic.
- Immutable cache entries are keyed by kind, exact revision ID, content hash, canonical-schema version, and relevant interpreter/renderer compatibility.
- A new publication, deprecation, or `latest` pointer does not invalidate an exact cached revision. Digest mismatch, quarantine, security withdrawal, incompatible schema, or explicit retention policy does.
- Cache eviction MUST prioritize reproducible derived data and downloaded bundles before unsynchronized edits. Storage pressure MUST NOT silently delete pending work.

### 7.2 Synchronization

Synchronization is explicit, resumable, and idempotent:

1. authenticate when cloud access is requested and resolve the authorized personal account;
2. compare local project ID, cloud project ID if assigned, exact base revision, CRDT or journal vector, schema version, and content hashes;
3. stage missing immutable objects in quarantine by digest;
4. upload authorized local operations or a migration candidate with idempotency keys;
5. receive remote operations/revisions and detect ownership, schema, or base-revision conflicts;
6. resolve safe CRDT operations under [ADR-0009](../decisions/ADR-0009.md), or require explicit fork/choice for semantic and ownership conflicts;
7. validate the converged candidate and create a new immutable cloud revision when the user saves/publishes;
8. mark local operations synchronized only after durable acknowledgement and checksum verification.

No sync process may silently overwrite a local draft, mutate an immutable revision, guess a package pin map, change model fidelity, or upload a guest project to an account without informed user action.

### 7.3 Conflict and recovery outcomes

| Condition | Required outcome |
|---|---|
| Same operation or upload is retried | return the original durable outcome idempotently |
| Both devices edit a mergeable draft | converge operations, then run semantic validation |
| Both sides publish from one base | preserve both immutable revisions; require explicit branch/fork/merge selection |
| Cloud project was archived or soft-deleted | preserve local work; require restore or duplicate/fork authorization |
| Ownership or access was revoked | stop upload and cloud reads; retain/export the user's authorized local draft according to policy |
| Cached bundle is withdrawn for security or law | preserve historical identity and project reference; block new execution/use and present remediation |
| IndexedDB migration fails | retain the last verified snapshot and journal; offer read-only export/retry |
| Network fails during local-to-cloud migration | keep the guest project unchanged; resume using the same migration ID |

## 8. Library identity and lifecycle

### 8.1 Identity

Every publishable library record has:

- a stable logical ID that survives revision changes;
- an immutable revision ID and semantic or policy-defined version;
- canonical content hash and schema version;
- entity kind, creator, creation timestamp, ownership scope, and publication state;
- provenance, license, redistribution restrictions, trust level, and validation status;
- compatibility, dependency, replacement, supersession, deprecation, archive, withdrawal, and tombstone metadata where applicable.

A mutable draft has its own draft ID and base revision. Updating a draft does not change a published revision. Publishing creates a new immutable revision and atomically advances an authorized publication pointer; existing projects remain pinned to their exact revision.

### 8.2 Lifecycle states

~~~mermaid
stateDiagram-v2
    [*] --> draft
    draft --> validated
    validated --> published
    draft --> discarded: unreferenced draft only
    validated --> draft: validation invalidated by edit
    published --> deprecated
    published --> superseded
    published --> archived
    published --> withdrawn
    deprecated --> superseded
    deprecated --> archived
    superseded --> archived
    withdrawn --> tombstone
    archived --> tombstone: retention and reference policy permit
~~~

- `published`, `deprecated`, `superseded`, `archived`, and `withdrawn` revisions remain immutable.
- Deprecation discourages new selection but preserves use and exact resolution.
- Supersession names an explicit compatible or migration-qualified replacement; it does not rewrite consumers.
- Archive removes normal discovery visibility without changing historical references.
- Withdrawal prevents new use for a stated security, legal, or scientific reason. Existing history retains a bounded tombstone and remediation policy.
- A tombstone preserves logical/revision identity, reason, dates, replacement, policy basis, and audit reference even when retained payload access is restricted.
- Hard deletion is permitted only for an unreferenced, unpublished draft after reverse-dependency, retention, audit, and legal-policy checks. Published or referenced records MUST NOT be hard-deleted.

### 8.3 System library

The system library contains official physics and primitive models, curated composite/behavioral models, generic and vendor devices, symbols, packages, pin profiles, bindings, boards/modules, reference systems, validation artifacts, and project templates.

- Only an authorized maintainer or administrator may create, revise, validate, publish, deprecate, supersede, archive, or withdraw system records.
- Normal users receive policy-filtered read and exact-revision resolution.
- Every change is a new draft/revision and emits an audit event.
- Publication requires schema, units/dimensions, dependencies, provenance, license, trust, validation, compatibility, and content-safety checks appropriate to the kind.
- Withdrawal never rewrites a project or erases scientific and audit history.

### 8.4 User library

Within supported declarative kinds, a user may create custom composite models, approved primitive declarations, devices, symbols, packages, bindings, boards, systems, project templates, simulation profiles, and private validation artifacts.

An owner may create and update drafts, duplicate, validate, publish a private revision, archive, soft-delete, restore, deprecate, and supersede according to policy. Public or shared publication requires the later review/moderation workflow. A user cannot publish a native kernel through ordinary Library Service CRUD.

Unreferenced unpublished drafts may be hard-deleted after checks. Referenced drafts are first detached or preserved; referenced published/private revisions remain immutable and resolvable under authorization.

### 8.5 Reverse-dependency safety

Before deprecation, supersession, withdrawal, soft deletion, payload removal, or migration, the service MUST resolve direct and transitive reverse dependencies across:

- physics, primitive, behavioral, and composite models;
- generic and vendor devices;
- symbols, packages, pin profiles, and device-package bindings;
- boards/modules, systems, project templates, and user projects;
- validation evidence, physical measurements, compiled artifacts, bundles, and results.

The operation response declares affected counts, kinds, exact revisions, blocking references, compatible replacements, required migrations, and visibility impact. A destructive operation fails when a protected dependency exists. Reference migration creates a new consumer draft/revision, validates it, records the transformation, and never edits published consumers in place.

## 9. Library Service contracts

### 9.1 Supported resource kinds

The service boundary supports physics models, primitive models, composite models, behavioral models, approved external-adapter descriptors, generic devices, vendor devices, symbols, physical representations, packages, pin profiles, device-package bindings, boards/modules, systems, project templates, user projects, simulation profiles, validation artifacts, and provenance records.

Not every caller may create every kind. Kind-specific schema, trust, ownership, publication, and executable-kernel policy determine allowed operations.

### 9.2 Command and query semantics

| Operation | Required contract |
|---|---|
| Create draft | kind, ownership scope, base/template revision if any, idempotency key, initial canonical document |
| Read exact revision | logical ID, revision ID, authorization context; never an implicit `latest` for reproducibility |
| Search/list | kind, lifecycle, tags, aliases, manufacturer, capability, fidelity, trust, validation, compatibility, cursor, stable sort |
| Update draft | draft ID, expected draft revision/vector, typed patch or replacement document, idempotency key |
| Validate | exact draft snapshot, requested publication/use intent, validation policy version |
| Publish revision | validated snapshot hash, expected base/publication pointer, version, release metadata, idempotency key |
| Deprecate | immutable revision, reason, effective date, optional replacement, impact summary |
| Supersede | immutable revision, exact replacement revision, compatibility/migration declaration, reason |
| Archive/soft delete | target, expected state, reverse-dependency evidence, retention decision, reason |
| Restore | soft-deleted/archived target, policy and ownership revalidation, expected state |
| Duplicate | exact source revision and new ownership; produce a new logical draft with lineage |
| Resolve dependencies | exact root revisions, depth/policy, deterministic graph and diagnostics |
| Resolve reverse dependencies | exact target revision, direct/transitive mode, authorization-filtered impact report |
| Compare revisions | two exact revisions, semantic and compatibility differences without payload mutation |
| Migrate references | exact consumer and replacement revisions, migration policy; create a new validated consumer revision |
| Import/export | staged validated artifact, declared format, source/license/trust; canonical output with manifest |
| Build bundle | exact roots, fidelity/analysis/placement policy; return validated immutable bundle or diagnostics |

Every write MUST pass authorization, schema and dimensional validation, dependency and pin/binding validation, provenance/trust/license checks, publication/lifecycle rules, idempotency, quota checks, and audit logging. Clients receive service commands, not unrestricted row-level CRUD, bucket keys, SQL filters, or database transactions.

### 9.3 Service-level API shape

The canonical semantics may be mapped to REST without exposing persistence:

| Method and resource shape | Semantics |
|---|---|
| `POST /v1/library/{kind}/drafts` | create an authorized draft |
| `GET /v1/library/{kind}/{logicalId}/revisions/{revisionId}` | read one exact revision |
| `GET /v1/library/{kind}` | cursor-search authorized records |
| `PATCH /v1/library/{kind}/drafts/{draftId}` | conditionally update a mutable draft |
| `POST /v1/library/{kind}/drafts/{draftId}/validate` | produce a validation report for a frozen draft snapshot |
| `POST /v1/library/{kind}/drafts/{draftId}/publish` | create an immutable revision |
| `POST /v1/library/{kind}/{logicalId}/revisions/{revisionId}/{command}` | deprecate, supersede, archive, withdraw, or restore through a typed command |
| `GET /v1/library/{kind}/{logicalId}/revisions/{revisionId}/dependencies` | resolve deterministic dependencies |
| `GET /v1/library/{kind}/{logicalId}/revisions/{revisionId}/reverse-dependencies` | inspect protected consumers |
| `POST /v1/library/bundles` | resolve and validate an immutable bundle |

Existing specialized package, import, project, and artifact routes in [API and Worker Protocols](./API_AND_WORKER_PROTOCOLS.md) MAY remain compatibility-oriented command surfaces. They MUST delegate to the same lifecycle, identity, authorization, and validation semantics rather than create a second source of truth.

Queries use opaque cursors and stable ordering. Search results expose publication pointers for discovery and exact revision IDs for selection. Authorization-filtered reverse-dependency results MUST NOT disclose private cross-owner resources; the service may report a protected anonymous blocker while preserving confidentiality.

### 9.4 Error classes and concurrency

Required error classes include invalid schema, invalid unit/dimension, invalid range, dependency missing, dependency cycle, revision conflict, draft conflict, immutable revision, protected dependency, replacement incompatible, provenance incomplete, license denied, trust insufficient, validation failed, quota exceeded, unauthorized, forbidden, not found, quarantined, and unsupported executable kernel.

Draft mutations and pointer-changing commands use optimistic concurrency and idempotency keys. A stale expected revision conflicts; it never becomes last-write-wins. Publication metadata and object references commit atomically after all required objects and validation evidence are durable.

## 10. Minimal personal identity and project persistence

### 10.1 Scope and identity boundary

The first account capability is deliberately small:

- Google OIDC sign-in through a provider-neutral identity adapter;
- no custom username/password credential system;
- guest and offline use without authentication;
- one personal account scope with private cloud projects and basic quota;
- save, load, rename, duplicate, archive, soft-delete, restore where policy permits, revision history, cloud backup, and explicit local-to-cloud migration;
- safe sign-out and controlled offline access to previously authorized cached projects.

The identity adapter validates issuer, audience, signature, expiry, nonce, state, PKCE where applicable, and a verified-email claim where the account policy requires email. It normalizes the provider subject and required verified claims into an internal opaque account identity. Project records never use an email address or Google subject as ownership identity. A future OIDC provider can be added behind the same adapter without changing project, library, or engine contracts.

The web flow SHOULD use the reviewed OIDC authorization-code flow with PKCE, state, and nonce, with secure HttpOnly SameSite session cookies or an equivalently reviewed server-side session boundary. Provider access/refresh tokens MUST NOT enter `.eesim` files, IndexedDB project records, Library Service documents, logs, simulation bundles, or worker messages.

### 10.2 Guest and offline guarantees

- Opening, editing, autosaving, importing/exporting, and eligible local simulation remain available without an account after required public assets are cached.
- A guest project has a device-local opaque ID and stays local until its user explicitly chooses an account and migration operation.
- Sign-in MUST NOT merge, upload, reassign, or delete guest projects automatically.
- Signing out revokes or ends the cloud session, stops pending cloud writes, clears authentication material, and does not delete cloud projects.
- Account-scoped projects marked for offline availability remain locally accessible only under the documented device/offline-access policy. Sign-out explains whether cached private copies will be retained in a locked/local-only state or removed; it never silently converts them to another account's project.
- Guest and local-only exports remain usable even when identity or cloud services are unavailable.

### 10.3 Guest-to-account and account-link migration

Migration is explicit, previewed, idempotent, and non-destructive:

1. authenticate the destination personal account and require recent confirmation;
2. inventory each selected project's snapshots, custom models, packages, firmware/HDL, documentation, results, sizes, provenance, licenses, and quota impact;
3. validate local schemas, exact library revisions, content hashes, ownership, and upload policy;
4. create a migration record and stage missing immutable objects in quarantine;
5. create the private cloud project and first immutable revision transactionally;
6. record a durable mapping from the device-local project to the cloud project without changing portable identity;
7. verify the uploaded revision against the local canonical digest;
8. retain the guest copy until the user explicitly chooses linked synchronization or removal.

Retrying a migration ID returns or resumes the same outcome. Quota, network, license, validation, ownership, or provider-link failure leaves the guest project unchanged and exportable.

Linking another provider identity to an existing account requires authenticated proof of both sides or an approved recovery flow. It MUST NOT create duplicate ownership, absorb another browser profile's guest work, or select an account solely from matching email text.

### 10.4 Personal project authorization and quota

The personal owner can manage only owned projects and authorized immutable library revisions. Every project command checks ownership server-side; object URLs and IDs never grant authority.

The basic quota contract MUST declare at least project count, total authoritative storage bytes, per-project/archive bytes, object/upload bytes, revision or retained-result policy, request rate, and restoration grace. Quota reservations and actual usage are durable and auditable. Quota exhaustion blocks the new cloud mutation with an actionable diagnostic but does not delete local work, existing cloud revisions, or the user's export path.

### 10.5 Explicitly deferred identity scope

Organizations, organization membership, complex RBAC, team invitations, enterprise SSO, shared billing, enterprise policies, large-scale collaboration, public-library moderation, and organization compute quotas remain in R10. The early personal layer MUST NOT pre-authorize those concepts through a hidden all-powerful role or tenant bypass.

## 11. Exact project revisions, lineage, and audit

Every saved or published cloud project revision references exact immutable revisions and hashes for all models, devices, symbols, packages, pin profiles, bindings, boards/modules, systems, materials, validation profiles, imported artifacts, and required executable-kernel manifests. A project MUST NOT persist a floating `latest` dependency as its reproducibility lock.

Later library publication, deprecation, or supersession may generate a migration recommendation. It never mutates a project revision. Accepting an upgrade creates a new project draft/revision with:

- source and replacement revision IDs and content hashes;
- parameter and binding transformations;
- migration tool/policy revision;
- validation results and newly introduced limitations;
- actor, time, reason, and parent project revision.

Audit events are required for sign-in/account-link security events, project creation and migration, ownership-affecting action, revision save/publication, restore and deletion, system/user library publication and lifecycle changes, dependency-protected denial, bundle resolution used for a released result, quota policy/override, import/quarantine, export, and administrator access.

An audit record contains actor or system principal, action, target logical and revision IDs, project revision when applicable, result, timestamp, correlation/idempotency ID, policy and authorization basis, source/replacement references, and bounded impact summary. It excludes provider tokens, model source payloads, schematic content, waveform values, and other sensitive content. Audit retention does not authorize access to an otherwise private payload.

## 12. Security and privacy invariants

- All imported and user-authored content remains untrusted after authentication.
- The Library Service parses and validates declarative data but never executes imported code in-process.
- A bundle is authorized for a purpose, project/account scope, placement, and lifetime; possessing its hash alone grants no access.
- Library search, exact reads, dependency queries, reverse-dependency reports, object transfers, audit reads, and offline synchronization enforce authorization independently.
- Public/system, private personal, project-embedded, and quarantined records use distinct visibility states; cache keys cannot cross those states.
- Validation evidence and a `published` state do not imply scientific accuracy beyond the declared fidelity, validity, uncertainty, provenance, and limitations.
- Withdrawal for a security or legal reason blocks new resolution according to policy while retaining identity, audit, affected-project analysis, and an explicit remediation path.
- Telemetry and search indexes exclude private model/project payloads by default and use bounded, policy-approved metadata.

## 13. Failure and recovery

| Failure | Required behavior |
|---|---|
| PostgreSQL unavailable | reject cloud mutations and bundle resolutions requiring uncached authority; local work continues |
| Object storage unavailable | do not publish metadata for missing objects; use a verified cached immutable bundle only when policy permits |
| Search index stale | exact-ID reads remain authoritative; label search as delayed and never infer deletion |
| Bundle dependency becomes unavailable during resolution | fail before execution; preserve the requested exact graph and diagnostic |
| Engine receives a corrupt bundle | reject before prepare/run and report digest/schema failure without querying storage |
| Publication transaction fails | retain draft and quarantined objects; no partial published revision becomes visible |
| Duplicate lifecycle command | return the original idempotent outcome |
| Reverse-dependency scan cannot complete | fail the destructive lifecycle operation closed |
| OIDC provider unavailable | guest/offline work continues; do not fabricate or extend an online session |
| Session expires while offline | preserve local work; defer cloud writes and require reauthentication before synchronization |
| Quota reached during migration | stop before authoritative publication or leave a resumable staged record; retain the guest project |
| Separate storage versions disagree | authoritative metadata plus content hashes determine visibility; quarantine inconsistent objects |

## 14. Release placement and gates

This architecture does not add or renumber releases. The roadmap remains R0 through R13.

| Release | Required placement |
|---|---|
| R0 | Freeze this boundary, lifecycle, storage ports, identity abstraction, bundle schema requirements, and traceable atomic work; no runtime claim |
| R1 | Implement local IndexedDB projects/cache/migrations, built-in immutable-library resolution, Library Service ports, minimal Google OIDC, private personal-project CRUD/revisions/cloud backup, explicit guest-to-account migration, and basic storage quota; exclude sharing and organizations |
| R2-R4 | Add validated immutable bundles and scientific/model records needed by each solver capability; R4 evidence must pin exact validated model revisions |
| R6 | Production-harden and accept the R1 guest/account paths, offline recovery, migration, safe sign-out, backup/restore, authorization, quota, privacy, and security evidence before the first production release |
| R7 | Complete production-catalog ingestion and system-library revision/validation evidence without claiming every market SKU |
| R10 | Add organizations, complex RBAC, invitations, shared projects, CRDT collaboration services, public-library publication/moderation, team quotas/billing policy, and hosted heavy-compute control plane |

R1 is the correct implementation placement for minimal personal persistence because `.eesim`, IndexedDB, autosave, and project storage already form the R1 project-foundation dependency. Deferring all account persistence to R10 would force the first production release to lack the requested personal cloud backup. R6 remains the production acceptance gate, while advanced multi-user authority and collaboration stay in R10. Cloud simulation workers, organization tenancy, and public collaboration are not prerequisites for the limited R1 personal-project service.

Any release plan that moves organizations, enterprise policy, shared billing, or team collaboration earlier requires its own documented dependency, risk, and gate change; the existence of a personal account does not imply those capabilities.

## 15. Acceptance criteria

1. A generic engine consumes a validated immutable bundle without a PostgreSQL, JSONB, S3, IndexedDB, authentication-provider, or Library Service dependency.
2. Resolving the same exact graph, canonical inputs, policy versions, and content hashes produces the same bundle fingerprint.
3. Missing dependencies, unsupported cycles, invalid dimensions, invalid pin maps, incompatible revisions, quarantined content, and unapproved kernels fail before engine execution.
4. A PostgreSQL JSONB implementation can be replaced behind the document port without changing engine or portable project contracts; adding a separate document database requires the defined ADR and evidence.
5. Declarative CRUD cannot execute arbitrary stored code; executable models follow review, digest, sandbox, resource, license, and validation gates.
6. Published system and user revisions are immutable, projects pin exact revisions, and a referenced published record cannot be hard-deleted.
7. Deprecation, supersession, withdrawal, archive, soft deletion, restoration, and tombstones preserve historical identity and produce audit evidence.
8. Reverse-dependency analysis prevents destructive lifecycle changes and reference migration creates new validated revisions.
9. A guest can edit, simulate eligible projects, autosave, recover, import, and export without authentication.
10. Google OIDC uses a provider abstraction; sign-in does not upload guest projects, and a failed/retried guest migration leaves the local source unchanged.
11. Personal private projects support the declared safe lifecycle and quota contract while organization/RBAC/collaboration capability remains gated to R10.
12. Offline cache migration, invalidation, synchronization, conflict, reauthentication, and sign-out paths preserve unsynchronized user work and authorization boundaries.
13. Library commands enforce authorization, validation, provenance, license, trust, dependency, publication, quota, and audit policy instead of exposing unrestricted database CRUD.
14. Every released result can identify its exact project revision, bundle fingerprint, model/library revisions, executable-kernel digests, provenance, validation status, and limitations.

## 16. Decision and source record

The feasibility brief requires browser-local storage, cloud database/object storage, project versioning, reusable component libraries, user accounts, collaboration, public sharing, and stored results. [Source PDF, pp. 31-32, 41-42] Local-first behavior and the browser/cloud execution split follow [ADR-0003](../decisions/ADR-0003.md); portable immutable project semantics follow [ADR-0004](../decisions/ADR-0004.md); concurrent draft convergence and immutable simulation revisions follow [ADR-0009](../decisions/ADR-0009.md).

The Library Service boundary and validated immutable bundle are locked by `ADR-0015`; mixed storage and the PostgreSQL JSONB initial document abstraction by `ADR-0016`; provider-neutral Google OIDC and minimal personal persistence by `ADR-0017`; immutable revisions and dependency-safe CRUD by `ADR-0018`; and declarative versus executable behavior by `ADR-0019`. These repository decisions keep storage, scientific behavior, identity, and release evidence separable.
