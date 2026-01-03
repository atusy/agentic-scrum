# Inspect and Adapt During Sprint Execution

This document provides guidance on the inspect-and-adapt cycle that distinguishes Sprint Execution from mere task completion.

## The Inspection Mindset

After each subtask, pause and reflect. Don't rush to the next subtask. The few moments spent inspecting often save significant rework later.

## What to Inspect

### Code Changes

- **Structure**: Did the implementation change the module/file structure?
- **Dependencies**: Were new dependencies introduced or removed?
- **Interfaces**: Did public APIs change in ways that affect other subtasks?
- **Patterns**: Did you establish patterns that subsequent subtasks should follow?

### Test Coverage

- **Edge cases**: Did tests reveal scenarios not covered by acceptance criteria?
- **Integration points**: Are there integration concerns the plan missed?
- **Test structure**: Is the test organization sustainable for remaining work?

### Design Implications

- **Simpler path**: Is there now a simpler way to achieve remaining subtasks?
- **Complexity**: Did complexity emerge that needs addressing before continuing?
- **Technical debt**: Was debt introduced that should be paid down now vs. later?

### Sprint Goal Progress

- **On track**: Is each subtask moving toward the Sprint Goal?
- **Blocked**: Are there impediments emerging?
- **Scope**: Is the remaining work still aligned with the PBI's acceptance criteria?

## When to Adapt

### Add Subtasks

```yaml
# Discovered edge case during implementation
- test: "Handle empty input gracefully"
  implementation: "Add early return for empty collections"
  type: behavioral
  status: pending

# Found prerequisite refactoring needed
- test: "N/A (structural)"
  implementation: "Extract validation logic before adding new validators"
  type: structural
  status: pending
```

### Modify Subtasks

When the original plan no longer makes sense:

```yaml
# Before: Overly complex approach
- test: "Parse complex nested JSON structure"
  implementation: "Build recursive parser with visitor pattern"

# After: Simpler approach discovered
- test: "Parse complex nested JSON structure"
  implementation: "Use existing library's streaming parser"
  notes: ["Adapted: Found simpler approach using existing dependency"]
```

### Remove Subtasks

When work is no longer needed:

```yaml
# Mark as completed with explanation (don't just delete)
- test: "Validate configuration schema"
  implementation: "Add JSON schema validation"
  type: behavioral
  status: completed
  notes: ["Removed: TypeScript already validates at compile time"]
```

### Reorder Subtasks

When dependencies change:

```yaml
# Move structural work before dependent behavioral work
subtasks:
  - { type: structural, ... }   # Was 3rd, now 1st
  - { type: behavioral, ... }   # Depends on above
  - { type: behavioral, ... }
```

## Preserving Sprint Goal

Adaptation must serve the Sprint Goal, not expand beyond it.

### Valid Adaptations

- Simplifying the path to the Sprint Goal
- Handling edge cases within the PBI's scope
- Fixing technical issues blocking progress
- Improving code quality for current changes

### Invalid Adaptations (Scope Creep)

- Adding features not in acceptance criteria
- "While I'm here" improvements to unrelated code
- Gold-plating beyond what's needed
- Work that belongs to a different PBI

**When in doubt**: Consult @agentic-scrum:scrum:team:scrum-team-product-owner before adapting.

## Recording Adaptations

Always document why you adapted in the subtask's `notes` array:

```yaml
notes:
  - "Adapted: Split into two subtasks after discovering separate concerns"
  - "Adapted: Added after edge case found in testing"
  - "Adapted: Removed - functionality already exists in utils module"
```

This creates a learning record for retrospectives.
