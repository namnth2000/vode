# Vode

**Vode** = **V**ibe c**ode**.

Vode is a product-building skill for AI coding agents. It helps you turn an idea into a usable, shipped product with a workflow that stays simple, direct, and close to what you actually want.

[Tiếng Việt](README_VI.md)

## BUILD at the core

Vode is the executable skill form of the BUILD product workflow:

**B**rainstorm -> **U**nderstand -> **I**mplement -> **L**aunch -> **D**istribute

Those five verbs remain the lifecycle anchors. Vode adds supporting verbs such as `decide`, `plan`, `debug`, `review`, `refine`, `iterate`, `pivot`, and `resume` so you can enter the workflow from the state your product is actually in.

You do not have to run every stage.

## Why Vode?

Vibecoding is fast when the agent understands the product. It gets frustrating when the agent guesses too much, over-engineers, rewrites working decisions, or starts coding before the idea is clear.

Vode can infer the right route from natural language:

```
vode what next?
vode I'm not sure whether this should be simpler.
vode should I use localStorage or a database?
vode this button is broken on mobile.
```

Explicit verbs are optional. Natural language is the default interface.

## Installation

Vode follows the Agent Skills format and can be installed with the `skills` CLI.

### Codex

Global installation:

```bash
npx skills add namnth2000/vode -a codex -g
```

Project-scoped installation:

```bash
npx skills add namnth2000/vode -a codex
```

### Claude Code

Global installation:

```bash
npx skills add namnth2000/vode -a claude-code -g
```

Project-scoped installation:

```bash
npx skills add namnth2000/vode -a claude-code
```

### Cursor

Global installation:

```bash
npx skills add namnth2000/vode -a cursor -g
```

Project-scoped installation:

```bash
npx skills add namnth2000/vode -a cursor
```

### OpenCode

Global installation:

```bash
npx skills add namnth2000/vode -a opencode -g
```

Project-scoped installation:

```bash
npx skills add namnth2000/vode -a opencode
```

### Manual installation

Download or clone this repository, then copy the entire `skills/vode/` directory into the skills directory used by your agent. Keep `SKILL.md` and the `references/` directory together.

| Agent | Global location | Project location |
| --- | --- | --- |
| Codex | `~/.codex/skills/vode/` | `.agents/skills/vode/` |
| Claude Code | `~/.claude/skills/vode/` | `.claude/skills/vode/` |
| Cursor | `~/.cursor/skills/vode/` | `.agents/skills/vode/` |
| OpenCode | `~/.config/opencode/skills/vode/` | `.agents/skills/vode/` |

If the agent is already running, restart it after installation if the skill is not detected immediately.

## Verbs

| Verb | Use it when | Edits by default? |
| --- | --- | --- |
| `brainstorm` | Explore an idea, concern, or possible improvement | No |
| `understand` | Clarify what should be built and what is still missing | No |
| `decide` | Choose between concrete options | No |
| `plan` | Turn a clear product direction into a build plan | No |
| `implement` | Build the next coherent product slice | Yes |
| `debug` | Find and fix broken behavior | Yes |
| `review` | Evaluate product, UX, scope, or implementation | No |
| `refine` | Improve an existing experience without redesigning everything | Yes |
| `launch` | Get the product ready for real users | Usually |
| `distribute` | Find the smallest practical path to users and feedback | No |
| `iterate` | Turn feedback, usage, or new ideas into the next version | No |
| `pivot` | Reconsider direction without throwing away useful assets | No |
| `resume` | Understand where the project is and recommend what to do next | No |
| `build` | Orchestrate the appropriate Vode steps from the current state | Depends |

## Examples

### Continue an existing project

```
vode what next?
```

Vode checks the available conversation context, project docs, current source, working changes, and relevant git history. It then recommends the highest-value next step instead of blindly inventing a new feature.

### Explore before coding

```
vode I'm wondering whether I should add CodeMirror to the editor.
```

This routes to `brainstorm`. Vode explores the trade-offs first. It does not modify code unless you ask.

### Fix something

```
vode the Preview control overlaps the heading on mobile, fix it.
```

This routes to `debug`: reproduce/inspect -> find the actual cause -> make the smallest fix -> verify affected behavior.

### Build from a vague idea

```
vode build
I want a tiny app that turns Markdown into a nice PDF.
```

If important product information is missing, Vode asks a small bundled question. If the answer can be inferred safely from the project or brief, it proceeds and states the assumption.

## Core philosophy

Vode prefers:

- product over technology
- working over theoretically perfect
- clear intent over guessed intent
- the simplest stack that solves the current problem
- small coherent changes over broad rewrites
- existing project decisions over agent preferences
- real usage over speculative infrastructure
- shipping over endless polishing
- feedback over feature accumulation

Vode does **not** promise that every model will produce identical results. It makes the workflow less dependent on a model correctly guessing product decisions on its own.

## Maintainers

See [TECHNICAL.md](TECHNICAL.md) for architecture, routing rules, file structure, and maintenance guidance.

## License

MIT.
