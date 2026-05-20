---
name: agent-orchestration
description: Orchestrates the correct selection of specialized agents for project tasks
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: multi-agent
---

## What I do

I am the agent orchestration skill. My responsibility is to:

1. **Identify the task type**
2. **Choose the right mode** between Light, Standard, and Full
3. **Choose the correct architecture and review tier**
4. **Select the right agent**
5. **Escalate only when there is a real risk signal**

## When to use me

Use this skill when:

- The user makes a request that requires multiple agents or steps
- It is necessary to choose which specialist agent to call
- It is necessary to keep architecture and review in all tasks without always using maximum depth
- It is necessary to avoid excessive cost in small tasks

## Available agents

| Agent | When to use | Responsibility |
|--------|-------------|-------------------|
| `general` | Versatile code tasks, debugging, and mixed implementation | Implements, debugs, refactors, prototypes, and automates |
| `backend-engineer` | APIs, domain logic, backend | Implements server-side code |
| `frontend-engineer` | React components, UI, state | Creates visual interface |
| `bug-perito` | Bugs, errors, diagnosis | Investigates and diagnoses problems |
| `infra-engineer` | Infrastructure, DevOps, Kubernetes | Configures environment and deployment |
| `pm` | Requirements, roadmap, prioritization | Defines what to build |
| `qa-engineer` | Testing and quality | Validates when mode requires |
| `ux-ui-designer` | Design, UI, and UX | Creates visual experience |
| `admin-assistant` | Tickets, branches, PRs | Handles repository operations |

## How to orchestrate

### Step 1: Analyze the request

Before invoking any agent, understand:

- What is the final objective?
- What type of expertise is needed?
- Does the task require code implementation or is it operational?
- Is the change small, medium, or critical?
- Is there any risk signal that justifies heavy validation?

### Step 2: Choose the mode

- **Light** → small, localized, low-risk change
- **Standard** → moderate change, with some logic or uncertainty
- **Full** → critical, broad, or sensitive change

### Step 2.5: Present the decision to the user

Before invoking any other agent, present to the user:

- chosen mode
- chosen architect
- chosen executor(s)
- chosen reviewer
- whether QA is included
- short reason for the choice

And ask explicitly whether they approve the path.

Do not proceed until approval is received, unless the user has already asked to continue automatically.

### Step 3: Select architecture and review

- **Light** → `architect-lite` + `code-reviewer-lite`
- **Standard** → `architect-standard` + `code-reviewer-standard`
- **Full** → `architect` + `code-reviewer`

QA remains mandatory in Full and optional in Standard when technically justified.

### Step 4: Select the execution agent

- **Small or mixed implementation** → `general`
- **Specialized implementation** → `backend-engineer` or `frontend-engineer`
- **Problem investigation** → `bug-perito`
- **Quality validation** → `qa-engineer`
- **Visual design** → `ux-ui-designer`
- **Infrastructure** → `infra-engineer`
- **Product and roadmap** → `pm`
- **Repository operations** → `admin-assistant`

### Step 5: Recommended flows

#### Light

```
Orquestrador ──► presents route ──► user approval ──► Architect-Lite ──► 1 execution agent ──► Code-Reviewer-Lite ──► delivery
```

#### Standard

```
Orquestrador ──► presents route ──► user approval ──► Architect-Standard ──► 1 execution agent ──► Code-Reviewer-Standard ──► delivery
                                                                                                                    │
                                                                                                                    └──► Optional QA
```

#### Full

```
Orquestrador ──► presents route ──► user approval ──► Architect ──► Engineer ──► QA ──► Deep Review ──► delivery
```

## Rules

### Rule 1: Start light

If the task appears safe and localized, start in Light.

### Rule 2: Validation must be proportional

- Light uses light architecture and review
- Standard uses medium architecture and review
- Full uses deep architecture and review

### Rule 3: Escalate by signal

Escalate when there is:
- test failure
- critical area touched
- multiple affected layers
- security or contract concern
- explicit user request for greater rigor

## Common mistakes to avoid

1. Escalating too early
2. Using full pipeline on small task
3. Using the wrong agent for the task
4. Skipping proportional validation in sensitive work

## Golden tips

- Start light
- Context is king
- Architecture and review are always mandatory
- Show the route and ask for approval before delegating
- Escalate based on evidence, not habit
- Use Full mode only when risk justifies it

---

Use me when you want to ensure the multi-agent flow is cost-efficient and proportional to risk.
