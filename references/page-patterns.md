# WhatsGPS Page Patterns

Use these patterns when generating new screens, restoring Figma, or reviewing consistency.

## Global Shell

- PC-first SPA with hash routes.
- Deep-blue left navigation:
  - Icon-only width: about `64px`.
  - Full text sidebar where used: `240px`.
  - Active item uses `color/brand/sidebar-active`.
- Top header:
  - Height `64px`.
  - Left: menu icon + page title.
  - Middle/right: global search with `设备 / 客户` switch.
  - Right: language flag, message icon, account dropdown.
- Main workspace:
  - Background `color/bg/page`.
  - White major surfaces with `radius/card`.
  - Floating right rail for `客服 / 帮助 / 提醒` or `客服 / 消息 / 提醒`.

## Dashboard / Account Home

Route: `/#/dashboard/index`

Use for account overview, operational totals, and import/sales/renewal actions.

- Top row: three large summary cards for customer, device, and service.
- Summary card style:
  - White surface, 20px radius, subtle shadow.
  - Main number uses `typography/display/number` and `color/brand/primary`.
  - Secondary labels use `color/text/tertiary`.
  - Small positive deltas use success background and `color/status/success`.
- Middle cards:
  - Operation card with tabs: 导入, 销售, 续费, 升级, 重置.
  - Status donut: online/offline/inactive.
  - Model statistics: table-like labels + progress bars.
- Lower area:
  - Trend charts and TOP10 modules.
  - Use compact chart headers and small segmented controls for 月/季/年.

Avoid: marketing-style hero, oversized empty illustrations, or low-density dashboard cards.

## Device List / Customer Device Management

Route: `/#/device/index`

This is the primary table page for customer-owned hardware devices.

- Left business panel:
  - Title: 客户列表.
  - Tabs: 全部 / 过期.
  - Search: 客户名/账号.
  - Tree list with customer names and counts.
- Main content:
  - Customer summary surface at top with customer name, account code, quick links such as 监控 and 编辑.
  - Stats row: 进货, 库存, 未用, 到期, 在线, 离线.
  - Toolbar:
    - Left: 批量销售, 批量续费, 批量导入, 批量升级, 更多.
    - Right: 包含下级 checkbox, column select, search input, 查询, 批量搜索, 筛选.
  - Table:
    - Key columns: 设备名称, IMEI, SIM号码, ICCID when available, 设备型号, 状态, 服务版本, 版本类型, 导入时间, 平台到期, 用户到期, 激活时间, 最后位置.
    - Operation column is fixed right and includes 详情 / 更多.
    - Table data is the main content; do not replace it with device cards.
  - Footer:
    - Selected count, total count, page size, pagination, jump-to-page, export/download.

Review risks:

- Missing fixed operation column.
- IMEI/SIM/ICCID hidden or visually de-emphasized.
- Batch actions placed below the table.
- Table row height too loose for operational scanning.

## Location Monitor

Route: `/#/monitor/index`

Use for map-first tracking pages.

- Layout:
  - Narrow left global icon sidebar.
  - Large map canvas as the primary surface.
  - Floating left device panel over the map.
  - Right map controls and floating support/message/reminder rail.
- Device panel:
  - Title: 定位监控.
  - Customer selector, device search, setting/list toggle.
  - Status pills: 全部 / 在线 / 离线 / 未激活.
  - Grouped device list with status and expiry/offline text.
- Map controls:
  - Search, map/satellite switch, fence, more, zoom.
- Notification toast/banner can appear over the map; use surface shadow and compact text.

Avoid: covering too much map area with large cards or decorative panels.

## Realtime Video

Route: `/#/video/realtime`

Use for live video monitoring.

- Left panel:
  - Device/customer tree with search.
  - Status row and grouped device list.
  - Include channel/video icons and online/offline/static text.
- Main area:
  - Top selection/action bar with current selected device and channel.
  - Grid controls for 1/4/9/16 views and more actions.
  - Video grid is primary; empty cells use blue/dark video placeholder style.
  - Empty video state: icon + `暂无视频播放 请先选择设备`.
- Keep video cells large and unframed by decorative cards.

## Trip Image / Journey Media

Route: `/#/video/trippics`

Use for device media and trip records.

- Left panel mirrors video pages: search, tree, status, batch operations.
- Main content:
  - Filter row with date range, 查询, 重置.
  - Info banner on the right for beta/availability notice.
  - Table header columns: 序号, 旅程, 旅程时长, 旅程里程, 旅程状态, 操作.
  - Empty state is allowed, but keep it inside a large white operational surface.

## Organization / Member Management

Route: `/#/organizational/index`

Use for internal organization members, not customer device management.

- Left/top navigation indicates 组织管理.
- Main table columns: 姓名, 角色, 账号, 创建时间, 操作.
- Use standard Element UI table and member management actions.

Do not confuse this route with the customer/device list; the customer/device workbench is `/#/device/index`.
