# Domain Lenses

Use only the relevant lens. These are reasoning prompts, not output checklists.

## Backend / API

Consider:

- API contract and versioning
- validation boundary
- authorization ownership
- transaction scope
- idempotency
- error semantics
- pagination/filtering
- long-running work boundaries
- synchronous vs asynchronous behavior
- rate/resource limits
- compatibility and migration

Prefer server-owned invariants over client-enforced correctness.

## Data Engineering

Consider:

- canonical source of truth
- immutable raw vs normalized/derived data
- lineage and provenance
- schema ownership/evolution
- data contracts
- reproducibility
- deterministic transforms
- partitioning and access patterns
- batch vs streaming
- backfill/replay
- idempotent ingestion
- quality validation
- versioning
- retention
- derived-state reconciliation

Keep probabilistic enrichment distinct from authoritative canonicalization unless
evaluation proves it safe.

## Databases

Consider:

- data ownership
- relational constraints
- transaction semantics
- consistency requirement
- indexing/query shape
- locking/concurrency
- migration sequencing
- backfills
- uniqueness/idempotency
- retention
- audit/history
- cache invalidation relationship

Do not use a second database merely because a feature maps nicely to its demo.

## Distributed Systems

Consider:

- failure domains
- delivery semantics
- ordering
- retry ownership
- duplicate handling
- idempotency
- consistency
- partition behavior
- timeouts
- backpressure
- reconciliation
- observability
- deployment/ownership boundaries

Prefer synchronous/local boundaries until independent failure, scale, ownership,
or durability requirements justify distribution.

## Frontend

Consider:

- server state vs client state vs local ephemeral state
- component responsibility
- state transitions
- URL-addressable navigation
- loading/error/empty/recovery states
- optimistic behavior
- accessibility
- rendering scale/virtualization
- caching and stale data
- responsive transformation
- design-system consistency
- testable state boundaries

Do not solve server-state problems with generic global client stores.

## AI / ML

Consider:

- deterministic vs probabilistic boundary
- authoritative vs advisory behavior
- evaluation metric and test set
- confidence/calibration
- false-positive/false-negative cost
- human approval
- provenance
- model/provider/version identity
- drift
- fallback
- latency
- cost
- privacy/security
- prompt/model change impact
- replay/reproducibility

Default to suggestion/decision-support when model errors would silently corrupt
authoritative data.

Build evaluation evidence before promoting probabilistic behavior to automatic
mutation.

## Infrastructure

Consider:

- deployment ownership
- isolation
- runtime requirements
- resource bounds
- secrets/configuration
- health/readiness
- scaling trigger
- persistence
- backup/recovery
- rollout/rollback
- observability
- operational burden

New infrastructure must solve a concrete capability gap.

## Developer Tooling

Consider:

- developer workflow fit
- deterministic behavior
- cross-platform support
- local/CI parity
- discoverability
- safe defaults
- failure visibility
- cache behavior
- incremental execution
- configuration ownership
- escape hatches

Prefer reducing cognitive load over adding another configurable framework.

## Security-Sensitive Architecture

Consider:

- trust boundaries
- authentication vs authorization
- least privilege
- server-owned permissions
- secrets
- input validation
- audit trail
- tamper resistance
- unsafe deserialization/execution
- data classification
- deletion/retention
- dependency/supply-chain risk

Do not trade away security invariants for UX convenience.

## Performance-Intensive Systems

First identify the actual bottleneck:

- CPU
- GPU
- memory
- disk
- network
- database/query
- serialization
- rendering
- synchronization
- external provider latency

Then consider:

- measurement/telemetry
- algorithm/data-structure changes
- batching
- parallelism
- bounded concurrency
- caching
- precomputation
- indexing
- virtualization
- streaming
- backpressure

Do not accept a user-prescribed cache, queue, or distributed service as the
diagnosis without evidence.
