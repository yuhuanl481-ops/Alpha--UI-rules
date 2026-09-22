# Alpha corner-radius tokens

Use these tokens for component corner radii. The source file contains unitless Figma numbers; in CSS or another pixel-based implementation, map the number to the platform's radius unit while preserving its numeric value.

| Token | Source value | Common use guidance |
|---|---:|---|
| `radius-4` | `4` | Small controls, compact fields, or subtle containment |
| `radius-5` | `5` | Small control variant when the component specification calls for the 5-step value |
| `radius-6` | `6` | Small-to-medium controls and compact cards |
| `radius-8` | `8` | Standard controls, cards, and common containers |
| `radius-10` | `10` | Medium cards or controls requiring more softness |
| `radius-12` | `12` | Larger cards, panels, and grouped surfaces |
| `radius-14` | `14` | Large surface variant when explicitly required |
| `radius-16` | `16` | Prominent panels, dialogs, or large containers |
| `radius-20` | `20` | Extra-large containers or prominent feature surfaces |
| `radius-24` | `24` | Very large rounded surfaces |
| `radius-full` | `999` | Pill controls, badges, chips, or circular shapes |

## Selection rules

- Prefer the smallest token that satisfies the component's approved visual role; do not choose a radius merely because it looks fashionable or similar.
- Keep one component's radius consistent across its related states unless the component specification explicitly assigns a state-specific token.
- Do not combine a radius token with an additional ad hoc radius override.
- `radius-5` is a valid source token even though it is not part of the otherwise common even-number sequence; do not round it to `radius-4` or `radius-6`.
- `radius-full` is the only token intended for pill/circular geometry. Do not approximate it with `radius-24`.
- If a component's intended radius cannot be inferred from the request, flag the ambiguity instead of silently selecting a value.
