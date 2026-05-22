---
name: complexity-labeling
description: Classify GitHub issues as `high`, `medium`, or `low` complexity and apply the matching label. Use when a user asks to triage issue difficulty, estimate implementation complexity from an issue, or label GitHub issues with `high`, `medium`, or `low`.
---

# Complexity Labeling

## Quick Start

1. Read the issue title, description, linked comments, and acceptance criteria.
2. Assess ambiguity, blast radius, risk, and pattern reuse.
3. Choose exactly one label: `high`, `medium`, or `low`.
4. Apply the label and remove the other two complexity labels if present.
5. Report the label with a short rationale.

## Rubric

### `low`

- Clear boundaries: changes stay within one file or one isolated component.
- Low ambiguity: the outcome and implementation path are clearly defined.
- Low systemic risk: mistakes are unlikely to break auth, data, infra, or security.
- Abundant patterns: the repo already has several close examples to copy.

### `medium`

- Some ambiguity: the issue needs light investigation, but the scope is still bounded.
- Moderate surface area: changes span a few files or one subsystem, not core platform layers.
- Moderate risk: mistakes could cause visible regressions, but failures stay contained.
- Partial patterns: the repo has related examples, but they need adaptation.

### `high`

- High ambiguity: the issue describes a problem, not a clear implementation path.
- Large blast radius: work touches shared infrastructure, global state, CI/CD, auth, payments, or core utilities.
- Performance or security implications: the issue affects query performance, encryption, concurrency, data integrity, or structural refactors.
- No existing patterns: the work introduces a new foundation or a novel third-party integration.

## Decision Rules

- Start at `medium`.
- Move to `low` only when the issue strongly matches the low criteria and no high-risk signal is present.
- Move to `high` when two or more high signals are present.
- Also move to `high` when a single high signal affects auth, payments, security, production data, shared infrastructure, or global performance.
- Prefer the higher label when uncertainty itself increases delivery risk.
- Do not use raw file count alone; repetitive, localized work can still be `low` or `medium`.

## Workflow

1. Read the issue and any relevant comments or linked docs.
2. Identify the likely code areas and whether the repo already has similar patterns.
3. Judge the issue on four axes:
   - ambiguity
   - blast radius
   - risk
   - novelty
4. Apply exactly one of `high`, `medium`, or `low`.
5. In the response, explain the choice in 2-4 short bullets.

## Edge Cases

- If the issue is underspecified and the missing detail hides architecture or risk, choose `high`.
- If the issue is underspecified but looks contained and familiar, choose `medium`.
- If labels do not exist yet, create the exact labels `high`, `medium`, and `low` if the workflow allows it.
- Re-evaluate if new comments materially narrow or expand the scope.

## Examples

- `low`: add a button to an existing settings panel using the same pattern as similar buttons.
- `medium`: add a new API endpoint by adapting existing endpoint patterns across a controller, service, and tests.
- `high`: migrate authentication providers or diagnose why large dataset loads are slow across the stack.
