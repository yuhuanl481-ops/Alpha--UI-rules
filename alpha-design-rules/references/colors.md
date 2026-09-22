# Alpha color tokens

Use this file whenever an Alpha interface contains color. Token paths are authoritative semantic identifiers; values are exact render values from the supplied Figma export.

## Text

| Token | Value |
|---|---|
| `text.dominant-950` | `#171717` |
| `text.strong-900` | `#333333` |
| `text.support-800` | `#4A4A4A` |
| `text.sub-700` | `#666666` |
| `text.muted-600` | `#737373` |
| `text.soft-neutral-500` | `#909399` |
| `text.soft-blue-400` | `#999999` |
| `text.disabled-300` | `#C3C6C8` |
| `text.white-0` | `#FFFFFF` |

## Background

| Token | Value |
|---|---|
| `bg.button-disabled` | `#D5D5D5` |
| `bg.strong-hover-250` | `#F0F0F7` |
| `bg.sub-200` | `#F6F7F9` |
| `bg.sub-hover-150` | `#F8F9FA` |
| `bg.soft-100` | `#F9FAFC` |
| `bg.weak-50` | `#FBFBFC` |
| `bg.white` | `#FFFFFF` |

## Icon

| Token | Value |
|---|---|
| `icon.dominant-950` | `#171717` |
| `icon.strong-900` | `#333333` |
| `icon.support-800` | `#4A4A4A` |
| `icon.sub-700` | `#666666` |
| `icon.muted-600` | `#737373` |
| `icon.soft-neutral-400` | `#999999` |
| `icon.disabled-350` | `#C3C6C8` |
| `icon.disabled-300` | `#D5D5D5` |
| `icon.white` | `#FFFFFF` |

## Stroke

| Token | Value |
|---|---|
| `stroke.strong` | `#DBDDDE` |
| `stroke.sub` | `#EBEBEE` |

## State

State families are reserved for status and feedback. `base` is the principal status color; `light` and `lighter` are progressively softer supporting treatments. Do not use them as ordinary brand or decoration colors.

| Token | Value |
|---|---|
| `state.success.base` | `#68C23B` |
| `state.success.light` | `#C4E9AD` |
| `state.success.lighter` | `#F1FAEB` |
| `state.error.base` | `#F6535C` |
| `state.error.light` | `#FECDCD` |
| `state.error.lighter` | `#FFF2F1` |
| `state.warning.base` | `#FA8919` |
| `state.warning.light` | `#FFD5AB` |
| `state.warning.lighter` | `#FFFAF6` |
| `state.information.base` | `#3E7CF9` |
| `state.information.light` | `#BED8FF` |
| `state.information.lighter` | `#EFF5FF` |

## Overlay

| Token | Value | Alpha | Render form |
|---|---:|---:|---|
| `overlay.overlay` | `#171717` | `0.5` | `rgba(23, 23, 23, 0.5)` |

All tokens other than `overlay.overlay` have alpha `1` in the source file.

## Selection rules

- Choose the category from the element type first, then select the semantic strength within that category.
- Never substitute an equal hex value from another category. For example, text must use a `text.*` token even if an `icon.*` token renders identically.
- Disabled text, icons, and backgrounds use their category-specific disabled tokens.
- Use `stroke.strong` or `stroke.sub` only for borders, dividers, and strokes according to their intended visual emphasis.
- Use `overlay.overlay` exactly as supplied. Do not apply 50% opacity a second time to its already-defined alpha.
- The orange theme defines the general primary/brand/action family. Use the `theme.orange.*` tokens for those roles rather than borrowing a state token.
