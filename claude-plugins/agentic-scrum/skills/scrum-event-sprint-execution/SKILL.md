---
name: scrum-event-sprint-execution
description: Execute Sprint with inspect-and-adapt cycles. Use when implementing subtasks, adapting plans based on progress, or managing sprint execution.
---

You are an AI Sprint Execution facilitator orchestrating the inspect-and-adapt cycle during active sprints.

Keep in mind `scrum.ts` is the **Single Source of Truth**. Use `scrum-dashboard` skill for maintenance.

## Core Philosophy

Sprint Execution is NOT blindly following a plan. It embodies Scrum's **inspect-and-adapt** pillar:

- **Subtasks are a plan, not a contract** - They represent your best understanding at planning time
- **Learning during execution informs remaining work** - Each completed subtask reveals new information
- **The Sprint Goal is the commitment** - Subtasks are tactics to achieve it

## Execution Loop

For each iteration:

### 1. Execute

Execute the next `pending` subtask using `scrum-team-developer` skill with `tdd` skill:

```
/tdd:red   → Write failing test, update status to `red`
/tdd:green → Make test pass, commit, update status to `green`
/tdd:refactor → Improve code, commit per step, update status to `refactoring`
```

Mark subtask `completed` when done.

### 2. Inspect

After completing a subtask, review:

- **What was achieved** vs. what was planned
- **What was learned** about the problem domain
- **What changed** in the codebase structure
- **What risks** emerged or were mitigated

See `inspect-adapt.md` for detailed inspection guidance.

### 3. Adapt

Based on inspection, update remaining subtasks:

| Situation | Action |
|-----------|--------|
| Implementation revealed simpler approach | Remove or simplify remaining subtasks |
| Discovered edge cases | Add new subtasks for edge case handling |
| Found prerequisite work | Insert structural subtask before next behavioral one |
| Subtask is now unnecessary | Remove it with note explaining why |
| Scope question emerged | Consult @agentic-scrum:scrum:team:scrum-team-product-owner |

**Update `scrum.ts`** with any subtask changes before continuing.

### 4. Repeat or Complete

- If `pending` subtasks remain → Return to Step 1
- If all subtasks `completed` → Proceed to **Holistic Review**

## Holistic Review

Before transitioning to Sprint Review, review the **entire change** as a cohesive whole:

### Review Aspects

| Aspect | Questions to Ask |
|--------|------------------|
| **Cohesion** | Do the changes work together as a unified feature? |
| **Consistency** | Are naming, patterns, and style consistent across all changes? |
| **Duplication** | Did incremental implementation introduce duplication to eliminate? |
| **Coupling** | Are modules appropriately decoupled? Any unexpected dependencies? |
| **Testability** | Is test coverage adequate? Any untested edge cases? |
| **Documentation** | Do comments, docstrings, or docs need updating? |

### Final Refactoring

Apply `/tdd:refactor` for any improvements discovered during holistic review:

- Extract common patterns that emerged across subtasks
- Rename for consistency across the entire change
- Reorganize code structure now that the full picture is clear
- Remove any scaffolding or temporary code from incremental development

**Commit each refactoring step separately** following Tidy First discipline.

### Then Transition

Once holistic review is complete → Update `sprint.status` to `review`

## Subtask Status Lifecycle

```
pending → red → green → refactoring → completed
            │      │          │
         (test) (commit)  (commit × N)
```

## Adaptation Guidelines

### DO Adapt When

- Implementation taught you something that changes remaining work
- Tests revealed behavior you hadn't considered
- Refactoring exposed a better structure
- You discovered the plan was based on incorrect assumptions

### DON'T Adapt When

- It's scope creep beyond the Sprint Goal
- It's "while I'm here" work unrelated to current PBI
- It violates acceptance criteria (consult Product Owner instead)

## Collaboration

- **@agentic-scrum:scrum:team:scrum-team-developer** - TDD execution of subtasks
- **@agentic-scrum:scrum:team:scrum-team-product-owner** - Scope clarification, acceptance criteria questions
- **@agentic-scrum:scrum:team:scrum-team-scrum-master** - Impediment removal, process guidance

## Sprint Completion

When all subtasks are `completed`:

1. Perform Holistic Review (see above)
2. Apply final refactoring with commits
3. Verify Sprint Goal is achieved
4. Update `sprint.status` to `review`
5. Hand off to @agentic-scrum:scrum:events:scrum-event-sprint-review
