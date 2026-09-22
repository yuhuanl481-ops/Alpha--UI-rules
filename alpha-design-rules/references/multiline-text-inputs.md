# Alpha multiline text-input specification

Source: Alpha Design System Figma node `476:1071` (`多行文本`). The supplied frame is the `输入框40` variant. Use one shared Textarea recipe with two dimensions:

1. **Appearance (2):** `fill` (`fill`) or `line` (`line`).
2. **State (5):** `default` (`默认`), `hover` (`悬浮`), `inputting` (`输入中`), `disabled` (`禁用`), or `error` (`Error`/`报错`).

The source node exposes a `76px` text-entry area, followed by a counter/help row. Do not substitute the single-line input heights for this multiline component. If other textarea heights are later supplied from Figma, add them as explicit variants rather than deriving them from the single-line sizes.

## Geometry and typography

- Text-entry area: `76px` high, full component width.
- Inner padding: `12px` horizontal and `8px` vertical.
- Field radius: `radius-8` (`8px`).
- Text: `PingFang SC`, regular weight `400`, `14px` font size, `24px` line height, top-aligned, multi-line capable.
- Counter/help row: `12px` text. The row sits `2px` below the field and uses `4px` horizontal padding.
- Placeholder: `请填写项目详情`, using `text.soft-neutral-500`.
- Inputting content: use `text.strong-900`; the Figma sample shows `自由如风，热烈无畏|` with the caret at the end.

## Appearance and state mapping

| Appearance | Default | Hover | Inputting | Disabled | Error |
|---|---|---|---|---|---|
| `fill` | `bg.sub-hover-150` background, no border | `bg.sub-hover-150` + `theme.orange.primary-brand-500` border | `bg.sub-hover-150` + `theme.orange.primary-brand-500` border | `bg.weak-50` + `stroke.sub` border | `bg.sub-hover-150` + `state.error.base` border |
| `line` | `bg.white` + `stroke.sub` border | `bg.white` + `theme.orange.primary-brand-500` border | `bg.white` + `theme.orange.primary-brand-500` border | `bg.weak-50` + `stroke.sub` border | `bg.white` + `state.error.base` border |

## Counter and error behavior

- Default, hover, inputting, and disabled states show a right-aligned counter in the form `0/1000`; the inputting and disabled examples in Figma show `10/1000`.
- The counter is not decorative. It must reflect the actual value length and the configured maximum.
- Error state replaces the simple counter row with an error message on the left (`请输入`) using `state.error.base`, while the right side shows `1000/1000`; the denominator remains the configured maximum in real implementations.
- Keep the `2px` gap between the 76px field and the counter/error row. Error text uses `12px / 18px`.
- The field itself remains 76px high in every state; only the overall component height grows to accommodate the counter/error row.

## Interaction and accessibility

- Use a native `<textarea>` or the framework's accessible textarea primitive. Keep value, max length, disabled/read-only, and error semantics in the control API.
- Enforce the configured maximum length and expose it to assistive technology where supported.
- Preserve `:focus-visible` with an accessible focus indicator; focus is independent of hover and error styling.
- Do not hide overflow or clip user content. The textarea may scroll vertically when the content exceeds the visible area.
- If a clear action is added by a consuming component, it must be a separate accessible button; the base Figma component does not define a clear icon.
- Do not invent loading, success, or warning variants. Add them only after an approved Alpha token and component specification exist.
