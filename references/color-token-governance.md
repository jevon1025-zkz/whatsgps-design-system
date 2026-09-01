# WhatsGPS Color Token Governance

Use this reference before any WhatsGPS HTML page, UI screen, UI component, Figma UI work, design token output, color system, or component styling task.

Primary source of truth:

```text
Canonical bundled source: [design-token-color-guide.md](../assets/source-materials/design-token-color-guide.md).
```

That project document is also the user's default global color-token and UI color governance reference unless they explicitly say the work belongs to another brand, another design system, or should not use this guide.

## Provenance Rule For Navigation 3.0

The final navigation Figma file reports No variables created in this file. Use it for approved layout and visual-state inspection, but do not describe any token as extracted from that file. Navigation token values come from the project-level color guide and bundled CSS mappings.

| Component token | Palette alias | Value |
|---|---|---|
| sidebar/bg-start | dark-blue/6 | #1C2758 |
| sidebar/bg-end | dark-blue/7 | #111835 |
| sidebar/menu-bg | grey/9 | #202020 |
| sidebar/submenu-bg | grey/8 | #333333 |
| sidebar/menu-text | grey/5 | #A2A2A2 |
| sidebar/menu-active-bg | brand/5 | #3370FF |
| sidebar/menu-active-text | white | #FFFFFF |

## Required Model

Use two color layers:

- `01 Gradient Palette`: base palette only.
- `02 Component Tokens`: daily UI/component/business mapping layer.

Do not introduce a separate `semantic` layer by default. The component-token layer already carries the practical semantic meaning needed for current work, such as button, table, input, sidebar, device, alarm, command, and video.

## Figma Variable Structure

Create or maintain these color collections:

| Collection | Mode | Purpose |
|---|---|---|
| `01 Gradient Palette` | `Base` | Primitive color ramps and source values. |
| `02 Component Tokens` | `Light`, `Dark` | Component and business usage tokens. |
| `Color` | Existing modes only | Legacy compatibility. Do not add new variables unless explicitly requested. |

`01 Gradient Palette` should contain primitive families such as:

- `white`
- `black`
- `brand`
- `green`
- `yellow`
- `red`
- `blue-grey`
- `grey`
- `dark-blue`

`02 Component Tokens` should contain the UI-facing tokens used by design and implementation:

- Text, background, border.
- Button.
- Input and dropdown.
- Table and tabs.
- Sidebar.
- Device, service, alarm, command, and video business states.

## Usage Rules

- Use `02 Component Tokens` for page and component work.
- Use `01 Gradient Palette` only when maintaining the base palette or creating aliases for component tokens.
- Preserve Light/Dark theme entry through `02 Component Tokens` modes.
- Do not change `01 Gradient Palette` values just to create dark mode.
- Keep dark-mode decisions in the `Dark` mode of `02 Component Tokens`.
- For existing pages or legacy Figma files, migrate gradually by replacing high-frequency styles first: text, page background, surface, border, primary button, table, input, sidebar, and alarm/status colors.

## Naming Rules

Use these final family names:

- `blue-grey`: the product's main cool neutral family, used for text, page background, surfaces, and borders.
- `grey`: Element Plus or legacy neutral compatibility family.
- `dark-blue`: sidebar, video, and deep container family.

Do not use `slate` or `navy` as final token family names unless the user explicitly reopens the naming decision.

## CSS and HTML Output

When generating HTML/CSS, map UI colors from `02 Component Tokens` first. Only expose palette variables when the output is documenting the palette itself.

Preferred CSS structure:

```css
:root {
  /* 01 Gradient Palette */
  --brand-brand-6: #0068ff;
  --blue-grey-blue-grey-7: #1b2559;

  /* 02 Component Tokens */
  --text-text-primary: var(--blue-grey-blue-grey-7);
  --bg-bg-page: var(--blue-grey-blue-grey-1);
  --button-primary-default: var(--brand-brand-6);
}

[data-theme="dark"] {
  --text-text-primary: var(--blue-grey-blue-grey-1);
  --bg-bg-page: var(--dark-blue-dark-blue-9);
}
```

Avoid inventing one-off colors in generated UI. If a color is missing, mark it as a token gap and recommend where it should be added in the two-layer model.
