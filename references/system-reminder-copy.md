# System Reminder Copy

## Source And Usage

Canonical source: [reminder-copy-source.xlsx](../assets/source-materials/reminder-copy-source.xlsx).

- Sheet 报警信息: A1:B8.
- Sheet 站内信息: A1:D62.
- PC message-center titles and mobile push content use the same approved wording for the same role/event.
- This reference records source text without editorial correction.
- Do not expand this into the excluded 68-alarm taxonomy or complete alarm mapping.

## Alarm Information

### Mobile Alarm Push

Current:

```text
#设备名称#：#报警类型#
您的爱车#设备名称#发生#报警类型#，请及时处理
```

New Chinese source:

```text
#设备名称#
你的设备检测到#空格#震动报警(IMEI：861234567890123)，请及时处理！
```

New English source:

    Your device has detected #报警类型#(IMEI:#imei号#). Please deal with it in time!

### Web Alarm Notification

Current title:

    #设备名称##报警类型#

Source decision: 不变.

## In-System Information

The source states that Web message-center titles and mobile push content remain consistent for the following types.

### SIM卡即将到期

- Current: 您有x张SIM卡即将到期，请及时续费！
- Ordinary/single-device CN: 您有X张SIM卡即将到期，为了不影响您的正常使用，请及时联系服务商续费。
- Ordinary/single-device EN: You have #数量# SIM cards that are about to expire. To ensure your normal use, please contact your service provider to renew them in time.
- Dealer/government-enterprise CN: 您有X张SIM卡即将到期，为了不影响您的正常使用，请及时续费。
- Dealer/government-enterprise EN: You have #数量# SIM cards that are about to expire. Please renew them in time to ensure uninterrupted use.

### SIM卡已到期

- Current: 您有x张SIM卡已到期，为避免设备断网，请及时续费！
- Ordinary/single-device CN: 您有x张SIM卡已到期，为避免设备断网，请及时联系服务商续费。
- Ordinary/single-device EN: You have #数量# SIM cards that have expired. To avoid your device losing network access, please contact your service provider to renew them as soon as possible.
- Dealer/government-enterprise CN: 您有X张SIM卡已到期，为避免设备断网，请及时续费。
- Dealer/government-enterprise EN: You have #数量# SIM cards that have expired. Please renew them in time to avoid your device being disconnected from the network.

### SIM卡流量预警

- Current: 您有x张SIM卡流量预警，请及时处理！
- Ordinary/single-device CN: 您有X张SIM卡流量余量不足，请及时联系服务商处理。
- Ordinary/single-device EN: You have #数量# SIM cards with insufficient data allowance. Please contact your service provider immediately for assistance.
- Dealer/government-enterprise CN: 您有X张SIM卡流量余量不足，请及时处理。
- Dealer/government-enterprise EN: You have #数量# SIM cards with insufficient data allowance. Please address this promptly.

### SIM卡流量已用尽

- Current: 您有x张SIM卡流量已耗尽，为避免产生额外费用，请及时处理！
- Ordinary/single-device CN: 您有X张SIM卡流量已用尽，为避免产生额外费用，请及时联系服务商处理。
- Ordinary/single-device EN: You have used up the data on #数量# SIM cards. To avoid additional charges, please contact your service provider immediately.
- Dealer/government-enterprise CN: 您有X张SIM卡流量流量已用尽，为避免产生额外费用，请及时处理。
- Dealer/government-enterprise EN: You have used up your data allowance on #数量# SIM cards. To avoid additional charges, please handle this promptly.

### 设备到期

- Current: 您有X台设备已到期，为避免设备停用，请及时续费！
- Ordinary/single-device CN: 您有X台设备已到期，当前设备已停用，请及时联系服务商处理。
- Ordinary/single-device EN: You have #数量# devices that have expired and are currently out of service. Please contact your service provider immediately for assistance.
- Dealer/government-enterprise CN: 您有X台设备已到期，当前设备已停用，请及时续费以恢复使用。
- Dealer/government-enterprise EN: You have #数量# devices that have expired and are currently out of service. Please renew your subscription in time to restore service.

### 设备续费

- Current: 您有4台设备即将到期，为避免设备停用，请及时续费！
- Ordinary/single-device CN: 您有X台设备即将到期，为避免设备停用，请在到期前联系服务商进行续费。
- Ordinary/single-device EN: You have #数量# devices whose leases are about to expire. To avoid the devices becoming unusable, please contact your service provider to renew them before the expiration date.
- Dealer/government-enterprise CN: 您有X台设备即将到期，为避免设备停用，请在到期前完成续费。
- Dealer/government-enterprise EN: You have #数量# devices whose leases are about to expire. To avoid the devices becoming unusable, please renew them before they expire.

### 设备升级

