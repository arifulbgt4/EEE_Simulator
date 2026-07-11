# Storage, Versioning, and Collaboration

Status: Normative  
Related: [Project File Format](./PROJECT_FILE_FORMAT.md), [Local, Cloud, and Worker Architecture](./LOCAL_CLOUD_AND_WORKER_ARCHITECTURE.md), [API and Worker Protocols](./API_AND_WORKER_PROTOCOLS.md)

## 1. Purpose

This document defines local persistence, cloud ownership, immutable versions, draft collaboration, offline synchronization, reusable libraries, retention, and conflict behavior. The source brief explicitly calls for browser IndexedDB, PostgreSQL, object storage, project versioning, team collaboration, public sharing, reusable component libraries, comments, documentation, and version history. [Source brief, pp. 31-32, 41-42]

## 2. Storage ownership

~~~mermaid
flowchart LR
    Browser["Browser working copy"] --> IDB["IndexedDB drafts and caches"]
    Browser <-->|"CRDT operations and snapshots"| Service["Project service"]
    Service --> PG["PostgreSQL metadata, ACL, CRDT log, versions"]
    Service --> Objects["Object storage: archives, models, packages, results"]
    Service --> Audit["Audit index"]
    IDB --> Export["Portable .eesim export"]
    Objects --> Export
~~~

| Store | Authoritative for | Not authoritative for |
|---|---|---|
| In-memory domain state | current tab's validated working revision | durable recovery |
| IndexedDB | device-local drafts, command journal, pending sync, bounded caches | cloud ACLs, published versions, organization truth |
| PostgreSQL | project metadata, permissions, branches, version records, durable CRDT operations, comments, job/result indexes | large binaries or waveform payloads |
| S3-compatible object storage | immutable .eesim archives, models, package assets, firmware/HDL, result chunks, checkpoints | authorization or mutable workflow state |
| Redis Streams | transient job dispatch and leases | project history, collaboration truth, or results |

## 3. Local persistence

Each local project has an opaque device-scoped project ID, an append-only command journal, periodic compact snapshots, asset references, and a last-known validation summary.

- A committed editor command MUST be journaled atomically with its resulting revision reference.
- Snapshot compaction MUST preserve the previous known-good snapshot until checksum verification succeeds.
- Crash recovery replays only complete, checksum-valid command batches.
- Imported assets and catalog/package definitions are content-addressed and immutable in cache.
- Working results use a separate bounded store so result eviction cannot delete the schematic.
- Storage pressure MUST offer explicit choices: evict results/cache, reduce retention, export, or stop. It MUST NOT silently delete unsynchronized edits.
- Service Worker caches may contain the public shell and immutable public assets, but never private API responses in a shared cache.

Local-only work remains usable without an account. Choosing cloud synchronization is an explicit operation that shows what project, models, firmware/HDL, custom packages, and documentation will be uploaded.

## 4. Cloud project model

A cloud project contains:

- opaque project ID, tenant/organization owner, title, classification, and retention policy;
- membership and role bindings;
- one or more mutable draft branches;
- immutable published versions;
- content-addressed project, model, component, package, and documentation objects;
- comments and review threads anchored to stable entity IDs and versions;
- simulation jobs bound to an immutable version;
- audit references and deletion state.

Object-store paths are implementation details and MUST NOT appear in portable identity. Metadata commits reference an object only after upload, media validation, digest verification, and tenant namespace checks succeed.

## 5. Drafts, versions, and branches

### 5.1 Draft

A draft is a mutable CRDT document plus its durable operation log and snapshots. A draft has a branch ID, schema version, catalog/package locks, and head vector.

### 5.2 Published version

A published version is immutable and contains:

- parent version(s) and source draft vector;
- canonical project/member digest set;
- catalog, component, package, pin-map, and model locks;
- author, time, message, provenance, and validation status;
- compatibility and migration status;
- optional release/checkpoint labels.

Publishing validates the converged snapshot and creates the immutable .eesim representation before updating version metadata. Published bytes, parents, and digests never change. Corrections create a new version.

