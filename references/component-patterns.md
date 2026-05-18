# WhatsGPS Component Patterns

Use these patterns when building or reviewing Vue/Element UI style UI.

## Element UI Baseline

Prefer these component mental models:

- Table: `el-table`
- Form: `el-form`, `el-form-item`
- Input: `el-input`
- Select: `el-select`
- Date/time: `el-date-picker`
- Button: `el-button`
- Tabs: `el-tabs`
- Dialog: `el-dialog` or custom base dialog
- Radio: `el-radio`, `el-radio-button`
- Checkbox: `el-checkbox`
- Switch: `el-switch`
- Pagination: `el-pagination`
- Tooltip: `el-tooltip`
- Tree/list: custom tree with Element-style controls

## Buttons

Heights:

- Toolbar/button default: 32px.
- Dialog footer: 40px.
- Icon-only action: 32px or 40px depending context.

Styles:

- Primary: blue fill, white text, used for 查询, 确定, 导入, major submit.
- Default: white surface, border, primary text.
- Text/link: blue text for row operations such as 详情, 更多, 查看地址.
- Danger: red only for destructive actions.

Rules:

- Keep batch operation buttons grouped left of table filters.
- Do not make every action primary.
- Icon + text is preferred for batch tools when space allows.

## Date Range Picker (日期区间选择器)

This is the platform's standard datetime range selection component. It is used on pages that require a start–end date range, such as 视频回放, 事件中心, 统计报表, and 定位监控 history queries.

### Trigger Input

- Single input field showing the selected range as `YYYY-MM-DD ~ YYYY-MM-DD`.
- A calendar icon (📅) sits on the right edge of the input.
- Height: 32px in filter-bar context; 36–40px in side-panel context.
- Border: `color/border/default` (`#E9EDF7`); focused border: `color/brand/primary` (`#0068FF`).
- Radius: 8px (`radius/control`).

### Dropdown Panel Layout

The panel drops down from the trigger input and has three sections arranged horizontally:

```
┌──────────────────────────────────────────────────────────────────────────────┐
│ [Left shortcuts]  │  [Header: date+time inputs]                              │
│                   │  [Dual-month calendars]                                  │
│                   │                                              [清空] [确定] │
└──────────────────────────────────────────────────────────────────────────────┘
```

**Left Shortcut Rail**

- Fixed-width vertical list (~80px).
- Each shortcut is a text-only row, left-aligned.
- Font: 14px, `color/text/primary`.
- Hover: `color/brand/primary` text, `color/bg/hover` background.
- Active/selected: `color/brand/primary` text, bold.
- Default shortcut set (base platform):
  - 今天
  - 昨天
  - 本周
  - 上周
  - 本月
  - 上月
- **For 视频回放 (after PRD optimization):** replace 昨天 with 近3天, making the set: 今天 / 近3天 / 本周 / 上周 / 本月 / 上月.

**Header Row (Date + Time inputs)**

- Two groups side by side, connected by a `→` arrow.
- Each group: `[date input  YYYY-MM-DD]` `[time input  HH:mm:ss]`.
- Start time defaults to `00:00:00`; end time defaults to `23:59:59`.
- Inputs are individually editable.
- Background: white; border: `color/border/default`; radius: 4px; height: 32px.

**Dual-Month Calendar**

- Two calendar months displayed side-by-side (left = start month, right = next month or end month).
- Navigation arrows: `«` (prev year) `‹` (prev month) on left header; `›` (next month) `»` (next year) on right header.
- Weekday row: 日 一 二 三 四 五 六.
- Day cell states:
  - Default: 13px text, `color/text/primary`, transparent background.
  - Other-month days: `color/text/disabled`.
  - Hover: `color/bg/hover` background.
  - Range start / Range end: `color/brand/primary` (`#0068FF`) fill, white text, 4px radius.
  - In-range (between start and end): `color/bg/selected` (`rgba(0,104,255,0.10)`) fill.
  - Today marker: blue fill when it is the selected endpoint; otherwise a subtle underline or dot.
- The selected start and end dates are both displayed as solid blue circles/squares; days between them use the light blue range fill.

**Footer**

- Right-aligned: `清空` (default/ghost button) and `确定` (primary blue button).
- `清空` clears the current selection and resets to empty.
- `确定` confirms the selection and closes the panel.

### Behavior Rules

