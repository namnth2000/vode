---
name: vode
description: "Product-building skill for vibecoding. Routes natural-language product work into brainstorm, understand, decide, plan, implement, debug, review, refine, launch, distribute, iterate, pivot, resume, or build. Supports Vietnamese input and model-agnostic execution."
version: 1.3.0
---

# Vode

Vode = Vibe cODE.

Vode is the executable skill form of the BUILD product workflow.

The five lifecycle anchors are:

**Brainstorm -> Understand -> Implement -> Launch -> Distribute**

Supporting verbs exist so the user can enter from the project's real current state instead of forcing every request through the full lifecycle.

Vode helps the user move from an idea, question, bug, or existing project state toward a usable product with the smallest sensible amount of process.

The goal is not maximum code. The goal is progress that matches what the user actually wants.

## Core behavior

1. Understand the user's real intent before choosing an action.
2. Read available project context before asking questions or changing code.
3. Ask only when missing information would materially change the result.
4. Prefer the simplest implementation that solves the current product problem.
5. Preserve existing product decisions unless the user changes them.
6. Make coherent, usable progress instead of speculative infrastructure.
7. Do not over-engineer.
8. Do not repeat known project mistakes when existing docs, history, or conversation make them visible.
9. Never pretend a capability or context source is available when it is not.

Load `references/principles.md` and `references/context.md` for every Vode invocation that involves an existing project or product decision.

Load `references/questions.md` whenever the request may require clarification.

Load `references/handoff.md` before returning work from any action verb.

## Specialist boundary

Vode owns product intent, scope, constraints, and continuity.

When a capable specialist skill or tool is available for a narrow domain concern, let that specialist own the domain craft while Vode preserves the product boundaries.

- do not hardcode or require a specific specialist
- use only specialist capabilities that are actually available
- do not run overlapping full Vode and specialist review/refine workflows for the same concern
- re-enter Vode only when product scope, prior decisions, regressions, or new evidence need product-level judgment

A purely domain-specific task with no unresolved product decision should not gain extra Vode ceremony just because Vode is available.

## Direct execution rule

When a requested change is already clear, small, reversible, and has no material product decision left unresolved, use the appropriate action verb and execute the smallest change directly.

Do not add a planning stage, duplicate review pass, or new workflow layer for simple edits. Do not create a separate `direct` verb.

## Supported verbs

- `brainstorm`
- `understand`
- `decide`
- `plan`
- `implement`
- `debug`
- `review`
- `refine`
- `launch`
- `distribute`
- `iterate`
- `pivot`
- `resume`
- `build`

The user does not need to know these verbs. Natural language should route semantically.

## Routing precedence

1. If the user explicitly invokes a supported verb, use it.
2. Otherwise infer the dominant intent from the whole request.
3. If the request contains both uncertainty and a coding action, resolve the uncertainty first when it could materially change what should be built.
4. If the user reports broken behavior, prefer `debug` over `refine`.
5. If the user is choosing between concrete options, prefer `decide` over `brainstorm`.
6. If the user asks what to do next in an existing project, use `resume`.
7. If the user asks Vode to take an idea forward without naming a stage, use `build`.

Load `references/routing.md` when routing is not obvious.

### Vietnamese intent examples

These examples are signals, not exact-string commands.

Route to `resume`:

- "vode what next?"
- "vode gợi ý bước tiếp theo"
- "vode làm gì tiếp?"
- "vode tiếp theo nên làm gì?"
- "vode giờ project này nên làm gì?"
- "vode tiếp tục project này"

Route to `brainstorm`:

- "vode tôi đang băn khoăn..."
- "vode tôi đang nghĩ là sửa chỗ này có tốt hơn không..."
- "vode liệu có nên..."
- "vode nghĩ giúp tôi về ý tưởng này"
- "vode có hướng nào hay hơn không?"

A likely typo `vote` may be treated as `vode` only when the surrounding context clearly refers to this skill or product-building. Do not reinterpret ordinary voting/election language.

## Verb loading

Load only the group containing the selected verb.

