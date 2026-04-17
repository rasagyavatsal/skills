# Design System Map

Research snapshot: 2026-04-17.

Design system is more than component library. Across Material, Carbon, Atlassian, GOV.UK, Primer, and DTCG, same shape appears:

- Foundations and reusable decisions
- Components and patterns
- Guidance for content and accessibility
- Design and code assets
- Tooling, docs, governance, release/adoption model

## Source-backed takeaways

- Material: design system = reusable design decisions expressed as guidance, components, and patterns; primitives like color, type, and shape build into larger UI pieces.
- Carbon: design system includes working code, design tools/resources, human interface guidance, patterns, and contributor community.
- Atlassian: foundations include tokens, accessibility, content, and visual styles; system also includes components, patterns, tools, and release phases.
- GOV.UK: design system packages styles, components, patterns, accessibility principles, community input, support, and roadmap.
- Primer: strong foundations alone are not enough; patterns should account for responsiveness, themeability, accessibility, content, interaction states, documentation/APIs, and Figma assets.
- DTCG: tokens are foundational data for sharing visual language reliably across tools, codebases, and platforms.

## Constituent Model

Use this as audit model for `DESIGN-SYSTEM.md`.

| Pillar | What to document | Typical evidence in repo |
| --- | --- | --- |
| Purpose and scope | Why system exists, products/platforms covered, users/teams served | README, docs home, architecture docs |
| Principles | Explicit design principles, UX tenets, brand rules, decision criteria | design docs, contribution docs, principles pages |
| Foundations | Color, typography, spacing, layout/grid, shape/radius, border, elevation/shadow, motion, iconography, illustration, brand assets | theme files, CSS vars, tokens, style guides |
| Design tokens | Raw and semantic tokens, naming scheme, aliasing, token tiers, platform export model | token JSON/YAML, Style Dictionary, theme packages |
| Themes and brands | Light/dark, density, locale, brand, platform variants | theme files, mode switches, multi-brand configs |
| Primitives | Low-level layout and style building blocks | `Box`, `Stack`, `Text`, `Grid`, utility classes |
| Components | Reusable UI pieces, states, variants, sizes, composition rules, API contracts | component folders, stories, tests, docs |
| Patterns and templates | Reusable flows, page recipes, form patterns, navigation shells, data-display recipes | docs, examples, app shells, route templates |
| Content design | Voice and tone, grammar, terminology, message design, microcopy rules | content guides, glossary, copy docs |
| Accessibility | WCAG baseline, semantic rules, keyboard support, contrast, motion, testing expectations | a11y docs, lint rules, tests, annotations |
| Implementation assets | Figma libraries, icons, illustrations, code libraries, platform ports | design file references, package manifests |
| Documentation | Usage guidance, examples, do/don'ts, migration notes, API docs | docs site, Storybook, MDX, markdown |
| Tooling and QA | Build system, linting, token pipelines, codegen, visual regression, test harnesses | CI config, scripts, Storybook, Chromatic, ESLint |
| Governance | Ownership, contribution model, review flow, lifecycle, deprecation, RFC process | CONTRIBUTING, CODEOWNERS, ADRs, issue templates |
| Release and adoption | Versioning, changelog, roadmap, release phases, training/support | changelog, releases, roadmap docs, office hours |

## What Usually Belongs Under Foundations

Most mature systems treat these as first-class:

- Color
- Typography
- Spacing
- Layout or grid
- Shape or radius
- Border and stroke
- Elevation or shadow
- Motion
- Iconography
- Illustration
- Brand or logo guidance
- Content and accessibility guidance

Not every repo will expose all of them in code. Document only what exists.

## Distinguish These Layers

- Token: named design decision stored as data
- Foundation: system-level rule set such as spacing scale or type scale
- Primitive: low-level building block used to compose components
- Component: reusable UI element with behavior and states
- Pattern: multi-component solution for recurring task or flow
- Template: page-level arrangement or shell
- Guidance: rules for correct usage, content, accessibility, and implementation
- Governance: how system evolves without drifting

## Writing Rules For `DESIGN-SYSTEM.md`

- Prefer facts from repo over generic theory.
- If repo lacks formal design system, document current UI system as-is.
- Use grouped categories, not giant component dumps.
- Call out unknowns explicitly.
- Separate `Current state` from `Recommended next steps`.
- Preserve useful project-specific notes when updating existing file.

## Source URLs

- Material Components: https://developer.android.com/design/ui/mobile/guides/components/material-overview?hl=en
- Carbon overview: https://carbondesignsystem.com/all-about-carbon/what-is-carbon/
- Atlassian foundations: https://atlassian.design/foundations/
- Atlassian accessibility: https://atlassian.design/foundations/accessibility
- GOV.UK Design System home: https://design-system.service.gov.uk/
- GOV.UK patterns: https://design-system.service.gov.uk/patterns/
- Primer design contribution guide: https://primer.style/contribute/design/
- Primer documentation guide: https://primer.style/contribute/documentation
- DTCG home: https://www.designtokens.org/
- DTCG format spec: https://www.w3.org/community/reports/design-tokens/CG-FINAL-format-20251028/
