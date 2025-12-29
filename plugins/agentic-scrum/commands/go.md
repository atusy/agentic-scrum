---
description: Execute Scrum process steps in sequence
---

Read `scrum.ts` and do the following steps

1. let @agentic-scrum:scrum:events:scrum-event-backlog-refinement agent refine the Product Backlog
2. let @agentic-scrum:scrum:events:scrum-event-sprint-planning agent plan the Sprint
3. let @agentic-scrum:scrum:team:scrum-team-developer agent do sprint execution with `tdd` skill
4. let @agentic-scrum:scrum:events:scrum-event-sprint-review agent review the Sprint
5. let @agentic-scrum:scrum:events:scrum-event-sprint-retrospective agent do the Retrospective
6. let @agentic-scrum:scrum:team:scrum-team-scrum-master do `scrum.ts` compaction (keep ≤300 lines)
7. recurse the above steps with /scrum:go command as long as refinable/ready PBIs remain