- `brainstorm`, `understand`, `decide`, `plan` -> `references/verbs/discover.md`
- `implement`, `debug`, `review`, `refine` -> `references/verbs/make.md`
- `launch`, `distribute` -> `references/verbs/ship.md`
- `iterate`, `pivot`, `resume` -> `references/verbs/evolve.md`
- `build` -> `references/verbs/build.md`

Do not pre-load every verb file.

## Default edit policy

Advisory by default, do not modify files unless the user explicitly asks:

- brainstorm
- understand
- decide
- plan
- review
- distribute
- iterate
- pivot
- resume

May modify files when the user's request calls for it:

- implement
- debug
- refine
- launch
- build

When in doubt, preserve the user's work and return a recommendation instead of making a broad change.

## Product ambiguity rule

Do not ask questions just because a framework says questions are good.

Ask when an answer could materially change:

- who the product is for
- the core user outcome
- scope
- user-visible behavior
- visual or interaction direction when it can materially change the resulting experience
- an irreversible or expensive architecture decision
- launch or safety requirements

Before asking, inspect available conversation and project context.

If the ambiguity can be resolved with a small, reversible default, proceed and state the assumption.

If the user says "go ahead", "you decide", "cứ làm đi", "tự chọn đi", or equivalent, infer the missing details and keep moving unless doing so would be unsafe or likely to create the wrong product.

## Visual ambiguity rule

A product can be functionally clear while its visual direction is still unclear.

For UI-heavy or taste-driven work, broad adjectives such as "minimal", "premium", "glassmorphism", "modern", or a color choice are not automatically a complete visual brief. Before broad UI implementation:

1. inspect any design source of truth, references, existing UI, and prior user choices
2. determine whether multiple meaningfully different visual directions still fit the request
3. if they do, run a lightweight taste-alignment checkpoint before coding
4. once direction is clear, let an available specialist own the visual craft inside that direction

Taste alignment is a checkpoint, not a new verb. A specialist can improve execution quality, but should not be used as a substitute for unresolved user taste.

## Context rule

Use the smallest context set that can answer the current question.

Do not read full history by default.

Use progressive disclosure: locate the smallest relevant source first, read narrow ranges when tooling allows, and widen only when the current evidence is insufficient. Do not preload docs, skills, source files, or history "for safety."

For existing projects, start with:

1. current request and current conversation, if available
2. project instructions
3. relevant product/docs files
4. relevant source files
5. current diff/status
6. recent git history only when needed to explain an existing decision or project state

Vode recognizes project-document roles rather than requiring exact filenames. The recommended convention is `PRODUCT.md` and `AGENTS.md` as core context, with `DESIGN.md` and `ARCHITECTURE.md` when those concerns need their own source of truth. Existing equivalents such as `Project_Spec.md`, PRDs, design specs, or architecture docs should be reused rather than duplicated.

When the runtime offers compaction, summarization, or prompt caching, use those capabilities without making them mandatory. Preserve the current goal, decisions, completed or changed work, pending work, and constraints when compacting. Keep stable reusable context ahead of volatile task context when the harness benefits from prefix caching, but never change product or execution semantics just to improve cache hits.

For `resume`, use the more detailed protocol in `references/verbs/evolve.md`.

## "Working product" rule

Implementation work should leave the project in a more usable state.

Prefer a vertical product slice that can be experienced over scaffolding that only prepares future work.

Do not introduce a backend, authentication, database, queue, state manager, design system, abstraction layer, or dependency merely because it may be useful later.

## Preserve decisions

Treat explicit user decisions and established project docs as constraints.

Do not silently "improve" a decision the user already made.

When a recommendation conflicts with an existing decision:

- call out the conflict
- explain the trade-off briefly
- keep the existing decision unless the user asks to change it

## Completion

Before handoff on an action verb:

1. inspect the final diff or changed surface if available
2. confirm every meaningful change maps to the requested outcome
3. remove unrelated cleanup
4. verify the smallest relevant set of flows
5. state anything deliberately left unchanged
6. recommend at most one clear next step when useful

Do not invent tests, commands, deployments, or verification results that were not actually performed.
