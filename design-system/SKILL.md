---
name: design-system
description: Create and maintain a DESIGN-SYSTEM.md file by auditing the codebase for components, patterns, and foundational elements. Use when the user mentions "design system", "component library", "style guide", or wants to document visual and technical standards.
---

# Design System

Manage and document the product ecosystem's visual language, component libraries, and design principles.

## Quick start

To initialize or update the design system documentation:
1. Run a codebase audit for design tokens (CSS variables, theme files) and components.
2. Create/update `DESIGN-SYSTEM.md` at the project root.

## Hierarchy

1. **Design System**: Overarching guidance, principles, and processes.
2. **Component & Pattern Libraries**: Reusable UI elements (buttons, inputs) and broader solutions (flows, layouts).
3. **Foundational Elements**: Visual language (colors, typography, icons) and accessibility guidelines.

## Workflows

### 1. Initialization & Audit
When asked to create a design system:
- **Foundations**: Search for `variables.css`, `theme.ts`, or Tailwind configs to extract colors, spacing, and typography.
- **Components**: Identify reusable UI components (e.g., in `src/components`) and categorize them.
- **Documentation**: Create `DESIGN-SYSTEM.md` using the standard hierarchy.

### 2. Maintenance & Sync
When a new component or token is added:
- Update the corresponding section in `DESIGN-SYSTEM.md`.
- Ensure technical specs and code snippets are current.
- Check for consistency with established design principles.

### 3. Gap Analysis
- Identify "one-off" styles that should be converted to tokens.
- Flag redundant components that could be consolidated into the pattern library.
