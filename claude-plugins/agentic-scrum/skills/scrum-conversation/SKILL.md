---
name: scrum-conversation
description: Run Scrum events as facilitated conversations between role agents (Product Owner, Developer, Scrum Master). Use when facilitating any Scrum event, assembling the team, or converging on decisions while recording dissent.
---

# Scrum Events as Conversations

Scrum events are conversations between roles with different incentives, not a checklist executed by one agent wearing every hat:

- **Product Owner** argues for value: outcome over output, smallest valuable slice
- **Developer** argues for simplicity: feasibility, small safe steps, YAGNI
- **Scrum Master** (the facilitator) guards the process: Definition of Ready/Done, Scrum values, convergence

When one agent plays all roles at once, disagreements silently resolve in favor of whatever that agent thought first. Forcing each role to speak from its own incentive surfaces trade-offs *before* they are decided.

## Team Setup (Persistent Role Agents)

The facilitator is the current conversation, wearing the Scrum Master hat (`scrum-team-scrum-master` skill).

Spawn each teammate **once per session** with the Agent tool, then continue the *same* agent with SendMessage so it keeps its context across events:

| Teammate | Agent | Context it accumulates |
|----------|-------|------------------------|
| PO | `@agentic-scrum:scrum:team:scrum-team-product-owner` | Why the backlog is ordered this way; what was accepted/rejected and why |
| Dev | `@agentic-scrum:scrum:team:scrum-team-developer` | Codebase learnings, technical risks discovered in earlier sprints |

Rules:

- First message introduces the session: "You are the Product Owner for this project. Read `scrum.ts` before answering."
- Never re-spawn a fresh agent when the conversation should build on earlier turns — use SendMessage to the existing one.
- Independent questions to different teammates may be sent in parallel.

## Turn Protocol

1. The facilitator poses **one focused question per turn**, with the minimum context needed to answer it.
2. The teammate answers from its role's incentive and **must end with a verdict line**:
   - `PROPOSE: <concrete proposal>`
   - `AGREE: <what is agreed>`
   - `OBJECT: <reason + counter-proposal>`
   - `NEED: <missing information or human input required>`
3. The facilitator routes verdicts: `PROPOSE` goes to the other role for reaction; `OBJECT` goes back to the proposer with the objection attached.

## Convergence Rules

- **Max 3 rounds per topic.** Still `OBJECT` after round 3 → the role with authority over the topic decides ("disagree and commit") and the dissent is recorded.
- `NEED` for information an agent can gather itself → gather it and continue the round.
- `NEED` for human input → record it (PBI `notes` or `sprint.impediments`) and move to the next topic; never fabricate an answer.
- Conversation does not change authority: the PO decides value, ordering, and acceptance; the Developer decides implementation approach; the facilitator only breaks process deadlocks.

## Minutes

Conversations are ephemeral; decisions are not. Record outcomes in `scrum.ts`:

- `sprint.decisions`: key decisions with a one-line rationale, **including overruled objections** — e.g. `"Dev objected: adds a dependency; PO decided to proceed because time-to-value outweighs it"`
- PBI `notes`: refinement decisions and open questions
- Commit the dashboard after the event, explaining the WHY in the commit message body

## Fallback: Inline Role-Play

When Agent/SendMessage are unavailable (e.g. the event runs inside a subagent), simulate the conversation inline, labeling every turn:

```
PO:  The top story bundles export and import. PROPOSE: split at export-only.
DEV: Export alone is demonstrable, import needs schema work anyway. AGREE: split at export-only.
```

Same protocol, same convergence rules, same minutes. The essential property — each role speaks from its own incentive before anything is decided — survives the loss of real isolation.
