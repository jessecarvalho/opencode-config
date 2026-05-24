---
name: full-delivery-governance
description: Use when routing, designing, validating, or reviewing work across direct, QA-gated, or wave-based flows with one architect and one reviewer and consistently deep rigor.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: delivery-governance
---

## Purpose

This skill defines the shared delivery governance model so multiple agents do not duplicate the same process rules.

Architecture and review are always deep in every mode. Modes change execution support, not rigor.

## Delivery Flows

### Direct flow

Use when the task is bounded in execution scope.

Typical path:
- `architect`
- one implementation agent
- `code-reviewer`
- no QA by default

### QA-gated flow

Use when the task has moderate scope, multiple related files, moderate logic change, or integration uncertainty.

Typical path:
- `architect`
- one or two implementation agents
- `code-reviewer`
- `qa-engineer` only when technically justified

### Wave-based flow

Use when the task involves security, auth, billing, PII, migrations, infra, contracts, production incidents, or broad cross-cutting impact.

Typical path:
- `architect`
- appropriate implementation specialists
- `qa-engineer`
- `code-reviewer`
- re-review after fixes when needed

## Governance Principles

- Keep architecture and review deep in every mode.
- Escalate only when evidence justifies it.
- Do not mistake bounded scope for low rigor.
- Do not skip validation for sensitive or high-blast-radius work.

## Escalation Signals

Escalate when you see:
- failed tests in important areas
- security or permission concerns
- schema or contract changes
- multiple system layers affected
- rollout or migration complexity
- low confidence from the executor

## Artifact Rules

### Use compact architecture guidance when:
- work is sensitive but bounded
- a full wave plan is unnecessary

### Use an architecture contract when:
- interfaces, schemas, responsibilities, or cross-layer behavior change

### Use a wave plan when:
- work must be split into dependent or independently deliverable stages

### Use QA artifacts when:
- a formal gate is required
- the task is high-risk or multi-wave

## Approval Guidance

- Ask for approval before non-obvious or expensive multi-agent execution.
- If the user already clearly asked to proceed and the route is straightforward, avoid unnecessary confirmation friction.

## Primary Agents That Benefit Most

- `product-owner`
- `architect`
- `qa-engineer`
- `code-reviewer`
