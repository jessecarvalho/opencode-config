---
name: purple-standards
description: Use when implementing, refactoring, reviewing, or validating code for Purple Stone Studio standards such as no comments, minimal safe changes, clarity, validation, and clean handoff.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: engineering-standards
---

## Purpose

This skill centralizes the shared engineering standards used across Purple Stone Studio agents.

Use it when code is being implemented, reviewed, debugged, or validated.

## Core Standards

### No Comments

Do not create comments in code unless the user explicitly asks for them.

Forbidden by default:
- line comments
- block comments
- TODO, FIXME, HACK, NOTE, XXX markers
- inline documentation comments
- explanatory comments in tests or config

Prefer self-explanatory code through naming, extraction, and simplification.

### Minimal Safe Change

- Change only what is needed for the task.
- Avoid parallel refactors unless they are required for correctness.
- Do not widen scope just because improvement opportunities exist.
- Preserve existing behavior outside the requested change.

### Clarity Over Cleverness

- Prefer readable naming and straightforward control flow.
- Keep responsibilities cohesive.
- Avoid hidden side effects.
- Make state transitions and failure paths explicit.

### Validation Before Finish

- Run the most relevant available validation before completion.
- If tests cannot be run, say so clearly.
- Report remaining risk or unverified areas explicitly.

### Safety Basics

- Do not hardcode secrets.
- Validate inputs at boundaries.
- Avoid logging sensitive data.
- Respect existing contracts and compatibility expectations.

## Required Handoff Format

When finishing technical work, report briefly:
- what changed
- where it changed
- what was validated
- what remains risky or unverified

## When Not to Use

Do not use this skill for product strategy, legal review, marketing analysis, or purely administrative ticket workflows.