- The panel opens on click of the trigger input; it does not open on hover.
- Clicking a shortcut immediately updates the date inputs and calendar selection but does NOT close the panel — the user must click `确定` to confirm.
- The `→` separator between start and end groups is decorative; it does not prevent end date being earlier than start date during editing (server-side or submit-time validation handles order).
- Maximum range validation (e.g. 31-day limit on 视频回放) is enforced at the `确定` click, not on calendar day hover.
- When the range exceeds the allowed maximum, show a toast after `确定` is clicked; do not close the panel.
- If the user clicks `清空`, the trigger input shows placeholder text and both calendar selections are cleared.

### Usage Notes

- Do not build a custom date picker for this platform. Always extend `el-date-picker` type `datetimerange` with a custom `picker-options.shortcuts` array.
- The shortcut list is the primary fast path for operators; ensure the most-used shortcuts appear at the top.
- When embedding in a narrow left side panel (e.g. 视频回放 filter panel), the panel can overflow out of the sidebar — ensure `overflow: visible` or portal rendering so the dropdown is not clipped.

## Inputs And Selects

Default:

- Height 32px in toolbar/table pages.
- Height 40px in side panels/search sections.
- Radius 8px.
- Border `color/border/default`.
- Placeholder disabled/muted.

Patterns:

- Global header search: search icon + placeholder + segmented `设备 / 客户`.
- Table filter input: column selector prepended to input, then 查询 button.
- Unit input: compact input + unit suffix such as `mi/H`, `H`, `V`, `L/100mi`.
- Read-only input: muted surface background and disabled-looking text.

Rules:

- Keep widths stable across rows.
- Unit labels should align on the right edge.
- Do not use vague placeholder copy when a field expects IMEI, SIM, or customer name.

## Forms

Use dense desktop form structure:

- Two-column layout for wide dialogs.
- Label width commonly 80-110px.
- Labels right-aligned.
- Row gap 16px.
- Column gap 24-48px depending content.
- Full-width fields for textarea, upload, alert banner, and table sections.

Required state:

- Red star before label.
- Validation text 12px under the control.

Read-only/disabled state:

- Muted background.
- Muted text.
- Still readable enough for ID fields.

## Tables

Use tables for repeated device/customer/service/command records.

Header:

- Height around 48-54px.
- Background light blue-gray.
- Text primary or tertiary depending context.
- Font 12-14px.

Rows:

- Height around 48px.
- White background.
- Bottom border only.
- Hover can use light blue.

Operation column:

- Fixed right when horizontal overflow exists.
- Use blue text links.
- Keep `详情` visible; `更多` can open overflow actions.

Footer:

- Selected count left.
- Total count, page size, pagination, jump input.
- Export/download button can sit right.

Rules:

- Do not replace device tables with card grids.
- Keep IMEI and device name easy to select/copy.
- Long cell text should truncate with tooltip.
- Empty table state should sit inside table/container, not take over the page.

## Tabs

Top-level page tabs:

- Height around 40-50px.
- Active: primary blue, 600 weight, 2px bottom line.
- Inactive: tertiary text, 400 weight.

Device detail workbench tabs:

- Height around 65px.
- Many tabs are expected.
- Preserve horizontal scan and active underline.
- Do not convert to left nav unless redesigning the whole workbench.

## Dialogs

Small dialogs:

- Confirmation or simple form only.
- Width 480-640px.

Large workbench dialogs:

- Device detail and hardware configuration.
- Width around 80vw, max around 1600px.
- Header tabs and footer actions.
- Scrollable content.

Rules:

- Do not use a small generic modal for device detail.
- Footer actions should remain predictable.
- Close icon always top-right.

## Tree / Side Panel

Used for customer/device grouping.

Panel content:

- Search at top.
- Status filters or tabs.
- Group rows with expand/collapse.
- Device/customer rows with count/status.
- Optional batch checkbox and settings.

Rules:

- Keep row height compact.
- Active row uses light blue selection.
- Counts should stay close to names.
- Do not make the side panel visually heavier than the main content.

## Status Tags And Inline States

Use semantic color only:

- Success for online/success.
- Warning for expiring/pending.
- Error for expired/destructive/failed.
- Disabled/muted for offline/inactive/non-actionable.

Inline states can be text-only when table density matters.

## Empty States

Use compact empty states:

- Centered illustration or icon.
- Text: 暂无数据 / 未找到相关结果 / 加载失败，点击重试.
- Optional primary action only when it directly resolves the empty state.

Avoid large decorative empty states on map/video/table work surfaces.

## Floating Rail

Right floating rail can include:

- 客服
- 帮助
- 提醒
- 消息

Style:

- White vertical pill/panel.
- 48px-ish width.
- Subtle shadow.
- Icon over text.

Do not duplicate primary page actions in the floating rail.
