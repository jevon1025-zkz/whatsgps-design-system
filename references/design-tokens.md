# WhatsGPS Design Tokens

This reference is the source for Figma Variables and frontend global variables. Use slash names for Figma variables and CSS custom property names for code output.

Color-token note: for current color work, [color-token-governance.md](color-token-governance.md) and the bundled [color guide](../assets/source-materials/design-token-color-guide.md) supersede the older `Color` / `color/*` guidance in this file. Use this file for typography, spacing, radius, shadow, size, motion, and historical frontend token reference unless the user explicitly asks to revisit the legacy color model.

## Figma Collections

Create these Figma variable collections:

- `Color`
- `Typography`
- `Spacing`
- `Radius`
- `Shadow`
- `Size`
- `Motion`

Use semantic token names first. Keep raw palette names as aliases only when needed.

## Color Tokens

| Figma variable | CSS variable | Value | Usage |
|---|---|---:|---|
| `color/brand/primary` | `--color-brand-primary` | `#0068FF` | Primary buttons, links, selected tabs, key numbers |
| `color/brand/active` | `--color-brand-active` | `#1755E7` | Pressed primary controls |
| `color/brand/sidebar-active` | `--color-brand-sidebar-active` | `#3370FF` | Sidebar active menu item |
| `color/status/success` | `--color-status-success` | `#05CD99` | Online, success, positive change |
| `color/status/warning` | `--color-status-warning` | `#FFCE20` | Warning, pending, expiring soon |
| `color/status/error` | `--color-status-error` | `#FF4D4F` | Error, delete, expired |
| `color/text/primary` | `--color-text-primary` | `#1B2559` | Main text, table body, important labels |
| `color/text/secondary` | `--color-text-secondary` | `#2B3574` | Secondary headings and emphasized metadata |
| `color/text/tertiary` | `--color-text-tertiary` | `#707EAE` | Table headers, helper text, inactive tabs |
| `color/text/legacy-muted` | `--color-text-legacy-muted` | `#889EAF` | Existing sidebar/legacy muted text seen online |
| `color/text/disabled` | `--color-text-disabled` | `#A3AED0` | Disabled text, placeholders, offline low emphasis |
| `color/text/inverse` | `--color-text-inverse` | `#FFFFFF` | Text on blue or dark backgrounds |
| `color/bg/page` | `--color-bg-page` | `#F4F7FE` | Main PC workspace background |
| `color/bg/surface` | `--color-bg-surface` | `#FFFFFF` | Cards, tables, dialogs, panels |
| `color/bg/surface-muted` | `--color-bg-surface-muted` | `#F5F7FA` | Disabled inputs, subtle muted areas |
| `color/bg/hover` | `--color-bg-hover` | `#F0F5FF` | Row hover, menu/control hover |
| `color/bg/selected` | `--color-bg-selected` | `rgba(0, 104, 255, 0.10)` | Selected tree rows, selected pills |
| `color/bg/info` | `--color-bg-info` | `rgba(0, 104, 255, 0.08)` | Info banners |
| `color/bg/success` | `--color-bg-success` | `rgba(5, 205, 153, 0.10)` | Success tags |
| `color/bg/warning` | `--color-bg-warning` | `rgba(255, 206, 32, 0.10)` | Warning tags/banners |
| `color/bg/error` | `--color-bg-error` | `rgba(255, 77, 79, 0.08)` | Error tags/banners |
| `color/border/default` | `--color-border-default` | `#E9EDF7` | Form controls, table dividers, card borders |
| `color/border/strong` | `--color-border-strong` | `#E4E7ED` | Element UI legacy borders |
| `color/overlay/modal` | `--color-overlay-modal` | `rgba(0, 0, 0, 0.45)` | Modal backdrop |
| `color/sidebar/start` | `--color-sidebar-start` | `#1C2758` | Sidebar gradient start |
| `color/sidebar/end` | `--color-sidebar-end` | `#111835` | Sidebar gradient end |
| `color/sidebar/deep` | `--color-sidebar-deep` | `#0F123F` | Dark containers/video dark zones |
| `color/video/bg` | `--color-video-bg` | `#0A1128` | Empty video cells |
| `color/sidebar/menu-text` | `--color-sidebar-menu-text` | `#A2A2A2` | Default sidebar menu text |
| `color/sidebar/menu-active-text` | `--color-sidebar-menu-active-text` | `#FFFFFF` | Selected sidebar menu text |
| `color/sidebar/menu-bg` | `--color-sidebar-menu-bg` | `#202020` | Sidebar menu item background |
| `color/sidebar/menu-hover-bg` | `--color-sidebar-menu-hover-bg` | `#202020` | Sidebar menu hover |
| `color/sidebar/menu-active-bg` | `--color-sidebar-menu-active-bg` | `#3370FF` | Selected sidebar item |
| `color/sidebar/submenu-bg` | `--color-sidebar-submenu-bg` | `#333333` | Sub-menu background |
| `color/sidebar/submenu-hover-bg` | `--color-sidebar-submenu-hover-bg` | `#333333` | Sub-menu item hover |
| `color/sidebar/submenu-active-bg` | `--color-sidebar-submenu-active-bg` | `#3370FF` | Selected sub-menu item |
| `color/icon/default` | `--color-icon-default` | `#707EAE` | Default icon (same as text/tertiary) |
| `color/icon/active` | `--color-icon-active` | `#0068FF` | Active/selected icon |
| `color/icon/disabled` | `--color-icon-disabled` | `#A3AED0` | Disabled icon |
| `color/icon/danger` | `--color-icon-danger` | `#FF4D4F` | Destructive action icon |
| `color/close/hover` | `--color-close-hover` | `#8C8C8C` | Close button (×) hover |

