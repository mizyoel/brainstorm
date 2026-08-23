# Changelog

## 1.2.0 — 2026-08-22

Adaptive exploration and handoff upgrade.

- removes the fixed 3-question/per-round ceiling
- introduces information-gain-based adaptive questioning
- starts with a small directive Decision Round and continues only while
  additional answers can materially improve the design
- adds Final Action Control after the completed recommendation and plan
- supports Start implementation, Create full design / architecture document,
  Keep brainstorming, and Stop here
- keeps brainstorm read-only/no-code only until explicit implementation handoff
- adds regression coverage for post-plan handoff behavior


## 1.1.0 — 2026-08-21

Professional web-app design upgrade.

- adds `references/web-app-design.md`
- adds visual hierarchy, typography, spacing/density, responsive composition,
  action hierarchy, affordance, progressive disclosure, forms, tables,
  dashboards, media-heavy interfaces, loading/error/recovery, motion,
  accessibility, keyboard-first, design-token, and perceived-performance lenses
- adds three-part design test: understandability, operating efficiency, and
  implementation/maintenance quality
- strengthens `/brainstorm` for product-grade web application redesign while
  preserving read-only/no-code behavior and concise outputs


## 1.0.2 — 2026-08-21

Brainstorm-depth patch.

- explicit `/brainstorm` now uses a Decision Round rather than a single shallow checkpoint
- normally asks two directive, trade-off-oriented questions
- supports up to three directive questions per round
- adds a native Exploration Control: Converge / Explore another direction /
  Ask deeper questions / Challenge assumptions
- final plan is blocked until the user explicitly converges
- additional question/exploration rounds occur only after user opt-in
- replaces the old global 3-question ceiling with a 3-per-round limit
- strengthens the broad-UX regression scenario


## 1.0.1 — 2026-08-21

Questionnaire reliability patch.

- explicit `/brainstorm` now requires a decision checkpoint when 2+ credible
  directions remain or unresolved UX/product intent can change the winner
- final recommendation/plan must wait until the checkpoint answer
- broad UX prompts treat primary experience objective as HIGH-impact uncertainty
- cross-host questionnaire support: `ask_user` in Copilot CLI and
  `vscode/askQuestions` in VS Code
- removed CLI-specific `allowed-tools` frontmatter for better Agent Skills
  portability
- added regression coverage for "better UX for the opportunity in main page"


## 1.0.0 — 2026-08-21

Initial `/brainstorm` package.

- repository-first reconnaissance
- explicit and automatic invocation
- strong architectural authority
- native `ask_user` clarification requirement
- 0–2 normal / 3 maximum question budget
- production-grade engineering evaluation
- backend, data, database, distributed, frontend, AI/ML, infrastructure lenses
- professional UI/UX architecture reference
- anti-pattern detection
- read-only and no-code boundaries
- 3–6 step final plan
- behavioral scenario and acceptance regression suite
