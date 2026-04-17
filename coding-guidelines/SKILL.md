---
name: coding-guidelines
description: Enforce implementation guidelines for writing and modifying code. add unit tests, prefer deep modules, review changes for security, remove redundancy, and run repository verification commands. Use when the user asks to implement, edit, refactor, or review code and wants a consistent delivery checklist without committing changes.
---

# Coding Guidelines

Apply these rules whenever writing or changing code.

## Core rules

- Before doing anything else, read `DESIGN-SYSTEM.md` and `UBIQUITOUS-LANGUAGE.md` if they exist in the repository.
- Create or update unit tests for every behavior change.
- Prefer deep modules: keep interfaces small and hide complexity behind stable boundaries.
- Test behavior at module boundaries instead of exposing internals only to make them testable.
- Treat security as a release blocker: do not leave known vulnerabilities in the changed scope.
- Do not commit changes.

## Implementation workflow

1. Understand the user-facing behavior and identify the narrowest interface that can own it.
2. Deepen shallow modules when needed by moving orchestration, validation, and policy behind that interface.
3. Write or update unit tests around the boundary that matters to users or callers.
4. Implement the change with the smallest surface area that satisfies the task.
5. Remove duplication, dead branches, and redundant helpers introduced or exposed by the change.

## Security checklist

- Validate and normalize untrusted input.
- Encode or escape output at the proper boundary.
- Prevent injection classes relevant to the stack: SQL, command, template, path, and HTML/script injection.
- Enforce authentication, authorization, and least privilege explicitly.
- Keep secrets out of source, logs, tests, and client-visible payloads.
- Prefer framework-safe defaults and well-maintained libraries over handwritten security logic.
- If any residual risk remains, call it out explicitly. Do not claim absolute security without evidence.

## Verification after implementation

- Remove redundant code in the touched area when safe.
- Run the relevant verification commands for the codebase.
- Fix failures caused by the change when they are in scope.
- Report any blockers, skipped checks, or residual risks clearly.
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
