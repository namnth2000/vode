# Discover verbs

This file defines `brainstorm`, `understand`, `decide`, and `plan`.

All are advisory by default.

## brainstorm

Purpose: explore uncertainty before committing to a direction.

### Flow

1. Restate the actual uncertainty in one sentence.
2. Read available product/project context.
3. Identify the underlying trade-off or opportunity.
4. Generate 2-4 meaningfully different directions, not cosmetic variants.
5. Cut options that violate current constraints or add unjustified complexity.
6. Recommend a direction when evidence is strong enough.
7. State what would change the recommendation.

Do not code unless the user explicitly asks.

Do not turn brainstorming into a giant feature list.

When the user says "I'm wondering if X would be better", compare X against the current approach, not against an imaginary greenfield product.

## understand

Purpose: make the product clear enough to build.

Try to establish:

- target user
- problem/job
- core loop
- must-have outcome
- V1 boundary
- explicit non-goals
- important constraints
- intended experience or visual direction when the product is UI-heavy or taste-driven
- definition of done

Read existing context before asking.

Functional clarity and visual clarity are separate. A product may be clear enough in behavior while still being unsafe to implement visually because several materially different directions fit the brief. When that happens, use the taste-alignment checkpoint in the clarification protocol before broad UI work.

If critical information is missing, use the clarification protocol.

### Output

Prefer a compact product understanding:

- **User**
- **Problem**
- **Core loop**
- **V1**
- **Not now**
- **Experience / visual direction**, only when material
- **Done when**
- **Open decision**, only if truly unresolved

Do not invent requirements just to make the document look complete.

## decide

Purpose: choose between concrete alternatives.

### Flow

1. Name the decision.
2. Define the few criteria that actually matter now.
3. Compare options against current product constraints.
4. Prefer the simpler/reversible option when value is close.
5. Make a recommendation.
6. State the condition that would justify revisiting it.

### Output

- **Decision**
- **Why**
- **Trade-off**
- **Revisit when**

Do not hide behind "it depends" when the available context supports a choice.

## plan

Purpose: translate a clear direction into the smallest sensible build sequence.

### Flow

1. Confirm the desired product outcome.
2. Inspect the existing project and reuse its architecture.
3. Identify the smallest coherent vertical slice.
4. Order work so something usable appears early.
5. Separate required work from nice-to-have work.
6. Identify material risks only.
7. Define how to know the slice is done.

### Plan format

- **Outcome**
- **Keep**
- **Change**
- **Build order**
- **Verify**
- **Not in this pass**

Avoid fake precision, story points, enterprise milestones, or speculative phases for small projects.