## Typography Tokens

Font stack:

```text
PingFang SC, Microsoft YaHei, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif
```

| Figma style | CSS variable set | Size | Weight | Line height | Usage |
|---|---|---:|---:|---:|---|
| `typography/display/number` | `--font-size-display-number` | `32px` | `700` | `38px` | Dashboard main numbers |
| `typography/page/title` | `--font-size-page-title` | `20px` | `600` | `28px` | Page title in header |
| `typography/section/title` | `--font-size-section-title` | `18px` | `600` | `25px` | Large card or section title |
| `typography/card/title` | `--font-size-card-title` | `16px` | `600` | `24px` | Card, modal section, tab active |
| `typography/body/md` | `--font-size-body-md` | `14px` | `400` | `22px` | Normal table/form text |
| `typography/body/md-medium` | `--font-size-body-md` + `--font-weight-medium` | `14px` | `500` | `22px` | Buttons and emphasized cell text |
| `typography/body/dense` | `--font-size-body-dense` | `13px` | `400` | `20px` | Dense input/pagination internals |
| `typography/caption` | `--font-size-caption` | `12px` | `400` | `18px` | Captions, helper text, tags |
| `typography/caption-bold` | `--font-size-caption` + `--font-weight-bold` | `12px` | `700` | `18px` | Small numeric emphasis |

Rules:

- Use `color/text/primary` for operational data.
- Use `color/brand/primary` for clickable IDs, links, active tabs, and key totals.
- Use tabular numeric alignment for large counts, IMEI-like numeric columns, and dashboards where possible.
- Do not scale font size by viewport width.

## Spacing Tokens

Use a 4px-compatible grid. Most layouts should read as 8px-based, with 12px and 20px used for dense Element UI alignment.

| Figma variable | CSS variable | Value | Usage |
|---|---|---:|---|
| `space/1` | `--space-1` | `4px` | Icon-text gap, validation text gap |
| `space/2` | `--space-2` | `8px` | Inline controls, button icon gap |
| `space/3` | `--space-3` | `12px` | Form inner padding, compact row gaps |
| `space/4` | `--space-4` | `16px` | Standard section gap, dialog header padding |
| `space/5` | `--space-5` | `20px` | Dense panel padding seen online |
| `space/6` | `--space-6` | `24px` | Page padding, modal content padding |
| `space/8` | `--space-8` | `32px` | Large region gap |
| `space/10` | `--space-10` | `40px` | Large control/search height |
| `space/12` | `--space-12` | `48px` | Major vertical separation |
| `space/16` | `--space-16` | `64px` | Header/sidebar major size |

