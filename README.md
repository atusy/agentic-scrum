[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

🚧WIP🚧 **This project is under active development.** Expect breaking changes.

# 🤖 Agentic Scrum

**Scrum optimized for AI agents** for stable autonomous software development.

## 🚀 Getting Started

Optional dependencies: deno

### For Claude Code Users

1. Use following prompts in Claude Code to add and install the plugin:

    ```
    /plugin marketplace add https://github.com/atusy/agentic-scrum
    ```

    ```
    /plugin install agentic-scrum@agentic-scrum
    ```
2. Run `/agentic-scrum:init` in your project to create `scrum.ts`
3. Prompt Claude Code to add a TODO in `scrum.ts` (i.e., PBI)
4. Run `/agentic-scrum:go` to start autonomous development

## 💡 Why Agentic Scrum?

Stable autonomous software development requires a structured process:

* 🧩 **Incremental decomposition** — Split the backlog into vertical, end-to-end slices (PBIs that each deliver value); break each slice into TDD subtasks *within* the sprint (never split PBIs by technical layer)
* 🔍 **Continuous quality inspection** — Verify completed functionality meets standards
* 🔄 **Adaptive prompting** — Evolve instructions based on what works

Scrum provides exactly this structure, and AI agents understand it well.

**Why adapt Scrum?** Traditional Scrum assumes human limitations: time-boxed sprints, sprint point estimation, and synchronous ceremonies. AI agents don't have these constraints.

**Agentic Scrum adapts the framework:**

| Traditional Scrum | Agentic Scrum |
|-------------------|---------------|
| 📅 Sprint = 2-4 weeks | ⚡ Sprint = 1 PBI (any duration) |
| 📊 Velocity planning | 🚫 No estimation needed |
| 👥 Team ceremonies | 🗣️ Agent-to-agent conversations |
| 📋 Sprint backlog items | 🎯 Single focused goal |

The result: **continuous autonomous iteration** with all the benefits of Scrum's inspect-and-adapt loop.

## 🏗️ Core Concepts

### 📄 Single Source of Truth: `scrum.ts`

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

### 🎭 AI Agent Roles

```
┌─────────────────────────────────────────────────────────────┐
│                  🧭 SCRUM MASTER                            │
│           Facilitates • Enforces • Removes Impediments      │
└─────────────────────────────────────────────────────────────┘
        │                                       │
        ▼                                       ▼
┌───────────────────┐                 ┌───────────────────────┐
│  📋 PRODUCT OWNER │                 │    💻 DEVELOPER       │
│                   │   ready PBI     │                       │
│  • Product Goal   │ ───────────────▶│  • TDD Cycle          │
│  • Backlog Order  │                 │  • RED → GREEN →      │
│  • Acceptance     │ ◀───────────────│    REFACTOR           │
│                   │   done PBI      │                       │
└───────────────────┘                 └───────────────────────┘
```

### 🗣️ Events are Conversations

Scrum events run as **facilitated conversations between role agents**, not a checklist executed by one agent wearing every hat:

- The **Scrum Master** (main conversation) facilitates; **PO** and **Developer** are persistent agents that keep their context across events — the PO remembers *why* the backlog is ordered, the Developer remembers what it learned in the code
- Each role argues from its own incentive (PO: value, Dev: simplicity) and ends every turn with a verdict: `PROPOSE` / `AGREE` / `OBJECT` / `NEED`
- Max 3 rounds per topic, then disagree-and-commit — with the dissent recorded in `scrum.ts` (`sprint.decisions`)

### 🔄 Status Lifecycles

```
PBI:      draft → refining → ready → done
Sprint:   planning → in_progress → review → done | cancelled
Subtask:  pending → 🔴 red → 🟢 green → 🔧 refactoring → ✅ completed
                     │        │              │
                  (test)  (commit)      (commit×N)
```

## 📌 Key Principles

- ⚡ **1 Sprint = 1 PBI** — Maximize iteration speed
- 📊 **Order = Priority** — Array position determines importance
- 🗂️ **Git is History** — No timestamps in dashboard
- 🔀 **Behavioral ↔ Structural** — Separate commits for features vs refactoring
- ✅ **Commits at GREEN only** — Never commit failing tests

## 📜 License

MIT © 2025 atusy
