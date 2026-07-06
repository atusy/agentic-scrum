---
description: Facilitate Product Backlog Refinement to make PBIs ready
---

# Task

Refine Product Backlog so that PBIs become ready for sprint planning

# Conversation

Run as a facilitated conversation (`scrum-conversation` skill):

* **PO leads**: proposes new/rewritten stories, splits, and ordering
* **Dev challenges**: feasibility, size, and whether acceptance criteria are executable
* Per PBI (up to 5 in `draft`/`refining`): PO proposes → Dev reacts → converge → record the decision and open questions in the PBI's `notes`
* A PBI becomes `ready` only when both roles `AGREE` it meets the Definition of Ready

# Skills

* `scrum-conversation` for the dialogue protocol
* `scrum-team-product-owner` to follow scrum principles
* `scrum-event-backlog-refinement` for refinement guidance
* `scrum-dashboard` skill for dashboard maintenance guidance
