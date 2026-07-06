---
description: Facilitate Sprint Planning to define Sprint Goal and subtasks
---

# Task

Facilitate Sprint Planning so that the team has a clear Sprint Goal and subtask breakdown

# Conversation

Run as a facilitated conversation (`scrum-conversation` skill), one topic at a time:

1. **WHY — Sprint Goal**: PO proposes the top `ready` PBI and the value it delivers; Dev confirms readiness or objects with what is missing
2. **WHAT — Scope**: PO and Dev agree what will be demonstrated at Sprint Review (work backwards from the demo)
3. **HOW — Subtasks**: Dev proposes the TDD subtask breakdown; PO checks each subtask still serves the Sprint Goal; facilitator checks Tidy-First/TDD discipline

Record the Sprint Goal rationale and any overruled objections in `sprint.decisions`.

# Skills

* `scrum-conversation` for the dialogue protocol
* `scrum-team-scrum-master` to follow scrum principles
* `scrum-team-developer` for subtask breakdown
* `scrum-event-sprint-planning` for planning guidance
* `scrum-dashboard` skill for dashboard maintenance guidance
