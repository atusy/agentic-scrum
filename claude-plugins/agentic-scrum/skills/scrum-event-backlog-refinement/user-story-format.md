# User Story Format

Format: **"As a [role], I want [capability], so that [benefit]"**

## Follow Ron Jeffries' 3C Principle

- **Card**: Story captured briefly (AI-Agentic: User Story in `scrum.ts`)
- **Conversation**: Details drawn out through refinement (AI-Agentic: autonomous codebase exploration)
- **Confirmation**: Acceptance tests confirm correct implementation (AI-Agentic: executable verification commands)

## Practices for Writing Valid User Stories

### Role: Use Specific Personas

❌ **Avoid generic roles** like "user" or "developer" - they hide context and intent.

✅ **Use specific personas** that reveal who needs this and why:

| Generic (Avoid) | Specific (Use) |
|-----------------|----------------|
| user | returning customer, first-time visitor, mobile shopper |
| developer | plugin developer, frontend developer, on-call engineer |
| admin | store manager, content editor, system administrator |

**Ask**: Who exactly needs this? What's their context?

### Capability: Focus on Need, Not Solution

❌ "I want a dropdown menu" (specifies solution)
✅ "I want to select my preferred language" (describes need)

**Ask**: What does the persona need to accomplish? (Not how)

### Benefit: Describe Observable Outcomes

❌ "so that we can make API calls" (enabled capability - just preparation)
✅ "so that I can track past purchases" (observable outcome - real value)

| Invalid Benefit (Avoid) | Valid Benefit (Use) |
|-------------------------|---------------------|
| "so that we can persist data" | "so that I don't lose my progress" |
| "so that deployments are automated" | "so that I get fixes within hours, not days" |
| "so that we have contracts" | "so that I see type errors before runtime" |

**Test**: Can this benefit be demonstrated at Sprint Review?

## Complete Examples

**Invalid** (merge with features):
- ❌ "As a backend developer, I want database schema created, so that we can store data"
- ❌ "As a DevOps engineer, I want CI/CD configured, so that deployments are automated"

**Valid**:
- ✅ "As a returning customer, I want to view my order history, so that I can track past purchases"
- ✅ "As a mobile shopper, I want the checkout button to work, so that I can complete purchases on my phone"
- ✅ "As a plugin developer, I want builds to complete in under 30 seconds, so that I get faster feedback on my changes"
- ✅ "As an on-call engineer, I want errors reported automatically, so that I fix issues before users report them"
