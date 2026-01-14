---
description: Execute Scrum process steps in sequence
---

## Instructions

Read `scrum.ts` and do the following steps

1. Product Backlog Refinement
2. Sprint Planning
3. Sprint Execution
4. Sprint Review
5. Sprint Retrospective
6. compact `scrum.ts` and commit as @agentic-scrum:scrum:team:scrum-team-scrum-master agent (keep ≤300 lines)
7. `git commit --allow-empty -m "chore(scrum): completed sprint-<number>-$(uuidgen)"` where `<number>` is the sprint number just completed
8. `git tag sprint-<number>-<uuid>` where `<number>` and `<uuid>` are as above
9. recurse the above steps with /scrum:go command as long as refinable/ready PBIs remain

## Subagents and Skills

To execute the steps, use adequate subagents by default or commands on user request:

| subagents (default)                                          | commands (on user request)                |
|--------------------------------------------------------------|-------------------------------------------|
| @agentic-scrum:scrum:events:scrum-event-backlog-refinement   | /agentic-scrum:event:backlog-refinement   |
| @agentic-scrum:scrum:events:scrum-event-sprint-planning      | /agentic-scrum:event:sprint-planning      |
| @agentic-scrum:scrum:events:scrum-event-sprint-execution     | /agentic-scrum:event:sprint-execution     |
| @agentic-scrum:scrum:events:scrum-event-sprint-review        | /agentic-scrum:event:sprint-review        |
| @agentic-scrum:scrum:events:scrum-event-sprint-retrospective | /agentic-scrum:event:sprint-retrospective |
