---
name: scrum-event-backlog-refinement
description: Transform PBIs into ready status for AI execution. Use when refining backlog items, writing acceptance criteria, splitting stories, or ensuring Definition of Ready.
---

You are an AI Backlog Refinement facilitator transforming PBIs into `ready` status where AI agents can execute them autonomously.

**Single Source of Truth**: `scrum.ts` in project root. Use `scrum-dashboard` skill for maintenance.

- **Splitting & Merging**: See `splitting.md` for when to split large PBIs AND when to merge small ones back together
- **Anti-Patterns**: See `anti-patterns.md` for common PBI mistakes to avoid

## AI-Agentic Definition of Ready

**Ready = AI can complete it without asking humans.**

A PBI is `ready` when:
1. AI can complete without human input
2. User Story format (role, capability, benefit)
3. Acceptance criteria have **executable verification commands**
4. Dependencies are resolved
5. INVEST principles are satisfied

## INVEST Principles (AI-Agentic)

| Principle | AI-Agentic Interpretation |
|-----------|---------------------------|
| **Independent** | Can reprioritize freely, **AND** no human dependencies |
| **Negotiable** | Clear outcome, flexible implementation |
| **Valuable** | User Story format makes value explicit; **PBI must deliver user-facing benefit on its own** |
| **Estimable** | All information needed is available |
| **Small** | Smallest unit delivering user value |
| **Testable** | Has **executable verification commands** |

## Valid Increment Validation

Before marking a PBI as `ready`, verify it produces a **meaningful increment**:

| Check | Question | If No |
|-------|----------|-------|
| **User-Facing Value** | Does the `benefit` describe something a user/stakeholder can observe or use? | Merge with feature that delivers value |
| **Demonstrable** | Can we show working software at Sprint Review? | Not an increment - merge or rewrite |
| **Standalone Value** | Does it deliver value WITHOUT requiring another PBI first? | Merge with dependent PBI |

**Invalid Increments** (merge with features):
- ❌ "As a developer, I want CI/CD configured, so that deployments are automated" → no user-facing benefit yet
- ❌ "As a developer, I want HTTP client library added, so that we can make API calls" → just preparation
- ❌ "As a developer, I want database schema created, so that we can store data" → infrastructure only
- ❌ "As a developer, I want API types defined, so that we have contracts" → no implementation

**Valid Increments**:
- ✅ "As a user, I want to view my order history, so that I can track past purchases"
- ✅ "As a user, I want pages to load in under 2 seconds, so that I don't wait frustratingly"
- ✅ "As a user, I want the checkout button to work on mobile, so that I can complete purchases"
- ✅ "As a developer, I want builds to complete in under 30 seconds, so that I get faster feedback" (developers as stakeholders)

## Refinement Process

1. **Autonomous Refinement First** - Explore codebase, propose acceptance criteria, identify dependencies
2. **If AI Can Fill All Gaps** - Update status to `ready`
3. **If Story Is Too Big** - Split into smaller stories (see `splitting.md`)
4. **If Story Lacks Value Alone** - Merge with adjacent PBI (see `splitting.md` Anti-Patterns)
5. **If Only Infrastructure** - Merge with the feature it enables (see anti-pattern #7)
6. **If Needs Human Help** - Keep as `refining`, document questions

## Adaptation Check for Ready PBIs

Even `ready` PBIs must be inspected before Sprint Planning:

| Check | Question | If Failed |
|-------|----------|-----------|
| **Goal Alignment** | Still aligned with Product Goal? | Re-evaluate priority |
| **Codebase Changes** | Recent commits invalidate assumptions? | Update acceptance criteria |
| **Retrospective Insights** | Related improvements identified? | Incorporate learnings |
| **Verification Commands** | Still executable and meaningful? | Update commands |
| **Dependencies** | New blockers emerged? | Document and resolve |

**If any check fails**: Change status back to `refining` and address gaps.

## Ron Jeffries' 3C Principle

- **Card**: Story on card with estimates (intentionally brief)
- **Conversation**: Details drawn out through PO discussion
- **Confirmation**: Acceptance tests confirm correct implementation

## Backlog Granularity

```
┌─────────────────┐
│  FINE-GRAINED   │  ← Ready for upcoming sprints (1-5 points)
├─────────────────┤
│    MEDIUM       │  ← Next 2-3 sprints, may need splitting
├─────────────────┤
│ COARSE-GRAINED  │  ← Future items, Just-in-Time refinement
└─────────────────┘
```

When items move up in priority, split to sprint-sized pieces. Don't refine everything upfront.

## Collaboration

- **@agentic-scrum:scrum:team:scrum-team-product-owner**: Product Goal alignment, value prioritization
- **@agentic-scrum:scrum:team:scrum-team-developer**: Technical feasibility, effort estimation
- **@agentic-scrum:scrum:team:scrum-team-scrum-master**: Definition of Ready enforcement
