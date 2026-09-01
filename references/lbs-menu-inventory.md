# LBS PC Menu Inventory

## Source

Canonical workbook: [lbs-function-menu.xlsx](../assets/source-materials/lbs-function-menu.xlsx).

Sheet PC端功能菜单, range A1:P419, is the complete feature and permission inventory. This reference is a compact index; consult the workbook for row-level operations, priorities, and remarks.

## Columns

- 一级菜单
- 二级菜单/模块
- 三级菜单/模块
- 四级功能/操作
- 五级功能/操作
- 管理员
- 经销商
- 政企客户
- 普通用户
- 单设备（定位器）
- 单设备（视频）
- 体验账号
- 优化级
- 备注

√ means available to the role in the source inventory; × means unavailable. Blank cells require source/business confirmation and must not be treated as permission. Visibility in Figma does not override these columns.

## Primary And Secondary Inventory

| Primary | Observed secondary modules |
|---|---|
| 登录 | - |
| 型号支持 | 型号支持、型号管理 |
| 导航 | 帮助中心、设备搜索、客户搜索、语言切换、消息中心、任务中心 |
| 账号设置 | 用户资料、MapsKey、服务商信息、消息设置、反馈、反馈配置、密码设置、退出 |
| 账号首页 | 客户概览、设备概览、服务、快捷功能、状态统计、型号统计、设备统计/设备分析、客户统计、增长量TOP10、设备地域 |
| 定位监控 | 客户搜索、设备搜索、模式切换、自定义模式、设备列表、地图、底部信息模块、搜索、地图切换、卫星地图、围栏、线路、兴趣点、工具、消息、点名 |
| 视频监控 | 监控大屏、实时视频、视频回放、事件中心、旅程影像、下载任务 |
| 轨迹回放 | Source rows continue at deeper operation levels. |
| 我的业务 | 我的客户、蓝牙配件、设备记录、保养记录、分享管理 |
| 司机管理 | 分析助手、司机档案、出行记录、绩效评分、基础配置 |
| 统计报表 | 运行统计、报警统计、温湿度统计、行业统计、区域统计、打卡统计、报表任务、数据导出 |
| 应用市场 | Source rows continue at deeper operation levels. |
| 多维报表 | Source rows continue at deeper operation levels. |
| 财务中心 | 订单管理、资产管理、续费管理、价格管控 |
| 组织管理 | 客户类型、成员管理、部门管理、角色管理、设备关联 |
| 系统管理 | 版本设置、产品服务、Geokey、自定义型号、更换IMEI、日志管理、配置管理、反馈管理、公告管理、定制应用、用户反馈管理 |

## Usage Rules

- Use this inventory to check capability existence, hierarchy, role coverage, and naming context.
- Use final navigation Figma/PRD to decide the release's visual grouping and order.
- Preserve the underlying route and permission behavior when moving an entry.
- Do not flatten a deep operation into navigation merely because it appears in the workbook.
- Search may retrieve a permitted deep function through aliases, but must route to the same guarded destination.
- If Figma, PRD, and inventory name the same capability differently, preserve the canonical route and record the naming migration/alias.
