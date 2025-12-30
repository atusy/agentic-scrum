## Retrospective Format in scrum.ts

```yaml
retrospectives:
  - sprint: 1
    improvements:
      - action: "Add pre-commit hook for linting"
        timing: immediate  # immediate | sprint | product
        status: completed  # active | completed | abandoned
        outcome: "Reduced lint errors"
```

Timing field guides when to execute:

| Timing | When to Execute | Examples |
|--------|-----------------|----------|
| `immediate` | During Retro | Update CLAUDE.md, skills, DoD, templates |
| `sprint` | Next Sprint subtask | Documentation, test helpers |
| `product` | New PBI in backlog | Automation, CI/CD |

**`immediate` constraints**: NO production code, single logical change.
