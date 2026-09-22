# Alpha single-line text-input specification

Source: Alpha Design System Figma node `474:811` (`单行文本框`). Use one shared TextInput recipe with three dimensions:

1. **Appearance (2):** `fill` (`Fill`) or `line` (`line`).
2. **State (5):** `default` (`Default`), `hover` (`Hover`), `inputting` (`Inputting`), `disabled` (`Disabled`), or `error` (`Error`).
3. **Size (3):** `32`, `36`, or `40` (height in px). `36` is the normal/default size; use 32 or 40 only when the surrounding density explicitly calls for it.

## Size matrix

| Size | Field height | Horizontal padding | Vertical padding | Radius | Text |
|---:|---:|---:|---:|---:|---:|
| `32` | `32px` | `10px` | `5px` | `radius-8` (`8px`) | `14px / 20px` |
| `36` | `36px` | `12px` | `6px` | `radius-8` (`8px`) | `14px / 20px` |
| `40` | `40px` | `12px` | `10px` | `radius-10` (`10px`) | `14px / 20px` |

The Figma medium reference uses `min-width: 200px` and a representative width of `300px`. Keep width controlled by the consuming layout; do not force `300px` globally.

## Appearance and state mapping

| Appearance | Default | Hover | Inputting | Disabled | Error |
|---|---|---|---|---|---|
| `fill` | `bg.sub-200` background, no border | `bg.white` + `theme.orange.primary-brand-500` border | `bg.white` + `theme.orange.primary-brand-500` border | `bg.weak-50` + `stroke.sub` border | `bg.white` + `state.error.base` border |
| `line` | `bg.white` + `stroke.sub` border | `bg.white` + `theme.orange.primary-brand-500` border | `bg.white` + `theme.orange.primary-brand-500` border | `bg.weak-50` + `stroke.sub` border | `bg.white` + `state.error.base` border |

## State behavior

- **Default:** show placeholder `请输入` using `text.soft-neutral-500`.
- **Hover:** keep placeholder and content structure; promote the border to `theme.orange.primary-brand-500`.
- **Inputting:** show the entered value in `text.strong-900` and a 16px clear icon on the trailing edge. The clear control must remove the value, not act as decoration.
- **Disabled:** use `bg.weak-50`, `stroke.sub`, and `text.soft-neutral-500`; block editing and clear actions with the native disabled/read-only API.
- **Error:** keep a 36px field shell with `state.error.base` border, then place an error message below it with `2px` spacing. Error text uses `state.error.base`, `12px / 18px`, and the message `请输入` shown in the Figma reference. For 32/40 variants, preserve the same relationship: field height follows the selected size and the message remains below the field.

## Layout and interaction

- Use `PingFang SC`, regular weight `400`, `14px` font size, `20px` line height, and single-line text.
- Use the native input or framework input primitive. Keep the value, placeholder, disabled/read-only, and error state semantic—not styling-only classes.
- Clear icon size is `16px`; it appears only while inputting and must have an accessible name such as “清除内容”.
- Preserve `:focus-visible` with an accessible focus indicator. Focus is not a substitute for hover or error styling.
- Keep the input's height stable between default, hover, and inputting states. Error text increases the overall component height but must not resize the field itself.
- Do not invent loading, success, or warning variants. Add them only after an approved Alpha token and component specification exist.