### 5.3 Branch

A branch is a named pointer to a draft and its last published version. Branch names are not identity. Fast-forward, merge, and fork operations create explicit history; no operation rewrites published ancestry.

## 6. CRDT collaboration

CRDT-based editing is the accepted baseline. It covers schematic entities, parameters, hierarchy, view placements, component/package bindings, declarative custom-package parameters, annotations, and comments where their data type has defined merge semantics.

~~~mermaid
sequenceDiagram
    participant A as Client A
    participant S as Collaboration service
    participant B as Client B
    participant D as Durable operation store

    A->>S: operation batch with causal state
    S->>S: authorize, schema-check, assign durable sequence
    S->>D: append accepted batch
    D-->>S: durable acknowledgement
    S-->>A: acknowledged vector
    S-->>B: accepted operations
    B->>S: reconnect with last vector
    S-->>B: missing operations or compact snapshot
~~~

- Accepted operations converge independent of delivery order under the declared CRDT type.
- Operation IDs are globally unique and idempotent.
- The server enforces authorization and schema/size limits before durability.
- Presence, selection, pointer, and viewport are ephemeral awareness data and never affect project truth.
- Undo creates compensating intent-scoped operations; it does not erase remote work.
- Large immutable assets are uploaded separately and referenced by digest only after authorization.

## 7. Conflict policy

CRDT convergence does not make every converged design electrically valid. Semantic validation runs after each accepted batch and at publication.

| Conflict | Required outcome |
|---|---|
| Two actors edit independent properties | converge normally |
| Two actors set one scalar differently | deterministic CRDT winner; retain both operation histories and surface an edit notice |
| Delete versus edit | retain recoverable tombstone metadata; UI explains the lost target |
| Concurrent wire/net edits | converge operations, recompute canonical topology, show electrical diagnostics |
| Concurrent hierarchy cycle | preserve operations but block publish/simulation until cycle is resolved |
| Package version and pin-map edited concurrently | block package binding until a single compatible pair is selected |
| Binary/model asset changed | create distinct content-addressed assets; never byte-merge |
| Migration and live edit | pause writes, migrate a snapshot, then rebase or fork with explicit report |

No conflict handler may silently merge nets, guess a pin mapping, reinterpret units, or discard an accepted operation.

## 8. Dual-view and package collaboration

Schematic and realistic physical/breadboard placements are view-specific CRDT records over the same component IDs and nets.

- Moving a component in one view changes only that view's transform.
- Changing a parameter, model, package binding, pin map, or connectivity changes shared domain state and appears in every view.
- A reusable package definition is independently versioned. Editing it creates a new package draft/version and never mutates existing projects pinned to an older digest.
- Custom-package parameters merge only at individual schema-declared fields; the generated geometry is a deterministic projection and is never directly merged.
- Publishing requires package schema validation, orientation checks, dimension bounds, and symbol/package/model pin equivalence.
- Optional footprint metadata may be referenced for interoperability, but this platform does not promise PCB layout, routing, DRC, or manufacturing-output authoring under REQ-038.

## 9. Offline synchronization

On reconnect:

1. authenticate or resume the authorized session;
2. fetch branch schema, policy, catalog/package locks, and server vector;
3. upload missing immutable assets to quarantine by digest;
4. validate and append pending operations in causal batches;
5. receive remote operations or a compact snapshot;
6. recompute domain topology, package pin equivalence, and diagnostics;
7. mark local operations synchronized only after durable acknowledgement.

If authorization was revoked, schema migration is required, an immutable asset is rejected, or the branch was deleted, automatic synchronization stops. The user may keep/export the local draft or create an authorized fork; the client MUST NOT create a hidden branch or upload elsewhere.

## 10. Simulation snapshot

A simulation cannot run directly against a changing CRDT head.

~~~mermaid
flowchart LR
    Draft["Converged draft vector"] --> Validate["Domain and package validation"]
    Validate --> Snapshot["Immutable simulation snapshot"]
    Snapshot --> Job["Local or cloud job"]
    Draft --> MoreEdits["Later edits"]
    MoreEdits -. no mutation .-> Snapshot
