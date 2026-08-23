# Professional Web App Design Reference

Use this reference when `/brainstorm` materially affects the design of a web
application, product surface, dashboard, workspace, editor, catalog, review
surface, admin tool, SaaS flow, or data-heavy interface.

This reference focuses on **product-grade visual and interaction design
architecture**, not decoration.

The goal is to help design interfaces that are:

- immediately understandable
- efficient for repeated use
- visually coherent
- responsive
- accessible
- scalable to real data/content
- maintainable in code
- realistic to build

## Core design test

Evaluate every proposed interface through three questions:

1. **Can the user understand it?**
2. **Can the user operate it efficiently?**
3. **Can we implement and maintain it cleanly?**

A visually impressive surface fails if one of these breaks.

## Visual hierarchy

Every screen should have a deliberate attention order.

Identify:

- primary task
- primary action
- supporting actions
- context
- secondary metadata
- background/system information

Prefer:

- one dominant visual anchor
- strong grouping
- consistent alignment
- progressive disclosure
- clear action hierarchy
- low-noise secondary information

Avoid:

- every element competing for attention
- repeated equal-weight cards
- excessive badges
- oversized headings consuming workspace
- visual hierarchy created only through color
- decorative chrome around operational data

### Focal priority

Ask:

> If the user looks at the page for two seconds, do they understand what to do?

If not, hierarchy is weak.

## Typography system

Use typography structurally.

Define roles rather than ad-hoc sizes:

- page/title
- section heading
- card/entity title
- body
- metadata
- label
- helper text
- status text
- numeric/data emphasis

Prefer a small number of type roles with predictable contrast.

Avoid:

- many arbitrary font sizes
- excessive bold text
- low-contrast metadata
- uppercase everywhere
- headings that dominate more than content

For dense professional tools, prioritize legibility and scanning over editorial
drama.

## Spacing and density

Density should match the user's work.

Use spacing tokens consistently.

Evaluate:

- information density
- scan frequency
- click/tap frequency
- precision required
- content type
- device
- novice vs expert usage

### Dense operational surfaces

Prefer:

- compact rows
- aligned labels/values
- predictable controls
- hover/focus detail
- adjustable density when justified

### Discovery surfaces

Allow:

- larger media
- more whitespace
- stronger visual hierarchy
- richer previews
- lower information density

Do not use one density model everywhere.

## Layout architecture

Choose layout based on task topology.

Common structures:

### Content-first shell
Use when the artifact/workspace should dominate.

### Rail + workspace + inspector
Use for data, media, annotation, admin, analysis, and creation tools.

### Master-detail
Use when users browse many entities and inspect one without losing context.

### Grid/catalog
Use for discovery, templates, opportunities, media, assets.

### Table/list
Use when comparison, sorting, scanning, and precision matter.

### Dashboard
Use for monitoring and decision support, not as a dumping ground for every KPI.

### Immersive workspace
Use for sustained creation, review, editing, or inspection.

Do not choose layout from aesthetics alone.

## Responsive composition

Responsive design should transform architecture, not merely shrink it.

Determine:

- what remains persistent
- what collapses
- what becomes modal/sheet
- what reorders
- what hides
- what becomes scrollable
- what becomes bottom navigation
- what requires larger touch targets

Prefer one coherent information architecture across devices.

### Desktop

Can support:

- persistent rail
- multi-column workspaces
- side inspectors
- dense controls
- hover states
- keyboard workflows

### Tablet

Often needs:

- collapsible rails
- temporary inspectors
- reduced density
- touch-friendly actions

### Mobile

Prefer:

- focused task flow
- bottom sheets
- explicit back/close
- large touch targets
- fewer persistent regions
- context preservation between surfaces

Never reproduce a desktop three-column workspace at 390 px width.

## Action hierarchy

Classify actions:

- primary
- secondary
- contextual
- destructive
- tertiary
- background/system

A page should normally have one clear primary action per active context.

Avoid:

- multiple primary buttons competing
- destructive actions next to primary actions without separation
- hidden critical actions
- action labels that describe implementation instead of outcome

Prefer outcome language such as `Create dataset`, `Use this vision`, or
`Start review` over generic labels such as `Submit` when the outcome is clearer.

## Interaction affordances

Users should understand what is interactive without guessing.

Use:

- cursor/hover/focus
- clear button/link styles
- selection states
- pressed/expanded states
- keyboard focus
- preview affordances
- consistent icon semantics

Do not rely on hover alone for essential actions.

## Progressive disclosure

Show information when it becomes useful.

Good candidates for delayed disclosure:

- advanced settings
- detailed metadata
- destructive actions
- low-frequency controls
- debug/system information
- deep configuration

Do not hide information users need to make the current decision.

## Context preservation

Preserve user orientation whenever possible.

Important for:

- catalog → detail
- search → inspection
- review → edit
- dashboard → drill-down
- multi-step flows

Use:

- drawers/sheets
- URL-backed state
- scroll restoration
- selection persistence
- back-stack semantics
- breadcrumbs/context labels

Avoid forcing users to reconstruct search/filter/selection state.

## Navigation

Navigation should reflect the mental model of the product.

Evaluate:

- global navigation
- local navigation
- task navigation
- entity context
- history/back behavior
- deep linking

Avoid mixing organizational hierarchy, workflow states, and user actions in one
navigation structure.

## Forms

Professional form architecture should consider:

- grouping by user intent
- sensible defaults
- progressive disclosure
- inline validation
- field-level help only when useful
- keyboard flow
- focus management
- error recovery
- dirty state
- save semantics
- autosave vs explicit commit
- destructive reset behavior

