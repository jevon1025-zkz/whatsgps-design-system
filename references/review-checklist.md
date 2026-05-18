# WhatsGPS UI Review Checklist

Use this checklist for UI reviews, Figma checks, consistency audits, or generated frontend QA.

## Findings Priority

Prioritize issues in this order:

1. Workflow breakage for device/customer operations.
2. Missing or hidden core hardware data.
3. Inconsistent layout pattern for the page type.
4. Token mismatch for colors, typography, spacing, radius, or shadows.
5. Missing interaction states.
6. Cosmetic polish.

## Token Consistency

- Primary blue is `#0068FF`; sidebar active blue is `#3370FF`.
- Text primary is `#1B2559`; muted text is usually `#707EAE`; disabled is `#A3AED0`.
- Page background is `#F4F7FE`; main surfaces are white.
- Standard controls use 8px radius.
- Cards and major dialogs use 20px radius.
- Use subtle shadows; avoid heavy neumorphic or glass effects.
- Do not introduce new dominant colors without a clear semantic role.

## Layout Consistency

- PC-first, optimized for 1920 and 1440 widths.
- Table and form pages should be dense and scan-friendly.
- Toolbar actions should sit above the table and support batch work.
- Side panels should serve filtering/tree selection, not decorative content.
- Floating right rail can hold support/help/reminder/message actions.
- Avoid nested cards inside cards.

## Hardware Data Visibility

Check whether the relevant screen exposes:

- Device name.
- IMEI.
- SIM number.
- ICCID when available.
- Device model.
- Online/offline/inactive/expired status.
- Service version.
- Platform/user expiry.
- Customer ownership.
- Last location or address when location-related.

If these are absent or buried, flag it.

## Component States

Review these states:

- Hover.
- Focus.
- Active/click.
- Disabled.
- Loading.
- Empty.
- Error/validation.
- Selected row or selected tree node.
- Batch selected count.
- Offline/expired device state.
- Long text truncation + tooltip.

## Page-Specific Checks

Dashboard:

- Main numbers use strong blue and clear labels.
- Operation card supports import/sales/renew/upgrade/reset.
- Charts do not dominate business controls.

Device list:

- Table is primary.
- Operation column is fixed or reliably visible.
- Batch actions and filters are above table.
- Pagination and export/download are visible.

Location monitor:

- Map remains the primary canvas.
- Device panel does not overtake the map.
- Status filtering and grouped devices are visible.

Realtime video:

- Video grid is primary.
- Empty video cells are large, clear, and not decorative cards.
- Device/channel selection remains accessible.

Device detail workbench:

- Use `device-detail-workspace.md`.
- Treat any generic modal design as a likely issue unless it preserves workbench density.

## Temporary Anti-Patterns

These are provisional rules inferred from the current product. Revise them when real counterexamples appear.

- Do not make marketing-style pages with hero sections, slogans, large decorative art, or low information density.
- Do not replace device/customer tables with card grids.
- Do not shrink the device detail workbench into a small modal.
- Do not hide IMEI, SIM, ICCID, expiry, status, or ownership data behind secondary actions.
- Do not introduce purple, beige, brown, heavy gradients, or large decorative blobs.
- Do not use glassmorphism or heavy shadows.
- Do not over-round controls beyond the existing 8px/20px system.
- Do not design mobile-first compressed layouts for the PC system unless the task explicitly targets mobile.
- Do not separate related hardware settings into isolated decorative cards; group them by device function.
