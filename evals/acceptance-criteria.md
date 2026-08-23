# /brainstorm v1 Acceptance Criteria

All critical criteria are release gates.

## AC-01 — Repository grounding [CRITICAL]

For an existing repository, every technical brainstorm performs targeted
reconnaissance before architectural recommendation.

PASS:
- recommendation cites or clearly relies on relevant existing patterns

FAIL:
- generic greenfield advice despite available repository context

## AC-02 — Native questioning [CRITICAL]

100% of clarification questions use the host-native interactive questionnaire
when it is available.

Recognized Copilot hosts include:

- CLI: `ask_user`
- VS Code: `vscode/askQuestions`

FAIL:
- any ordinary-text clarification question while a native questionnaire tool is available
- assuming the CLI tool identifier is portable to every host

## AC-03 — Adaptive question discipline [CRITICAL]

For explicit `/brainstorm`:

- start with a small directive Decision Round, usually about 2 questions
- there is no fixed global question limit
- additional questions are allowed only when their answers can materially
  improve or change the design
- stop when remaining uncertainty affects implementation detail only

FAIL:

- arbitrary hard question cap prevents necessary exploration
- unbounded questioning with low information gain
- repeated questions on the same decision axis
- questioning continues after the design is already sufficiently resolved

## AC-04 — Question necessity

Every question must be traceable to a decision capable of materially changing:

- architecture
- ownership
- scope
- material risk
- recommendation

Questions that affect only implementation detail fail this criterion.


## AC-04B — Explicit Decision Round and Exploration Control [CRITICAL]

For explicit `/brainstorm` with multiple credible directions:

PASS:

- directions are shown before questioning when useful
- directive questions shape real design decisions
- questioning continues as needed when important uncertainty remains
- the Exploration Control is shown between meaningful exploration rounds
- recommendation appears only after sufficient convergence

FAIL:

- one shallow poll substitutes for meaningful brainstorming
- arbitrary cap truncates a complex brainstorm
- repository feasibility is mistaken for user-intent certainty

## AC-04C — Adaptive depth

Every additional question must be traceable to expected information gain.

PASS:
- complex problems may use more questions
- simple problems still converge quickly

FAIL:
- question count is optimized instead of decision quality
- questions are asked because the workflow says to ask them rather than because
  the answer matters

## AC-04D — Final Action Control [CRITICAL]

After the final recommendation and plan, explicit `/brainstorm` must present a
native next-action menu.

Minimum useful options:

- Start implementation
- Create full design / architecture document
- Keep brainstorming
- Stop here

PASS:
- implementation begins only after explicit selection
- document expansion preserves brainstorm decisions
- Keep brainstorming resumes from the current state without repetition
- Stop here performs no additional work

FAIL:
- the conversation simply ends after the plan
- implementation starts automatically
- the agent asks a generic prose "what next?" instead of native interaction

## AC-05 — Credible divergence

Alternative directions differ at meaningful architectural boundaries.

FAIL:
- cosmetic/naming variants
- weak third option added for symmetry

## AC-06 — Decisive convergence

Every completed brainstorm ends with a preferred direction unless evidence
genuinely prevents a safe recommendation.

FAIL:
- "it depends" neutrality without identifying the deciding constraint

## AC-07 — Production quality [CRITICAL]

The recommendation does not knowingly introduce correctness, security,
persistence, recovery, or maintainability dead ends.

Production-grade must remain proportional rather than maximal.

## AC-08 — No gold-plating

The recommendation avoids infrastructure and abstraction that do not solve a
demonstrated requirement.

## AC-09 — Architectural challenge [CRITICAL]

The skill rejects or reframes technically weak user proposals when repository
evidence or strong engineering reasoning warrants it.

## AC-10 — Read-only [CRITICAL]

The skill performs no repository modification or implementation action.

## AC-11 — No code

The response contains no implementation code, interfaces, pseudocode,
configuration scaffolding, or generated implementation snippets.

## AC-12 — Concrete plan

The final plan contains 3–6 meaningful architectural implementation slices.

FAIL:
- generic lifecycle steps such as analyze/design/implement/test/deploy

## AC-13 — UI/UX rigor

For UI/UX work, interaction architecture is treated with engineering depth:

- state
- navigation/context
- synchronization
- responsiveness
- accessibility
- performance
- workflow topology

## AC-13B — Professional web-app design quality

For professional web-app design requests, the brainstorm must consider the
relevant subset of:

- visual hierarchy
- typography
- spacing/density
- responsive composition
- action hierarchy
- interaction affordances
- progressive disclosure
- forms/tables/media architecture
- loading/error/recovery states
- accessibility
- motion
- design tokens
- keyboard/expert workflows
- perceived performance

PASS:
- these factors influence the architecture without becoming a checklist dump

FAIL:
- design is reduced to colors/cards/visual styling
- component patterns are proposed without user-job reasoning
- responsive or accessibility architecture is ignored
- novelty is prioritized over operational usability


## AC-14 — Pattern discipline

Professional software/UI patterns are selected for fit rather than novelty.

FAIL:
- pattern-name dumping
- fashionable architecture without user/system justification

## AC-15 — Tone

The response is:

- collaborative
- analytical
- encouraging
- concise
- confident

It uses "we" and "let's" naturally where appropriate and challenges
constructively.

FAIL:
- authoritarian scolding
- vague consultancy language
- motivational filler

## AC-16 — Compression

No unnecessary:

- repository report
- principle lecture
- giant comparison matrix
- repeated summary
- filler introduction
- conclusion that repeats the recommendation

## AC-17 — Quiet automatic invocation [CRITICAL]

Automatic invocation does not turn trivial or settled implementation work into a
visible brainstorm flow.

## AC-18 — Questionnaire fallback

If `ask_user` is unavailable:

- no plain-text interrogation
- make a production-safe assumption
- state only material assumptions
- continue to a recommendation

## Release gate

v1.0.0 requires:

- all critical acceptance criteria passing
- at least 10 of the 12 core scenarios passing cleanly
- zero critical failures in AC-01, AC-02, AC-03, AC-04B, AC-07, AC-09, AC-10, or AC-17

## Suggested evaluation record

For each scenario, record:

- PASS / FAIL
- questions asked
- whether `ask_user` was used
- number of directions
- recommendation present
- plan steps
- critical AC failures
- unnecessary architecture introduced
- short reviewer note

Prefer behavioral review over keyword matching.
