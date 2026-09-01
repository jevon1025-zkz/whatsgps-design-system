# WhatsGPS 颜色 Token 规范

> 适用对象：立即定位 / WhatsGPS PC Web 设计系统  
> 当前阶段：颜色基础规范 v0.2  
> 来源：`theme.scss`、`variables.scss`、`layer-1-gradient-palette.html`、Figma Variables

## 1. 目标

这份文档用于统一 WhatsGPS 颜色规范的使用方式，解决以下问题：

- 新旧页面颜色混用
- Figma 色值、前端 SCSS、Element UI 封装样式不一致
- 设计时不知道应该从基础色板取色，还是从组件色取色
- 后续需要预留浅色 / 深色主题切换入口

当前颜色体系不单独增加 `semantic` 层，采用更直接的两层结构：

```text
Layer 1: Gradient Palette 基础梯度色板
Layer 2: Component Tokens 组件 / 业务映射
```

## 2. Figma 变量结构

当前 Figma 中应维护两个新的变量集合：

| Collection | Mode | 用途 | 使用者 |
|---|---|---|---|
| `01 Gradient Palette` | `Base` | 基础色阶，只表达颜色本身 | 设计系统维护者 |
| `02 Component Tokens` | `Light` / `Dark` | 页面、组件、业务状态实际使用色 | 日常设计、组件库、页面设计 |

旧的 `Color` collection 暂时保留，作为历史兼容层，不建议继续新增。

## 3. 使用原则

### 日常做需求页

优先使用：

```text
02 Component Tokens
```

例如：

```text
text/primary
bg/page
button/primary/bg
input/border
table/header-bg
device/online
service/expired
```

### 不建议日常直接使用

```text
01 Gradient Palette
```

基础色板只负责提供颜色原料。除非是在维护设计系统、补组件状态、做新业务映射，否则不要在页面里大量直接使用基础色阶。

### 旧稿迁移

旧设计稿不会自动切换到新变量。迁移策略：

| 场景 | 处理方式 |
|---|---|
| 新需求页 | 直接使用 `02 Component Tokens` |
| 旧页面局部改版 | 改到哪里，替换哪里的变量 |
| 公共组件 | 优先迁移到新变量 |
| 历史零散页面 | 暂不强制全量替换，后续改版时迁移 |

## 4. 命名结论

### Blue Grey

`blue-grey` 是产品主中性色。它不是普通灰色，而是偏蓝灰，用于页面背景、边框、文字层级。

来源色：

```text
#F4F7FE
#E9EDF7
#A3AED0
#707EAE
#2B3574
#1B2559
```

### Grey

`grey` 是 Element / 旧样式中性灰，主要来自旧按钮、下拉菜单、侧栏菜单等。

来源色：

```text
#F5F5F5
#D9D9D9
#A2A2A2
#8C8C8C
#333333
#202020
```

### Dark Blue

`dark-blue` 是侧栏、深色容器、视频深色背景的基础色阶。

来源色：

```text
#1C2758
#111835
#0F123F
#040507
```

不再使用 `slate`、`navy` 作为正式命名。

## 5. Layer 1: Gradient Palette

### Base

| Figma Token | CSS Token | Value |
|---|---|---|
| `white` | `--white` | `#FFFFFF` |
| `black` | `--black` | `#000000` |

### Brand

| Figma Token | CSS Token | Value | 备注 |
|---|---|---|---|
| `brand/1` | `--brand-1` | `#F1F5FF` | 来源：active dropdown bg |
| `brand/2` | `--brand-2` | `#E6F1FC` | 来源：button hover bg |
| `brand/3` | `--brand-3` | `#C8DDFF` | 补齐梯度 |
| `brand/4` | `--brand-4` | `#86B5FF` | 补齐梯度 |
| `brand/5` | `--brand-5` | `#3370FF` | 来源：menu active bg |
| `brand/6` | `--brand-6` | `#0068FF` | 主品牌蓝 |
| `brand/7` | `--brand-7` | `#1755E7` | 来源：click |
| `brand/8` | `--brand-8` | `#0047B8` | 补齐梯度 |
| `brand/9` | `--brand-9` | `#003680` | 补齐梯度 |

说明：`#006AFF` 与 `#0068FF` 极接近，统一收敛为 `brand/6 #0068FF`。

### Green

