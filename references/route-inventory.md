# WhatsGPS Route Inventory

Use this reference when a task depends on the real page map of the WhatsGPS/Justrack/立即定位 PC web platform.

## Source And Limits

- Audit date: 2026-05-06.
- Method: read-only browser audit, opening each route in a fresh page after login to avoid hash-router state leakage.
- Coverage: 44 candidate routes tested; 36 loaded usable product pages; 8 returned `Page Not Fount`.
- Scope: current pre-release environment and current account permissions. A 404 route may mean disabled menu, missing permission, unfinished feature, or removed route. Confirm with product/Figma before designing those routes as active pages.
- This audit records page structure, route, tabs, tables, filters, and component density. It is not a complete visual screenshot archive.

## How To Use

- For page generation, classify the target route against the page family below before choosing layout.
- For Figma restoration, use this file to understand neighboring pages and navigation context.
- For UI review, check whether the screen follows its page family's density, toolbar, table, filter, and empty-state conventions.
- For requirement design drafts, use route names and tab names from this file to avoid inventing menu terminology.

## Global Shell

Common PC shell patterns:

- Deep-blue left navigation with modules such as 账号首页, 定位监控, 视频监控, 我的业务, 财务中心, 统计报表, 组织管理, 系统管理.
- White top bar with hamburger/menu icon, current page title, global search, language/message/user controls.
- Light blue-gray workspace background with white content panels.
- Right floating support rail for 客服, 帮助, 消息, 提醒 depending on page.
- Element UI style controls: inputs, selects, tabs, tables, pagination, dialogs, switches, radios, checkboxes.

## Route Families

### Dashboard

Routes:

- `/dashboard/index` - account home dashboard.

Primary surface:

- Summary cards for 客户, 设备, 服务.
- Import/sales/renew/upgrade operation tabs.
- Status/model/customer/growth statistical cards and charts.

Design guidance:

- Keep the dashboard operational. It should surface counts, renewal/import actions, and device/service risk, not become a marketing landing page.
- Cards may be larger here than in table pages, but still use dashboard metrics and quick operations as the first priority.

### Device And Customer Management

Routes:

- `/device/index` - 我的客户 / device list.
- `/device/device-record` - device operation records.
- `/device/maintain-log` - maintenance records.
- `/device/share-log` - track share management.

Primary surface:

- Customer tree or customer list panel plus device summary.
- Batch action toolbar: 批量销售, 批量续费, 批量导入, 批量升级, 更多, 筛选.
- Dense `el-table` device list with identifiers: 设备名称, IMEI, SIM号码, 设备型号, 状态, 服务版本, 版本类型, 导入时间, 平台到期, 用户到期, 激活时间, 最后位置, 操作.
- Record pages use tabbed logs: 导入记录, 升级记录, 销售记录, 转移记录, 标签关联记录.
- Maintenance/share pages use explanatory notice copy, filters, tables, and row actions.

Design guidance:

- This is the core list-to-detail workflow. Preserve selected customer context, batch selection state, total count, page size, and row action column.
- The device detail dialog/workbench usually launches from this page. Do not simplify it into a small modal.
- Identifiers and expiry state are more important than decorative status cards.

### Device Detail Workbench

Observed from the device list:

- Wide modal with top tabs: 详情, 服务版本, 所属客户, 追踪, 指令, 续费, 转移, 报警设置, 设备保养, 设置定时任务, 自定义提醒.
- Additional hardware/config tabs observed in route behavior and screenshots: 载重设置, 油量设置, 门磁设置, 温湿度标签.
- Tab content includes dense forms, editable/disabled fields, hardware icon selection, switches, threshold inputs, service/payment tables, and footer actions.

Design guidance:

- Treat this as the product's hardware operations cockpit.
- Keep device identity visible or easy to recover: 设备名称, IMEI, 型号, SIM, ICCID, 所属客户, 到期时间.
- Hardware settings should use grouped rows, unit inputs, switches, tooltips, and compact validation.

### Location And Tracking

Routes:

- `/monitor/index` - live location monitor.
- `/monitor/history` - historical playback.
- `/track-saas` - standalone tracking view.

Primary surface:

- Full map canvas with left device tree/filter panel.
- Device status counters: 全部, 在线, 离线, 未激活.
- Map controls: 地图, 卫星, 围栏, 更多, zoom, street view when available.
- History playback includes date range, quick ranges, speed/trajectory detail panels, and map overlays.

Design guidance:

- Map is the primary work surface. Side panels should be dense and collapsible enough for the map to remain useful.
- Empty/error states should be local and operational, such as no selected device or request error.

### Video

Routes:

- `/video/realtime` - realtime video.
- `/video/trippics` - trip images.
- `/video/playback` - video playback.
- `/video/eventcenter` - event center.
- `/video/evidence` - download task / event evidence.

Primary surface:

- Realtime video: customer/device tree, device status counters, current selection, channel controls, media grid.
- Trip images: tree/filter panel, date range, batch operations, table/empty state for V7pro trial capability.
- Playback: device/date query plus calendar/video result area.
- Event center: event dashboard metrics, risk levels, filters, event table.
- Evidence/download: tabs for 视频下载 and 事件证据, storage notice, filters, table.

Design guidance:

- Media pages should not be generic tables. They need a strong selected-device and channel model.
- Empty video tiles should say the operational reason, e.g. select a device first or no playable channel.

### Finance And Service

Routes:

