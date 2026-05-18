# Device Detail Workspace

The device detail dialog is a core product workbench, not a generic modal. It is the highest-priority pattern for hardware device management UI.

## Entry

Primary entry: `/#/device/index` table operation column `详情`.

The workbench opens over the device table with a dark modal overlay. The background device list remains visible but inactive.

## Container

- Width: use `size/modal/device-width` with max width around `size/modal/device-max-width`.
- Height: close to viewport height when content is dense.
- Radius: `radius/modal`.
- Surface: `color/bg/surface`.
- Header:
  - Horizontal tab bar, 65px observed online.
  - Close icon on far right.
  - Active tab uses `color/brand/primary`, 600 weight, bottom 2px active line.
  - Inactive tabs use `color/text/tertiary`.
- Content:
  - Scrollable when needed.
  - Dense forms and tables are expected.
- Footer:
  - Fixed or visually anchored bottom-right actions.
  - Default: 取消 and 确定, 40px high, 8px radius.

## Tabs

Observed tabs include:

- 详情
- 服务版本
- 所属客户
- 追踪
- 指令
- 载重设置
- 油量设置
- 门磁设置
- 续费
- 转移
- 报警设置
- 设备保养
- 设置定时任务
- 自定义提醒
- 温湿度标签

When designing a new tab, keep the same tab architecture and action footer unless the task explicitly needs a read-only view.

## Workbench Layout System

The workbench should behave like a desktop console:

- Header tabs provide task switching.
- Current device context stays visible in content or copied into the active tab.
- Content is grouped by hardware function, not by decorative visual categories.
- Footer actions remain predictable.
- Dense control rows are acceptable when they improve scanability.

Recommended content zones:

- Context row: device name, model, IMEI, customer, status, expiry if relevant.
- Work area: form/table/switch matrix/command group.
- Helper row: info banners, tooltip icons, unit hints, validation.
- Footer: cancel/confirm or task-specific submit.

## Detail Tab

Purpose: edit and inspect physical device and vehicle metadata.

Structure:

- Section: 设备信息.
  - Fields: 设备名称, 型号, IMEI, SIM卡号, ICCID, 导入时间, 激活时间, 平台到期, 用户到期, 卫星模组号.
  - Include quick device operation icons near the section heading when applicable: location, crosshair/target, play/video.
  - Read-only/disabled values use muted surface background.
  - Important IDs should remain easy to scan and copy.
- Section: 车辆信息.
  - Fields: 车牌号码, 联系人, 图标, 油耗, 电话, 图片.
  - Vehicle icon picker is a grid of small hardware/vehicle icons; selected item gets a primary border.
  - Upload area is dashed, square, plus icon, and helper text such as jpg/jpeg/png under 1MB.

Layout:

- Two columns on desktop.
- Labels align right; values align left.
- Keep field widths stable.
- Do not split this into many small cards.

## Renewal Tab

Purpose: renew one or more devices using renewal cards or service period settings.

Common content:

- Add device row: 添加设备 + IMEI input + confirm icon + add icon.
- Device table: 序号, 设备名称, IMEI, 所属客户, 操作.
- Required service period radio: 1年 / 终生.
- Payment method: renewal card option, available card count, explanatory copy.
- Remark textarea with 100-character guidance.

Rules:

- Device table comes before payment settings.
- Required markers use `color/status/error`.
- Payment count or insufficient resources should be prominent but not decorative.

## Transfer Tab

Purpose: move device ownership/customer association.

Use dense form/table structure:

- Device or target customer selector.
- Current customer and target customer display.
- Confirmation action in footer.
- Preserve traceability: show device name and IMEI before transfer action.

## Alarm Settings Tab

Purpose: configure hardware alarm thresholds and switches.

Observed controls:

- Switches for overspeed, offline, fatigue driving, low voltage, etc.
- Checkbox groups for ACC alarms such as 打火 / 熄火.
- Unit inputs such as `mi/H`, `H`, `V`.
- Info icon next to technical labels.
- I/O settings section with select rows such as `input-1`.

Rules:

