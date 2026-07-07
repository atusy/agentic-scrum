---
description: Execute Scrum process steps in sequence
---

## Setup

1. Read `scrum.ts` (use `scrum-dashboard` skill)
2. Assemble the persistent team following the `scrum-conversation` skill:
   - Spawn `@agentic-scrum:scrum:team:scrum-team-product-owner` and `@agentic-scrum:scrum:team:scrum-team-developer` **once**
   - Continue the same agents with SendMessage across all events so they accumulate context (PO remembers backlog rationale; Dev remembers codebase learnings)
3. You facilitate as Scrum Master (`scrum-team-scrum-master` skill)

## Sprint Loop

Repeat while refinable or `ready` PBIs remain:

1. **Backlog Refinement** — run `/agentic-scrum:event:backlog-refinement` as a team conversation. If no `ready` PBI results (all remaining items are stuck in `refining` awaiting human input), apply the Stop Conditions instead of continuing.
2. **Sprint Planning** — run `/agentic-scrum:event:sprint-planning` as a team conversation (selects the top `ready` PBI)
3. **Sprint Execution** — delegate to `@agentic-scrum:scrum:events:scrum-event-sprint-execution` (fresh subagent per sprint keeps heavy implementation out of the facilitator's context); when it surfaces scope questions, relay them to the PO teammate
4. **Sprint Review** — run `/agentic-scrum:event:sprint-review` as a team conversation, then branch on the outcome:
   - **Accepted** (`scrum.sprint` cleared, sprint `done`) → continue to Retrospective
   - **Minor fix** (Review set the sprint back to `in_progress` and added fix subtasks) → return to step 3 (Execution) and re-run Review; do **not** advance to Retrospective yet
   - **Cancelled** (`scrum.sprint` cleared, sprint `cancelled`) → continue to Retrospective to analyze the root cause
5. **Sprint Retrospective** — run `/agentic-scrum:event:sprint-retrospective` as a team conversation
6. **Bookkeeping** (Scrum Master):
   1. compact `scrum.ts` (keep ≤300 lines) and commit any dashboard changes
   2. `git commit --allow-empty -m "chore(scrum): completed sprint-<number>"` where `<number>` is the sprint just completed
   3. `git tag "sprint-<number>-$(git rev-parse --short HEAD)"`

## Stop Conditions

Stop the loop and report to the user when:

- No `ready` PBIs remain and refinement cannot make more ready without human input
- A `NEED: human input` verdict or a `waiting_human` impediment blocks progress
- Repeated failures suggest the process itself needs human attention

On stopping, summarize: sprints completed, increment(s) delivered, current backlog state, and exactly what human input is needed.

## Delegating Whole Events

Conversational events run in the main conversation by default so the persistent team can participate. On user request, delegate an entire event to its subagent instead (it will use the inline role-play fallback of `scrum-conversation`):

| subagent (on user request)                                    | command (default)                          |
|---------------------------------------------------------------|--------------------------------------------|
| @agentic-scrum:scrum:events:scrum-event-backlog-refinement    | /agentic-scrum:event:backlog-refinement    |
| @agentic-scrum:scrum:events:scrum-event-sprint-planning       | /agentic-scrum:event:sprint-planning       |
| @agentic-scrum:scrum:events:scrum-event-sprint-execution      | /agentic-scrum:event:sprint-execution      |
| @agentic-scrum:scrum:events:scrum-event-sprint-review         | /agentic-scrum:event:sprint-review         |
| @agentic-scrum:scrum:events:scrum-event-sprint-retrospective  | /agentic-scrum:event:sprint-retrospective  |

Exception: **Sprint Execution defaults to its subagent** as described in the Sprint Loop.
