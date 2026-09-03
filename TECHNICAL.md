# Vode Technical Guide

This document is for Vode developers and maintainers.

## Goal

Vode is a model-agnostic product-building protocol packaged as an agent skill.

BUILD is the lifecycle backbone:

**Brainstorm -> Understand -> Implement -> Launch -> Distribute**

Supporting verbs exist around those anchors because real projects are rarely entered at a clean lifecycle boundary.

Vode's job is not to make an agent "smarter" in the abstract. Its job is to reduce avoidable product mistakes by giving the agent:

1. a stable routing layer
2. a small set of product-building principles
3. a context-reading order
4. verb-specific execution protocols
5. a consistent handoff contract

## Repository structure

```text
vode/
├── README.md
├── README_VI.md
├── TECHNICAL.md
├── AGENTS.md
├── LICENSE
└── skills/
    └── vode/
        ├── SKILL.md
        └── references/
            ├── principles.md
            ├── context.md
            ├── routing.md
            ├── questions.md
            ├── handoff.md
            ├── routing-cases.md
            └── verbs/
                ├── discover.md
                ├── make.md
                ├── ship.md
                ├── evolve.md
                └── build.md
```

## Architecture

### SKILL.md is the router

`SKILL.md` should stay small enough to load cheaply. It defines:

- what Vode is
- supported verbs
- routing precedence
- default behavior
- which references to load
- universal safety and scope rules

It should not duplicate the full protocol for every verb.

### References are loaded by need

Universal references:

- `principles.md`
- `context.md`
- `questions.md`
- `handoff.md`

Routing reference:

- `routing.md`

Verb groups:

- `discover.md`: brainstorm, understand, decide, plan
- `make.md`: implement, debug, review, refine
- `ship.md`: launch, distribute
- `evolve.md`: iterate, pivot, resume
- `build.md`: orchestration

The grouping is deliberate. One file per verb would create unnecessary file and context overhead. One giant file would make every invocation expensive.

## Routing model

Routing is semantic.

Priority:

1. explicit verb
2. direct action intent
3. dominant user intent
4. current project state
5. conservative fallback

Example:

```
vode tôi đang băn khoăn có nên thêm login không
```

routes to `brainstorm`, not `implement`.

```
vode login đang redirect sai, sửa giúp tôi
```

routes to `debug`.

```
vode nên dùng localStorage hay D1?
```

routes to `decide`.

See `references/routing.md` and `references/routing-cases.md`.

## Vietnamese support

All operational instructions are written in English to keep the skill compact and predictable.

Vietnamese support lives primarily in semantic routing examples and phrase families. Do not build a brittle exact-string command parser.

The model should understand Vietnamese naturally, then execute the selected verb using the English protocol.

A common typo `vote` may be treated as `vode` only when the surrounding message clearly refers to product-building and the current conversation already establishes Vode. Never interpret generic election/voting language as Vode.

## Context strategy

Vode reads context before asking questions or changing code.

It uses a capability ladder:

1. current user request
2. current conversation, if available
3. project instructions and docs, if available
4. current source and working diff, if available
5. recent git history, only when it helps explain current state
6. external sources, only when requested or materially necessary and available

No single capability is mandatory. Vode must degrade gracefully.

Vode must never pretend it read chat history, git, files, browser output, or external services it cannot actually access.

## Context efficiency

Vode should optimize context selection before introducing a custom agent runtime.

The preferred flow is:

```text
request
  -> route concern
  -> select relevant project truth
  -> locate relevant source
  -> read the smallest useful ranges
  -> execute
  -> keep only decision-relevant tool output
  -> widen context only when blocked
```

This is progressive disclosure. It reduces context pressure without requiring embeddings, a vector database, a generated repo index, or a mandatory session-state file.

### Stable and volatile context

When the host supports prompt caching, keep reusable context as stable as practical and place volatile task data later. Typical stable material includes durable agent instructions and tool definitions. Typical volatile material includes the current task, current diff, errors, and newly retrieved source.

This is capability-based guidance. Vode must not require a provider-specific cache API, and correctness must not depend on a cache hit.

### Long-running sessions

If the host can compact or summarize conversation state, retain the minimum durable working state:

- current goal
- decisions and constraints
- completed or changed work
- pending work
- unresolved failures

Do not add `SESSION_STATE.md`, telemetry, or a Vode database by default. Add persistent machinery only after repeated real tasks show that the host's native capabilities are insufficient.

## Questions

Questions are conditional, not ceremonial.

Ask only when the missing answer could materially change:

- the product direction
- scope
- user-visible behavior
- irreversible architecture
- launch safety

Before asking, inspect available context.

Bundle questions once, normally up to three. Prefer a recommended default.

Do not ask about implementation details that can be inferred from the existing project.

## Edit policy

Advisory verbs do not edit by default:

- brainstorm
- understand
- decide
- plan
- review
- distribute
- iterate
- pivot
- resume

Action verbs may edit:

- implement
- debug
- refine
- launch
- build, when it routes to an action verb

User intent overrides this table.

## Model independence

Core skill rules must not require:

- a specific LLM
- proprietary memory
- a specific shell
- a specific browser
- a specific Git provider
- a specific coding-agent tool name

Write capability-based instructions:

Good:

> If git history is available and current docs do not explain the decision, inspect the smallest relevant commit range.

Bad:

> Call tool X with parameter Y.

Tool-specific installation examples are allowed in README files, not in the core execution protocol.

## Avoiding over-engineering

A change is suspicious when it introduces machinery without solving a current product need.

Before broadening a change, ask:

- Is this required for the current user-visible outcome?
- Does the project already have a pattern for this?
- Can a smaller reversible change solve it?
- Is the abstraction serving more than one real use case today?

Vode should not create infrastructure for hypothetical scale.

## Regression discipline

When changing Vode behavior:

1. Add or update a case in `routing-cases.md` when routing changes.
2. Keep user-facing verb tables in README EN/VI synchronized.
3. Do not add the same rule to multiple reference files.
4. Prefer one durable rule over multiple narrow examples.
5. Remove rules that repeatedly create worse outputs.
6. Review the final diff for scope creep.

## Versioning

Use semantic versioning in `skills/vode/SKILL.md`.

- patch: wording, examples, non-behavioral clarifications
- minor: new verb, routing capability, or workflow behavior
- major: incompatible routing or execution contract

## What not to add yet

Keep Vode small until real failures justify expansion.

Do not add by default:

- mandatory project state files
- telemetry
- generated configuration
- a Vode-specific database
- per-model forks
- large prompt libraries
- automatic changelog generation
- mandatory test frameworks

If a future capability solves a repeated real failure, add the smallest version first.