- `/finance/asset` - asset management.
- `/finance/order` - order route loaded as a blank/simple shell in this audit.
- `/finance/renew` - renewal management.

Primary surface:

- Asset management uses tabs such as 点卡管理 and 视频带宽流量, with account balance/card inventory and ledger table.
- Renewal management uses tabs: 续费升级, SIM卡续费, 待续费设备, 到期不续, 待升级设备.
- Renewal tables prioritize 设备名称, IMEI, 车牌号, 设备型号, 所属客户, 服务版本, 到期倒计时, 到期类型, 平台到期, 用户到期.

Design guidance:

- Finance pages are action-heavy and risk-sensitive. Keep balance, available cards, expiry type, and batch result visible.
- `/finance/order` needs additional screenshot/product confirmation before using it as a design source.

### Line Path

Routes:

- `/linePath/setting` - route/line setup.
- `/linePath/alarmSetting` - route alarm setup.

Primary surface:

- Line setup combines route table and map.
- Alarm setup uses filters and table fields: 线路, 适用设备, 状态, 偏移距离, 超速阈值, 适用时间, 报警方式, 开始地点, 结束地点, 修改时间, 操作.

Design guidance:

- Preserve map context and alarm thresholds. This page family belongs with location/geofence workflows, not generic system settings.

### Organization

Routes:

- `/organizational/index` - member management.
- `/organizational/departManager` - department management.
- `/organizational/roleManager` - role management.
- `/organizational/deviceRelation` - device association for supervisors.
- `/organizational/clientType` - 404 in this audit.

Primary surface:

- Organization pages use compact management tables and simple CRUD actions.
- Member management fields include 姓名, 角色, 账号, 创建时间, 操作.
- Role/device relation pages define permissions and visible device lists.

Design guidance:

- Keep permissions, roles, and device visibility explicit. This page family controls who can see which hardware assets.

### Reports

Routes:

- `/report/overview` - running statistics.
- `/report/alarm` - alarm statistics.
- `/report/tempHumidity` - temperature/humidity statistics.
- `/report/industry` - industry statistics.
- `/report/region` - region/fence statistics.
- `/report/punch` - driver punch statistics.
- `/report/report-task` - report tasks.
- `/report/export` - data export.

Primary surface:

- Multi-tab analytics pages with date range filters, customer/group filters, query/reset actions, tables, metrics, and charts.
- Running statistics tabs: 运行总览, 里程统计, 超速详单, 停留详单, ACC统计, 行程统计, 离线统计, 怠速统计, 静止统计.
- Alarm statistics tabs: 报警总览, 报警统计, 报警详单.
- Industry statistics tabs include 油量, 电压, 条码, 驾驶行为, 抓拍, 充电, 载重分析, 开关门.
- Region statistics tabs include 出入围栏统计, 出入围栏详单, 围栏报警详单, 线路报警详单.
- Data export includes field configuration and task list behavior.

Design guidance:

- Reports need strong filter clarity and table/chart pairing. Do not convert them into isolated KPI cards only.
- Date range constraints are part of UX; preserve helper text such as maximum range rules.

### System Configuration

Routes:

- `/system/config` - configuration management.
- `/system/customize` - custom model list.
- `/system/manage` - custom model edit/create form.
- `/system/command` - command configuration.
- `/system/index`, `/system/feedback`, `/system/operatelogs`, `/system/replace`, `/system/bulletin`, `/system/customizeApp` - 404 in this audit.

Primary surface:

- Configuration pages use filters, add/copy actions, tables, and dense admin forms.
- Custom model edit includes fields for model name, sort, domain, port, connection method, protocol, device type, image, alarm platform capabilities, and feature toggles.
- Command configuration is a very dense form for command name, group, type, control type, remarks, query parameters, supported platforms, permissions, sorting, confirmation, template, and parameter configuration.

Design guidance:

- These pages are for admin setup, not daily monitoring. They can be denser and more form-heavy.
- Command/model configuration should use clear grouping, collapsible sections, and validation. Avoid hiding key compatibility fields.

### User Center And Messages

Routes:

- `/user/center` - personal center.
- `/user/message` - message center.

Primary surface:

- Personal center has basic info, password, service provider info, and system settings behavior.
- Message center uses tabs: 报警信息, 站内信息, 系统公告, 活动公告, with table actions such as 全部已读, 标记已读, 删除.

Design guidance:

- Keep these pages simple and table/form based. They are secondary to device operations but must preserve message status and account identity.

## Currently Unverified Or Not Usable As Source

Routes returning 404 in the current audit:

- `/organizational/clientType`
- `/product/index`
- `/system/index`
- `/system/feedback`
- `/system/operatelogs`
- `/system/replace`
- `/system/bulletin`
- `/system/customizeApp`

Route loaded but did not expose meaningful page content:

- `/finance/order`

Before designing these routes, ask for a screenshot, Figma frame, product requirement, or permission-confirmed account.

## Route-To-Pattern Shortcut

- Dashboard metrics: use dashboard cards/charts from `page-patterns.md`.
- Device/customer tables: use device list and device detail workbench references.
- Map pages: use map canvas with left device panel.
- Video pages: use tree plus media grid or event/download table depending on route.
- Finance pages: use tabs, balance/card state, and renewal batch tables.
- Organization pages: use compact CRUD tables with role/device visibility.
- Reports: use filters plus tabbed analytics table/chart layouts.
- System configuration: use dense forms with grouped sections.
