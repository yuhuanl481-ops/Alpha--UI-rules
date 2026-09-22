---
name: alpha-design-rules
description: Use when creating, modifying, or reviewing Alpha product interfaces, design mockups, UI specifications, frontend styles, or component visuals that must conform to the Alpha design system.
---

# Alpha Design Rules

Apply Alpha design tokens as hard constraints to every in-scope visual decision. Preserve the user's product requirements, but do not invent visual values when the Alpha system provides or requires a token.

## Current scope

This version defines color, orange-theme, corner-radius, button, tag, checkbox, search-input, text-input, and multiline-text-input rules. Do not imply that typography, spacing, shadow, layout, or other component behavior has already been standardized here; those foundations will be added later.

Before choosing, generating, editing, or reviewing any color, read [references/colors.md](references/colors.md). For the orange theme, also read [references/orange-theme.md](references/orange-theme.md). Consult [references/alpha-colors.json](references/alpha-colors.json) or [references/orange-theme.tokens.json](references/orange-theme.tokens.json) when exact source metadata, Figma variable aliases, sRGB components, or alpha values are needed.

Before choosing, generating, editing, or reviewing corner radii, read [references/radii.md](references/radii.md). Consult [references/mode-1-radii.tokens.json](references/mode-1-radii.tokens.json) when exact source metadata or numeric values are needed.

Before choosing, generating, editing, or reviewing a button, read [references/buttons.md](references/buttons.md). The button reference is distilled from Figma node `402:1029` and is intentionally expressed as composable dimensions rather than a list of every instance. Use the seven approved importance styles in that reference even where the source Figma instances have duplicate or inaccurate style names.

Before choosing, generating, editing, or reviewing a tag, read [references/tags.md](references/tags.md). The tag reference is distilled from Figma node `598:5815` and is expressed as one compact recipe.

Before choosing, generating, editing, or reviewing a checkbox, read [references/checkboxes.md](references/checkboxes.md). The checkbox reference is distilled from Figma node `815:4869` and is expressed as one compact state recipe.

Before choosing, generating, editing, or reviewing a search input, read [references/search-inputs.md](references/search-inputs.md). The search-input reference is distilled from Figma node `482:5823` and treats 36px as the default height.

Before choosing, generating, editing, or reviewing a single-line text input, read [references/text-inputs.md](references/text-inputs.md). The text-input reference is distilled from Figma node `474:811` and treats 36px as the default height.

Before choosing, generating, editing, or reviewing a multiline text input, read [references/multiline-text-inputs.md](references/multiline-text-inputs.md). The multiline reference is distilled from Figma node `476:1071` and preserves its 76px input area and character-counter layout.

## Required color behavior

1. Select colors by semantic role, not by visual similarity or personal preference.
2. Use only tokens listed in the color reference. Match the token's hex value and alpha exactly.
3. Keep token categories separate: text for text, bg for surfaces, icon for icons, stroke for borders/dividers, state for feedback, and overlay for modal or blocking overlays.
4. Reuse the token name in design specs and code when the target format supports tokens or variables. If a literal value is unavoidable, annotate it with the corresponding token path.
5. Do not introduce raw hex, RGB, HSL, named colors, gradients, adjusted opacity, derived tints, or visually similar replacements that are absent from the reference.
6. Do not reinterpret a state color as a general brand or action color. In particular, `state.warning.*` remains warning-only even though `state.warning.base` currently shares the same rendered value as `theme.orange.primary-brand-500`.
7. When no suitable token exists, keep the decision unresolved and report the missing semantic token. Ask for an approved token instead of inventing one.
8. Preserve existing compliant colors during unrelated edits. When reviewing, identify each noncompliant value, its location, and the closest semantically correct token only when the intended role is clear.

## Output expectations

- For design descriptions or mockup specifications, name every applied color by full token path, such as `text.sub-700`.
- For implementation, prefer the project's established token mechanism. Do not create a second naming system merely to mirror this reference.
- For generated images or tools that cannot bind design tokens, use the exact rendered values and include a short token-to-element mapping in the handoff.
- If a request conflicts with this skill, surface the conflict explicitly and wait for the user to approve a design-system exception.

## Required radius behavior

1. Use only radius tokens listed in the radius reference. Match the source number exactly.
2. Select a radius by component role and interaction pattern, not by visual preference or arbitrary proportional scaling.
3. Do not introduce raw radius values, percentages, `9999px`, or custom calculations when an approved radius token is available.
4. Use `radius-full` only for fully pill-shaped or circular treatments. Do not use it as a generic replacement for smaller component radii.
5. Preserve the token name in design specifications and code when the target format supports variables. If a literal value is unavoidable, annotate it with the corresponding token path.
6. The source values are unitless Figma numbers. Preserve the number across platforms; when a target implementation requires a unit (such as CSS), use the platform's appropriate unit mapping without changing the token's numeric value.
7. When no suitable radius exists, report the missing semantic token and ask for an approved value instead of inventing one.
