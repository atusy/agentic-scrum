# Increment

In AI-Agentic Scrum, an **Increment** is the outcome of a completed Sprint: a single PBI that delivers **observable, user-facing value** as working software.

## Why Increment Matters for Backlog Refinement

The Increment concept is the **validation gate** for refinement. A PBI cannot reach `ready` status unless it will produce a valid Increment when completed.

During refinement, always ask:

> "When this PBI is done, what working software can we demonstrate to stakeholders?"

If the answer is "nothing visible yet" or "it enables future work," the PBI is **not ready** — it needs to be merged with a value-delivering PBI.

## What Makes a Valid Increment

A valid Increment must be:

| Criterion | Description |
|-----------|-------------|
| **Observable** | Users/stakeholders can see, use, or experience the benefit |
| **Standalone** | Delivers value WITHOUT requiring another PBI to complete first |
| **Demonstrable** | Can be shown at Sprint Review as working software |
| **Complete** | Passes all acceptance criteria AND Definition of Done checks |

### Valid Increment Examples

```
✅ "User can view their order history"
   → Observable: user sees orders on screen
   → Standalone: works without other features
   → Demonstrable: can show the order list

✅ "System sends email notification when payment fails"
   → Observable: user receives email
   → Standalone: payment system already exists
   → Demonstrable: trigger failure, show email

✅ "Admin can export user data as CSV"
   → Observable: admin downloads file
   → Standalone: export works independently
   → Demonstrable: click export, show CSV
```

## What is NOT a Valid Increment

Work that **cannot be demonstrated as user-facing value** on its own:

| Anti-Pattern | Why Invalid | Resolution |
|--------------|-------------|------------|
| Dependency library added | No user sees the library | Merge with feature that uses it |
| Interface/type definitions | Code structure, not behavior | Include in the feature PBI |
| Database schema created | Infrastructure, not value | Bundle with feature reading/writing data |
| Tests written | Verification, not value | Tests are part of PBI subtasks, not separate PBIs |
| Refactoring completed | Structural change, not behavioral | Do as "Tidy First" within feature PBI |
| CI/CD pipeline configured | DevOps tooling | Not a PBI; add as Definition of Done check |
| Logging/monitoring added | Developer tooling | Bundle with feature or add to DoD |

### Invalid Increment Examples

```
❌ "Backend developer wants HTTP client added"
   → Problem: Preparation for future work, not user value
   → Fix: Merge with "User can fetch external data" PBI

❌ "DevOps engineer wants CI/CD configured"
   → Problem: Infrastructure without user-facing benefit
   → Fix: Not a PBI; implement as project setup

❌ "Tech lead wants authentication module refactored"
   → Problem: Structural improvement, no new user capability
   → Fix: Perform refactoring as "Tidy First" during a feature Sprint

❌ "QA wants integration tests for payment flow"
   → Problem: Tests alone aren't demonstrable to users
   → Fix: Tests are subtasks within a behavioral PBI
```

## The Increment Test

Before marking a PBI as `ready`, apply this test:

```
┌─────────────────────────────────────────────────────────────┐
│                    INCREMENT VALIDATION                     │
├─────────────────────────────────────────────────────────────┤
│ 1. Can we show working software at Sprint Review?           │
│    YES → Continue                                           │
│    NO  → Merge with a value-delivering PBI                  │
│                                                             │
│ 2. Does a user/stakeholder benefit DIRECTLY?                │
│    YES → Continue                                           │
│    NO  → This is infrastructure; bundle or add to DoD       │
│                                                             │
│ 3. Does it work WITHOUT another PBI completing first?       │
│    YES → Valid Increment ✓                                  │
│    NO  → Resolve dependency or merge PBIs                   │
└─────────────────────────────────────────────────────────────┘
```

## Increment and INVEST

The Increment concept enforces the **V (Valuable)** principle in INVEST:

> **Valuable**: Every PBI must produce a valid Increment — observable, user-facing benefit that can be demonstrated as working software.

A PBI that fails the Increment test **cannot satisfy INVEST** and therefore **cannot be `ready`**.

## Structural Work and Increments

Structural improvements (refactoring, dependencies, infrastructure) are essential but are **not Increments**. Handle them as:

1. **Subtasks** — Structural work within a behavioral PBI (preferred)
2. **Tidy First** — Refactoring before a behavioral change
3. **Definition of Done** — Infrastructure requirements for all PBIs

This ensures every Sprint produces demonstrable value while still allowing necessary technical work.
