# Alpha search-input specification

Source: Alpha Design System Figma node `482:5823` (`搜索框`). Use one shared SearchInput recipe with three dimensions:

1. **Appearance (2):** `fill` (`Fill`) or `line` (`line`).
2. **State (4):** `default` (`Default`), `hover` (`Hover`), `inputting` (`Inputting`), or `disabled` (`Disabled`).
3. **Size (3):** `32`, `36`, or `40` (height in px). `36` is the normal/default size; use 32 or 40 only when the surrounding density explicitly calls for it.

## Size matrix

| Size | Height | Horizontal padding | Radius | Text size/line height | Icon size |
|---:|---:|---:|---:|---:|---:|
| `32` | `32px` | `10px` | `radius-8` (`8px`) | `14px / 20px` | `16px` |
| `36` | `36px` | `12px` | `radius-8` (`8px`) | `14px / 20px` | `20px` |
| `40` | `40px` | `12px` | `radius-10` (`10px`) | `14px / 20px` | `20px` |

Keep the default minimum width at `200px`; the Figma reference uses a wider 250–300px presentation depending on the state/content arrangement. Do not force a fixed width when the consuming layout supplies one.

## Appearance and state mapping

| Appearance | Default | Hover | Inputting | Disabled |
|---|---|---|---|---|
| `fill` | `bg.sub-200` background, no border | `bg.white` + `theme.orange.primary-brand-500` border | `bg.white` + `theme.orange.primary-brand-500` border | `bg.weak-50` + `stroke.sub` border |
| `line` | `bg.white` + `stroke.sub` border | `bg.white` + `theme.orange.primary-brand-500` border | `bg.white` + `theme.orange.primary-brand-500` border | `bg.weak-50` + `stroke.sub` border |

State semantics:

- **Default:** show the leading search icon, placeholder `请输入`, trailing separator, and `搜索` action.
- **Hover:** keep the same structure as default and promote the border/icon/action to the hover treatment.
- **Inputting:** show the entered value in `text.strong-900`, a 16px clear icon, and a 20px search icon/action. The clear control must remove the value; it is not decorative.
- **Disabled:** preserve the default structure but use `text.soft-neutral-500`, `bg.weak-50`, and `stroke.sub`; block editing, clear, and search actions.

## Layout and interaction

- Use `PingFang SC`, regular weight `400`, `14px` font size, `20px` line height, and single-line text.
- The leading search icon is 20px at the 36/40 sizes and 16px at size 32. The input and icons are vertically centered.
- Use an `8px` gap between the leading icon and text. In the action area, use a `12px` gap around the 14px vertical separator and the `搜索` label.
- In `inputting`, place the clear icon before the search action; the clear icon is 16px and the search icon remains the size-specific search icon.
- Keep the search action as a real button with an accessible name. Keep the clear action as a separate real button with an accessible name such as “清除搜索内容”.
- Use a native input or framework input primitive. `disabled` must be a real disabled/read-only control, not only a muted style.
- Preserve `:focus-visible`; the Figma state matrix does not replace keyboard focus behavior.
- Do not invent loading, error, or pressed search-input variants. If needed, extend this recipe only with an approved Alpha token and documented state.
