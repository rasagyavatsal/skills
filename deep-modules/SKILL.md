---
name: deep-modules
description: Guides software design toward deep modules by minimizing interface surface area and hiding complexity behind simpler abstractions. Use when a user asks about module boundaries, API design, reducing coupling, simplifying parameters, hiding implementation details, or comparing shallow vs deep modules.
---

# Deep Modules

## Quick Start

Core idea: prefer a small interface with substantial implementation behind it.

When reviewing a module, ask:

- Can the public surface area be smaller?
- Can the parameters or configuration be simpler?
- Can more sequencing, branching, or validation move inside the module?

## Signals

Deep module:

- Few entry points
- Simple parameters
- Callers need little internal knowledge
- Complex logic is encapsulated

Shallow module:

- Many methods or flags
- Thin pass-through behavior
- Callers must coordinate multiple steps
- Internal details leak into the API

## Workflow

1. Identify the current public interface.
2. List what callers must know to use it correctly.
3. Look for pass-through methods, duplicated rules, or setup spread across call sites.
4. Collapse related operations behind fewer entry points where that improves clarity.
5. Move validation, sequencing, and edge-case handling inward.
6. Re-check whether call sites became shorter and easier to understand.

## Guardrails

- Do not hide important domain semantics just to make an API smaller.
- Do not generalize prematurely; deeper is not the same as more abstract.
- Prefer clearer interfaces over clever ones.
- Judge success by whether callers become simpler, not whether implementation gets bigger.

## Review Checklist

- [ ] Interface exposes only what callers truly need
- [ ] Parameter list is easy to understand
- [ ] Module hides operational complexity
- [ ] Call sites are simpler after the change
- [ ] No thin wrapper methods remain without strong reason
