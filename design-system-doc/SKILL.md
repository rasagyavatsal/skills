---
name: design-system-doc
description: Create or update a `DESIGN-SYSTEM.md` file by auditing a repo's UI foundations, tokens, components, patterns, accessibility, content, tooling, and governance. Use when user asks to document a design system, inventory UI primitives, audit consistency, or maintain `DESIGN-SYSTEM.md` in a codebase.
---

# Design System Doc

Use this skill to create or refresh `DESIGN-SYSTEM.md` in repo root.

Read [references/design-system-map.md](references/design-system-map.md) before writing. Use [references/design-system-template.md](references/design-system-template.md) as the default shape.

## Workflow

1. Find repo root and existing system docs.
   - Look for `DESIGN-SYSTEM.md`, `README*`, `docs/`, Storybook, theme files, token files, component packages, and contribution docs.
2. Inventory actual evidence in codebase.
   - Foundations: color, typography, spacing, layout/grid, radius, border, elevation/shadow, motion, iconography, illustration, brand assets.
   - Tokens and theming: CSS vars, JSON/YAML token files, Style Dictionary, Tailwind theme, dark/light themes, multi-brand themes.
   - UI building blocks: primitives, components, states, variants, responsive rules.
   - Patterns: flows, page shells, templates, form recipes, navigation, feedback, data display.
   - Quality rails: accessibility, content/voice, i18n, testing, linting, visual regression.
   - Delivery: packages, code libraries, Figma/design libraries, docs site, Storybook.
   - Governance: owners, contribution path, review rules, lifecycle, release cadence, roadmap.
3. Read existing `DESIGN-SYSTEM.md` if present.
   - Preserve clearly intentional project-specific notes.
   - Replace stale facts. Do not keep contradictions.
4. Write concise current-state documentation.
   - Separate observed facts from inference.
   - If evidence is missing, write `Not yet documented` or `Open question` instead of guessing.
5. End with gaps and next steps.
   - If repo has partial system only, document current state and missing pieces.

## Search Hints

- `rg -n "design token|tokens|theme|theming|semantic|--[a-z0-9-]+|style dictionary|tailwind|theme.extend"`
- `rg -n "components|primitives|patterns|templates|storybook|stories|figma|zeroheight"`
- `rg -n "a11y|accessibility|aria|wcag|contrast|alt text|keyboard"`
- `rg -n "content|copy|voice|tone|microcopy|terminology|glossary"`
- `rg -n "contributing|governance|owner|maintainer|review|release|roadmap|changelog"`

## Output Rules

- Default path: repo root `DESIGN-SYSTEM.md`.
- Prefer grouped categories over dumping long component lists.
- Document what exists, what is missing, and what is inferred.
- Keep guidance repo-specific. Web research defines structure, not repo facts.
