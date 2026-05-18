# Figma Variable System

Use this reference when creating Figma variable files, token tables, or import instructions.

## Recommended Collection

Create one collection named:

```text
WhatsGPS Tokens
```

Within it, use these variable groups:

- `color`
- `space`
- `radius`
- `size`
- `font`
- `shadow`
- `motion`
- `platform`

## Naming Rules

Use slash names:

- `color/brand/primary`
- `color/text/primary`
- `color/bg/page`
- `space/4`
- `radius/control`
- `size/table/row-height`
- `font/size/body-md`

Do not use SCSS `$primary` style names in Figma. Keep old SCSS names only as aliases in documentation.

## Import Format

When the user asks for a file to import into Figma Variables, output DTCG JSON.

Supported practical token types:

- `color`
- `dimension`
- `number`
- `string`
- `fontFamily`
- `duration`

Use colors as sRGB components and alpha. Use dimensions as px.

## What Figma Variables Cannot Fully Replace

Figma variables do not fully replace:

- Text Styles.
- Effect Styles.
- Gradients as reusable full gradient styles.
- Complex shadows.

Provide variables plus manual style instructions.

## Manual Text Styles To Create

Create these Figma Text Styles after importing variables:

| Style | Size | Weight | Line height | Color |
|---|---:|---:|---:|---|
| Display / Number | 32 | 700 | 38 | `color/brand/primary` |
| Page / Title | 20 | 600 | 28 | `color/text/primary` |
| Section / Title | 18 | 600 | 25 | `color/text/primary` |
| Card / Title | 16 | 600 | 24 | `color/text/primary` |
| Body / MD | 14 | 400 | 22 | `color/text/primary` |
| Body / MD Medium | 14 | 500 | 22 | `color/text/primary` |
| Body / Dense | 13 | 400 | 20 | `color/text/primary` |
| Caption | 12 | 400 | 18 | `color/text/tertiary` |

## Manual Effect Styles To Create

Create these Figma Effect Styles:

- `Shadow / Surface`: `0 4 12 0 rgba(15, 18, 63, 0.10)`
- `Shadow / Hover`: `0 8 24 0 rgba(15, 18, 63, 0.15)`
- `Shadow / Header`: `0 1 4 0 rgba(0, 21, 41, 0.08)`
- `Shadow / Floating`: `0 0 12 0 rgba(213, 214, 223, 0.50)`
- `Shadow / Light`: `0 0 7 0 rgba(0, 0, 0, 0.05)`

## Manual Gradient Styles To Create

Create sidebar gradient style:

```text
linear-gradient(0deg, color/sidebar/start #1C2758, color/sidebar/end #111835)
```

## Token Governance

- Add a new color only if it has a semantic purpose.
- Use existing alpha colors for hover, selected, banner, tag, and overlay states.
- Keep light/dark modes out of scope unless the user explicitly asks; the current system is PC light mode with dark sidebar.
- For Figma libraries, publish the token file only after checking common components: button, input, table, tabs, dialog, tree panel, device detail workbench.
