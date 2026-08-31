# Handoff contract

Keep handoffs useful and compact.

## Advisory verb

Return the decision or recommendation first.

Then include only what helps the user act:

- why
- important trade-offs
- assumptions
- recommended next verb/action

Do not turn a simple decision into a long report.

## Execution handoff

When handing a clear work package to another executor or tool, prefer a compact product contract:

- **Goal** - product/user outcome
- **Change** - required changes
- **Preserve** - existing decisions that must remain
- **Avoid** - material non-goals or known traps
- **Verify** - smallest relevant user flow

Omit fields that have nothing material to say. Do not restate implementation details that the executor can discover from the project, and do not inflate a clear task into a second planning document.

## Action verb

When files or product behavior changed, summarize:

1. **Changed** - what materially changed
2. **Why** - how it maps to the user's request
3. **Verified** - what was actually checked
4. **Left unchanged** - important boundaries deliberately preserved
5. **Next** - at most one high-value next step, when useful

Do not claim verification that did not happen.

## Review output

Use practical severity:

- Critical - blocks the core product or creates real user/data/safety risk
- Major - meaningful friction or regression
- Minor - worthwhile polish
- Won't fix - intentional or not worth changing now

A review should be allowed to say the product is already good enough.

## Avoid ceremony

Do not emit framework scores, badges, state files, or lengthy checklists unless they help the user make a decision.
