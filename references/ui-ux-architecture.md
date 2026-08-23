# UI/UX Architecture Reference

Treat interaction architecture with the same rigor as backend architecture.

Choose patterns because they fit the primary user job, information topology,
state model, and scale. Do not stack patterns for novelty.

## Evaluation lens

For UI/UX brainstorms, reason about:

1. primary user job
2. information hierarchy
3. navigation model
4. workspace topology
5. state ownership
6. interaction state machine
7. server/client synchronization
8. optimistic behavior and rollback
9. collaboration model
10. content density
11. context preservation
12. responsive transformation
13. accessibility
14. design-system/token architecture
15. performance at realistic data scale
16. discoverability vs expert efficiency
17. loading/error/empty/recovery behavior
18. pattern fit vs novelty

## Professional patterns

### Multiplayer Collaborative Architecture

Use when multiple users materially share a workspace or artifact.

Consider:

- ephemeral presence vs persisted domain state
- cursors/selections/comments
- authoritative server state
- optimistic local changes
- conflict semantics
- reconnect/reconciliation
- permissions
- activity/history
- CRDT/OT/local-first only when offline/conflict requirements justify them

Presence should rarely become authoritative domain data.

### Finite State-Machine Driven UI

Use for complex workflows with meaningful modes, guards, transitions, recovery,
or impossible-state risk.

Good fits:

- capture/record workflows
- import/review/publish lifecycles
- multi-stage jobs
- editors with explicit modes
- payment or approval flows

Model states and transitions before multiplying booleans.

Do not introduce a state-machine library for a trivial three-state component.

### Tokenized Variables Architecture

Use for coherent design systems and multi-surface products.

Tokenize semantic decisions:

- color roles
- typography
- spacing
- density
- radius
- motion
- elevation
- state/feedback
- responsive scale

Prefer semantic tokens over raw visual constants.

### Infinite Canvas Workspace

Use when spatial composition itself is part of the user's work:

- node graphs
- diagrams
- free-form planning
- visual investigations
- spatial annotation
- large connected artifacts

Avoid when the core job is sequential review, table/list navigation, or stable
information retrieval. Infinite canvas adds navigation, accessibility, selection,
zoom, persistence, and spatial-memory complexity.

### Personalized Matrix Layout

Use when expert users have materially different monitoring/analysis priorities
and benefit from saved layout/density/panel configurations.

Avoid personalization before a stable default workflow exists.

### Optimistic Execution Interaction

Use for low-latency perceived interaction where server mutation can reconcile.

Require:

- immediate local feedback
- stable mutation identity
- explicit pending state
- rollback/reconciliation
- conflict/error feedback
- retry semantics

Never hide failed authoritative mutations.

### Adaptive Content Shell

Use when surrounding controls should adapt to selected content, workflow mode,
role, or device while preserving a stable global frame.

Avoid excessive shell mutation that destroys spatial memory.

### Contextual Sliding Sheet / Immersive Hero

Use when users need deep inspection without losing browse context.

Good fits:

- media catalog details
- entity inspection
- metadata editing
- review details
- contextual actions

Use immersive/full-screen modes when the task needs sustained focus and the
surrounding context becomes noise.

### Content-Centric Application Shell

Use for professional tools where the artifact/workspace should dominate.

Keep navigation and global chrome quiet. Promote controls contextually.

Strong fit for:

- annotation
- media review
- editors
- data investigation
- creative tools

### Infinite Discovery Scroll

Use for exploratory browsing where users discover rather than navigate to known
positions.

Require:

- virtualization
- restoration of scroll/context
- stable identity
- filters/search
- loading/error recovery

Avoid when users need deterministic pagination, auditing, or repeatable position.

### Unidirectional Engagement Loops

Design clear loops such as:

discover → inspect → act → feedback → continue

Keep transitions directional enough that users understand where they are and
what changed. Preserve escape/back paths.

### Cross-Platform Responsive Rail

Use for persistent navigation, filters, or action categories that transform
across desktop/tablet/mobile.

Prefer one information architecture with responsive presentation over separate
desktop/mobile products.

### Asymmetric Bento Grid Architecture

Use when overview/dashboard content has naturally different importance, media
type, or urgency.

Good for discovery and summaries.

Avoid in dense operational workspaces where stable spatial memory and
comparability matter more than visual hierarchy.

### Store-Presented Component Pattern

Separate domain/store state from presentational rendering when it improves:

- testability
- predictable data flow
- component reuse
- complex server/client state coordination

Do not introduce a global store for local component state.

### Headless UI Component Library

Use when accessibility and behavior primitives should be stable while visual
identity remains product-specific.

Strong for:

- dialogs
- menus
- comboboxes
- tabs
- disclosure
- popovers
- focus management

Do not let a component library dictate product information architecture.

### Layered Scaffold Workspace

Use for professional applications with stable layers such as:

global shell
→ navigation/context
→ primary workspace
→ contextual inspector
→ transient overlays

This creates strong spatial memory while supporting complex tools.

## Adjacent patterns

Consider when relevant:

- master-detail / inspector architecture
- keyboard-first interaction
- command palette
- URL-addressable state
- progressive disclosure
- local draft vs committed server state
- virtualized large-data surfaces
- local-first/offline-first
- activity/history timeline
- permission-aware UI
- undo/redo command architecture
- dockable/resizable panels
- breadcrumb/context-stack navigation
- responsive density
- accessibility-first primitives
- skeleton/loading/error/empty/recovery states

## Pattern discipline

Do not output a catalog of pattern names.

Prefer:

> Let's keep browsing content-centric and open session details in a contextual
> sheet so users retain their search and selection context.

Over:

> Use Content-Centric Shell + Sliding Sheet + Responsive Rail + FSM + Bento.

Name a pattern when the shared vocabulary genuinely improves communication.

## UI architecture authority

Challenge fashionable proposals when the user job does not fit them.

Examples:

- Reject infinite canvas for fundamentally sequential review.
- Reject bento grids inside dense operational workspaces requiring stable layout.
- Reject collaborative CRDT complexity when server-authoritative updates are
  sufficient.
- Reject optimistic mutation without rollback/reconciliation semantics.
- Reject global state for state that belongs locally or in server cache.

A visually exciting direction is useful only if it remains operable,
accessible, performant, and understandable.