| Figma Token | CSS Token | Value |
|---|---|---|
| `green/1` | `--green-1` | `#E6FBF5` |
| `green/2` | `--green-2` | `#C7F7E9` |
| `green/3` | `--green-3` | `#93ECD5` |
| `green/4` | `--green-4` | `#5EE0C0` |
| `green/5` | `--green-5` | `#27D3A7` |
| `green/6` | `--green-6` | `#05CD99` |
| `green/7` | `--green-7` | `#04A87E` |
| `green/8` | `--green-8` | `#037F60` |
| `green/9` | `--green-9` | `#025C46` |

### Yellow

| Figma Token | CSS Token | Value |
|---|---|---|
| `yellow/1` | `--yellow-1` | `#FFF9E6` |
| `yellow/2` | `--yellow-2` | `#FFF0B8` |
| `yellow/3` | `--yellow-3` | `#FFE58F` |
| `yellow/4` | `--yellow-4` | `#FFD666` |
| `yellow/5` | `--yellow-5` | `#FFCE20` |
| `yellow/6` | `--yellow-6` | `#D9A40F` |
| `yellow/7` | `--yellow-7` | `#AD7D00` |
| `yellow/8` | `--yellow-8` | `#805800` |
| `yellow/9` | `--yellow-9` | `#593B00` |

### Red

| Figma Token | CSS Token | Value |
|---|---|---|
| `red/1` | `--red-1` | `#FFF1F0` |
| `red/2` | `--red-2` | `#FFCCC7` |
| `red/3` | `--red-3` | `#FFA39E` |
| `red/4` | `--red-4` | `#FF7875` |
| `red/5` | `--red-5` | `#FF4D4F` |
| `red/6` | `--red-6` | `#F5222D` |
| `red/7` | `--red-7` | `#CF1322` |
| `red/8` | `--red-8` | `#A8071A` |
| `red/9` | `--red-9` | `#820014` |

### Blue Grey

| Figma Token | CSS Token | Value | 建议用途 |
|---|---|---|---|
| `blue-grey/1` | `--blue-grey-1` | `#F4F7FE` | 页面背景 |
| `blue-grey/2` | `--blue-grey-2` | `#E9EDF7` | 边框 / 分割线 |
| `blue-grey/3` | `--blue-grey-3` | `#CBD5E8` | 补齐梯度 |
| `blue-grey/4` | `--blue-grey-4` | `#A3AED0` | 禁用 / 弱化 |
| `blue-grey/5` | `--blue-grey-5` | `#707EAE` | 三级文字 / 表头 |
| `blue-grey/6` | `--blue-grey-6` | `#2B3574` | 二级文字 |
| `blue-grey/7` | `--blue-grey-7` | `#1B2559` | 主文字 |

### Grey

| Figma Token | CSS Token | Value | 备注 |
|---|---|---|---|
| `grey/1` | `--grey-1` | `#F7F7F7` | 补齐梯度 |
| `grey/2` | `--grey-2` | `#F5F5F5` | 下拉 hover |
| `grey/3` | `--grey-3` | `#E5E5E5` | 补齐梯度 |
| `grey/4` | `--grey-4` | `#D9D9D9` | 默认按钮边框 |
| `grey/5` | `--grey-5` | `#A2A2A2` | 侧栏默认文字 |
| `grey/6` | `--grey-6` | `#8C8C8C` | close hover |
| `grey/7` | `--grey-7` | `#595959` | 注释旧按钮文字色，作为灰阶桥接 |
| `grey/8` | `--grey-8` | `#333333` | 二级菜单背景 |
| `grey/9` | `--grey-9` | `#202020` | 菜单背景 |

### Dark Blue

| Figma Token | CSS Token | Value | 建议用途 |
|---|---|---|---|
| `dark-blue/1` | `--dark-blue-1` | `#EEF2FF` | 补齐梯度 |
| `dark-blue/2` | `--dark-blue-2` | `#CFD7F0` | 补齐梯度 |
| `dark-blue/3` | `--dark-blue-3` | `#9AA8D0` | 补齐梯度 |
| `dark-blue/4` | `--dark-blue-4` | `#6878AD` | 补齐梯度 |
| `dark-blue/5` | `--dark-blue-5` | `#3B4A80` | 补齐梯度 |
| `dark-blue/6` | `--dark-blue-6` | `#1C2758` | 侧栏渐变起点 |
| `dark-blue/7` | `--dark-blue-7` | `#111835` | 侧栏渐变终点 |
| `dark-blue/8` | `--dark-blue-8` | `#0F123F` | 深色容器 |
| `dark-blue/9` | `--dark-blue-9` | `#040507` | 深色 hover / 控制条 |

## 6. Layer 2: Component Tokens

### Text / Background / Border

