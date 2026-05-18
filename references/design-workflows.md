# WhatsGPS Design Workflows

Use these workflows to turn vague requests into useful UI, Figma, review, or docs output.

## Workflow: Generate A Frontend Page

1. Identify page type:
   - Dashboard/account home.
   - Device/customer list.
   - Device detail workbench tab.
   - Location monitor.
   - Realtime video.
   - Trip image/media.
   - Organization/member management.
2. Identify primary entity:
   - Device, customer, service/version, command, alarm, sensor, map, video, organization.
3. Read:
   - `product-domain-model.md`
   - `design-tokens.md`
   - `component-patterns.md`
   - Relevant section in `page-patterns.md`
   - `device-detail-workspace.md` when any device detail/configuration flow is involved.
4. Build structure before styling:
   - Shell/sidebar/header.
   - Main work area.
   - Toolbar/filter region.
   - Table/form/grid/map/video surface.
   - Footer/pagination/action area.
   - Empty/loading/error states.
5. Apply tokens:
   - Colors first.
   - Typography.
   - Spacing/radius.
   - Shadow only where the existing system uses it.
6. Check hardware data visibility:
   - Device name, IMEI, SIM, ICCID, model, status, service, expiry, customer.

## Workflow: Modify An HTML Prototype

1. Preserve the current prototype's purpose and route/page type.
2. Add or update CSS variables from `design-tokens.css`.
3. Normalize layout:
   - Page background.
   - White surfaces.
   - 8px control radius.
   - 20px card/dialog radius.
   - Compact table/form density.
4. Replace generic UI with platform-specific patterns:
   - Device/customer tables.
   - Workbench tab shell.
   - Hardware configuration groups.
   - Unit inputs and switches.
5. Review in a browser if possible.

## Workflow: Restore From Figma

1. Inspect the Figma node or screenshot.
2. Map each visual element to an existing pattern:
   - Header/sidebar.
   - Page card.
   - Toolbar.
   - Table.
   - Side tree panel.
   - Device detail workbench tab.
3. Extract values:
   - Colors.
   - Font sizes/weights.
   - Control heights.
   - Gaps/paddings.
   - Radius/shadows.
4. Prefer existing tokens over raw values.
5. Only introduce a new token if the value repeats or expresses a stable semantic role.
6. Add missing interaction states that Figma often omits.

## Workflow: Review UI

1. Lead with risks:
   - Wrong page pattern.
   - Missing hardware data.
   - Broken scanability.
   - Wrong modal/workbench structure.
   - Token drift.
2. Use `review-checklist.md`.
3. When giving fixes, map each issue to a concrete change:
   - Use table instead of cards.
   - Move batch actions above table.
   - Restore IMEI column.
   - Change radius to 8px.
   - Use primary blue only for selected/primary actions.
4. Mention remaining uncertainty only when the source material is missing.

## Workflow: Write A Requirement Design Draft

1. Use `requirements-design-doc-template.md`.
2. Start from business object and route.
3. Specify page structure, not just "make a page".
4. Define table columns/forms/actions/states.
5. Define validation and permission behavior.
6. Include visual rules tied to tokens.

## Workflow: Produce Figma Variables

1. Read `figma-variable-system.md`.
2. Use semantic slash names.
3. Output DTCG JSON when the user says "导入 Figma".
4. Also include a human-readable table when the user needs review.
5. State which parts require manual Figma styles:
   - Effect styles.
   - Text styles.
   - Gradients.

## Decision Heuristics

- If the request includes IMEI/SIM/ICCID/device model/status, treat it as device-management UI.
- If it includes alarms/sensors/thresholds/units, treat it as hardware configuration inside the device workbench.
- If it includes route/video/channel/playback, treat video grid or media table as primary.
- If it includes map/location/fence/track, preserve map-first layout.
- If it includes batch operations, prioritize toolbar and table selection states.
- If it includes "详情", assume the device detail workbench unless context says member/customer detail.
