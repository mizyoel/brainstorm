# Engineering Architecture Reference

Use this reference to evaluate candidate directions. Apply it silently unless a
specific trade-off materially helps the user understand the recommendation.

## Evaluation hierarchy

### 1. Correctness and safety

A design must remain correct under realistic production behavior.

Consider when relevant:

- invalid or impossible states
- partial failure
- concurrency and races
- retries and duplicate execution
- idempotency
- transaction boundaries
- authorization and trust boundaries
- data loss/corruption
- rollback and recovery
- backwards compatibility
- migration safety

A locally elegant design loses if it makes correctness harder.

### 2. Architectural fit

Ask where this responsibility naturally belongs in the existing system.

Evaluate:

- ownership boundaries
- cohesion and coupling
- dependency direction
- source-of-truth ownership
- installed infrastructure
- existing module/service/job boundaries
- deployment boundaries
- repository conventions

Prefer extending a sound existing boundary over creating a parallel architecture.

Do not preserve a bad boundary merely because it exists.

### 3. Simplicity

Apply KISS and YAGNI as architecture principles.

Prefer:

- fewer concepts
- fewer moving parts
- explicit behavior
- existing infrastructure
- small blast radius
- understandable failure semantics
- easy rollback

Do not confuse fewer lines of code with simpler architecture.

A durable job abstraction may be simpler than an in-process callback if
restarts and retries are real requirements.

### 4. Maintainability and testability

Prefer designs with:

- clear responsibility boundaries
- explicit contracts
- deterministic core behavior
- isolated side effects
- small stable interfaces where justified
- replaceable dependencies only where replacement is realistic
- test seams aligned with real boundaries
- minimal hidden/global coupling

Apply SOLID and separation of concerns through decisions, not vocabulary.

### 5. Reliability and operability

A production system must be diagnosable and recoverable.

Consider:

- timeouts
- retries and retry ownership
- bounded work/resources
- terminal failure state
- restart behavior
- health signals
- logs and structured events
- metrics
- tracing only where it provides real value
- rate limits
- configuration ownership
- reconciliation
- operator recovery paths

Do not add an "observability stack" when a few precise metrics/logs solve the need.

### 6. Performance and scalability

Start with realistic workload characteristics.

Consider:

- algorithmic complexity
- I/O patterns
- query shape
- memory bounds
- large-collection virtualization/pagination
- hot paths
- batching
- caching only after identifying a reusable/stable result
- horizontal scaling only when the ownership boundary supports it

Do not design for imaginary planetary traffic.

Reject obvious scale dead ends for known large workloads.

### 7. Extensibility

Prefer purposeful extension points where variation pressure is visible.

Useful signals:

- multiple current implementations
- explicitly planned variants
- external provider replacement risk
- stable domain contract around unstable implementation
- known independent scaling/ownership requirement

Avoid speculative factories, plugin systems, strategy layers, and generic
frameworks for one use case.

Duplication can be cheaper than the wrong abstraction.

### 8. Implementation and migration cost

After correctness and architecture are sound, consider:

- amount of change
- migration complexity
- rollout sequencing
- data backfills
- compatibility bridge
- testing burden
- operational burden
- team familiarity
- reversibility

A slightly less elegant solution may win when it meets all production
requirements and materially reduces migration risk.

## Cross-cutting principles

### State ownership

Every important piece of state should have one clear source of truth.

Derived state should be reproducible or explicitly reconciled.

Avoid duplicated mutable truth across client/server, services, caches, and stores.

### Contract boundaries

Prefer explicit contracts at meaningful boundaries:

- API
- service/module
- storage
- queue/event
- provider
- data/schema

Do not create interfaces only to satisfy a pattern.

### Failure ownership

For each asynchronous or distributed action, know:

- who retries
- who records terminal failure
- who reconciles
- whether duplication is safe
- what happens after restart
- what the user/operator sees

### Reversibility

Prefer incremental changes with:

- clear rollout boundary
- compatibility where needed
- measurable behavior
- rollback/recovery path

Avoid rewrite-first strategies unless the existing architecture prevents safe
incremental migration.

### Security

Apply least privilege, server-owned authorization, trusted boundaries, safe
input handling, secret isolation, and auditable mutation paths where relevant.

Do not bolt security on as a final checklist item.

## Senior default

When two designs satisfy the requirement similarly well, prefer the one with:

- clearer ownership
- fewer moving parts
- stronger fit with existing architecture
- deterministic behavior
- easier testing
- smaller failure domain
- observable operation
- easier rollback
- an explicit evolution path

Production-grade means robust and proportionate, not maximal.
