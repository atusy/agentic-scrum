---
name: scrum-dashboard
description: Maintain scrum.ts dashboard following Agentic Scrum principles. Use when reading and editing scrum.ts, updating sprint status, or managing Product Backlog.
---

## Core Principles

| Principle | Practice |
|-----------|----------|
| **Single Source of Truth** | All Scrum artifacts live in `scrum.ts` |
| **Git is History** | Commit every meaningful change on `scrum.ts` to track the background context and to make timestamps unneeded |
| **Order is Priority** | Higher in `product_backlog` array = higher priority |
| **Schema is Fixed** | Only edit the data section; request human review for type changes |

## Editing Rules

- **`scrum.ts` is TypeScript, not YAML.** Some skills show snippets in YAML for readability; translate them to TypeScript object syntax (quoted strings, `[]` arrays) when writing the file.
- **Register user-story roles first.** `story.role` is typed against the `userStoryRoles` tuple at the top of the file. Before writing (or refining) a PBI whose role is not already listed, add that role string to `userStoryRoles` — otherwise `deno check` fails with a `never`-type error. Prune obsolete roles freely.

## Validation

```bash
deno check scrum.ts          # Type check after edits
deno run scrum.ts | jq '.'   # Query data as JSON
wc -l scrum.ts               # Line count (target: ≤300, hard limit: 600)
```

## Compaction

After retrospective, prune if >300 lines:
- `completed`: Keep latest 2-3 sprints only; empty their `impediments`/`decisions` and nested subtask `notes`/`commits` (git history keeps them)
- `retrospectives`: Remove `completed`/`abandoned` improvements
- `product_backlog`: Remove `done` PBIs

## Integration

- `/agentic-scrum:init` - Create new dashboard
    - Use `scrum.template.ts` in this skill directory as the starting point for new dashboards.
- `/agentic-scrum:event:*` commands - Sprint events as team conversations (`@agentic-scrum:scrum:events:*` agents as delegation fallback)
