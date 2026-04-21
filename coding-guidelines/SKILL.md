---
name: coding-guidelines
description: Enforce strict implementation standards for secure, reliable, and maintainable code changes. Require tests, deep modules, frontend token/component/pattern compliance, and full verification, and block completion when quality gates fail. Use when implementing, editing, refactoring, or reviewing code and the user wants production-grade consistency without committing changes.
---

# Coding Guidelines

Apply these rules whenever writing or changing code.

## Non-negotiable rules

- Before doing anything else, read `UBIQUITOUS-LANGUAGE.md` if it exists in the repository.
- Never mark work complete unless Security, Reliability, and Maintainability gates all pass for the changed scope.
- Create or update unit tests for every behavior change.
- Prefer deep modules: keep interfaces small and hide complexity behind stable boundaries.
- Test behavior at module boundaries instead of exposing internals only to make them testable.
- Treat security defects as release blockers in the changed scope.
- Do not commit changes.

## Frontend rules (strict)

- For frontend changes, use design tokens for visual values (color, spacing, typography, radius, shadow, motion, z-index). Do not introduce one-off hardcoded values when a token exists.
- Reuse existing component library primitives and composites before creating new UI components.
- Follow established pattern library flows, layouts, and interaction patterns; do not invent new patterns when an approved pattern exists.
- If a required token, component, or pattern is missing, add it to the relevant library first (or report a blocker if out of scope) and then consume it in feature code.
- Keep behavior and styling consistent across responsive breakpoints; avoid ad-hoc overrides that bypass library conventions.

## Quality gates (strict)

### Security gate

- Validate, normalize, and constrain all untrusted input.
- Encode or escape output at the correct boundary.
- Prevent relevant injection classes (SQL, command, template, path, HTML/script).
- Enforce authentication, authorization, and least privilege explicitly.
- Keep secrets out of source, logs, tests, and client-visible payloads.
- Prefer safe framework defaults and maintained dependencies over custom security logic.
- If residual risk remains, report it explicitly and do not claim "fully secure" without evidence.

### Reliability gate

- Handle failures explicitly; do not swallow errors or hide degraded states.
- Add timeouts, retries, and backoff where external or unstable dependencies are involved.
- Keep side-effecting operations idempotent when retries or replays are possible.
- Guard against race conditions, partial writes, and resource leaks in changed paths.
- Preserve backward compatibility for data contracts, and provide safe migration/rollback behavior where relevant.
- Add or preserve observability (logs/metrics/traces) for critical paths touched by the change.

### Maintainability gate

- Keep modules cohesive with small, stable public interfaces.
- Remove duplication, dead branches, and obsolete helpers in touched areas.
- Favor clear names and straightforward control flow over clever shortcuts.
- Add brief comments for non-obvious invariants, policies, or edge-case handling.
- Avoid unbounded TODOs and speculative abstractions without a concrete need.
- Keep tests readable and behavior-focused so future changes remain safe.

## Implementation workflow

1. Understand the user-facing behavior and identify the narrowest interface that can own it.
2. For frontend work, map requirements to existing design tokens, component library components, and pattern library references before implementing UI changes.
3. Deepen shallow modules when needed by moving orchestration, validation, and policy behind that interface.
4. Write or update unit tests around the boundary that matters to users or callers.
5. Implement the change with the smallest surface area that satisfies the task.
6. Apply and verify all Security, Reliability, and Maintainability gates for the changed scope.
7. Remove duplication, dead branches, and redundant helpers introduced or exposed by the change.

## Verification after implementation

- Remove redundant code in the touched area when safe.
- Run the relevant verification commands for the codebase.
- Fix failures caused by the change when they are in scope.
- Report any blockers, skipped checks, or residual risks clearly.
- If any quality gate fails, stop and report the failure instead of declaring completion.
- Never create a commit as part of this workflow.

## TypeScript codebases

1. Identify the repo's package manager and scripts from `package.json`.
2. Run the repository test script.
3. Run the repository type-check script.
4. Run the repository lint script.
5. Run the repository build script.
6. Do not mark the task complete while these checks fail, unless you clearly report the blocker.

## Flutter codebases

1. Run `flutter test`.
2. Run `flutter analyze`.
3. Run `flutter doctor`.
4. Fix issues in the changed scope or report the blocker precisely.

## Delivery

- Summarize the code change, test coverage, verification results, and any remaining risks.
- Keep the user informed about assumptions and tradeoffs.
- Stop before any git commit, amend, or push step.