- Current: 您有1台设备体验即将到期，请及时升级！
- Ordinary/single-device CN: 您有X台设备的基础版服务即将到期，到期后，部分功能可能无法正常使用，请及时联系服务商升级。
- Ordinary/single-device EN: Your basic service for #数量# devices is about to expire. After the expiration, some functions may no longer be available. Please contact your service provider to upgrade as soon as possible.
- Dealer/government-enterprise CN: 您有X台设备的基础版服务即将到期，到期后，部分功能可能无法正常使用，可使用导入点为设备升级。
- Dealer/government-enterprise EN: The basic service for #数量# devices is about to expire. After the expiration, some functions may no longer be available. You can use the import point to upgrade the devices.

### 设备保养

- Current: 您的V6-203728已到保养周期，请及时进行保养！
- Ordinary/single-device CN: 您的#设备名称#已到保养周期，请及时进行保养。
- Ordinary/single-device EN: Your equipment #设备名称# has reached its maintenance period. Please perform maintenance in a timely manner.
- Dealer/government-enterprise: source cells are blank.

### 带宽流量预警

- Current: 您有10台视频Pro版设备带宽流量预警，为避免无法使用视频功能，请及时联系上级咨询购买平台带宽流量！
- Ordinary/single-device CN: 您有X台专业版设备的视频带宽流量余量不足，为保障视频功能正常使用，请及时前往应用市场购买视频带宽流量。
- Ordinary/single-device EN: You have insufficient video bandwidth on #数量# professional devices. To ensure normal use of video functions, please purchase more video bandwidth from the app store as soon as possible.
- Dealer/government-enterprise: source cells are blank.

### 带宽流量已用尽

- Current: 您有10台视频Pro版设备带宽流量耗尽，视频相关功能不可用，请及时联系上级咨询购买平台带宽流量！
- Ordinary/single-device CN: 您有X台专业版设备的视频带宽流量已用尽，为保障视频功能正常使用，请及时前往应用市场购买视频带宽流量。
- Ordinary/single-device EN: You have exhausted the video bandwidth for #数量# professional devices. To ensure normal use of video functions, please go to the app store to purchase more video bandwidth as soon as possible.
- Dealer/government-enterprise: source cells are blank.
- Source note: cell D40 contains 66 without a defined header/meaning.

### 自定义提醒

Source decision for ordinary/single-device and dealer/government-enterprise: 不改.

Current source structure:

    2.自定义提醒
    标题：{设备名称}:{提醒项目名称}
    内容：
    设备名称
    提醒项目名称
    提醒时间
    用户填写的备注

The sheet contains a second 自定义提醒 heading with empty copy cells; preserve current behavior until clarified.

### 轨迹回放增值服务 - 服务到期

- Current: 您有X台设备轨迹回放服务已到期，增值服务功能已停用！
- Single-device CN: 您有X台设备轨迹回放服务已到期，增值服务功能已停用，请及时联系服务商续费以恢复使用。
- Single-device EN: You have #数量# devices whose Track Playback service has expired, and their value-added service features are currently out of service. Please contact your service provider immediately to renew the service and restore access.
- Dealer/government-enterprise/ordinary-user CN: 您有X台设备轨迹回放服务已到期，当前设备增值服务功能已停用，请及时续费以恢复使用。
- Dealer/government-enterprise/ordinary-user EN: You have #数量# devices whose Track Playback service has expired, and their value-added service features are currently out of service. Please renew the service in time to restore access.

### 轨迹回放增值服务 - 服务续费

- Current: 您有X台设备轨迹回放服务即将到期，为避免增值服务功能停用，请及时续费！
- Single-device CN: 您有X台设备轨迹回放服务即将到期，为避免增值服务功能停用，请在到期前联系服务商进行续费。
- Single-device EN: You have #数量# devices whose Track Playback service is about to expire. To avoid the value-added service features becoming unavailable, please contact your service provider to renew the service before the expiration date.
- Dealer/government-enterprise/ordinary-user CN: 您有X台设备轨迹回放服务即将到期，为避免增值服务功能停用，请在到期前完成续费。
- Dealer/government-enterprise/ordinary-user EN: You have #数量# devices whose Track Playback service is about to expire. To avoid the value-added service features becoming unavailable, please renew the service before it expires.

## Implementation Notes Requiring Confirmation

Do not silently fix these source issues:

- x, X, #数量#, and concrete numbers are used inconsistently.
- SIM卡流量流量已用尽 repeats 流量.
- 可使用导入点为设备升级 may contain an incorrect business term.
- The new Chinese alarm example hard-codes 震动报警 and sample IMEI 861234567890123 while English uses variables.
- Alarm placeholders vary between #imei号#, #设备名称#, #报警类型#, #空格#, and brace-style custom-reminder placeholders.
- Confirm punctuation/full-width conventions and placeholder schema before implementation; preserve approved visible wording across PC and mobile afterward.
