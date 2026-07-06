---
description: Run Sprint Review to verify the increment and decide acceptance
---

# Task

Run Sprint Review so that the increment is verified against Definition of Done and acceptance criteria

# Conversation

Run as a facilitated conversation (`scrum-conversation` skill):

* **Dev demonstrates**: what the increment does (achievement, not activity), with DoD and acceptance-criteria evidence from actually executed commands
* **PO inspects**: re-runs verification commands, probes the demo from the user's perspective, then decides `AGREE` (accept) or `OBJECT` (reject with specifics)
* **Both adapt**: feedback that is out of scope becomes new `draft` PBIs, never scope creep in this sprint

Acceptance is the PO's decision alone; record it with rationale in `sprint.decisions`.

# Skills

* `scrum-conversation` for the dialogue protocol
* `scrum-team-product-owner` to follow scrum principles
* `scrum-event-sprint-review` for review guidance
* `scrum-dashboard` skill for dashboard maintenance guidance
