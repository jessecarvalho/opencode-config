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
2. **Choose the right execution flow**
3. **Always use deep architecture and deep review**
4. **Select the right agent**
5. **Escalate only when there is a real risk signal**

## When to use me

Use this skill when:

- The user makes a request that requires multiple agents or steps
- It is necessary to choose which specialist agent to call
- It is necessary to keep architecture and review deep in all tasks without adding fake lite or standard specialists

## Available agents

| Agent | When to use | Responsibility |
|--------|-------------|-------------------|
| `general` | Versatile code tasks, debugging, and mixed implementation | Implements, debugs, refactors, prototypes, and automates |
| `backend-engineer` | APIs, domain logic, backend | Implements server-side code |
| `frontend-engineer` | React components, UI, state | Creates visual interface |
| `bug-perito` | Bugs, errors, diagnosis | Investigates and diagnoses problems |
| `infra-engineer` | Infrastructure, DevOps, Kubernetes | Configures environment and deployment |
| `pm` | Requirements, roadmap, prioritization | Defines what to build |
| `qa-engineer` | Testing and quality | Validates when the change needs an explicit quality gate |
| `ux-ui-designer` | Design, UI, and UX | Creates visual experience |
| `admin-assistant` | Tickets, branches, PRs | Handles repository operations |

## How to orchestrate

### Step 1: Analyze the request

Before invoking any agent, understand:

- What is the final objective?
- What type of expertise is needed?
- Does the task require code implementation or is it operational?
- What execution support and validation are required?
- Is there any risk signal that justifies heavy validation?

### Step 2: Choose the execution flow

- **Direct flow** → bounded execution with one implementation agent and no separate QA gate
- **QA-gated flow** → implementation followed by QA and review
- **Wave-based flow** → ticket/branch preparation, architecture artifacts, implementation, QA, review, and re-review when needed

### Step 2.5: Present the decision to the user

Before invoking any other agent, present to the user:

- chosen flow
- chosen architect
- chosen executor(s)
- chosen reviewer
- whether QA is included
- short reason for the choice

And ask explicitly whether they approve the path.

Do not proceed until approval is received, unless the user has already asked to continue automatically.

### Step 3: Select architecture and review

- `architect` is always required
- `code-reviewer` is always required
- `qa-engineer` is included whenever the change needs an explicit quality gate

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

#### Direct flow

```
Orquestrador ──► presents route ──► user approval ──► Architect ──► 1 execution agent ──► Code-Reviewer ──► delivery
```

#### QA-gated flow

```
Orquestrador ──► presents route ──► user approval ──► Architect ──► 1 execution agent ──► Code-Reviewer ──► delivery
                                                                                                                    │
                                                                                                                    └──► Optional QA
```

#### Wave-based flow

```
Orquestrador ──► presents route ──► user approval ──► Architect ──► Engineer ──► QA ──► Deep Review ──► delivery
```

## Rules

### Rule 1: Keep architecture and review deep in every flow

### Rule 2: Flows change support, not rigor

### Rule 3: Escalate by signal

Escalate when there is:
- test failure
- critical area touched
- multiple affected layers
- security or contract concern
- explicit user request for greater rigor

## Common mistakes to avoid

1. Escalating too early
2. Treating a smaller flow as a license for shallow analysis
3. Using the wrong agent for the task
4. Skipping deep validation in sensitive work

## Golden tips

- Keep architecture and review deep in every flow
- Context is king
- Architecture and review are always mandatory
- Show the route and ask for approval before delegating
- Escalate based on evidence, not habit
- Use wave-based execution only when the change truly needs it

---

Use me when you want to ensure the multi-agent flow stays rigorous and correctly routed.
