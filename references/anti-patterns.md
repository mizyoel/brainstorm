# Anti-Patterns

Use this reference as an architectural smoke detector.

Do not mechanically mention these names to the user. Detect them and adjust the
recommendation.

## Interaction anti-patterns

### Question avalanche

Asking many questions because reasoning/context gathering was not done first.

Response:
- inspect repository
- use safe defaults
- ask only architecture-changing uncertainty through `ask_user`

### Grill loop

Serial one-question-at-a-time interrogation that delays value.

Response:
- show credible directions first when possible
- ask the highest-information question
- batch only tightly related high-impact decisions
- converge quickly

### Wall of text

Long analysis that repeats the prompt, repository structure, and generic
principles.

Response:
- compress
- surface only decision-relevant evidence
- keep final plan to 3–6 steps

## Architecture anti-patterns

### Premature microservice

Creating a deployment/network boundary without independent scale, ownership,
failure isolation, or lifecycle requirements.

### Queue by default

Introducing a queue when synchronous/local work already satisfies durability and
latency requirements.

### Event bus as abstraction

Publishing events merely to decouple code that should share a clear local
boundary.

### Redis reflex

Adding caching infrastructure before identifying the real bottleneck and cache
semantics.

### Multiple sources of truth

Maintaining the same authoritative mutable state in several places.

### Duplicate ownership

Two modules/services both own lifecycle or persistence decisions for the same
concept.

### Distributed monolith

Separating deployment units while retaining synchronous, tightly coupled
behavior and shared-state assumptions.

### God service/module

Accumulating unrelated responsibilities behind one central object.

### Premature generic framework

Building plugin/config/strategy/factory infrastructure without real variation
pressure.

### Abstraction by duplication count

Extracting a shared abstraction only because two pieces of code look similar,
without a stable shared concept.

### Local architecture island

Introducing a different architecture style inside one feature while the
repository has a sound established pattern.

### Blind consistency

Forcing new work into an existing abstraction even when that abstraction is the
source of the design problem.

### Rewrite-first refactor

Replacing a mature system wholesale instead of defining an incremental migration
boundary.

### Prototype dead end

Using "prototype" to justify unsafe state ownership, unrecoverable persistence,
or impossible migration.

### Production gold-plating

Equating production-grade with maximum services, queues, abstractions, HA,
tracing, or configuration.

### Trend-driven architecture

Selecting a fashionable technology without a concrete capability requirement.

## AI/Data anti-patterns

### Probabilistic authority without evaluation

Allowing model output to silently mutate canonical state without measured
precision, provenance, rollback, or human control.

### Semantic similarity equals truth

Treating embedding proximity as authoritative identity or taxonomy equivalence.

### Irreproducible enrichment

Derived metadata cannot be traced to input, model/version, rules, or timestamp.

### Schema drift by convenience

Allowing each ingestion source to redefine canonical structure.

## UI/UX anti-patterns

### UI pattern bingo

Stacking modern patterns regardless of user job.

### Infinite canvas because it is cool

Adding pan/zoom/spatial complexity to a fundamentally sequential/list-detail
workflow.

### Bento operational workspace

Using irregular visual hierarchy where users need stable spatial memory and
comparison.

### Optimism without reconciliation

Updating UI immediately without stable pending/error/rollback semantics.

### Global-store everything

Putting local ephemeral or server-cache state into one global client store.

### Boolean state explosion

Representing a workflow with many independent booleans that permit impossible
combinations instead of explicit states/transitions.

### Responsive redesign divergence

Creating separate desktop/mobile information architectures rather than one
coherent model with responsive transformation.

### Inspector destroys context

Navigating away for every detail view when users need to preserve search,
selection, or workspace state.

### Unbounded rendering

Rendering large media/data collections without virtualization, paging, or
incremental loading.

## Brainstorm anti-patterns

### Fake alternatives

Options differ in naming rather than architectural boundary.

### Neutrality theater

"All approaches have pros and cons" when evidence clearly favors one.

### User-tech obedience

Treating "use Kafka/Redis/microservice/LLM" as a requirement without identifying
the underlying constraint.

### Principle recital

Outputting SOLID/DRY/KISS/YAGNI as evidence instead of applying them.

### Repository tourism

Reporting many inspected files instead of explaining the one finding that
changes the recommendation.

### Plan wallpaper

`Analyze → design → implement → test → deploy`

Replace with 3–6 concrete architecture slices.

### Frontier-for-show

Including a cutting-edge option merely to sound innovative.

A frontier option must solve a real problem better enough to deserve discussion.
