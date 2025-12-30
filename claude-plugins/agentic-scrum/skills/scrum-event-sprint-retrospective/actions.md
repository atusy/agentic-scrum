# Improvement Actions

## Common improvement categories for AI-Agentic Scrum retrospectives.

### Prompt Engineering

Improve how AI agents receive and interpret instructions.

| Signal | Action |
|--------|--------|
| Agent misunderstood requirements | Clarify skill descriptions or acceptance criteria format |
| Agent made avoidable mistakes | Add anti-patterns or examples to relevant skill |
| Agent asked unnecessary questions | Pre-answer common questions in CLAUDE.md or skills |
| Agent took suboptimal approach | Add decision guidance or preferred patterns |

### Testing & Verification

Strengthen the safety net for future sprints.

| Signal | Action |
|--------|--------|
| Bug escaped to completion | Add e2e test covering the scenario |
| Manual verification was needed | Automate verification command |
| Flaky tests caused confusion | Fix or quarantine unreliable tests |
| Coverage gaps discovered | Add unit tests for uncovered paths |

### Process Adaptation

Tune Scrum artifacts and events to the project.

| Signal | Action |
|--------|--------|
| PBIs frequently need re-refinement | Update Definition of Ready criteria |
| Acceptance criteria ambiguous | Add project-specific examples to refinement skill |
| Subtasks too large/small | Adjust subtask guidelines in sprint planning skill |
| Sprint Review found gaps | Strengthen Definition of Done |

### Tooling & Automation

Reduce friction and manual steps.

| Signal | Action |
|--------|--------|
| Repeated manual commands | Add to Definition of Done or pre-commit hooks |
| Slow feedback loops | Optimize CI/CD or add local checks |
| Missing development tools | Add setup instructions to CLAUDE.md |
| Error-prone deployments | Automate deployment steps |

### Knowledge Capture

Preserve learnings for future sprints.

| Signal | Action |
|--------|--------|
| Had to research same topic twice | Document in CLAUDE.md or ADR |
| External API behavior unclear | Add integration notes |
| Architectural decision implicit | Create or update ADR |
| Onboarding friction | Improve README or setup docs |

## Implementing Actions

**Do not disturb existing configurations.** When adding improvements:

| Existing Setup | Correct Approach |
|----------------|------------------|
| Global git hooks | Local hooks should call global hooks first, then add project-specific checks |
| Shared CI/CD templates | Extend or override specific steps, don't replace entire pipelines |
| Team-wide CLAUDE.md | Add project-specific sections, don't remove inherited guidance |
| Common test utilities | Import and extend, don't duplicate |

**Principle**: Improvements should be **additive**. If you must modify shared configurations, verify the change doesn't break other projects or workflows.

## Choosing Actions

Use **Impact/Effort Matrix** to prioritize:

```
        High Impact
             │
   Quick     │    Strategic
   Wins ◄────┼────► Investments
             │
   ──────────┼──────────
             │
   Fill      │    Avoid
   Time ◄────┼────► (or defer)
             │
        Low Impact
```

**Prefer**: Quick Wins (high impact, low effort) first.