| Figma Token | CSS Token | Light 引用 | Dark 入口 | 用途 |
|---|---|---|---|---|
| `text/primary` | `--text-primary` | `blue-grey/7` | 已预留 | 正文、表格主体、核心字段 |
| `text/secondary` | `--text-secondary` | `blue-grey/6` | 已预留 | 二级标题、次级信息 |
| `text/tertiary` | `--text-tertiary` | `blue-grey/5` | 已预留 | 表头、placeholder、辅助文字 |
| `text/disabled` | `--text-disabled` | `blue-grey/4` | 已预留 | 禁用、不可操作、弱化状态 |
| `text/inverse` | `--text-inverse` | `white` | 已预留 | 深色背景反白文字 |
| `bg/page` | `--bg-page` | `blue-grey/1` | 已预留 | 页面工作区背景 |
| `bg/surface` | `--bg-surface` | `white` | 已预留 | 卡片、表格、弹窗、面板 |
| `border/default` | `--border-default` | `blue-grey/2` | 已预留 | 表单、卡片、表格分割线 |

### Button

| Figma Token | CSS Token | Light 引用 | 用途 |
|---|---|---|---|
| `button/primary/bg` | `--button-primary-bg` | `brand/6` | 查询、确定、导入、主提交 |
| `button/primary/hover-bg` | `--button-primary-hover-bg` | `brand/5` | 主按钮 hover |
| `button/primary/active-bg` | `--button-primary-active-bg` | `brand/7` | 主按钮按下态 |
| `button/default/bg` | `--button-default-bg` | `white` | 默认按钮背景 |
| `button/default/border` | `--button-default-border` | `grey/4` | 默认按钮边框 |
| `button/default/hover-bg` | `--button-default-hover-bg` | `brand/2` | 默认按钮 hover 背景 |
| `button/danger/bg` | `--button-danger-bg` | `red/5` | 删除、危险操作 |

### Input / Select / Dropdown

| Figma Token | CSS Token | Light 引用 | 用途 |
|---|---|---|---|
| `input/bg` | `--input-bg` | `white` | 输入框、选择器背景 |
| `input/border` | `--input-border` | `blue-grey/2` | 默认边框 |
| `input/border-hover` | `--input-border-hover` | `brand/4` | hover 边框 |
| `input/border-focus` | `--input-border-focus` | `brand/6` | focus 边框 |
| `input/border-error` | `--input-border-error` | `red/5` | 校验错误 |
| `dropdown/hover-bg` | `--dropdown-hover-bg` | `grey/2` | 下拉菜单 hover |
| `dropdown/active-bg` | `--dropdown-active-bg` | `brand/1` | 下拉菜单选中 |

### Table / Tabs

| Figma Token | CSS Token | Light 引用 | 用途 |
|---|---|---|---|
| `table/header-bg` | `--table-header-bg` | `blue-grey/1` | 表头背景 |
| `table/border` | `--table-border` | `blue-grey/2` | 表格分割线 |
| `table/row-bg` | `--table-row-bg` | `white` | 表格行背景 |
| `table/row-hover-bg` | `--table-row-hover-bg` | `brand/1` | 表格行 hover / 轻选中 |
| `table/text-header` | `--table-text-header` | `blue-grey/5` | 表头文字 |
| `tab/text-active` | `--tab-text-active` | `brand/6` | 激活 Tab 文字 |
| `tab/line-active` | `--tab-line-active` | `brand/6` | 激活 Tab 下划线 |

### Sidebar

| Figma Token | CSS Token | Light 引用 | 用途 |
|---|---|---|---|
| `sidebar/bg-start` | `--sidebar-bg-start` | `dark-blue/6` | 侧栏渐变起点 |
| `sidebar/bg-end` | `--sidebar-bg-end` | `dark-blue/7` | 侧栏渐变终点 |
| `sidebar/menu-bg` | `--sidebar-menu-bg` | `grey/9` | 旧菜单默认背景 |
| `sidebar/submenu-bg` | `--sidebar-submenu-bg` | `grey/8` | 旧二级菜单背景 |
| `sidebar/menu-text` | `--sidebar-menu-text` | `grey/5` | 侧栏默认文字 |
| `sidebar/menu-active-bg` | `--sidebar-menu-active-bg` | `brand/5` | 侧栏选中背景 |
| `sidebar/menu-active-text` | `--sidebar-menu-active-text` | `white` | 侧栏选中文字 |

## 7. Layer 2: Business Tokens

### Device / Service

