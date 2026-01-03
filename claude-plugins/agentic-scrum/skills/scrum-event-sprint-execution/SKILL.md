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

### 2. Inspect & Adapt (Daily Scrum)

This phase fulfills the Daily Scrum's purpose in AI-Agentic Scrum: inspect progress and adapt the plan. In continuous AI execution, this happens after each subtask rather than once per day.

#### Subtask-Level Inspection

Review what the completed subtask revealed:

- **What was achieved** vs. what was planned
- **What was learned** about the problem domain
- **What changed** in the codebase structure
- **What risks** emerged or were mitigated

#### Sprint Goal Progress Check

Step back and assess the bigger picture:

- **Are we on track** toward the Sprint Goal?
- **Is remaining work** still the right path, or should we re-prioritize?
- **Are there impediments** blocking progress?

If impediments exist, report to @agentic-scrum:scrum:team:scrum-team-scrum-master:
```yaml
# Add to scrum.ts sprint.impediments
impediments:
  - description: "What is blocking progress"
    impact: "How it affects Sprint Goal"
    reported_at_subtask: "subtask description"
```

See `inspect-adapt.md` for detailed inspection guidance.

#### Adapt the Plan

Based on inspection, update remaining subtasks:

| Situation | Action |
|-----------|--------|
| Implementation revealed simpler approach | Remove or simplify remaining subtasks |
| Discovered edge cases | Add new subtasks for edge case handling |
| Found prerequisite work | Insert structural subtask before next behavioral one |
| Subtask is now unnecessary | Remove it with note explaining why |
| Scope question emerged | Consult @agentic-scrum:scrum:team:scrum-team-product-owner |

**Update `scrum.ts`** with any subtask changes before continuing.

### 3. Repeat or Complete

- If `pending` subtasks remain → Return to Step 1
- If all subtasks `completed` → Proceed to **Holistic Review**

## Holistic Review

Before transitioning to Sprint Review, review the **entire change** as a cohesive whole. See `holistic-review.md` for detailed guidance.

## Subtask Status Lifecycle

```
pending → red → green → refactoring → completed
            │      │          │
         (test) (commit)  (commit × N)
```

## Collaboration

- **@agentic-scrum:scrum:team:scrum-team-developer** - TDD execution of subtasks
- **@agentic-scrum:scrum:team:scrum-team-product-owner** - Scope clarification, acceptance criteria questions
- **@agentic-scrum:scrum:team:scrum-team-scrum-master** - Impediment removal, process guidance

## Sprint Completion

When all subtasks are `completed`:

1. Perform Holistic Review (see `holistic-review.md`)
2. Update `sprint.status` to `review`
3. Hand off to @agentic-scrum:scrum:events:scrum-event-sprint-review
