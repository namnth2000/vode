# Evolve verbs

This file defines `iterate`, `pivot`, and `resume`.

All are advisory by default.

## iterate

Purpose: convert real signals into the next smallest meaningful version.

### Inputs may include

- user feedback
- personal usage
- analytics
- bugs
- support messages
- new ideas

### Classify each signal

- Fix now
- Improve next
- Experiment
- Wishlist
- Ignore for now

Prioritize repeated friction and core-loop problems over novel feature requests.

Recommend one coherent next version rather than a pile of unrelated tasks.

## pivot

Purpose: reconsider product direction while preserving useful assets and learning.

### Flow

1. Separate "product is bad" from "distribution is weak" and "too early to know".
2. Identify what evidence actually exists.
3. Identify reusable assets:
   - code
   - workflow
   - audience insight
   - content
   - data
   - domain knowledge
4. Propose the smallest direction change first.
5. Compare:
   - continue
   - reposition
   - narrow
   - pivot
   - stop
6. Recommend one.

Do not prescribe a pivot merely because early traction is low.

## resume

Purpose: answer "where are we and what should we do next?"

Examples:

- "vode what next?"
- "vode gợi ý bước tiếp theo"
- "vode làm gì tiếp?"
- "vode tiếp tục project này"

### Context scan

Use available sources in this order, stopping when the current state is clear:

1. **Current conversation**
   - latest goal
   - recent decisions
   - work just completed
   - rejected directions

2. **Project instructions/docs**
   - AGENTS or equivalent
   - README
   - product/spec docs
   - roadmap/backlog
   - design/architecture docs only if relevant

3. **Current project state**
   - relevant source
   - working diff/status
   - TODOs that are actually tied to the current goal

4. **Recent history, if necessary**
   - recent commits
   - relevant PRs/changelog
   - use history to understand the last completed slice or why an odd decision exists

Do not read deep git history by default.

Do not invent a next feature just because nothing is obviously broken.

### Determine project state

Summarize:

- **Now** - what the product currently is / current milestone
- **Done** - most relevant recently completed work
- **Open** - unresolved issue, decision, or launch gap
- **Next** - one highest-value next step
- **Why** - why this outranks alternatives

If two next steps are genuinely close, offer at most two and recommend one.

### Route forward

After recommending the next step, name the likely next verb:

- unclear product -> understand
- uncertain direction -> brainstorm/decide
- clear work package -> plan/implement
- broken behavior -> debug
- working but rough -> refine
- ready for users -> launch
- launched but no feedback loop -> distribute/iterate

Do not edit files during `resume` unless the user also explicitly asks to execute the recommendation.
