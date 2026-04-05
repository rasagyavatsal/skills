---
name: write-an-issue
description: Create a GitHub issue through user interview, codebase exploration, and module design. Use when the user wants to write an issue or plan a new feature.
---

This skill will be invoked when the user wants to create an issue. 

1. Sketch out the major modules you will need to build or modify to complete the implementation. Actively look for opportunities to extract deep modules that can be tested in isolation.

A deep module (as opposed to a shallow module) is one which encapsulates a lot of functionality in a simple, testable interface which rarely changes.

2. Check with the user that these modules match their expectations. Once you have a complete understanding of the problem and solution, create a GitHub issue.

3. Be extremely concise. Sacrifice grammar for the sake of clarity.