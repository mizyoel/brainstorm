# 🧠 /brainstorm

[![GitHub](https://img.shields.io/badge/GitHub-mizyoel%2Fbrainstorm-181717?logo=github)](https://github.com/mizyoel/brainstorm)
[![Install with npx](https://img.shields.io/badge/install-npx%20skills%20add-CB3837?logo=npm)](#installation)
[![AI Coding Skill](https://img.shields.io/badge/AI%20Coding-Skill-7C3AED)](#)
[![UX & Architecture](https://img.shields.io/badge/UX%20%26%20Architecture-Pro%20Grade-2563EB)](#)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

<p align="center">
  <img src="brainstorm-skill.webp" alt="/brainstorm skill" width="320">
</p>

> **Don't code the first idea. Brainstorm the right one.**

`/brainstorm` is a professional brainstorming skill for coding agents.

It transforms rough ideas, feature requests, UX problems, and architecture questions into **focused decisions, strong design directions, trade-offs, and implementation-ready plans**.

```text
rough idea
    ↓
understand the problem
    ↓
ask the questions that matter
    ↓
explore strong directions
    ↓
compare trade-offs
    ↓
choose a direction
    ↓
build the plan
```

## Installation

One command:

```bash
npx skills add mizyoel/brainstorm
```

Then start brainstorming:

```text
/brainstorm redesign the dataset import experience
```

---

## Why `/brainstorm`?

Coding agents are extremely good at building things.

Sometimes a little **too** good.

Give an agent:

```text
add a better experiment selector
```

and five minutes later you may have:

* three new components
* four hooks
* two API endpoints
* an abstraction called `ExperimentSelectorManagerProvider`
* and absolutely no agreement about what "better" meant

`/brainstorm` inserts the missing step:

> **Figure out what should be built before deciding how to build it.**

---

## What it can brainstorm

### 🎨 Product & UX

```text
/brainstorm better UX for selecting the active experiment
```

Explore:

* information hierarchy
* user flows
* navigation
* interaction patterns
* page architecture
* workspace design
* progressive disclosure
* empty/loading/error states
* responsive behavior
* professional web-app UX patterns

### 🏗 Architecture

```text
/brainstorm architecture for collaborative annotation
```

Explore:

* service boundaries
* domain ownership
* state architecture
* APIs
* background jobs
* event flows
* persistence
* scalability
* failure handling
* SOLID design

### 🧬 Data

```text
/brainstorm a better ingestion architecture for heterogeneous vision datasets
```

Explore:

* schemas
* normalization
* lineage
* pipelines
* metadata
* ontology
* validation
* versioning
* storage boundaries
* indexing and retrieval

### ✨ Features

```text
/brainstorm semantic auto-normalization for dataset tags
```

Explore:

* user value
* interaction model
* system behavior
* edge cases
* technical feasibility
* AI boundaries
* architecture
* rollout strategy

### 🔧 Refactoring

```text
/brainstorm simplify this service before we add more features
```

Explore:

* responsibilities
* coupling
* abstractions
* module boundaries
* state ownership
* migration strategies
* technical debt

---

## How it works

`/brainstorm` does not immediately jump to a solution.

It progressively reduces uncertainty.

### 1. Understand

First, identify:

* the actual problem
* the user or system affected
* important constraints
* existing architecture
* what must remain unchanged

### 2. Question

Ask focused, directive questions where the answer can materially change the design.

For example:

```text
Who performs this workflow most often?

A. Data engineers
B. Annotators
C. Project managers
D. Multiple roles
```

Or:

```text
What should happen when switching experiments?

A. Switch immediately
B. Warn only when there are unsaved changes
C. Always require confirmation
D. Keep multiple experiments open
```

There is **no artificial three-question limit**.

If an important uncertainty remains, keep exploring.

---

## Questions with purpose

The goal is not:

```text
Question
Question
Question
Question
Question
Question
```

The goal is:

```text
uncertainty
    ↓
high-value question
    ↓
better understanding
    ↓
stronger design
```

Questions should be:

* directive
* decision-oriented
* contextual
* short
* useful

Not an interrogation form from the Department of Software Permits.

---

## Explore multiple directions

When several good solutions exist, `/brainstorm` should expose them.

For example:

### A. Workspace Switcher

Treat the active experiment as global application context.

**Strengths**

* fast switching
* always visible
* scales well across pages

**Trade-off**

* occupies persistent shell space

### B. Command Palette

Use search-first navigation.

**Strengths**

* extremely fast for expert users
* handles large experiment counts

**Trade-off**

* less discoverable

### C. Contextual Selector

Keep experiment selection near relevant content.

**Strengths**

* strong local context
* simpler interface

**Trade-off**

* weaker global orientation

Then compare them and recommend the strongest direction for the actual workflow.

---

## Pro-grade UX reasoning

For application design, `/brainstorm` can reason using patterns such as:

* Content-Centric Application Shell
* Contextual Sliding Sheet
* Adaptive Content Shell
* Asymmetric Bento Grid
* Infinite Canvas Workspace
* Optimistic Execution
* Cross-Platform Responsive Rail
* Finite State-Machine Driven UI
* Headless Component Architecture
* Tokenized Design Systems
* Personalized Matrix Layout
* Layered Scaffold Workspace

The goal is not to sprinkle fashionable names over a mockup.

The goal is to answer:

> **Which interaction architecture best matches this user's work?**

---

## Engineering principles

Implementation recommendations should favor:

* clear ownership
* explicit state
* simple data flow
* small responsibilities
* composable components
* testability
* production failure handling
* maintainable abstractions
* incremental migration
* SOLID principles

Avoid architecture astronauts.

Avoid giant god components.

Avoid creating `AbstractUniversalFactoryManagerFactory` because the button may someday become blue.

---

## Example

```text
/brainstorm improve the experiment selector in our capture application
```

### Problem discovered

```text
Current experiment
├── visually disconnected from the main workflow
├── switching and creation compete for attention
├── recent experiments have weak hierarchy
└── users can lose context when switching
```

### Important questions

```text
How often do users switch experiments?

Should exactly one experiment always be active?

Should recent experiments be immediately accessible?

What happens to unsaved work when switching?
```

### Directions

```text
A ─ Workspace Switcher
B ─ Search / Command Palette
C ─ Persistent Experiment Rail
```

### Recommendation

```text
Workspace Switcher
+
Recent Experiments
+
Search
+
Explicit "Create Experiment" action
```

### Implementation direction

```text
ApplicationShell
│
├── ExperimentContext
│
├── ActiveExperiment
│
├── ExperimentSwitcher
│   ├── RecentExperiments
│   ├── Search
│   └── CreateExperiment
│
└── Route
    └── experimentId
```

A fuzzy feature request becomes a design decision that is ready to implement.

---

## Keep exploring

Brainstorming should not suddenly slam the door after the recommendation.

At each useful decision point, you can continue with:

```text
▶ Start Implement
```

Turn the selected direction into implementation work.

```text
📄 Create Full Document
```

Expand it into a PRD, architecture document, technical design, or implementation specification.

```text
✨ Enhance My Idea
```

Push the selected concept further.

```text
🧭 Explore More
```

Generate additional directions or investigate unanswered questions.

```text
■ Stop Here
```

Keep the current result as the decision checkpoint.

---

## Agents can use it proactively

You can explicitly invoke:

```text
/brainstorm ...
```

But `/brainstorm` is also designed to be useful when an agent recognizes that a request contains meaningful product or architectural uncertainty.

For example:

```text
Add a way for users to organize datasets into groups.
```

There are many plausible interpretations.

Instead of immediately manufacturing tables and endpoints, the agent can first reason about:

```text
group
├── folder?
├── collection?
├── project?
├── saved query?
├── dataset version?
└── taxonomy?
```

That tiny detour can prevent a very expensive wrong turn.

---

## Great prompts

```text
/brainstorm better UX for the opportunity section
```

```text
/brainstorm redesign the home page around the current experiment
```

```text
/brainstorm architecture for multiplayer annotation
```

```text
/brainstorm how we should normalize user-created tags
```

```text
/brainstorm simplify this React state architecture
```

```text
/brainstorm a production-grade import workflow for COCO datasets
```

```text
/brainstorm whether this should be a modal, drawer, page, or inline workflow
```

```text
/brainstorm how to make this tool feel professional for expert operators
```

---

## Bad idea → better idea

```diff
- User asks for feature
- Agent immediately starts coding
- Architecture emerges accidentally
- UX decisions are hidden inside implementation
- Everyone discovers the problems during review

+ User asks for feature
+ /brainstorm identifies the real problem
+ Important uncertainties are resolved
+ Multiple directions are explored
+ Trade-offs become explicit
+ One direction is selected
+ Implementation starts with intent
```

---

## The `/brainstorm` loop

```text
       ┌───────────────┐
       │   Rough Idea  │
       └───────┬───────┘
               │
               ▼
       ┌───────────────┐
       │ Ask What      │
       │ Actually      │
       │ Matters       │
       └───────┬───────┘
               │
               ▼
       ┌───────────────┐
       │ Explore       │
       │ Directions    │
       └───────┬───────┘
               │
               ▼
       ┌───────────────┐
       │ Compare       │
       │ Trade-offs    │
       └───────┬───────┘
               │
               ▼
       ┌───────────────┐
       │ Recommend     │
       └───────┬───────┘
               │
          ┌────┴────┐
          │         │
          ▼         ▼
     Implement   Explore More
```

---

## Philosophy

Software development has a dangerous shortcut:

```text
idea → code
```

`/brainstorm` adds the missing middle:

```text
idea
  ↓
understanding
  ↓
questions
  ↓
directions
  ↓
trade-offs
  ↓
decision
  ↓
architecture
  ↓
code
```

Because the fastest way to build the wrong thing is to build it extremely well.

---

## Install

```bash
npx skills add mizyoel/brainstorm
```

Then bring your coding agent a half-formed idea.

**Let `/brainstorm` sharpen it before the compiler gets involved.** 🧠
