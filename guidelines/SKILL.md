---
name: guidelines
description: Guidelines for writing code.
---

1. create unit tests.

2. create deep modules see deep-modules.md for more details.

3. code should be 100% secure, no security vulnerabilities.

4. after implementing the task:

  * find and remove redundant code, if any.

  * for typescript codebase:
    a. run test script.
    b. run type-check script to check for type errors.
    c. run lint script to check for lint errors.
    d. run build script to check for build errors.

  * for flutter codebase:
    a. run flutter test & flutter analyze & flutter docter to check for errors.

5. dont commit changes.

