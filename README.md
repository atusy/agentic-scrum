# Agentic Scrum

**Scrum optimized for AI agents** — A framework where AI takes on Scrum roles (Developer, Product Owner, Scrum Master) to autonomously deliver software increments.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

## Getting Started

### For Claude Code Users

1. Use following prompts in Claude Code to add and install the plugin:

    ```
    /plugin marketplace add https://github.com/atusy/agentic-scrum 
    ```

    ```
    /plugin install agentic-scrum@agentic-scrum
    ```
2. Run `/scrum:init` in your project to create `scrum.ts`
3. Run `/scrum:go` to start autonomous development

## Why Agentic Scrum?

Traditional Scrum assumes human limitations: time-boxed sprints, velocity estimation, and synchronous ceremonies. AI agents don't have these constraints.

**Agentic Scrum adapts the framework:**

| Traditional Scrum | Agentic Scrum |
|-------------------|---------------|
| Sprint = 2-4 weeks | Sprint = 1 PBI (any duration) |
| Velocity planning | No estimation needed |
| Team ceremonies | Autonomous coordination |
| Sprint backlog items | Single focused goal |

The result: **continuous autonomous iteration** with all the benefits of Scrum's inspect-and-adapt loop.

## Core Concepts

### Single Source of Truth: `scrum.ts`

All Scrum artifacts live in one TypeScript file that AI agents read and write:

```typescript
const scrum: ScrumDashboard = {
  product_goal: { statement: "...", success_metrics: [...] },
  product_backlog: [...],      // Ordered by priority
  sprint: { goal: "...", subtasks: [...] },
  definition_of_done: { checks: [...] },
  completed: [...],            // Sprint history
  retrospectives: [...]        // Process improvements
};
```

### AI Agent Roles

```
┌─────────────────────────────────────────────────────────────┐
│                     SCRUM MASTER                            │
│           Facilitates • Enforces • Removes Impediments      │
└─────────────────────────────────────────────────────────────┘
        │                                       │
        ▼                                       ▼
┌───────────────────┐                 ┌───────────────────────┐
│   PRODUCT OWNER   │                 │      DEVELOPER        │
│                   │   ready PBI     │                       │
│  • Product Goal   │ ───────────────▶│  • TDD Cycle          │
│  • Backlog Order  │                 │  • RED → GREEN →      │
│  • Acceptance     │ ◀───────────────│    REFACTOR           │
│                   │   done PBI      │                       │
└───────────────────┘                 └───────────────────────┘
```

### Status Lifecycles

```
PBI:      draft → refining → ready → done
Sprint:   planning → in_progress → review → done
Subtask:  pending → red → green → refactoring → completed
                     │      │           │
                  (test) (commit)   (commit×N)
```

## Key Principles

- **1 Sprint = 1 PBI** — Maximize iteration speed
- **Order = Priority** — Array position determines importance
- **Git is History** — No timestamps in dashboard
- **Behavioral ↔ Structural** — Separate commits for features vs refactoring
- **Commits at GREEN only** — Never commit failing tests

## License

MIT © 2025 atusy
