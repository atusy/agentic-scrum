---
description: Run Sprint Review to verify the increment and decide acceptance
---

# Task

Run Sprint Review so that the increment is verified against Definition of Done and acceptance criteria

# Conversation

Run as a facilitated conversation (`scrum-conversation` skill):

* **Dev demonstrates**: what the increment does (achievement, not activity), with DoD and acceptance-criteria evidence from actually executed commands
* **Facilitator re-runs**: independently re-executes the verification commands (the PO deliberately has no Bash — it judges, it does not execute) and hands the PO the transcripts
* **PO inspects**: probes the demo and transcripts from the user's perspective, then decides `AGREE` (accept) or `OBJECT` (reject with specifics)
* **Both adapt**: feedback that is out of scope becomes new `draft` PBIs, never scope creep in this sprint

Acceptance is the PO's decision alone; the PO records the rationale in `sprint.decisions`. The outcome must leave the dashboard in one of the states the `/agentic-scrum:go` loop branches on — apply the `scrum-event-sprint-review` skill's Failure Handling:

- **AGREE (accept)**: PBI → `done`, sprint → `done`, Sprint object → `completed`, `scrum.sprint` → `null`
- **OBJECT, minor fix**: set sprint back to `in_progress`, add fix subtask(s) — execution re-runs, then Review again
- **OBJECT, Sprint Goal unachievable**: scope-reduce, or cancel (sprint → `cancelled`, archive, `scrum.sprint` → `null`, PBI → `refining`)

# Skills

* `scrum-conversation` for the dialogue protocol
* `scrum-team-scrum-master` for facilitation
* `scrum-event-sprint-review` for review guidance
* `scrum-dashboard` skill for dashboard maintenance guidance
