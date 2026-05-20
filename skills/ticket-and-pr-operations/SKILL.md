---
name: ticket-and-pr-operations
description: Use when preparing tickets, creating branches, drafting pull requests, or updating GitHub and Linear workflow state for planned work.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: repository-operations
---

## Purpose

This skill centralizes operational repository workflow for ticket and PR handling.

## Scope

Use for:
- issue lookup
- issue and ticket updates
- branch creation
- PR drafting or creation
- lightweight release coordination

## Operating Rules

- Be exact and conservative.
- Do not assume branch naming, base branch, or platform conventions without evidence.
- Inspect repository state before acting.
- Do not push, merge, or create PRs unless requested.
- Do not rewrite history unless explicitly instructed.

## Ticket Handling

When updating a ticket:
- confirm the platform if not obvious
- use GitHub CLI for GitHub issues when available
- use Linear only when credentials and workspace details exist
- if direct update is impossible, report the blocker clearly

## Branch Handling

When creating a branch:
- inspect the repository for the correct base branch and naming pattern
- follow repo conventions when they exist
- ask if naming or base branch remains ambiguous

## PR Handling

Before creating a PR:
- inspect `git status`
- inspect the intended diff
- inspect recent commits
- draft a concise title and body aligned with repository style

## Required Output

Report:
- what was updated or created
- what remains blocked
- what is ready for the next step

## Best Fit Agents

- `admin-assistant`
- `product-owner` when preparing a route involving traceability
