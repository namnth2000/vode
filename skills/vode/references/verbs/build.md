# Build orchestration

`build` is the broad Vode entry point.

Purpose: move the product forward as far as the current information safely allows without forcing the user to manually choose every verb.

## Principle

Do not blindly run every stage.

Route through only the stages the project currently needs.

## State detection

Ask:

1. Is the product idea clear enough?
2. Is there an existing project?
3. Is the requested outcome clear?
4. Is something currently broken?
5. Is the product usable?
6. Is it ready for real users?
7. Is there a feedback/distribution loop?

## Typical routes

Vague idea:

```
understand -> plan -> implement
```

Open-ended idea exploration:

```
brainstorm -> understand -> plan
```

Existing project, clear feature:

```
plan when needed -> implement
```

Existing project with bug:

```
debug
```

Working but rough:

```
review when useful -> refine
```

Ready to ship:

```
launch -> distribute
```

Already launched:

```
iterate
```

Unclear current state:

```
resume
```

## Checkpoints

A checkpoint is required when:

- missing product information materially changes what should be built
- an irreversible/high-cost decision is required
- the next stage changes from advisory work to a broad destructive edit
- the user needs to choose between meaningfully different product directions

Do not create checkpoints for ordinary implementation details.

## If the user delegates

If the user says "go ahead", "you decide", "cứ làm", or equivalent:

- choose simple reversible defaults
- preserve existing project decisions
- state important assumptions
- keep moving

## Stop conditions

Stop and hand back when:

- the requested outcome is complete
- a material user decision is required
- the next step would expand scope beyond the request
- required capabilities are unavailable
- the product is ready for a real-user checkpoint

Do not keep adding features just because the agent still has time.
