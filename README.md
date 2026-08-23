# /brainstorm

A fast, repository-aware senior engineering brainstorming skill for GitHub
Copilot.

`/brainstorm` investigates an existing codebase, explores only credible
architecture directions, challenges weak assumptions, asks very few
decision-changing questions through Copilot's native questionnaire UI, and
finishes with a concise production-grade plan.

## Design goals

- fast enough for everyday engineering
- repository-first
- 2–3 real options, not fake variants
- strong architectural authority
- adaptive directive questioning: start small, continue as needed while each answer can materially improve the design
- native interactive questionnaire for clarification (`ask_user` in CLI, `vscode/askQuestions` in VS Code)
- user-controlled exploration depth: Continue / Explore / Deeper Questions / Challenge
- final native handoff menu: Start implementation / Create full document / Keep brainstorming / Stop here
- production-grade without gold-plating
- strong backend, data, AI, infrastructure, frontend, and UI/UX reasoning
- professional web-app design intelligence: hierarchy, density, typography, responsive composition, accessibility, forms, tables, media, motion, tokens, and perceived performance
- collaborative "we / let's" tone
- read-only
- no implementation code
- 3–6 step final plan

## Install

### Repository skill

Copy this `brainstorm` directory to:

`.github/skills/brainstorm/`

GitHub Copilot also supports project skills under `.claude/skills` and
`.agents/skills`.

### Personal skill

Copy this directory to:

`~/.copilot/skills/brainstorm/`

or:

`~/.agents/skills/brainstorm/`

Then start a new Copilot CLI session, or run:

`/skills reload`

## Use

Explicit:

`/brainstorm add durable image processing`

The skill also allows model invocation, so Copilot can load it automatically
when a prompt contains meaningful architectural uncertainty. The description is
intentionally written to avoid trivial/mechanical tasks.

For explicit `/brainstorm`, v1.0.2 adds a short Decision Round: normally two
directive questions shape the design, followed by a native Exploration Control.
The user can converge immediately, explore another direction, request deeper
questions, or ask the agent to challenge its assumptions.

## Read-only behavior

The skill itself instructs Copilot to remain read-only.

Important: `allowed-tools` in skill frontmatter is an approval mechanism, not a
hard security sandbox. If hard read-only enforcement is required for a CLI
session, restrict the tools visible to Copilot using Copilot CLI tool controls
such as `--available-tools` / `--excluded-tools`, and deny write/shell behavior
as appropriate for your environment.

## Package

- `SKILL.md` — compact orchestration and UX contract
- `references/engineering-architecture.md` — production architecture foundation
- `references/ui-ux-architecture.md` — professional interaction/workspace patterns
- `references/web-app-design.md` — product-grade visual, responsive, accessibility, and interaction design quality
- `references/domain-lenses.md` — backend, data, AI, distributed, infra, frontend lenses
- `references/anti-patterns.md` — architecture and brainstorming smoke detector
- `evals/scenarios.md` — behavioral regression scenarios
- `evals/acceptance-criteria.md` — v1 release gates

## Product principle

**Curiosity expands the possibility space. Engineering discipline collapses it
into something we can confidently build.**
