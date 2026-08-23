# /brainstorm v1 Evaluation Scenarios

Run these scenarios against representative repositories. Judge behavior using
`acceptance-criteria.md`, not by matching exact wording.

## Scenario 1 — Vague new feature

Prompt:

`/brainstorm add smart search`

Expected behavior:

- targeted repository inspection before architecture advice
- determine current search/data architecture from evidence
- 2–3 credible approaches only if meaningful
- questionnaire only if a major product/architecture distinction remains
- concise recommendation and 3–6 step plan
- no generic search-engine essay

Critical failures:

- no repo grounding
- immediate question dump
- recommends vector DB/LLM without evidence

---

## Scenario 2 — Proposed overengineering

Prompt:

`/brainstorm let's create a microservice and Redis queue for generating thumbnails`

Expected behavior:

- inspect existing media/job/worker architecture
- challenge the proposed service/queue if existing boundaries can absorb it
- explain capability gap required before a service becomes justified
- recommend reuse when appropriate

Critical failures:

- treats requested technology as requirement
- presents microservice as equal option without justification

---

## Scenario 3 — Real architecture ambiguity

Prompt:

`/brainstorm add image processing that can take 20 minutes`

Repository does not reveal whether jobs must survive restart.

Expected behavior:

- inspect current processing patterns
- identify durability as HIGH-impact uncertainty
- use `ask_user`, ideally one high-information questionnaire
- re-evaluate after response
- converge, no question loop

Critical failures:

- plain-text clarification question while `ask_user` exists
- >3 questions
- no durability/failure reasoning

---

## Scenario 4 — Frontend workspace redesign

Prompt:

`/brainstorm redesign the dataset review page`

Expected behavior:

- inspect routing, state ownership, current workspace, detail surfaces, tests
- reason about user job and context preservation
- selectively consider content-centric shell, contextual inspector, responsive
  rail, virtualization, state-machine behavior, optimistic interaction
- choose only patterns that fit
- concise architecture plan

Critical failures:

- visual styling advice only
- UI pattern bingo
- no state/interaction architecture

---

## Scenario 5 — Fashionable UI request

Prompt:

`/brainstorm let's convert the review app into an infinite canvas`

Expected behavior:

- inspect actual workflow
- challenge infinite canvas when spatial composition is not the user job
- preserve it only as a credible experimental direction when justified
- recommend stable workspace architecture if stronger

Critical failures:

- accepts infinite canvas solely because requested
- ignores navigation/accessibility/performance complexity

---

## Scenario 6 — Data normalization

Prompt:

`/brainstorm automatically normalize imported dataset tags`

Expected behavior:

- inspect ingestion/tag/taxonomy architecture
- distinguish canonical deterministic normalization from semantic assistance
- consider versioning, provenance, replay/reproducibility, source of truth
- recommend evaluation before autonomous semantic mutation

Critical failures:

- embeddings/LLM become authoritative by default
- no lineage/versioning consideration

---

## Scenario 7 — Autonomous AI mutation

Prompt:

`/brainstorm let an LLM automatically correct metadata`

Expected behavior:

- challenge authoritative autonomous writes
- separate probabilistic suggestion from canonical state
- reason about evaluation, model/version provenance, confidence, fallback,
  approval, drift
- describe safe promotion path toward automation if evidence supports it

Critical failures:

- direct LLM write path recommended without measured safety
- no provenance/recovery boundary

---

## Scenario 8 — Performance diagnosis

Prompt:

`/brainstorm the page is slow, add Redis`

Expected behavior:

- inspect actual data/render/network/query path
- treat Redis as proposed solution, not diagnosis
- identify likely bottleneck from evidence
- recommend cache only if cache semantics and measurements justify it

Critical failures:

- immediate Redis recommendation
- no bottleneck reasoning

---

## Scenario 9 — Trivial task

Prompt without explicit skill invocation:

`change the button text from Save to Apply`

Expected behavior:

- `/brainstorm` should not auto-invoke visibly
- no architecture exploration
- no questionnaire

Critical failure:

- turns task into brainstorm ceremony

---

## Scenario 10 — Obvious local bug

Prompt without explicit skill invocation:

`fix null handling in UserMapper`

Expected behavior:

- no visible brainstorm unless repository evidence reveals a material contract or
  architecture decision

Critical failure:

- automatic architecture essay for a mechanical fix

---

## Scenario 11 — Ownership boundary

Prompt:

`/brainstorm should this logic live in the API or worker?`

Expected behavior:

- inspect callers, lifecycle, persistence, execution semantics, tests
- recommend ownership from evidence
- ask only if a missing operational constraint can genuinely flip the decision

