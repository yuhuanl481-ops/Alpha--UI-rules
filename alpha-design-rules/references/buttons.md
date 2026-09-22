# Alpha button specification

Source: Alpha Design System Figma node `402:1029` (`按钮`). Use one shared button model and choose values across four independent dimensions:

1. **Family (2):** `normal` (`主要`) or `error` (`Error`).
2. **Importance/style (7):** choose exactly one approved tier from the table below. These names are the normalized Alpha specification; they take precedence over duplicate or incorrect `样式` names in the source Figma instances.
3. **State (4):** `default` (`默认`), `hover` (`悬浮`), `pressed` (`点击`), or `disabled` (`禁用`).
4. **Size (4):** `40`, `36`, `32`, or `28` (height in px).

The Figma component also supports **icon placement** independently: `none`, `left`, `right`, or `only` (icon-only). Icon placement is not an importance level. This separation keeps the implementation small while covering all Figma variants.

## Seven importance styles

| Style | Normal family default | Error family default | Use when |
|---|---|---|---|
| `primary` 主要按钮 | `theme.orange.primary-brand-500` fill + white content | `state.error.base` fill + white content | The single strongest action in a region |
| `secondary` 次要按钮 | `bg.white` + `theme.orange.primary-brand-500` border/content | `bg.white` + `state.error.base` border/content | An important alternative action |
| `soft` 弱化按钮 | `theme.orange.primary-bg-light-50` fill + primary content | `state.error.lighter` fill + error content | A supportive action with a tinted surface |
| `accent-outline` 强调描边按钮 | `bg.white` + `theme.orange.primary-accent-700` border/content | `bg.white` + `state.error.light` border/content | A stronger outlined action without a filled surface |
| `neutral-outline` 中性描边按钮 | `bg.white` + `stroke.sub` border + `text.support-800` content | `bg.white` + `stroke.sub` border + `text.support-800` content | A low-emphasis bordered action |
| `text-primary` 主要文字按钮 | Transparent + `theme.orange.primary-brand-500` content | Transparent + `state.error.base` content | Inline or low-chrome primary action |
| `text-neutral` 中性文字按钮 | Transparent + `text.strong-900` content | Transparent + `text.support-800` content | Inline, tertiary, or utility action |

The seven styles are the importance axis. Do not collapse them into four because the source component property is mislabeled; do not add an eighth tier without an approved design-system change.

For `hover`, `pressed`, and `disabled`, keep the same family/style structure and swap only the corresponding state tokens. Never use normal orange tokens in the error family or error tokens in the normal family.

## State mapping

| State | Normal family | Error family | Interaction requirement |
|---|---|---|---|
| default | Base style tokens | Error base style tokens | Resting appearance; actionable when enabled |
| hover | `theme.orange.primary-hover-400` for primary emphasis; `theme.orange.primary-bg-light-50` for secondary/weak surfaces | Use the matching lighter error treatment from `state.error.light`/`lighter` | Apply only on pointer hover; preserve keyboard focus visibility |
| pressed | `theme.orange.primary-text-800` or the Figma pressed token for the selected style | `state.error.base` with pressed treatment | Must be visibly distinct from default and hover |
| disabled | `theme.orange.primary-disabled-300` for primary; `bg.sub-hover-150` + `text.soft-neutral-500` for secondary/text | Use disabled neutral treatment with `text.soft-neutral-500` | Use the native disabled state; no click/hover action |

If a state-specific token is not explicitly present in the source tokens, do not synthesize a new color. Keep the state mapping documented as unresolved and request an approved token.

## Size matrix

| Size | Height | Horizontal padding | Vertical padding | Text | Icon | Radius |
|---:|---:|---:|---:|---:|---:|---:|
| `40` | `40px` | `16px` | `10px` | `14px / 20px` | `20px` | `radius-10` |
| `36` | `36px` | `16px` | `8px` | `14px / 20px` | `20px` | `radius-8` |
| `32` | `32px` | `12px` | `6px` | `14px / 20px` | `16px` | `radius-8` |
| `28` | `28px` | `8px` | `5px` | `13px / 18px` | `16px` | `radius-8` |

The Figma instances use `min-width: 72px`. Preserve that minimum for text buttons; icon-only buttons may use a square dimension appropriate to the chosen size. Icon + label layouts use a `4px` gap for left icons and a `6px` gap for right icons at size 40; scale to the closest documented spacing in the target system rather than adding arbitrary values.

## Implementation rules

- Choose family first, then importance/style, then state, then size; icon placement is orthogonal.
- Keep the same dimensions across states. State changes must not cause layout shift.
- Use `PingFang SC`, weight `500`, with the size-specific line height above unless the project already provides the approved equivalent.
- Use the native button element/API, expose an accessible name for icon-only buttons, and preserve `:focus-visible` even when Figma only shows default/hover/pressed/disabled.
- Do not enumerate or create hundreds of bespoke components. Implement one Button component or tokenized style recipe with these dimensions.
- The two families, seven importance styles, four states, four sizes, and independent icon placement form one reusable Button recipe. Do not enumerate bespoke components for each combination.