- Use grouped rows; avoid turning each setting into a separate card.
- Left/right columns are acceptable.
- Unit inputs should be compact and aligned.
- Disabled switches should look intentionally off, not broken.
- Technical labels may remain terse; add tooltips for ambiguous hardware terms.

## Load Setting / 载重设置 Tab

Purpose: configure vehicle load sensors, calibration, thresholds, and device-specific load behavior.

Expected patterns:

- Configuration summary at top: device name, model, sensor state, last calibration time.
- Form groups for:
  - Sensor enable/disable.
  - Calibration mode.
  - Empty-load/full-load reference values.
  - Alarm threshold.
  - Unit display.
- Use compact rows with switches, inputs, and unit suffixes.
- If calibration has steps, use a horizontal stepper or numbered rows, not a marketing timeline.
- If showing sample data, use a compact table or chart inside the work area.

Rules:

- Keep raw hardware readings and interpreted values visually separate.
- Keep units visible on every numeric input.
- Provide disabled states for unsupported models.

## Oil Setting / 油量设置 Tab

Purpose: configure fuel consumption, oil sensor calibration, and fuel-related alarms.

Expected patterns:

- Vehicle fuel consumption field such as `L/100mi` or local unit.
- Sensor or oil type selector.
- Calibration table for points/levels when required.
- Alarm threshold for abnormal consumption or low fuel.

Rules:

- Use tables for multi-point calibration.
- Preserve numeric precision and units.
- Do not hide calibration data behind collapsed cards when editing.

## Door Magnet / 门磁设置 Tab

Purpose: configure door sensor/magnet input and alarms.

Expected patterns:

- Enable switch.
- Input channel selector.
- Trigger condition.
- Alarm copy and notification behavior.
- Optional linkage with ACC or I/O settings.

Rules:

- Show channel mapping clearly.
- If multiple doors/channels exist, use rows or a table.

## Temperature And Humidity Labels / 温湿度标签 Tab

Purpose: configure sensor labels, thresholds, and display names.

Expected patterns:

- Sensor list/table.
- Label/name input.
- Temperature threshold and humidity threshold with units.
- Alarm enable switch.
- Status column for sensor online/offline or unsupported.

Rules:

- Use table format for multiple sensors.
- Use unit suffixes: `℃`, `%`, or localized product units.
- Keep label editing inline or in a compact subdialog.

## Command Tab

Purpose: send commands and inspect command records.

Common content:

- Subtabs or segmented areas: 发送指令, 指令记录.
- Command groups: 设置指令, 查询指令, 更多指令, 自定义指令.
- Example commands: 删除SOS号码, 温度报警, 断电报警, 中心号码管理, 重启设备, 删除中心号码, SOS号码管理, 油电控制, 上传间隔, 震动报警, 蓝牙参数查询.
- Device name context should remain visible when sending commands.

Rules:

- Commands are operational and potentially risky; make action hierarchy clear.
- Do not hide device identity while a command is being configured.
- Use confirmation patterns for destructive or irreversible commands.

## Service Version Tab

Purpose: inspect or adjust service package/version.

Expected data:

- Current version.
- Service period.
- Platform/user expiry dates.
- Upgrade/renewal actions when permitted.

Use a table or compact form depending on data volume.

## Customer Tab

Purpose: inspect or change ownership relation.

Expected data:

- Current customer.
- Parent/customer hierarchy.
- Account code/name.
- Transfer-related actions should link to transfer flow rather than duplicate logic.

## Maintenance / Scheduled Task / Reminder / Sensor Tabs

Use the same workbench shell:

- Keep forms dense and grouped.
- Preserve device name and IMEI context.
- Show empty states inside the content area, not as full-page illustrations.
- Use tables for repeated records such as maintenance logs or scheduled tasks.

## Review Checklist For This Workbench

- Is the dialog wide enough for two-column hardware forms?
- Are IMEI, SIM, ICCID, model, status, and expiry visible in the relevant flow?
- Are active tabs and footer actions consistent with the existing workbench?
- Are form labels aligned and controls stable in width?
- Are command/alarm settings grouped by hardware meaning?
- Are dangerous operations confirmable?
- Are disabled/read-only fields visually distinct from editable fields?
