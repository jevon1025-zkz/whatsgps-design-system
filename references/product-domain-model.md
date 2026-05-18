# WhatsGPS Product Domain Model

Use this reference to understand what the UI is really managing. This platform is not a generic admin system; it is a hardware-device operations system.

## Product Names And Context

- Product/platform names: WhatsGPS, Justrack, 立即定位.
- PC routes observed:
  - Dashboard: `/#/dashboard/index`
  - Device/customer management: `/#/device/index`
  - Location monitor: `/#/monitor/index`
  - Realtime video: `/#/video/realtime`
  - Trip images: `/#/video/trippics`
  - Organization member management: `/#/organizational/index`
- Frontend convention: Vue 2 SPA, hash router, Element UI component classes.

## Core Entities

### Device

Primary operational object.

High-priority fields:

- 设备名称
- IMEI
- SIM号码
- ICCID
- 设备型号
- 状态
- 服务版本
- 版本类型
- 导入时间
- 平台到期
- 用户到期
- 激活时间
- 最后位置 / 查看地址
- 所属客户

Design rule: never hide IMEI, status, expiry, and ownership in device-list or device-detail workflows.

### Customer / Client

Represents account, customer, dealer, or organization owner of devices.

Common fields:

- 客户名 / 账号
- 客户层级 / 下级客户
- 直属客户
- 进货 / 库存
- 未用 / 到期
- 在线 / 离线

Design rule: customer pages often combine a customer tree, summary card, toolbar, and device table.

### Service / Version

Represents paid packages, feature access, and expiration.

Common fields:

- 标准版
- 1年 / 终生
- 平台到期
- 用户到期
- 已过期 / 即将过期
- 续费卡 / 可用续费卡

Design rule: service state must be close to device identity, because operators act on expiry.

### Location / Tracking

Represents GPS map, last point, historical track, and tracking operations.

Common data:

- 位置 / 查看地址
- 在线 / 离线
- 速度
- 默认分组
- 地图 / 卫星 / 围栏 / 更多

Design rule: map canvas is primary. Device panel supports filtering and selection; do not over-card the map.

### Video

Represents realtime video, playback, trip image, evidence, event center, and storage.

Common data:

- 通道
- 实时视频
- 视频回放
- 旅程影像
- 事件中心
- 视频存储
- 视频设备状态

Design rule: video grid or media table is primary. Empty states should explain device selection, not become decorative.

### Command

Represents device command sending and query operations.

Command groups:

- 设置指令
- 查询指令
- 更多指令
- 自定义指令

Examples:

- 删除SOS号码
- 温度报警
- 断电报警
- 中心号码管理
- 重启设备
- 删除中心号码
- SOS号码管理
- 油电控制
- 上传间隔
- 震动报警
- 蓝牙参数查询

Design rule: keep device identity visible when configuring or sending commands. Destructive commands need confirmation.

### Alarm / Sensor / Hardware Configuration

Represents thresholds, switches, I/O, and sensor configuration.

Common areas:

- 报警设置
- 载重设置
- 油量设置
- 门磁设置
- 温湿度标签
- I/O 设置
- 静止阈值
- 疲劳驾驶
- 低压报警
- ACC 报警

Design rule: group by hardware function. Use switches, unit inputs, checkboxes, and tooltips. Avoid one-card-per-setting layouts.

## Status Model

Use consistent visual treatment:

- 在线: success or primary emphasis depending on context.
- 离线: muted text; still operationally important.
- 未激活: muted or warning depending on actionability.
- 已过期: error.
- 即将过期: warning.
- 静止: blue/tertiary operational state.
- 加载中: local spinner or skeleton.
- 无数据: compact empty state inside current surface.
- 无权限: empty/locked state with clear copy.

## Action Model

Primary actions:

- 查询
- 确定
- 导入
- 续费
- 升级

Secondary actions:

- 重置
- 取消
- 更多
- 批量搜索
- 筛选

Row/link actions:

- 详情
- 更多
- 查看地址
- 监控
- 编辑
- 移除

Danger actions:

- 删除
- 停止
- 重置设备
- 删除中心号码
- 删除 SOS 号码

Design rule: danger actions should not be styled as ordinary blue links without confirmation.

## Field Priority

For generated or reviewed pages, preserve this priority order:

1. Entity identity: device/customer/service name.
2. Hardware identifiers: IMEI, SIM, ICCID, model.
3. Operational status: online/offline/inactive/expired.
4. Ownership and service state: customer, version, expiry.
5. Action controls: detail, search, batch, renew, transfer, command.
6. Supporting metadata: import time, activation time, last address, notes.

If space is constrained, hide supporting metadata before hiding identifiers or status.
