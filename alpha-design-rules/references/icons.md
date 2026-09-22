# Alpha icon asset specification

The following four SVG files are the approved icon sources for the search input and checkbox components. Reuse these assets directly whenever the target implementation supports SVG. Do not replace them with a Unicode glyph, icon font, third-party icon, CSS-drawn shape, or an approximate redraw.

## Approved assets

| Asset | Original supplied file | Intrinsic size / viewBox | Fill(s) | Use |
|---|---|---|---|---|
| [`search-line.svg`](../assets/icons/search-line.svg) | `icon-search-line.svg` | `20×20`, `0 0 20 20` | `#C3C6C8` | Search input leading/search-action icon. At 32px input height, render this same asset at 16px only when the component's size recipe calls for 16px. Do not redraw or stretch it non-proportionally. |
| [`search-close-fill.svg`](../assets/icons/search-close-fill.svg) | `icon-close-fill.svg` | `16×16`, `0 0 16 16` | `#C3C6C8` | Search input clear action in the `inputting` state. |
| [`checkbox-checked-default.svg`](../assets/icons/checkbox-checked-default.svg) | `样式=默认, 选中=on, 复选=off.svg` | `16×16`, `0 0 16 16` | Outer `#FA8919`; check `#FFFFFF` | Checkbox `checked` + `normal` + `default` treatment. |
| [`checkbox-indeterminate-default.svg`](../assets/icons/checkbox-indeterminate-default.svg) | `样式=默认, 选中=off, 复选=on.svg` | `16×16`, `0 0 16 16` | Outer `#FA8919`; inner mark `#FA8919`; white separator layer | Checkbox `indeterminate` + `default` treatment. |

## State mapping

- Search input: use `search-line.svg` for the leading icon and search action in every enabled state; use `search-close-fill.svg` only for the clear action while `inputting`. Keep the supplied 20px/16px dimensions from [search-inputs.md](search-inputs.md). The supplied path and `#C3C6C8` fill are canonical; do not substitute a different magnifying-glass or close shape. If a future approved state-specific asset is supplied, use that asset explicitly rather than recoloring this one.
- Checkbox: use `checkbox-checked-default.svg` for the default checked visual and `checkbox-indeterminate-default.svg` for the default indeterminate visual. For hover, pressed, or disabled variants that do not have a supplied file, preserve the exact 16px viewBox, geometry, corner radii, and check/indeterminate paths from the corresponding canonical asset and change only the fills required by the checkbox state matrix. Never use a text checkmark or CSS pseudo-element as a substitute.
- Unchecked normal checkboxes have no check/indeterminate mark; use the box treatment in [checkboxes.md](checkboxes.md). Do not place a supplied checked asset over an unchecked state.

## Implementation requirements

1. Keep each asset's `viewBox`, aspect ratio, and intrinsic geometry. Do not crop, rotate, mirror, outline, add a drop shadow, or apply a filter.
2. When an icon must be exposed as a button, keep the SVG as the visual child of a real accessible button; the asset itself is not the hit target or accessible name.
3. If the platform cannot load the asset file, inline the same SVG markup (including paths, dimensions, viewBox, and fills) rather than approximating it. Record the asset path in the implementation handoff.
