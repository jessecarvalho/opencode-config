# Purple Stone Studio — Development Workflow

> **Status**: Workflow with cost and risk routing
> **Última atualização**: 2026-05-14

---

## Overview

The workflow now uses **flow-based routing**. Every request goes through the same **architect** and **code reviewer**, and both must operate with deep rigor in every flow.

## Core Principles

1. **Deep architecture and review always**
2. **Signal-based escalation**: increase execution support and validation when there is a real trigger
3. **Waves for large work**: waves remain for broad deliveries
4. **Architecture and review always present**: no downgrade in depth
5. **Explicit user approval before delegation**
6. **Re-review only when there is a formal reviewer with fixes**

## Flow Matrix

| Flow | When to use | Architecture | Implementation | Review |
|------|-------------|-------------|---------------|--------|
| **Direct** | bounded execution with one implementation agent | `architect` | 1 agent | `code-reviewer` |
| **QA-gated** | changes that need an explicit quality gate | `architect` | 1 or 2 agents + QA | `code-reviewer` |
| **Wave-based** | broad, sensitive, or staged delivery | `architect` | multi-agent wave flow | `code-reviewer` |

## Escalation Triggers

Escalate the direct or QA-gated flow when there is:

- test failure
- critical area touched
- scope growth
- multiple impacted layers
- security, contract, or data concerns
- explicit user request for greater rigor

## Flows

### Direct flow

| Step | Agent | Action |
|-------|--------|------|
| 1 | Orquestrador | Chooses the direct flow |
| 2 | Orquestrador | Presents flow, architecture, execution, and review to the user |
| 3 | User | Approves the path |
| 4 | Architect | Performs deep architectural analysis |
| 5 | General or specialist | Implements the change |
| 6 | Code-Reviewer | Performs deep review |
| 7 | Orquestrador | Delivers to user or escalates |

### QA-gated flow

| Step | Agent | Action |
|-------|--------|------|
| 1 | Orquestrador | Chooses the QA-gated flow |
| 2 | Orquestrador | Presents flow, architecture, execution, and review to the user |
| 3 | User | Approves the path |
| 4 | Architect | Performs deep architectural analysis |
| 5 | General, Backend, or Frontend | Implements |
| 6 | Code-Reviewer | Performs deep review |
| 7 | QA-Engineer | Optional when integration, testing, or risk justifies it |
| 8 | Orquestrador | Delivers to user or escalates |

### Wave-based flow

| Step | Agent | Action | Artifact |
|-------|--------|------|----------|
| 1 | Orquestrador | Chooses the wave-based flow | — |
| 2 | Orquestrador | Presents flow, architecture, execution, and review to the user | — |
| 3 | User | Approves the path | — |
| 4 | Zoe | Updates ticket and creates branch when applicable | ticket or branch |
| 5 | Architect | Creates wave plan or specs | `iaReports/{TICKET}_WAVE_PLAN.md` |
| 6 | Backend + Frontend | Implement in parallel when possible | code + tests |
| 7 | QA-Engineer | Reviews quality | `iaReports/{TICKET}_WAVE{N}_QA_REPORT.md` |
| 8 | Code-Reviewer | Reviews at maximum depth | `iaReports/{TICKET}_WAVE{N}_CODE_REVIEW.md` |
| 9 | Code-Reviewer | Re-review after fixes, if needed | review update |
| 10 | User | Approves wave or final delivery | — |
| 11 | Zoe | PR and issue update at completion | PR |

## Critical Rules

### Mandatory
- **Do not downgrade architecture or review depth** for any change
- **Do not skip escalation** when a real risk signal appears
- **Do not skip architecture or code review** in any flow
- **Do not delegate agents before user approval**
- **Do not skip re-review** after fixes when `code-reviewer` requests changes
- **Do not advance wave without user approval** in wave-based flow

### Parallelization
- Backend + Frontend in parallel when truly independent
- Do not parallelize by reflex when coordination cost is not justified
- QA and deep review remain sequential in wave-based flow

### Documentation
- Everything that generates a formal artifact goes in `iaReports/`
- Waves and formal reports are mainly required in wave-based flow
- Branch naming for planned deliveries: `feature/{ticket-id}-wave-{N}-{short-name}`

## Agents and Their Roles

| Agent | Main Role | When to Trigger |
|--------|-----------------|----------------|
| **Orquestrador** | Classification, cost, gates | Always |
| **Zoe (Admin)** | Tickets, branches, PRs | Planned or wave-based work |
| **Architect** | Deep architecture for every mode | Always |
| **General** | Fast execution support | Direct and QA-gated flows |
| **Backend-Engineer** | Specialized backend | When backend needs a specialist |
| **Frontend-Engineer** | Specialized frontend | When frontend needs a specialist |
| **QA-Engineer** | Quality gate | QA-gated or wave-based flows |
| **Code-Reviewer** | Deep review for every mode | Always |

## Orquestrador Checklist

For each request:
- [ ] Did I classify size and risk before delegating?
- [ ] Did I choose the lowest safe mode?
- [ ] Did I request the correct architecture depth from `architect`?
- [ ] Did I request the correct review depth from `code-reviewer`?
- [ ] Did I present the decision to the user?
- [ ] Did I receive approval before delegating?
- [ ] Is there any escalation trigger?
- [ ] Did the user request a mode override?

If in wave-based flow:
- [ ] Were Architect or specs actually necessary?
- [ ] Did QA report?
- [ ] Did `code-reviewer` report?
- [ ] If there were fixes, was re-review called?
- [ ] Did the user approve?
