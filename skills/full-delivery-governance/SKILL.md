---
name: full-delivery-governance
description: Use when routing, designing, validating, or reviewing medium-to-critical work that needs proportional governance across Light, Standard, or Full delivery modes.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: delivery-governance
---

## Purpose

This skill defines the shared delivery governance model so multiple agents do not duplicate the same process rules.

## Delivery Modes

### Light

Use when the task is localized, low risk, and unlikely to affect contracts or critical flows.

Typical path:
- `architect-lite`
- one implementation agent
- `code-reviewer-lite`
- no QA by default

### Standard

Use when the task has moderate scope, multiple related files, moderate logic change, or integration uncertainty.

Typical path:
- `architect-standard`
- one or two implementation agents
- `code-reviewer-standard`
- `qa-engineer` only when technically justified

### Full

Use when the task involves security, auth, billing, PII, migrations, infra, contracts, production incidents, or broad cross-cutting impact.

Typical path:
- `architect`
- appropriate implementation specialists
- `qa-engineer`
- `code-reviewer`
- re-review after fixes when needed

## Governance Principles

- Start with the lowest safe level.
- Escalate only when evidence justifies it.
- Do not force a full pipeline on bounded low-risk work.
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
- `architect-lite`
- `architect-standard`
- `architect`
- `qa-engineer`
- `code-reviewer-lite`
- `code-reviewer-standard`
- `code-reviewer`
