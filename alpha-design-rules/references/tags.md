# Alpha tag specification

Source: Alpha Design System Figma node `598:5815` (`标签`). Use one shared Tag recipe with three independent dimensions:

1. **Style (3):** `light` (`浅色`), `solid` (`填充`), or `outline` (`描边`).
2. **Color (8):** `orange` (`橙色`), `cyan` (`青色`), `pink` (`粉色`), `blue` (`蓝色`), `purple` (`紫色`), `green` (`绿色`), `red` (`红色`), or `gray` (`灰色`).
3. **Shape (2):** `regular` (`胶囊标签=off`) or `pill` (`胶囊标签=on`).

Do not enumerate every combination as a separate component. Select the style, color, and shape, then apply the token recipe below.

## Shared geometry and typography

- Text: `PingFang SC`, weight `500`, `12px` font size, `18px` line height, no wrapping.
- Regular tag: horizontal padding `radius-6` (`6px`), vertical padding `1px`, `radius-4` (`4px`) corners.
- Pill tag: horizontal padding `radius-8` (`8px`), vertical padding `1px`, `radius-full` (`999px`) corners.
- Tags are content-width by default; do not stretch them to fill a container unless the surrounding component explicitly requires it.
- A regular tag uses a `0.5px` border for the light style and a `1px` border for outline. Preserve these border widths exactly.

## Color recipe

| Color | Text / foreground | Light background | Light border | Solid background | Outline border |
|---|---|---|---|---|---|
| `orange` | `theme.orange.primary-brand-500` | `#FFF6EE` | `#FFD6AE` | `theme.orange.primary-brand-500` | `theme.orange.primary-brand-500` |
| `cyan` | `#079FAE` | `#ECFAFB` | `#A9E2E7` | `#079FAE` | `#079FAE` |
| `pink` | `#E85287` | `#FFF1F6` | `#F6C0D4` | `#E85287` | `#E85287` |
| `blue` | `#3E7CF9` | `#F2F9FF` | `#D1EBFF` | `#3E7CF9` | `#3E7CF9` |
| `purple` | `#6766E6` | `#F2F2FF` | `#D1D1FF` | `#6766E6` | `#6766E6` |
| `green` | `#00B36D` | `#E8F8F4` | `#ADE7D1` | `#00B36D` | `#00B36D` |
| `red` | `#F26649` | `#FFF4F2` | `#FFD9D1` | `#F26649` | `#F26649` |
| `gray` | `text.muted-600` (`#737373`) | `#FBFBFD` | `#E6E6E6` | `text.muted-600` | `text.muted-600` |

The supplied Figma tag node includes several tag-specific color values that are not yet represented by the global color-token JSON. Preserve them as tag-scoped values only; do not promote them to global palette tokens or reuse them for unrelated components without an approved token update.

## Style behavior

- `light`: use the color-specific light background, `0.5px` light border, and color foreground.
- `solid`: use the color foreground as background and `text.white-0` for text/icons.
- `outline`: use `bg.white`/transparent surface, `1px` color border, and color foreground.
- Shape changes only padding and radius. It must not change the selected color or style semantics.
- There are no hover, pressed, or disabled variants in this Figma tag component. Do not invent interactive states; if a tag becomes interactive, use a Button or another approved interactive component recipe.
- Keep tag labels short and single-line. Truncation or wrapping behavior must be specified by the consuming component, not inferred here.
