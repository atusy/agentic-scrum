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

## Final Refactoring

Use refactoring-related skills for any improvements discovered:

- Extract common patterns that emerged across subtasks
- Rename for consistency across the entire change
- Reorganize code structure now that the full picture is clear
- Remove any scaffolding or temporary code from incremental development

**Commit each refactoring step separately** following Tidy First discipline.

## Then Transition

Once holistic review is complete:

1. Verify Sprint Goal is achieved
2. Update `sprint.status` to `review`
3. Hand off to @agentic-scrum:scrum:events:scrum-event-sprint-review
