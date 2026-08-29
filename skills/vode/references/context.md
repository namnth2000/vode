# Context protocol

Vode should understand the project before asking the user to repeat information or before changing working code.

## Context ladder

Use only the levels needed for the current task.

### Level 1 - request

Read the user's current message carefully.

Extract:

- desired outcome
- explicit constraints
- explicit non-goals
- whether the user wants advice or action

### Level 2 - conversation

If current conversation context is available, use it for:

- decisions already made
- rejected approaches
- current goals
- recent failures
- user corrections

Do not claim access to conversations that are not available.

### Level 3 - project instructions and docs

When available, inspect the most relevant files first:

- AGENTS.md or equivalent agent instructions
- README
- product/spec docs
- roadmap/backlog
- design or architecture docs
- deployment docs when launch is in scope

Do not read every document simply because it exists.

### Level 4 - source and current work

Inspect:

- target files
- nearby existing patterns
- current working diff/status when available
- configuration only when relevant

Prefer understanding the existing implementation over inventing a new one.

### Level 5 - history

Use recent commits, blame, PR history, or changelog only when needed to answer questions such as:

- Why does this odd behavior exist?
- Was this recently changed?
- What was the last completed product slice?
- Is a current difference intentional?
- What should `resume` recommend next?

History is evidence, not a ritual. Skip it when current docs/source are enough.

### Level 6 - external context

Use web or external sources only when:

- the user asked for research/current verification
- the answer materially depends on changing external facts
- an integration/API requires current documentation
- launch/distribution needs live platform information

## Context budget

Do not load everything "for safety".

For each additional context source, ask:

> Can this source materially change the decision I am about to make?

If no, skip it.

## Conflict order

When context disagrees, prefer:

1. current explicit user instruction
2. current project instructions
3. current product docs
4. current implementation behavior
5. recent history
6. generic best practice

Flag meaningful conflicts rather than silently choosing.
