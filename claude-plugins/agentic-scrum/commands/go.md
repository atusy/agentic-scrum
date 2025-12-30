---
description: Execute Scrum process steps in sequence
---

## Instructions

Read `scrum.ts` and do the following steps

1. Product Backlog Refinement
2. Sprint Planning
3. Sprint execution as scrum-team-developer following `tdd` skill
4. Sprint Review
5. Sprint Retrospective
6. compact `scrum.ts` and commit as scrum-team-scrum-master (keep ≤300 lines)
7. `git commit --allow-empty -m "chore(scrum): completed sprint-<number>-$(uuidgen)"` where `<number>` is the sprint number just completed
8. `git tag sprint-<number>-<uuid>` where `<number>` and `<uuid>` are as above
9. recurse the above steps with /scrum:go command as long as refinable/ready PBIs remain

## Skills and Subagents

To execute the steps, use adequate skills by default or subagents on user request:

| skills (default)                 | subagents (on user request)                                  |
|----------------------------------|--------------------------------------------------------------|
| scrum-event-backlog-refinement   | @agentic-scrum:scrum:events:scrum-event-backlog-refinement   |
| scrum-event-sprint-planning      | @agentic-scrum:scrum:events:scrum-event-sprint-planning      |
| scrum-event-sprint-retrospective | @agentic-scrum:scrum:events:scrum-event-sprint-retrospective |
| scrum-event-sprint-review        | @agentic-scrum:scrum:events:scrum-event-sprint-review        |
| scrum-team-developer             | @agentic-scrum:scrum:team:scrum-team-developer               |
| scrum-team-scrum-master          | @agentic-scrum:scrum:team:scrum-team-scrum-master            |
| scrum-team-product-owner         | @agentic-scrum:scrum:team:scrum-team-product-owner           |
