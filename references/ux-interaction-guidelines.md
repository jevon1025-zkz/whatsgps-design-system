# WhatsGPS UX Interaction Guidelines

Use this reference when writing requirements, reviewing prototypes, designing interactions, or generating UI for WhatsGPS/Justrack. It adapts general UX design principles to the current PC hardware device management platform.

## 1. UX Positioning

WhatsGPS is an operations console, not a content website. UX quality is measured by whether operators can complete hardware and customer management tasks accurately, quickly, and with fewer mistakes.

Primary UX goals:

- Make the current object clear: customer, device, service, route, video, report, or configuration.
- Make the next action obvious.
- Prevent risky hardware and account mistakes.
- Preserve scanability in dense tables and forms.
- Show enough state for operators to recover from errors.
- Keep visual changes consistent with the existing system.

## 2. User And Task Lens

Before designing or reviewing a requirement, identify:

- Who is using it: administrator, dealer, supervisor, finance/operator, customer-service role.
- What object they are acting on: device, customer, IMEI, SIM, ICCID, service version, sensor, command, alarm.
- What the task outcome is: find, compare, configure, renew, transfer, bind, unbind, export, monitor, troubleshoot.
- What can go wrong: wrong device, wrong customer, device offline, expired service, insufficient cards, unsupported model, failed command, permission denied.

If the requirement cannot answer these four points, it is not ready for interaction design.

## 3. Information Architecture Rules

### 3.1 Route And Page Family

Every feature should belong to an existing page family unless there is a strong product reason:

- Dashboard/account overview.
- My customers/device management.
- Device detail workbench.
- Location/map.
- Video/media.
- Finance/service.
- Organization/permission.
- Reports/export.
- System configuration.
- User center/message.

Use `route-inventory.md` to choose the page family.

### 3.2 Object Context

Keep object context near the action:

- Customer pages: selected customer, account, customer level, device count, stock, online/offline counts.
- Device pages: device name, IMEI, model, customer, status, service version, expiry.
- Sensor pages: device, model support, transmission mode, binding state, calibration state.
- Finance pages: target customer/device, available cards/balance, expiry type, batch count.

Do not force the user to remember a selected device/customer from a previous page or hidden panel.

### 3.3 Labeling

Labels should match product language:

- Use IMEI, SIM号码, ICCID, 设备型号, 所属客户, 平台到期, 用户到期.
- Use 在线, 离线, 未激活, 已过期, 即将过期.
- Use 详情, 更多, 查询, 重置, 确定, 取消, 续费, 转移, 导入, 升级.

Avoid vague labels such as 设置, 管理, 处理 when the action can be named more specifically.

## 4. User Flow Rules

For every requirement, document at least:

- Entry point.
- Default state.
- Happy path.
- Save/submit feedback.
- Error path.
- Exit or return path.

### 4.1 Default State

The first screen should answer:

- Where am I?
- Which customer/device is selected?
- What data is currently shown?
- What can I do next?

### 4.2 Query And Filter Flow

Requirements must specify:

- Default filters.
- Required filters.
- Whether filters include lower-level customers.
- What happens after query.
- What happens after reset.
- Empty result copy.
- Whether filter state is preserved after returning from detail.

### 4.3 Edit And Save Flow

Requirements must specify:

- Which fields are editable.
- Which fields are read-only.
- Which fields are required.
- Validation timing: blur, submit, or real-time.
- Whether save requires device response.
- Whether offline devices can save pending configuration.
- Success feedback.
- Failure feedback.

### 4.4 Batch Flow

Batch operations must specify:

- Selection rule: current page only or cross-page.
- Disabled state when nothing is selected.
- Confirmation content.
- Partial success/failure result.
- Whether failed rows can be exported or retried.

## 5. Interaction Patterns

### 5.1 Recognition Over Recall

Show available choices instead of asking users to remember values:

- Use selects for model, customer, status, service version, command group.
- Use segmented controls for clear binary/few-choice modes: 有线/蓝牙, 1年/终生.
- Use tables for multiple devices, tags, sensors, cards, records.
- Use tooltips for technical labels, not long visible explanations.

### 5.2 Feedback

Every important action needs feedback:

- Query: loading or skeleton, then result count or empty result.
- Save: success or failure message.
- Command: queued, waiting response, success, failed.
- Bluetooth binding: checking, paired, failed, low battery, unbound.
- Batch operation: selected count, processing, partial result.

