# WhatsGPS UI/UX Quality Gates

This reference adapts useful parts of `ui-ux-pro-max` to the WhatsGPS/Justrack PC hardware device management platform.

Do not use this file to import unrelated visual styles. WhatsGPS should stay a dense B-end operations console, not a landing page, glassmorphism UI, bento showcase, or decorative SaaS marketing interface.

## 1. How To Use

Use this file when:

- Reviewing generated UI or PM prototypes.
- Checking whether a page is usable enough for development.
- Improving forms, tables, buttons, charts, states, loading, and accessibility.
- Producing a final UI/UX checklist before handoff.

Use it after selecting the correct page family from `route-inventory.md` and after applying `design-tokens.md`.

## 2. Priority Order

Review in this order:

1. Accessibility and readability.
2. Interaction completeness.
3. Error prevention and recovery.
4. Layout stability and responsiveness.
5. Table/form scanability.
6. Data visualization clarity.
7. Performance and loading behavior.
8. Motion and polish.

Do not start with decorative polish if workflow, state, or data visibility is incomplete.

## 3. Accessibility Gate

Minimum requirements:

- Text contrast should be readable on white and `#F4F7FE` backgrounds.
- Focus states must be visible for inputs, selects, buttons, tabs, row operations, and dialog controls.
- Keyboard flow should follow visual order.
- Dialogs must support close/cancel/confirm via keyboard.
- Icon-only controls need tooltip or accessible label.
- Error states must include text, not color alone.
- Disabled text must remain legible enough to identify the value or reason.

WhatsGPS-specific checks:

- IMEI, SIM, ICCID, model, status, and expiry values must remain readable even in disabled/read-only fields.
- Dense tables should not reduce font size below readable PC-table scale.

## 4. Interaction Gate

Every important action must define:

- Default state.
- Hover/focus/active state.
- Disabled state and reason.
- Loading state.
- Success feedback.
- Failure feedback.

Async actions requiring loading or disabled buttons:

- 查询.
- 保存/确定.
- 批量续费/销售/升级/导入.
- 指令发送.
- 蓝牙通信校验.
- 配件绑定/解绑.
- 模拟量获取.
- 导出/下载.

Rules:

- Disable submit while the request is in progress.
- Do not silently change state after save.
- Keep user input after failed submit.
- Show retry for network, command, Bluetooth, or data-fetch failures.

## 5. Error Prevention Gate

Prevent high-risk mistakes:

- Show device name + IMEI before 续费, 转移, 指令, 报警, 解绑, 删除, 重置.
- Confirm destructive or irreversible actions.
- Warn when an operation affects multiple devices or lower-level customers.
- Validate units and ranges before submit.
- Explain why unsupported models cannot configure a feature.
- Explain whether offline devices can save pending configuration.

Danger actions:

- 删除.
- 解绑.
- 重置设备.
- 转移.
- 删除中心号码 / 删除 SOS 号码.
- 停止 or disabling critical monitoring.

Danger actions should not look like ordinary blue links without confirmation.

## 6. Layout And Responsiveness Gate

WhatsGPS is PC-first. Design primarily for 1920px and 1440px desktop widths.

Requirements:

- Main content should not overlap floating rail, sidebar, or fixed operation column.
- Tables with many fields must support horizontal scroll or column management.
- Operation column should remain visible where possible.
- Toolbar layout should not wrap into unclear two-line controls at 1440px.
- Dialogs should remain usable within viewport height.
- Loading/empty/error states should not resize the layout in a jarring way.

Avoid:

- Mobile-first compressed layouts for PC tasks.
- Cards inside cards.
- Oversized headings in dashboards, dialogs, side panels, or tables.
- Decorative whitespace that pushes core data below the fold.

## 7. Table Quality Gate

Tables are the primary WhatsGPS work surface.

Must check:

- Header labels are clear and use product terms.
- Important columns are not hidden by default: 设备名称, IMEI, 设备型号, 状态, 服务版本, 到期, 所属客户 when relevant.
- Long values truncate with tooltip.
- IMEI/SIM/ICCID are easy to copy or at least easy to read.
- Row hover and selected states are distinct.
- Batch selected count is visible.
- Empty table state sits inside the table area.
- Pagination shows total count and page size when applicable.

Do not:

- Replace operational tables with card grids.
- Hide all row actions inside a vague menu.
- Use color-only status without text.

## 8. Form Quality Gate

Forms must be optimized for accurate configuration.

Must check:

- Labels are visible and stable.
- Required fields are marked.
- Read-only and disabled fields are visually distinct but readable.
- Unit suffixes are visible for numeric inputs.
- Validation copy appears near the field.
- Related fields are grouped by task.
- Footer actions are predictable: 取消 / 确定 unless a task requires more specific action text.

For hardware settings:

- Separate hardware configuration, calibration/parameters, and alarm settings.
- Do not hide calibration data behind decorative collapsed cards while editing.
- Show unsupported/offline states before submit.

## 9. Chart And Report Gate

Use charts only when they improve comparison or trend understanding.

Chart mapping:

- Trend over time: line chart.
- Category comparison: bar chart.
- Composition: donut only when category count is small.
- Ranking: horizontal bar or table with ranking.
- Detail/traceability: table.

Report requirements:

- Provide table detail or export path for chart data.
- Label units clearly.
- Preserve date range constraints.
- Do not use too many similar blues that are hard to distinguish.
- Use accessible contrast for chart legends and labels.

For WhatsGPS reports, charts should support operational review, not visual decoration.

## 10. Loading And Performance Gate

Requirements:

- Use skeletons or local loading states for table/card areas.
- Reserve layout space for async content to avoid content jumping.
- Lazy-load media or large map/video assets when appropriate.
- Large tables should avoid rendering unnecessary full datasets at once.
- Realtime video/map pages must keep primary canvas responsive while side panels update.

User-visible behavior:

- Query/loading state should not clear old data too early unless explicitly required.
- Long-running export/download should show progress or task state.
- Batch operations should show processing and final result.

## 11. Motion Gate

Motion should support feedback, not decoration.

Allowed:

- 150-300ms hover/focus/dialog transitions.
- Loading skeleton shimmer if subtle.
- Small feedback transitions for switch, tab, and selection.

Avoid:

- Large decorative animations.
- Motion that shifts table rows or form fields during input.
- Animations that hide status changes.
- Effects that conflict with reduced-motion settings.

## 12. Style Guardrails

Do not import these generic `ui-ux-pro-max` styles into WhatsGPS unless explicitly approved:

- Glassmorphism.
- Neumorphism.
- Claymorphism.
- Brutalism.
- Bento marketing grid.
- Landing-page hero composition.
- Heavy gradients.
- Large decorative blobs.
- Fashion/editorial typography.
- Mobile-app-first navigation.

Allowed improvements:

- Better focus states.
- Better loading states.
- Better empty/error copy.
- Clearer form grouping.
- Stronger table scanability.
- Cleaner chart labels.
- More consistent icon buttons and tooltips.

## 13. Handoff Checklist

Before marking a UI/prototype ready:

- Page family is correct.
- Main user task is clear.
- Core hardware/customer fields are visible.
- Form/table layout follows WhatsGPS density.
- Loading/empty/error/disabled/no-permission/offline/expired states are defined.
- Risky actions have prevention or confirmation.
- Async actions have loading and feedback.
- Unit inputs and validation rules are clear.
- Accessibility basics pass.
- Visual tokens are consistent.
