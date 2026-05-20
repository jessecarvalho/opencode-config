---
name: documentation-governance
description: Use when creating, updating, organizing, or validating project documentation, reports, contracts, PRDs, or technical incident records.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: documentation
---

## Purpose

This skill centralizes document structure, placement, and maintenance rules.

## Document Placement

### Executive
- `/docs/executive/product/`
- `/docs/executive/marketing/`
- `/docs/executive/legal/`
- `/docs/executive/finances/`
- `/docs/executive/design/`

### Technical
- `/docs/technical/backend/`
- `/docs/technical/frontend/`
- `/docs/technical/infra/`
- `/docs/technical/testing/`
- `/docs/technical/incidents/`

### Delivery Artifacts
- `/iaReports/` for wave plans, specs, QA reports, investigation reports, and architecture contracts

## Documentation Rules

- Keep executive and technical documentation separated.
- Prefer concise, maintainable documentation over bloated documents.
- Do not invent decisions that were never made.
- If code and documentation conflict, flag it clearly.

## Recommended Frontmatter

For living documents, include:
- `last_updated`
- `version`
- `status`

## Artifact Guidance

Use `/iaReports/` for:
- wave plans
- wave specs
- QA reports
- investigation reports
- architecture contracts

Use `/docs/` for:
- durable knowledge
- reference material
- product and design documentation
- post-mortem or incident records intended to persist

## Best Fit Agents

- `doc-librarian`
- `architect`
- `pm`
- `bug-perito`
- `admin-assistant` when operational artifacts are needed