## Radius Tokens

| Figma variable | CSS variable | Value | Usage |
|---|---|---:|---|
| `radius/xs` | `--radius-xs` | `2px` | Checkbox inner marks, tiny indicators |
| `radius/sm` | `--radius-sm` | `4px` | Table badges, pagination current page |
| `radius/md` | `--radius-md` | `6px` | Legacy small surfaces |
| `radius/control` | `--radius-control` | `8px` | Inputs, selects, buttons, tags |
| `radius/panel` | `--radius-panel` | `12px` | Small floating panels |
| `radius/card` | `--radius-card` | `20px` | Dashboard cards, page cards |
| `radius/modal` | `--radius-modal` | `20px` | Device detail workbench and major dialogs |
| `radius/pill` | `--radius-pill` | `999px` | Pills, segmented controls, search containers |
| `radius/circle` | `--radius-circle` | `50%` | Avatar, circular icon buttons |

## Shadow Tokens

| Figma variable | CSS variable | Value | Usage |
|---|---|---|---|
| `shadow/surface` | `--shadow-surface` | `0 4px 12px rgba(15, 18, 63, 0.10)` | Cards, dialogs, dropdowns |
| `shadow/hover` | `--shadow-hover` | `0 8px 24px rgba(15, 18, 63, 0.15)` | Card hover, dragging |
| `shadow/header` | `--shadow-header` | `0 1px 4px rgba(0, 21, 41, 0.08)` | Fixed top header |
| `shadow/floating` | `--shadow-floating` | `0 0 12px rgba(213, 214, 223, 0.50)` | Right floating help/action rail |
| `shadow/light` | `--shadow-light` | `0 0 7px rgba(0, 0, 0, 0.05)` | Subtle internal panels |

## Size Tokens

| Figma variable | CSS variable | Value | Usage |
|---|---|---:|---|
| `size/header/height` | `--size-header-height` | `64px` | PC top header |
| `size/sidebar/icon-width` | `--size-sidebar-icon-width` | `64px` | Collapsed icon sidebar |
| `size/sidebar/full-width` | `--size-sidebar-full-width` | `240px` | Full text sidebar |
| `size/panel/business-width` | `--size-panel-business-width` | `420px` | Device/customer list side panel |
| `size/panel/map-width` | `--size-panel-map-width` | `486px` | Location monitor side panel max |
| `size/control/sm-height` | `--size-control-sm-height` | `32px` | Toolbar controls, buttons |
| `size/control/md-height` | `--size-control-md-height` | `40px` | Search box, larger form controls |
| `size/control/top-search-height` | `--size-control-top-search-height` | `36px` | Header global search |
| `size/table/row-height` | `--size-table-row-height` | `48px` | Default data row |
| `size/table/header-height` | `--size-table-header-height` | `54px` | Element UI table header seen online |
| `size/modal/device-width` | `--size-modal-device-width` | `80vw` | Device detail workbench minimum target |
| `size/modal/device-max-width` | `--size-modal-device-max-width` | `1600px` | Device detail workbench max |
| `size/floating/action-width` | `--size-floating-action-width` | `48px` | Right customer/help/reminder rail |

## Motion Tokens

| Figma variable | CSS variable | Value | Usage |
|---|---|---:|---|
| `motion/duration/fast` | `--motion-duration-fast` | `120ms` | Hover feedback |
| `motion/duration/base` | `--motion-duration-base` | `200ms` | Dialog, tabs, menus |
| `motion/easing/base` | `--motion-easing-base` | `ease` | Default UI transitions |

## Figma Variable Notes

- Figma variables cannot fully represent gradients as one reusable color token. Create `color/sidebar/start` and `color/sidebar/end`, then document the sidebar fill as `linear-gradient(0deg, start, end)`.
- Keep `rgba(...)` tokens for overlays, hover backgrounds, tags, and banners.
- If a new color appears in screenshots or code, add it only after mapping it to a semantic purpose.
- Do not create page-specific color tokens unless the color repeats across at least two components or expresses a stable status/state.