Critical failures:

- generic API-vs-worker pros/cons
- questions repository could answer

---

## Scenario 12 — Mature-system refactor

Prompt:

`/brainstorm refactor our ingestion architecture`

Expected behavior:

- system-level scan
- identify actual structural weaknesses
- distinguish ideal target from migration path
- preserve compatibility and authoritative state
- recommend incremental migration unless evidence requires replacement
- plan limited to first coherent production architecture slice

Critical failures:

- rewrite-first recommendation without necessity
- enormous roadmap instead of 3–6 meaningful steps

---

# Optional stress scenarios

## Ambiguous but safe default exists

Prompt:

`/brainstorm add caching for user preferences`

If repository shows single-process app and inexpensive preferences lookup:

Expected:
- no questionnaire
- challenge whether caching is needed at all

## Frontier option

Prompt:

`/brainstorm make collaborative editing work offline`

Expected:
- CRDT/local-first may be credible
- still compare with server-authoritative sync and constrained offline queue
- explicit complexity/recovery trade-off

## Existing bad abstraction

Prompt:

`/brainstorm add another source type to this importer`

Repository shows importer already has a large conditional/god module.

Expected:
- do not blindly "follow existing pattern"
- identify current boundary as the problem
- recommend incremental responsibility split with compatibility path


---

## Regression R1 — Broad UX prompt must run a directive decision round

Prompt:

`/brainstorm better UX for the opportunity in main page`

Representative repository evidence:

- opportunity cards already have rich preview metadata
- activation path already exists
- multiple credible presentation/interaction directions remain

Expected behavior:

1. inspect the existing opportunity surface and activation path
2. show 2–3 credible UX directions
3. use the host-native questionnaire for a **Decision Round**, starting with two
   directive questions such as:

   **Primary opportunity outcome**
   - fastest inspiration → creation
   - more confidence before choosing
   - deeper discovery/comparison

   **Role of the main page**
   - focused launchpad
   - hybrid launchpad + category browsing
   - full opportunity explorer

4. include the **Exploration Control**:
   - converge on strongest direction
   - explore another strong direction
   - ask a deeper question round
   - challenge current assumptions

5. if the user chooses deeper exploration, do **not** emit the final plan yet
6. continue asking additional directive questions if important uncertainty remains
7. produce recommendation + 3–6 step plan after sufficient convergence
8. show the native **Final Action Control**:
   - Start implementation
   - Create full design / architecture document
   - Keep brainstorming
   - Stop here

Critical failures:

- only one shallow question when multiple independent design axes exist
- concludes repository evidence alone determines desired UX objective
- emits final recommendation/plan before Exploration Control
- prints questions as ordinary text while native questionnaire exists
- continues deeper questioning without explicit user choice



---

## Scenario 13 — Professional web-app redesign quality

Prompt:

`/brainstorm redesign the main dashboard to feel more professional`

Expected behavior:

- inspect the existing page shell, navigation, state, responsive behavior, and
  key data/actions before proposing visual changes
- generate 2–3 coherent design directions, not component/pattern soup
- ask directive questions about the primary user job and density/interaction
  trade-off when they could change the winning design
- reason about:
  - visual hierarchy
  - typography roles
  - spacing/density
  - action hierarchy
  - responsive transformation
  - accessibility
  - loading/error/empty states
  - perceived performance
  - maintainable design tokens/components
- reject decorative complexity that hurts scanability or expert efficiency
- converge on a production-grade design architecture and 3–6 step plan
- do not generate implementation code

Critical failures:

- focuses mainly on colors/cards
- dumps a list of trendy UI patterns
- proposes desktop-only composition without responsive behavior
- ignores accessibility/state/error behavior
- treats "professional" as purely aesthetic


---

## Regression R2 — Final plan must hand off instead of ending

Prompt:

`/brainstorm improve the main page opportunity UX`

Assume the user has completed the Decision Round and the design has converged.

Expected behavior:

1. output final Recommendation
2. output concise 3–6 step Plan
3. invoke native **Final Action Control**
4. offer at least:
   - Start implementation
   - Create full design / architecture document
   - Keep brainstorming
   - Stop here
5. if Start implementation is selected, exit brainstorm read-only mode and
   continue as the normal coding agent using the approved plan
6. if Keep brainstorming is selected, resume from current decisions rather than
   restarting discovery

Critical failures:

- final plan ends the interaction with no action control
- implementation begins without explicit user selection
- action choices are printed only as prose when native questionnaire exists
- brainstorming restarts from scratch after Keep brainstorming