| Figma Token | CSS Token | Light 引用 | 用途 |
|---|---|---|---|
| `device/online` | `--device-online` | `green/6` | 在线、正常 |
| `device/offline` | `--device-offline` | `blue-grey/4` | 离线、不可用、弱化设备 |
| `device/moving` | `--device-moving` | `green/6` | 行驶、运动 |
| `device/stopped` | `--device-stopped` | `brand/6` | 静止、停车 |
| `device/idle` | `--device-idle` | `yellow/5` | 怠速、未定位、提醒状态 |
| `service/expiring` | `--service-expiring` | `yellow/5` | 即将到期 |
| `service/expired` | `--service-expired` | `red/5` | 已过期 |

### Alarm / Command / Video

| Figma Token | CSS Token | Light 引用 | 用途 |
|---|---|---|---|
| `alarm/info` | `--alarm-info` | `brand/6` | 普通提示、信息类告警 |
| `alarm/warning` | `--alarm-warning` | `yellow/5` | 提醒、注意、临界状态 |
| `alarm/critical` | `--alarm-critical` | `red/5` | 超速、断油电、严重告警 |
| `command/success` | `--command-success` | `green/6` | 指令成功、保存成功 |
| `command/failed` | `--command-failed` | `red/5` | 指令失败、保存失败 |
| `video/bg` | `--video-bg` | `dark-blue/8` | 视频空画面、深色容器 |
| `video/control-bg` | `--video-control-bg` | `dark-blue/9` | 视频控制条、深色 hover |

## 8. 深浅主题入口

深浅主题不通过第一层色板切换，而是通过第二层 `02 Component Tokens` 的 mode 切换。

```text
01 Gradient Palette
  Base

02 Component Tokens
  Light
  Dark
```

当前 `Dark` mode 是预留入口，不代表最终暗色主题已经完成。后续做暗色主题时：

1. 不改第一层 `01 Gradient Palette`
2. 只调整 `02 Component Tokens` 中 `Dark` mode 的引用关系
3. 页面和组件继续绑定同一个第二层变量名
4. 切换 mode 后，组件自动变化

示例：

| Token | Light | Dark |
|---|---|---|
| `bg/page` | `blue-grey/1` | `dark-blue/8` |
| `bg/surface` | `white` | `dark-blue/7` |
| `text/primary` | `blue-grey/7` | `blue-grey/2` |
| `border/default` | `blue-grey/2` | `dark-blue/5` |

## 9. CSS 草案

```scss
:root {
  /* text */
  --text-primary: var(--blue-grey-7);
  --text-secondary: var(--blue-grey-6);
  --text-tertiary: var(--blue-grey-5);
  --text-disabled: var(--blue-grey-4);
  --text-inverse: var(--white);

  /* background and border */
  --bg-page: var(--blue-grey-1);
  --bg-surface: var(--white);
  --border-default: var(--blue-grey-2);

  /* button */
  --button-primary-bg: var(--brand-6);
  --button-primary-hover-bg: var(--brand-5);
  --button-primary-active-bg: var(--brand-7);
  --button-default-bg: var(--white);
  --button-default-border: var(--grey-4);
  --button-default-hover-bg: var(--brand-2);
  --button-danger-bg: var(--red-5);

  /* input */
  --input-bg: var(--white);
  --input-border: var(--blue-grey-2);
  --input-border-hover: var(--brand-4);
  --input-border-focus: var(--brand-6);
  --input-border-error: var(--red-5);

  /* table and tabs */
  --table-header-bg: var(--blue-grey-1);
  --table-border: var(--blue-grey-2);
  --table-row-bg: var(--white);
  --table-row-hover-bg: var(--brand-1);
  --tab-text-active: var(--brand-6);
  --tab-line-active: var(--brand-6);

  /* business */
  --device-online: var(--green-6);
  --device-offline: var(--blue-grey-4);
  --device-moving: var(--green-6);
  --device-stopped: var(--brand-6);
  --device-idle: var(--yellow-5);
  --service-expiring: var(--yellow-5);
  --service-expired: var(--red-5);
  --alarm-critical: var(--red-5);
  --video-bg: var(--dark-blue-8);
}
```

## 10. 维护规则

1. 新增颜色前，先判断是否已有基础色阶可覆盖。
2. 页面设计优先使用第二层 token，不直接使用第一层色阶。
3. `Color` 旧 collection 暂时只做兼容，不继续新增。
4. 如果一个颜色是具体组件状态，放到 `02 Component Tokens`。
5. 如果一个颜色是设备、服务、告警、命令、视频等业务状态，也放到 `02 Component Tokens`。
6. 深色主题只改第二层 `Dark` mode，不改第一层基础色板。
7. 旧页面迁移优先级：公共组件 > 高频模板页 > 业务核心页面 > 历史零散页面。
