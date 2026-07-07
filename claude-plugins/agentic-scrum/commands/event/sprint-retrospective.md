---
description: Facilitate Sprint Retrospective to identify and execute improvements
---

# Task

Facilitate Sprint Retrospective so that the team identifies and executes the most helpful improvements

# Conversation

Run as a facilitated conversation (`scrum-conversation` skill):

* Ask **each role separately** what went well and what to improve, from its own incentive:
  - PO: did the sprint deliver the intended value? was the PBI well-refined?
  - Dev: where did the process create friction? what surprised you in the code?
* Cross-examine: let each role react to the other's observations before converging
* Converge on the **few most helpful** improvements (Impact/Effort); dissenting views on dropped proposals are recorded in the retrospective entry

# Skills

* `scrum-conversation` for the dialogue protocol
* `scrum-team-scrum-master` to follow scrum principles
* `scrum-event-sprint-retrospective` for retrospective guidance
* `scrum-dashboard` skill for dashboard maintenance guidance
