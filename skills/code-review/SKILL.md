---
name: code-review
description: Performs JavaScript, TypeScript, and C# code review with depth proportional to risk
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: code-review
  languages: js-ts,csharp
---

## What I do

I perform code reviews by analyzing:

1. Security
2. Performance
3. Quality
4. Logic
5. Tests

## When to use me

Use this skill when:

- You need to review code before merge
- You want to identify potential problems
- You need to validate another developer's code

## Recommended depth

- **Light**: quick review or sanity check, without extensive report
- **Standard**: normal review focused on regression, correctness, and basic security
- **Deep**: auth, billing, infra, contracts, migrations, and broad changes

If the change is small, do not force deep review.

## Supported languages

- JavaScript and TypeScript
- C# and .NET

## Review Checklist

### Security
- input validation
- authentication
- sensitive data
- access control

### Performance
- queries
- memória
- rede
- algoritmo

### Quality
- naming
- functions
- tests
- modularization

### Logic
- rules
- edge cases
- flows
- domain validations

### Tests
- coverage
- test types
- assertions

## Review Format

```markdown
## Review

### Decision
- approved
- approved with notes
- changes requested
- escalate to deeper review

### Findings
- item

### Recommendation
- next action
```

---

Use this skill when formal review truly adds value. For small tasks, prefer light review.
