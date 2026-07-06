---
description: Execute Sprint through TDD-based inspect-and-adapt cycles
---

# Task

Execute Sprint so to deliver increment through disciplined TDD-based inspect-adapt cycles

## Sprint Workflow

### Tidy first

1. Do tidy first refactoring to prepare upcoming changes

### Do subtasks

#### Starting a Subtask

1. Find next `pending` subtask in dashboard
2. Inspect and adapt the detail to the current situation
3. Update status to `red` when writing test
4. Begin TDD cycle with `/tdd:red`

#### Completing a Subtask

1. Ensure all tests pass
2. Update status to `completed` in dashboard
3. Move to next subtask

### Ensure all changes are wired

1. Verify new code is actually called from existing code paths
2. If not wired: add subtasks to integrate, or remove unused code (YAGNI)
3. Return to **Do subtasks** if new subtasks were added

### Inspect and adapt the changes

1. Ask subagents to perform strict multi-perspective reviews
2. Fact-check the review findings against actual code
3. Adapt based on verified issues
4. Repeat until confident (minimum 3 cycles)

### Comprehensive Refactoring

1. Ask subagents to identify refactoring opportunities
2. Fact-check proposed refactorings for validity
3. Apply refactorings using `/tdd:refactor` or `refactoring` skill
4. Repeat until code quality is satisfactory (minimum 3 cycles)

### Completing the Sprint
1. All subtasks marked `completed`
2. Run all acceptance criteria verification commands
3. Run Definition of Done checks
4. Update `sprint.status` to `done`
5. Notify @agentic-scrum:scrum:team:scrum-team-product-owner for acceptance

# Skills

* `scrum-team-developer` for TDD implementation
* `scrum-event-sprint-execution` for execution guidance
* `scrum-dashboard` skill for dashboard maintenance guidance
