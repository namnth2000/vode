# Vode maintainer rules

- Keep Vode model-agnostic and capability-based.
- Keep `skills/vode/SKILL.md` focused on routing and universal rules.
- Put detailed verb behavior in `references/verbs/`.
- Do not duplicate the same rule across multiple files.
- Do not add a dependency, state file, or framework unless a repeated real failure justifies it.
- Routing is semantic. Do not turn Vietnamese support into an exact-string command parser.
- When routing behavior changes, update `references/routing-cases.md`.
- Keep README.md and README_VI.md behaviorally consistent.
- Advisory verbs must not edit by default unless the user explicitly asks.
- Read project context before asking the user for information that may already exist.
- Ask only questions that materially affect the result. Bundle them once where possible.
- Prefer the smallest coherent change. Do not refactor unrelated parts of Vode while changing one behavior.
- Before committing, inspect the diff and remove speculative cleanup.
