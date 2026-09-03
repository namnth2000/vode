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

When available, inspect the most relevant source of truth for the concern at hand:

- agent instructions: `AGENTS.md` or equivalent
- product truth: prefer `PRODUCT.md`; recognize equivalents such as `Project_Spec.md`, `PRD.md`, `SPEC.md`, `docs/product.md`, or `docs/spec.md`
- design truth when relevant: prefer `DESIGN.md`; recognize equivalent UI/style/design specifications
- architecture truth when relevant: prefer `ARCHITECTURE.md`; recognize equivalents such as `TECH.md` or `docs/architecture.md`
- README, roadmap/backlog, and deployment docs only when they can materially change the current decision

Do not read every document simply because it exists.

## Recommended project document convention

Vode recommends these roles for new projects:

### Core

- `PRODUCT.md` - what the product is, who it serves, the current scope, user-visible behavior, product rules, and definition of done
- `AGENTS.md` - how agents should work in the repository: commands, technical constraints, durable implementation decisions, known pitfalls, and verification expectations

### When relevant

- `DESIGN.md` - visual direction, interaction principles, references, explicit do/don't guidance, and durable taste decisions
- `ARCHITECTURE.md` - technical structure and significant architecture decisions that should persist across tasks

These filenames are conventions, not requirements. Reuse equivalent existing documents instead of renaming or creating duplicates just to satisfy Vode.

A project can be product-clear without being visually clear. The presence of `PRODUCT.md` does not remove the need to inspect `DESIGN.md`, references, or existing UI when visual direction materially affects the result.

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

## Progressive disclosure

Treat context loading as a narrowing loop rather than a one-time dump:

1. route the current concern
2. locate likely sources with the lightest available evidence, such as search results, file names, imports, current diff, or error locations
3. read the smallest relevant files or ranges
4. widen only when the current evidence cannot answer or safely execute the task

Prefer targeted source ranges over whole-file reads when the surrounding context is not needed. Prefer current diff and failing paths over broad repository scans for local fixes.

Do not load unrelated docs, specialist skills, source areas, or history merely because they are available.

## Tool-output discipline

Tool output is context too.

When the runtime allows filtering or summarization, keep the evidence that can change the next action:

- command and exit status
- failing tests or checks
- relevant errors and warnings
- concise changed diff or affected paths

Avoid carrying repeated success logs, dependency progress, unchanged listings, or very large outputs after their useful signal has been extracted.

Never compact away evidence needed to diagnose an unresolved failure.

## Long sessions and caching

When native compaction or summarization is available, preserve a compact working state containing:

- current goal
- decisions that must remain true
- completed or changed work
- pending work
- important constraints and known failures

Do not create a mandatory Vode state file just to implement this. Prefer capabilities the current agent already has.

When prompt caching is available, keep stable reusable instructions and definitions ahead of volatile task-specific context when the harness benefits from prefix reuse. Cache behavior is an optimization, not part of Vode's correctness contract.


## Conflict order

When context disagrees, prefer:

1. current explicit user instruction
2. the relevant source of truth for that concern:
   - product behavior -> product docs such as `PRODUCT.md`
   - visual/interaction direction -> design docs such as `DESIGN.md`
   - technical structure -> architecture docs such as `ARCHITECTURE.md`
   - execution constraints -> `AGENTS.md` or equivalent project instructions
3. current implementation behavior
4. recent history
5. generic best practice

Project instructions govern how work is executed, but should not silently redefine product, design, or architecture truth outside their concern.

Flag meaningful conflicts rather than silently choosing.
