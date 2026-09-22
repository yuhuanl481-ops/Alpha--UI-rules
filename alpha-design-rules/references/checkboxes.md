# Alpha checkbox specification

Source: Alpha Design System Figma node `815:4869` (`复选框`). Use one checkbox recipe with three independent dimensions:

1. **State (4):** `default` (`默认`), `hover` (`悬浮`), `pressed` (`点击`), or `disabled` (`禁用`).
2. **Selection (2):** `unchecked` (`选中=off`) or `checked` (`选中=on`).
3. **Mode (2):** `normal` (`复选=off`) or `indeterminate` (`复选=on`).

The source exposes 16 combinations. `indeterminate` is the half-selected state and must not be represented as a checked state with a decorative mark.

## Geometry

- Outer control box: `16px × 16px`.
- Outer colored/neutral layer: `14px × 14px`, centered, `radius-4` (`4px`).
- Inner layer: `12px × 12px`, centered, `radius-?` source value `3px`. Because the current radius token file does not define `radius-3`, keep this as a checkbox-local primitive and do not promote it to a global radius token without approval.
- Indeterminate mark: `8px × 8px`, centered, `2px` corners. The source uses `radius-2` behavior; treat it as checkbox-local until a global radius-2 token is supplied.
- Keep the control at 16px in every state so state changes never shift adjacent content.

## State matrix

| State | Unchecked | Checked | Indeterminate |
|---|---|---|---|
| `default` | Neutral disabled-looking outline layer `icon.disabled-350` + white inner layer, as shown in the source | Orange selected asset/treatment with white check mark | `theme.orange.primary-brand-500` outer layer + white inner layer + orange `8px` center mark |
| `hover` | `theme.orange.primary-brand-500` outer layer + white inner layer | Orange hover selected asset/treatment | `theme.orange.primary-hover-400` outer layer + white inner layer + matching `8px` center mark |
| `pressed` | `theme.orange.primary-accent-700` outer layer + white inner layer | Orange pressed selected asset/treatment | `theme.orange.primary-accent-700` outer layer + white inner layer + matching `8px` center mark |
| `disabled` | `stroke.strong` outer layer + `bg.sub-hover-150` inner layer | Disabled selected asset/treatment from the Figma source | `stroke.strong` outer layer + white inner layer + `stroke.strong` center mark |

The Figma source represents checked states partly through supplied SVG assets. When implementing, use the project's icon/asset mechanism or an equivalent accessible check mark; do not substitute a text glyph whose shape or baseline differs.

## Interaction and accessibility

- Use a native checkbox control or the framework's accessible checkbox primitive. Keep `checked`, `indeterminate`, and `disabled` as real control state, not styling-only classes.
- `hover` and `pressed` are visual interaction states; `default` and `disabled` are persistent states.
- Preserve `:focus-visible` with an accessible focus indicator even though the Figma matrix does not show a separate focus variant.
- The checkbox needs an accessible name from its associated label or an explicit `aria-label` when no visible label exists.
- Clicking the label should toggle the checkbox when a label is present. Do not make the 16px visual box the only hit target in product UI.
- Do not invent error, loading, or mixed-color variants. If an error state is required, request an approved checkbox-specific error treatment or use the established form-field error pattern.