Do not convert every form into a wizard unless steps are truly dependent.

## Tables and high-density data

Use tables when comparison and precision are primary.

Consider:

- column priority
- sticky headers
- horizontal overflow
- column visibility
- sorting/filtering
- row selection
- bulk actions
- inline vs drawer editing
- pagination/virtualization
- empty/loading/error states
- row identity
- keyboard navigation

Avoid card grids for data users need to compare across many attributes.

## Media-heavy interfaces

For image/video/frame-heavy products:

- prioritize the media itself
- preserve aspect ratio
- use stable placeholders
- support progressive loading
- virtualize large collections
- separate preview from authoritative full-resolution content
- preserve zoom/pan state where useful
- provide clear selection/review state
- keep metadata available without covering content

Use immersive modes when sustained visual inspection is the primary task.

## Dashboards

A dashboard should answer specific operational questions.

Prioritize:

1. what needs attention
2. what changed
3. what action should follow
4. supporting context

Use visual hierarchy based on importance, not widget symmetry.

Avoid:

- KPI walls
- redundant charts
- decorative trend lines
- excessive bento fragmentation
- identical card treatment for all metrics

## Empty, loading, error, and success states

### Empty
Explain what is missing, why it matters, and the most useful next action.

### Loading
Match feedback to expected duration:
- optimistic interaction for reversible low-risk actions
- skeletons for structured content
- inline spinners for local work
- progress for long-running jobs
- background status for durable jobs

Avoid blocking the entire application for a local request.

### Error
Explain:
- what failed
- what remains safe
- what the user can do next
- whether retry is safe

Preserve entered work and context whenever possible.

Do not rely on toast-only errors for important failures.

### Success
Prefer changed state, inline confirmation, subtle toast, or completed status.
Avoid modal celebration for routine actions.

## Optimistic interaction

Use optimistic UI only when:

- mutation is likely to succeed
- rollback is clear
- conflicts are manageable
- authoritative state can reconcile

Always represent:

- pending
- success
- failure
- rollback/retry

Never create the illusion that a critical mutation succeeded when it has not.

## Motion and transition architecture

Motion should explain change.

Use it to:

- preserve spatial context
- show hierarchy changes
- explain opening/closing surfaces
- communicate reordering
- indicate progress
- reinforce cause/effect

Prefer short, restrained transitions.

Avoid:

- long page animations
- motion on every interaction
- decorative parallax in operational tools
- animations that delay expert users

Respect reduced-motion preferences.

## Design tokens

Use semantic tokens for:

- surface
- foreground
- border
- accent
- success
- warning
- danger
- focus
- spacing
- radius
- elevation
- motion
- density

Prefer semantic names such as `surface-subtle`, `text-secondary`,
`border-critical`, `space-panel`, and `radius-control` over raw visual values.

Design tokens should express product semantics, not just colors.

## Accessibility

Accessibility is part of architecture.

Consider:

- semantic HTML
- keyboard access
- visible focus
- focus order
- screen-reader labels
- target size
- contrast
- color independence
- reduced motion
- dialog/sheet focus traps
- error association
- form labels
- live regions for dynamic status
- table semantics

Do not treat accessibility as a final QA pass.

## Expert vs novice workflows

Professional applications often serve both.

Use:

- progressive disclosure for advanced options
- shortcuts/command palette for experts
- discoverable default paths for new users
- persistent user preferences where valuable
- stable spatial layout
- undo/recovery

Do not make expert efficiency dependent on hidden undocumented gestures.

## Keyboard-first architecture

For high-frequency professional tools, consider:

- predictable tab order
- selection movement
- command shortcuts
- command palette
- escape/back semantics
- Enter/Space activation
- focus restoration
- shortcut discoverability

Keyboard workflows should coexist with mouse/touch.

## Personalization

Personalization is useful when users have stable differences in workflow.

Good examples:

- saved filters/views
- column visibility
- panel layout
- density
- favorites
- recent items

Avoid personalization before a strong default experience exists.

## Perceived performance

Design for perceived speed as well as actual speed.

Use:

- immediate acknowledgement
- prefetching where justified
- optimistic low-risk actions
- skeletons
- progressive media
- cache-aware transitions
- preserving previous content during refresh
- background work

Avoid blanking the whole screen for small updates.

## Design consistency

Consistency should apply to:

- spacing
- typography
- interaction states
- action hierarchy
- icon semantics
- navigation
- dialogs/sheets
- forms
- error states
- terminology

Do not enforce consistency when a different interaction pattern genuinely serves
a different user job better.

## Visual novelty vs usability

A professional app can feel distinctive without sacrificing clarity.

Innovative ideas are welcome when they:

- reduce cognitive load
- improve spatial understanding
- accelerate repeated work
- reveal useful context
- improve collaboration
- make complex state easier to understand

Reject novelty that:

- hides controls
- damages accessibility
- reduces scanability
- breaks predictable navigation
- makes dense work slower
- adds animation/space without information value

## Output discipline

Do not output a generic design checklist.

Translate this reference into:

- 2–3 coherent design directions
- concrete interaction topology
- meaningful visual/UX trade-offs
- a strong recommendation
- a production-grade design plan

Example:

> Let's keep the main page as a fast launchpad, but give each opportunity a
> richer contextual preview before activation. A hybrid shelf + category view
> preserves inspiration while fixing discoverability, and a sliding inspector
> lets us expose media, workflow, and ingredients without destroying browse
> context.

That is stronger than listing pattern names.
