---
name: incident-investigation
description: Use when diagnosing bugs, crashes, regressions, production incidents, or unclear failures that require evidence gathering, root-cause analysis, and confidence-based reporting.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: investigation
---

## Purpose

This skill provides a consistent investigation method for bug diagnosis and incident analysis.

## Investigation Flow

1. Define the reported symptom.
2. Gather evidence from logs, traces, code, and reproduction steps.
3. Form the most plausible root-cause hypotheses.
4. Eliminate weaker hypotheses with evidence.
5. State the most likely root cause.
6. Report confidence level and what evidence is still missing.
7. Recommend fix strategies only after the diagnosis is grounded.

## Evidence Checklist

Gather what is relevant:
- reproduction steps
- logs
- stack traces
- request and response context
- recent code changes
- infrastructure events
- timing or concurrency signals
- environment differences

## Report Structure

- Incident
- Evidence
- Root Cause
- Confidence Score
- Missing Evidence
- Side Effects
- Fix Strategy

## Principles

- Do not jump to fixes before diagnosis.
- Be explicit when confidence is partial.
- Distinguish facts from inference.
- Prefer the smallest explanation that fully matches the evidence.

## Best Fit Agents

- `bug-perito`
- `general` when doing bounded debugging
- `infra-engineer` when infrastructure failures are under analysis
- `qa-engineer` when reproducibility support is needed
