# Changelog

All notable changes to Vode are documented here.

## [1.3.0] - 2026-09-03

### Changed

- Added progressive context disclosure so Vode locates and reads the smallest relevant sources before widening context.
- Added tool-output discipline to retain failures and decision-relevant evidence without carrying unnecessary logs forward.
- Added capability-based guidance for long-session compaction and prompt caching without requiring state files or provider-specific APIs.

## [1.2.0] - 2026-08-31

### Changed

- Added a recommended project-document convention: `PRODUCT.md` and `AGENTS.md` as core context, with `DESIGN.md` and `ARCHITECTURE.md` when relevant, while continuing to recognize existing equivalent filenames.
- Added a lightweight taste-alignment checkpoint for UI-heavy work when broad aesthetic language still permits materially different visual directions.
- Separated functional product clarity from visual clarity so Vode does not start broad UI implementation before user taste is sufficiently resolved.
- Clarified that specialist design skills improve craft after direction is clear; they should not silently choose unresolved user taste.

## [1.1.0] - 2026-08-31

### Changed

- Clarified the boundary between Vode and specialist skills: Vode owns product intent, scope, constraints, and continuity while available specialists own narrow domain craft.
- Added a direct execution rule for clear, small, reversible changes so simple edits do not gain unnecessary planning or review ceremony.
- Narrowed `review` and `refine` toward product semantics, scope, regressions, and continuity instead of duplicating specialist critique.
- Added a compact execution handoff contract: Goal, Change, Preserve, Avoid, Verify.
- Simplified installation to a single primary command: `npx skills add namnth2000/vode`.
- Added routing regression cases for direct execution and specialist delegation.

## [1.0.0] - 2026-08-29

### Added

- Initial public version of the Vode product-building skill.
- BUILD lifecycle anchors: Brainstorm, Understand, Implement, Launch, Distribute.
- Supporting verbs for decision-making, planning, debugging, review, refinement, iteration, pivoting, resuming, and broad build orchestration.
- Natural-language routing with English and Vietnamese examples.
- Context, clarification, handoff, and anti-overengineering guidance for AI coding agents.
