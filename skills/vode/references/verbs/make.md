# Make verbs

This file defines `implement`, `debug`, `review`, and `refine`.

## implement

Purpose: build the next coherent user-visible product slice.

### Before editing

1. Read project instructions.
2. Read only the docs relevant to the requested behavior.
3. Inspect existing implementation patterns.
4. Identify explicit decisions that must remain unchanged.
5. Clarify only material ambiguity.

### Implementation rules

- prefer existing patterns
- keep the change surface focused
- do not refactor unrelated code
- do not add dependencies without current need
- do not build infrastructure for hypothetical scale
- prefer a usable vertical slice over scaffolding
- update docs only when project truth changed

### Before handoff

Inspect the changed surface/diff if possible.

Every meaningful changed hunk should map to:

- the requested outcome
- a necessary regression fix
- required documentation

Remove speculative cleanup.

Verify the smallest relevant user flow.

## debug

Purpose: fix observed broken behavior without broadening scope.

### Flow

1. Capture the observed behavior and expected behavior.
2. Reproduce or inspect the smallest relevant path.
3. Find the actual cause, not just the visible symptom.
4. Check whether the bug is a regression from a known product decision.
5. Make the smallest robust fix.
6. Verify the failing path and nearby regression risk.
7. Avoid opportunistic refactors.

If the root cause is uncertain, say so and gather evidence before editing broadly.

## review

Purpose: assess the product or implementation without editing by default.

Review against the user's goal, not a generic best-practice catalog.

Prioritize:

1. core product failure
2. regression or broken UX
3. unnecessary complexity
4. confusing scope/flow
5. polish

Use:

- Critical
- Major
- Minor
- Won't fix

A common pattern may be intentional. Do not classify taste as a defect simply because a rulebook dislikes it.

End with the 1-3 highest-value changes, not a mandate to fix everything.

## refine

Purpose: improve something that already works.

### Flow

1. Identify the specific friction or quality gap.
2. Preserve existing behavior and product semantics.
3. Make the smallest visual/interaction/copy change that addresses it.
4. Check neighboring states and responsive behavior when relevant.
5. Stop when the requested quality gap is solved.

Refine is not permission to redesign the whole product.

If the issue is broken behavior, switch to `debug`.
