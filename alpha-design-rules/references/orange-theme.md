# Alpha orange theme

Use these tokens for primary brand and action treatments when the active Alpha theme is `🍊橙`. These are theme-semantic tokens; do not use them for success, error, warning, or information feedback merely because a rendered value looks similar.

| Token | Source name | Value | Intended role |
|---|---|---|---|
| `theme.orange.primary-text-800` | `primary-text-800` | `#ED6C00` | Primary text or strong text treatment in the orange theme |
| `theme.orange.primary-accent-700` | `primary-accent-700` | `#FF7400` | Primary accent treatment |
| `theme.orange.primary-brand-500` | `primary-brand-500` | `#FA8919` | Primary brand/action color |
| `theme.orange.primary-hover-400` | `primary-hover-400` | `#FA9A2A` | Hover state for primary brand/action controls |
| `theme.orange.primary-disabled-300` | `primary-disabled-300` | `#FDC48C` | Disabled state for primary brand/action controls |
| `theme.orange.primary-border-hover-200` | `primary-border-hover-200` | `#FFD5AB` | Hover border or soft border treatment for primary controls |
| `theme.orange.primary-bg-light-50` | `primary-bg-light-50` | `#FFFAF6` | Light primary-tinted surface or background |

All tokens in this source have alpha `1`. Use the exact hex value; do not derive darker, lighter, transparent, gradient, or intermediate variants.

## Usage rules

- Use `theme.orange.primary-brand-500` for the default primary action/brand treatment.
- Use `theme.orange.primary-hover-400` only for the corresponding hover state; do not use it as the default primary color.
- Use `theme.orange.primary-disabled-300` only when the primary control is disabled.
- Use `theme.orange.primary-border-hover-200` for the primary control's hover-border treatment, not as a replacement for `stroke.*` on unrelated components.
- Use `theme.orange.primary-bg-light-50` for a softly tinted primary surface, not as a generic page background when a `bg.*` token is appropriate.
- Keep theme tokens separate from category tokens. A primary button background may use a theme token while its label, icon, and border still use the relevant `text.*`, `icon.*`, or `stroke.*` token.
- If a different theme is active or the active theme is unspecified, do not silently apply orange values. Ask for the active theme or report that a theme decision is missing.
