# Holistic Review

Before transitioning to Sprint Review, review the **entire change** as a cohesive whole. This step catches issues that aren't visible when looking at individual subtasks.

## Why Holistic Review?

Incremental TDD implementation can lead to:
- **Emergent duplication** - Similar patterns appear across subtasks
- **Naming drift** - Terms evolve during implementation, leaving inconsistencies
- **Scaffolding remnants** - Temporary code from "Fake It" steps

The Holistic Review provides the "step back" moment to see the forest, not just the trees.

## Review Aspects

| Aspect | Questions to Ask |
|--------|------------------|
| **Increment Delivered** | Does the implementation deliver the observable, user-facing value promised in the PBI? |
| **Cohesion** | Do the changes work together as a unified feature? |
| **Consistency** | Are naming, patterns, and style consistent across all changes? |
| **Duplication** | Did incremental implementation introduce duplication to eliminate? |
| **Coupling** | Are modules appropriately decoupled? Any unexpected dependencies? |
| **Testability** | Is test coverage adequate? Any untested edge cases? |
| **Documentation** | Do comments, docstrings, or docs need updating? |

## Ensure All Changes Are Wired

1. Verify new code is actually called from existing code paths
2. If not wired: add subtasks to integrate, or remove unused code (YAGNI)
3. Return to subtask execution if new subtasks were added

## Multi-Perspective Review

1. Ask subagents to perform strict multi-perspective reviews **in parallel** (e.g. correctness, security, API design, test quality)
2. Fact-check the review findings against actual code — subagent findings are hypotheses, not verdicts
3. Adapt based on verified issues
4. Repeat until a review round surfaces no new verified issues (minimum 3 rounds)

## Comprehensive Refactoring

1. Ask subagents to identify refactoring opportunities
2. Fact-check proposed refactorings for validity
3. Apply refactorings using refactoring-related skills:
   - Extract common patterns that emerged across subtasks
   - Rename for consistency across the entire change
   - Reorganize code structure now that the full picture is clear
   - Remove any scaffolding or temporary code from incremental development
4. Repeat until code quality is satisfactory (minimum 3 rounds)

**Commit each refactoring step separately** following Tidy First discipline.

## Then Transition

Once holistic review is complete:

1. Verify Sprint Goal is achieved
2. Update `sprint.status` to `review`
3. Hand off to @agentic-scrum:scrum:events:scrum-event-sprint-review