Avoid silent state changes.

### 5.3 Error Prevention

Prevent mistakes before they happen:

- Show device/customer context before risky actions.
- Confirm destructive actions.
- Disable actions that are impossible and explain why.
- Validate units and ranges before submit.
- Show expiry/service limitations before renewal or feature configuration.
- Warn when an operation affects multiple devices or lower-level customers.

### 5.4 Recovery

Error states should help the user continue:

- Keep already-entered form data after save failure.
- Provide retry for command, network, or Bluetooth status refresh.
- Show which rows failed in batch operations.
- Provide next action for unsupported device models or offline devices.

## 6. Form UX Rules

Use forms for dense hardware and account configuration.

Required behavior:

- Labels must be visible, not only placeholders.
- Required fields use a red marker.
- Unit inputs must show unit suffixes.
- Read-only fields use muted background but remain readable.
- Validation text appears near the field.
- Related fields are grouped by business function.

For new or substantially redesigned WhatsGPS PC forms, place each label above its control and order fields vertically by task. Use multi-column structures only for repeated setting matrices, tables, or genuine side-by-side comparison. Preserve a legacy form when the current task does not authorize its redesign.

## 7. Table UX Rules

Tables are the default pattern for device/customer/service records.

Required behavior:

- Operation column remains visible or fixed.
- Device name and IMEI remain easy to scan/copy.
- Long text truncates with tooltip.
- Selected count is visible for batch operations.
- Pagination includes total count and page size when available.
- Empty state sits inside the table container.

Do not replace high-density device tables with card grids.

## 8. Device Detail Workbench UX

The device detail workbench is a task hub.

UX rules:

- Keep the top tab system stable.
- Do not make each tab feel like a different product.
- Keep current device context visible in complex tabs.
- Keep footer actions predictable.
- When a tab has a long form, group sections by task: hardware, parameters, alarm, records.
- For high-risk tabs such as 续费, 转移, 指令, 报警设置, show clear confirmation or feedback.

## 9. Sensor UX Rules

Sensor configuration has higher interaction risk than ordinary form editing.

Every sensor flow must define:

- Supported models.
- Unsupported model state.
- Enable/disable behavior.
- Wired vs Bluetooth behavior.
- Bluetooth host check.
- Accessory binding source.
- Accessory status.
- Calibration rule.
- Alarm threshold rule.
- Offline behavior.
- Save and device-response behavior.

Recommended order:

1. Device context.
2. Sensor installation/usage note.
3. Enable switch.
4. Hardware/transmission configuration.
5. Binding or calibration table.
6. Alarm settings.
7. Footer actions.

## 10. Accessibility And Keyboard Basics

This platform is PC-first, so keyboard and readable states matter.

Minimum requirements:

- Visible focus state for inputs, selects, buttons, table operations, tabs.
- Keyboard access for dialog close, cancel, confirm, and basic form traversal.
- Text contrast must be readable on white and light-blue backgrounds.
- Icon-only buttons need tooltip or accessible label.
- Error copy should not rely on color alone.
- Disabled state should remain legible.

Do not sacrifice readability to make the interface look lighter.

## 11. PM Requirement UX Checklist

Before a requirement is handed to UI/front-end, check:

1. User role and task are clear.
2. Page family and route are clear.
3. Entry and return path are clear.
4. Default state is specified.
5. Main object context is visible.
6. Fields are listed with editable/read-only/required status.
7. Query/filter/reset behavior is specified.
8. Save/submit behavior is specified.
9. Loading, empty, error, disabled, no-permission states are specified.
10. Offline, expired, unsupported device states are specified when relevant.
11. Batch operation rules are specified when relevant.
12. Risky actions have confirmation or prevention.
13. Success and failure feedback are specified.
14. Visual pattern follows existing page family and tokens.

If items 1-10 are missing, the requirement is not interaction-complete.

## 12. UX Review Output Format

When reviewing a prototype or generated page, use this order:

1. Workflow blockers.
2. Missing business context or hardware identifiers.
3. Missing states or feedback.
4. Error-prevention gaps.
5. Layout and component consistency.
6. Visual token issues.
7. Polish.

Each finding should include:

- Problem.
- User impact.
- Suggested fix.
- Related page family or component rule.
