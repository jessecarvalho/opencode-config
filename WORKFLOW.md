# Purple Stone Studio — Development Workflow

> **Status**: Workflow with cost and risk routing
> **Última atualização**: 2026-05-14

---

## Overview

The workflow now uses **mode-based routing**. Every request goes through **architecture** and **code review**, but the density changes between **Light**, **Standard**, and **Full**.

## Core Principles

1. **Default Light**: start with the lowest safe density
2. **Signal-based escalation**: only increase depth when there is a real trigger
3. **Waves for large work**: waves remain for broad deliveries and Full mode
4. **Architecture and review always present**: small tasks use light tiers
5. **Explicit user approval before delegation**
6. **Re-review only when there is a formal reviewer with fixes**

## Mode Matrix

| Mode | When to use | Architecture | Implementation | Review |
|------|-------------|-------------|---------------|--------|
| **Light** | rename, copy, docs, localized adjustment, low risk | `architect-lite` | 1 agent | `code-reviewer-lite` |
| **Standard** | medium change, multiple files, moderate logic | `architect-standard` | 1 or 2 agents | `code-reviewer-standard` |
| **Full** | auth, billing, infra, contract, migration, broad refactor | `architect` | multi-agent flow | `code-reviewer` |

## Escalation Triggers

Escalate Light or Standard when there is:

- test failure
- critical area touched
- scope growth
- multiple impacted layers
- security, contract, or data concerns
- explicit user request for greater rigor

## Flows

### Light

| Step | Agent | Action |
|-------|--------|------|
| 1 | Orquestrador | Classifies as Light |
| 2 | Orquestrador | Presents mode, architecture, execution, and review to the user |
| 3 | User | Approves the path |
| 4 | Architect-Lite | Defines minimal approach |
| 5 | General or specialist | Implements the change |
| 6 | Code-Reviewer-Lite | Performs light review |
| 7 | Orquestrador | Delivers to user or escalates |

### Standard

| Step | Agent | Action |
|-------|--------|------|
| 1 | Orquestrador | Classifies as Standard |
| 2 | Orquestrador | Presents mode, architecture, execution, and review to the user |
| 3 | User | Approves the path |
| 4 | Architect-Standard | Defines mini-spec |
| 5 | General, Backend, or Frontend | Implements |
| 6 | Code-Reviewer-Standard | Performs standard review |
| 7 | QA-Engineer | Optional when integration, testing, or risk justifies it |
| 8 | Orquestrador | Delivers to user or escalates |

### Full

| Step | Agent | Action | Artifact |
|-------|--------|------|----------|
| 1 | Orquestrador | Classifies as Full | — |
| 2 | Orquestrador | Presents mode, architecture, execution, and review to the user | — |
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
- **Do not force Full mode** for trivial changes
- **Do not skip escalation** when a real risk signal appears
- **Do not skip architecture or code review** in any mode
- **Do not delegate agents before user approval**
- **Do not skip re-review** after fixes when deep or standard reviewer requests changes
- **Do not advance wave without user approval** in Full mode

### Parallelization
- Backend + Frontend in parallel when truly independent
- Do not parallelize by reflex on small tasks
- QA and deep review remain sequential in Full mode

### Documentation
- Everything that generates a formal artifact goes in `iaReports/`
- Waves and formal reports are mainly required in Full mode
- Branch naming for planned deliveries: `feature/{ticket-id}-wave-{N}-{short-name}`

## Agents and Their Roles

| Agent | Main Role | When to Trigger |
|--------|-----------------|----------------|
| **Orquestrador** | Classification, cost, gates | Always |
| **Zoe (Admin)** | Tickets, branches, PRs | Planned or Full |
| **Architect-Lite** | Minimal architectural direction | Light |
| **Architect-Standard** | Mini-spec and integration | Standard |
| **Architect** | Deep design and specs | Full |
| **General** | Fast execution and light review | Light and Standard |
| **Backend-Engineer** | Specialized backend | When backend needs a specialist |
| **Frontend-Engineer** | Specialized frontend | When frontend needs a specialist |
| **QA-Engineer** | Quality gate | Standard or Full |
| **Code-Reviewer-Lite** | Quick review | Light with extra confidence |
| **Code-Reviewer-Standard** | Normal review | Standard |
| **Code-Reviewer** | Deep review and critical re-review | Full |

## Orquestrador Checklist

For each request:
- [ ] Did I classify size and risk before delegating?
- [ ] Did I choose the lowest safe mode?
- [ ] Did I call the correct architecture tier?
- [ ] Did I call the correct review tier?
- [ ] Did I present the decision to the user?
- [ ] Did I receive approval before delegating?
- [ ] Is there any escalation trigger?
- [ ] Did the user request a mode override?

If in Full mode:
- [ ] Were Architect or specs actually necessary?
- [ ] Did QA report?
- [ ] Did deep review report?
- [ ] If there were fixes, was re-review called?
- [ ] Did the user approve?
