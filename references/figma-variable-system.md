# Figma Variable System

Use this reference for Figma Variables, token tables, or import instructions. Read color-token-governance.md and the project-level color guide first.

## Provenance

- The navigation 3.0 Figma has no local Variables. Do not claim a variable export from it.
- Color architecture comes from the bundled [color guide](../assets/source-materials/design-token-color-guide.md).
- Use Figma frames to validate visual application, not to invent undocumented variable provenance.

## Collections

| Collection | Modes | Purpose |
|---|---|---|
| 01 Gradient Palette | Base | Primitive color ramps. |
| 02 Component Tokens | Light, Dark | UI/component/business color aliases used in design and implementation. |
| WhatsGPS Tokens | As needed | Non-color variables such as space, radius, size, font, motion, and platform. |
| Color | Existing modes only | Legacy compatibility; do not add variables by default. |

Do not add a separate semantic color collection by default. Business meaning belongs in 02 Component Tokens.

## Naming

- Color palette: brand/5, grey/9, dark-blue/6.
- Component colors: sidebar/bg-start, button/primary/default, device/moving.
- Non-color: space/4, radius/control, size/table/row-height, font/size/body-md.
- Use blue-grey, grey, and dark-blue; do not introduce slate or navy as final family names.

## Import And Styles

- For Variables import, prefer DTCG JSON with color, dimension, number, string, fontFamily, and duration types.
- Figma Variables do not replace Text Styles, Effect Styles, or reusable gradient styles. Provide those separately when requested.
- Preserve legacy aliases during migration; replace high-frequency text, background, surface, border, button, table, input, sidebar, and state usages first.

## Navigation Mapping

Use the mappings documented in pc-navigation-guidelines.md. Keep legacy frontend aliases in design-tokens.css until consumers migrate.

## Publication Check

Before publishing a library, inspect button, input, table, tabs, dialog, tree panel, navigation expanded/collapsed states, message popover, search, device states, and device-detail workbench in both relevant modes.