~~~

Snapshot creation records the exact CRDT vector, project digest, catalog/package/model locks, pin maps, analysis settings, and deterministic seed. Later edits do not affect a running job. A rerun against new edits creates a new snapshot identity.

## 11. Roles and authorization

Minimum project roles:

| Role | Capabilities |
|---|---|
| Owner | project lifecycle, membership, policy, publish, delete |
| Maintainer | edit, review, publish, manage reusable project assets within policy |
| Editor | edit drafts, comment, run allowed simulations |
| Commenter | view and comment |
| Viewer | authorized read/export according to policy |

Organization policy may further restrict public sharing, exports, external engines, regions, retention, or custom models. Authorization is checked on every command and object authorization, not only at UI navigation.

Share links use revocable, scoped grants with expiry and optional version pinning. Public library publication creates an explicit immutable publication record; making a project public does not automatically publish private comments, results, models, firmware, or custom package assets.

## 12. Library publication

Reusable components, models, subcircuits, symbols, physical representations, and IC packages have independent versioned library records.

Before publication, each asset MUST pass:

- schema, stable-ID, provenance, and license checks;
- compatibility and supported-analysis declaration;
- package dimension, orientation, marking, and pin-map checks where applicable;
- model and golden validation required by its lifecycle;
- content safety and malware/import validation;
- tenant policy and reviewer approval.

Consumers pin exact versions/digests. Deprecation never removes an asset from an existing project; revocation for security or legal reasons prevents new use and displays a remediation path.

## 13. Retention and deletion

- Retention is defined separately for drafts, published versions, audit records, jobs, results, checkpoints, temporary uploads, and public assets.
- Temporary uploads and orphaned result objects are garbage-collected only after a grace period and reference scan.
- Deleting a project is an auditable, recoverable tombstone operation until the policy grace period expires.
- Legal hold or organization policy may delay physical deletion and MUST be visible to authorized administrators.
- After expiry, metadata and objects are deleted through an idempotent workflow with evidence; derived caches are invalidated.
- Backups age out under the documented backup retention schedule; deletion is not falsely described as immediate removal from every backup.
- A user may export an authorized portable .eesim package before deletion, subject to data policy.

## 14. Failure and recovery

| Failure | Required behavior |
|---|---|
| IndexedDB transaction failure | keep last good snapshot/journal; report unsaved state |
| WebSocket disconnect | continue local edits, queue operations, show offline state |
| Duplicate operation | idempotent acknowledgement |
| PostgreSQL unavailable | no cloud write acknowledgement; local work may continue |
| Object upload incomplete | quarantine object remains unreferenced and later expires |
| CRDT snapshot corrupt | recover from prior verified snapshot plus operation log |
| Package digest unavailable | preserve project; block affected physical rendering/publish, never substitute |
| Membership revoked mid-session | reject subsequent writes and close private streams |
| Branch deleted remotely | preserve local draft; require explicit export/fork decision |

## 15. Acceptance criteria

1. Two offline clients reconnect with concurrent component, wire, parameter, and view-placement changes and converge without losing accepted operations.
2. Concurrent invalid topology or pin maps converge but block publish/simulation with actionable diagnostics.
3. A published version and a running simulation remain unchanged by later edits.
4. Schematic/physical movement stays view-local while connectivity and parameters remain shared.
5. Reusable package updates create new versions; pinned projects retain the old digest.
6. Cross-tenant object, comment, version, and collaboration access is denied without revealing existence.
7. Crash recovery restores every fully committed local command and no partial batch.
8. Export, deletion, retention, and public publication include only explicitly authorized data.

## 16. Source record

Project contents, IndexedDB, cloud databases/object storage, versioning, collaboration, public sharing, reusable libraries, comments, and documentation are required or proposed by the source brief. [Source brief, pp. 31-32, 41-42] CRDT selection, immutable version mechanics, exact conflict policy, package-version independence, optional footprint boundary, and retention workflow are repository decisions supporting REQ-006, REQ-031, REQ-037, and REQ-038.

