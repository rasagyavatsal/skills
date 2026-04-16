---
name: guidelines
description: Enforce project-specific coding standards including unit testing, deep module design, security, contextual analysis (UBIQUITOUS_LANGUAGE, DESIGN-SYSTEM), and post-implementation validation for TypeScript and Flutter. Use when implementing new features, fixing bugs, or when the user mentions coding guidelines or validation scripts.
---

# Guidelines

Follow these core mandates and post-implementation workflows to ensure code quality, security, and stability.

## Core Mandates

1.  **Contextual Analysis:** If `UBIQUITOUS_LANGUAGE.md` or `DESIGN-SYSTEM.md` exist in the project, analyze them to ensure consistent terminology and alignment with established design patterns.
2.  **Unit Testing:** Always create unit tests for new logic. Verify that existing tests still pass.
3.  **Deep Modules:** Favor "deep modules" as defined by John Ousterhout (*A Philosophy of Software Design*). A deep module has a small interface hiding a large implementation. This makes the codebase more testable and AI-navigable, allowing you to test at the boundary rather than internal details.
4.  **Security:** Ensure code is 100% secure. Conduct a self-review for common vulnerabilities (e.g., injection, insecure data handling, improper authentication) before finalizing.
5.  **No Commits:** Do not commit changes unless explicitly directed by the user.

## Post-Implementation Workflow

After implementing a task, perform the following validation steps:

### 1. Cleanup
*   Identify and remove redundant or dead code introduced or discovered during the task.

### 2. Workspace Validation

#### For TypeScript Codebases:
*   **Test:** Run the project's test script (e.g., `npm test`, `yarn test`).
*   **Type-Check:** Run the type-checking script (e.g., `npm run type-check`, `tsc --noEmit`).
*   **Lint:** Run the linting script (e.g., `npm run lint`, `eslint .`).
*   **Build:** Run the build script (e.g., `npm run build`) to ensure no build errors.

#### For Flutter Codebases:
*   **Test:** Run `flutter test`.
*   **Analyze:** Run `flutter analyze`.
*   **Doctor:** Run `flutter doctor` to ensure the environment is healthy.

## Quick Checklist
- [ ] Contextual analysis (UBIQUITOUS_LANGUAGE/DESIGN-SYSTEM) completed?
- [ ] Unit tests created and passing?
- [ ] Module interfaces simplified (Deep Modules)?
- [ ] Security review completed?
- [ ] Redundant code removed?
- [ ] Environment-specific validation scripts (TS/Flutter) executed successfully?
