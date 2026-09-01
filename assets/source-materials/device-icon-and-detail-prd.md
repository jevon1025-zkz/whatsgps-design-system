# 设备图标重构与设备详情优化产品需求文档

版本号：V1.0.2

| **版本** | **时间** | **修订人** | **备注** |
| --- | --- | --- | --- |
| V1.0.0 | 2026/06/30 | 周靖雯 | 创建 PRD |
| v1.0.1 | 2026/07/03 | 周靖雯 | 修改方向框规则、新增方向框测试注意事项；<br>修改验收标准中的地图位置的方向框规则； |
| v1.0.2 | 2026/07/06 | 周靖雯 | 修改方向框规则、新增方向框测试注意事项；<br>修改验收标准中的地图位置的方向框规则； |
| v1.0.3 | 2026/07/15 | 周靖雯 | 新增 断油电 图标不在地图中展示；<br>断油电 在地图中展示为灰色（离线状态）； |

## 一、概述

### 1.1 背景介绍

设备图标是定位监控、设备详情、轨迹回放、设备选择等场景中的核心识别元素。当前需要对设备图标体系进行重构，统一图标视觉、地图展示规则和设备详情信息层级，降低用户在地图上识别设备类型、设备方向、设备状态时的认知成本。

本次改版以设计稿《设备图标》和最终图标规则表为准，覆盖 30 个默认图标，并补充自定义图标上传、裁剪、回显和地图展示规则。

设计稿链接：[https://www.figma.com/design/txoCSedmKc5MTzYF2wJSlD/%E8%AE%BE%E5%A4%87%E5%9B%BE%E6%A0%87?node-id=0-1&t=sTWIRd0vL2bWQu5Z-1](https://www.figma.com/design/txoCSedmKc5MTzYF2wJSlD/%E8%AE%BE%E5%A4%87%E5%9B%BE%E6%A0%87?node-id=0-1&t=sTWIRd0vL2bWQu5Z-1)

### 1.2 产品目标

| **目标类型** | **目标** | **验收方式** |
| --- | --- | --- |
| 图标体系 | 默认图标库整理为 30 个图标，新增 8 个图标 | 图标清单、设计稿、开发枚举一致 |
| 地图展示 | 地图展示规则统一为两类：直接展示、使用方向框 | 每个图标都有唯一展示规则 |
| 状态表达 | 统一静止、行驶、怠速/未定位、离线/断油电、超速 5 类状态 | 状态色、图标、方向框展示一致 |
| 设备详情 | 优化设备详情页整体信息层级 | 核心设备信息优先展示，操作入口清晰 |
| 交互流程 | 完成默认图标选择、自定义上传、裁剪、预览、回显、保存流程 | 正常、异常、取消、删除状态闭环 |

### 1.3 目标用户

| **角色** | **使用场景** | **核心诉求** |
| --- | --- | --- |
| 平台管理员 | 配置、查看、维护设备信息 | 快速识别设备类型和状态 |
| 经销商/客户管理员 | 管理客户设备、查看定位 | 在地图和详情页中快速判断设备情况 |
| 客服/运营人员 | 排查设备问题、协助客户操作 | 通过 IMEI、设备名、状态和图标快速定位对象 |
| 普通客户 | 查看自己的设备位置和状态 | 图标含义直观，地图方向清楚 |

### 1.4 名词说明

| **名词** | **说明** |
| --- | --- |
| 默认图标库 | 系统内置的 30 个设备图标 |
| 自定义图标 | 用户上传并裁剪后的设备图标，不计入默认图标库数量 |
| 直接展示 | 地图上直接展示图标本体，图标随设备方向或业务状态展示 |
| 方向框 | 地图上承载图标并表达方向的外层容器 |

## 二、产品范围

### 2.1 本期范围

| **模块** | **范围** | 涉及终端 |
| --- | --- | --- |
| 默认图标库 | 30 个默认图标的名称、排序、展示规则、状态适配 | web、app |
| 图标优化 | 小轿车、出租车、警车、小货车、大货车、公交、搅拌车、农机、装载车、火车、挖掘机、船、摩托车、标记、自行车、滑板车、电动车、猫咪、狗狗、牲畜、宠物、人物 | web、app |
| 新增图标 | 越野车、微型车、皮卡、牵引车、卡车、挂车、集装箱、拖拉机 | web、app |
| 地图展示 | 直接展示、使用方向框两套规则 | web、app |
| 状态展示 | 静止、行驶、怠速/未定位、离线/断油电、超速 | web、app |
| 标记图标 | 优化标记图标在地图中的展示效果 | web、app |
| 方向框 | 优化方向框视觉、尺寸、锚点、状态适配 | web、app |
| 设备详情页 | 优化所有信息层级，包括摘要、详情字段、图标字段、操作入口 | web |
| 切换图标交互 | 默认图标选择、自定义上传、裁剪、查看、删除、回显、保存 | web |
| 传感器二期优化 | 侧边栏多语言适配<br>带框单选多语言适配 | web |

## 三、默认图标清单

默认图标库共 30 个图标。自定义图标作为上传能力单独定义，不计入默认图标库数量。

[请至钉钉文档查看附件《设备图标优化》。](https://alidocs.dingtalk.com/i/nodes/R1zknDm0WRkmaMO3U0ylQzzgVBQEx5rG?iframeQuery=anchorId%3DX02mr1r7yaq4dxearptzo4)

[请至钉钉文档查看附件《B端需求翻译》。](https://alidocs.dingtalk.com/i/nodes/R1zknDm0WRkmaMO3U0ylQzzgVBQEx5rG?iframeQuery=anchorId%3DX02mr1x0gc9gb3awyp7l2f)

| **序号** | **图标名称** | 图列 | **地图展示规则** | **优化类型** |
| --- | --- | --- | --- | --- |
| 1 | 小轿车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/841020e4-946b-4a17-9dd0-5d09748ca10d.png) | 直接展示 | 保留优化 |
| 2 | 出租车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/ebc453fc-069f-49cd-a2ea-541d4cea801e.png) | 直接展示 | 保留优化 |
| 3 | 警车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/3df7287a-d663-42b9-86f0-78434419d472.png) | 直接展示 | 保留优化 |
| 4 | 越野车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/fafdfc01-de06-4831-9fa5-e0d8d24a86e5.png) | 直接展示 | 新增图标 |
| 5 | 微型车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/4850e653-eb81-49b8-b21b-1d318d863fdf.png) | 直接展示 | 新增图标 |
| 6 | 皮卡 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/444d1d9b-ce8f-4e73-a0ab-0962dcb904e1.png) | 直接展示 | 新增图标 |
| 7 | 小货车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/91f62312-c541-42f1-8e76-6c2c91d4175f.png) | 直接展示 | 保留优化 |
| 8 | 大货车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/be0286e3-68a7-4c93-a0db-eca3a395485e.png) | 直接展示 | 保留优化 |
| 9 | 牵引车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/ae4b2e24-d68a-412c-a81d-439d051002be.png) | 直接展示 | 新增图标 |
| 10 | 公交 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/16c74871-ab83-40a1-92c1-e07927a072e6.png) | 直接展示 | 保留优化 |
| 11 | 搅拌车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/d75554cc-3b25-4004-9a8b-0e5b9d06058c.png) | 直接展示 | 保留优化 |
| 12 | 卡车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/90b43433-101d-4afe-9a77-5899ce7d017c.png) | 直接展示 | 新增图标 |
| 13 | 农机 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/31e24e42-7720-4448-8a1c-94b84da5bac2.png) | 直接展示 | 保留优化 |
| 14 | 装载车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/1164e6f9-7f6a-4954-b475-1dd79e0330d4.png) | 直接展示 | 保留优化 |
| 15 | 挂车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/b6d6db99-9bf3-4342-8c09-493e271ef9ed.png) | 直接展示 | 新增图标 |
| 16 | 集装箱 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/65e61a83-0479-4528-a504-7031aaa8dc02.png) | 直接展示 | 新增图标 |
| 17 | 火车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/f4e40601-998b-4dc5-b82d-ff95e63fd110.png) | 直接展示 | 保留优化 |
| 18 | 挖掘机 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/b94c866d-f9de-4481-ba89-620a447e81e7.png) | 直接展示 | 保留优化 |
| 19 | 拖拉机 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/a1197af5-da72-4596-8e52-9a8ec24d5c16.png) | 直接展示 | 新增图标 |
| 20 | 船 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/7792e64f-2d38-4d20-9303-5d6b47f09828.png) | 直接展示 | 保留优化 |
| 21 | 摩托车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/316a498f-c7a4-412a-955b-7df2cde5f4f3.png) | 直接展示 | 保留优化 |
| 22 | 标记 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/f4084251-c3b9-4cb6-9524-b31ca3a7bdcf.png) | 直接展示 | 地图展示优化项 |
| 23 | 自行车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/43377748-4710-41be-89e1-bd730434a006.png) | 使用方向框 | 地图展示优化项 |
| 24 | 滑板车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/29c84086-1f79-4317-8f83-cab93b7417c5.png) | 使用方向框 | 地图展示优化项 |
| 25 | 电动车 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/84e6bb66-d38d-4c62-b50f-37a9f3e1b5e3.png) | 使用方向框 | 地图展示优化项 |
| 26 | 猫咪 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/664909ff-a510-4651-a9ef-e0bd36331096.png) | 使用方向框 | 地图展示优化项 |
| 27 | 狗狗 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/b7fc1567-b466-42b5-a5aa-b6bf6938d600.png) | 使用方向框 | 地图展示优化项 |
| 28 | 牲畜 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/e05faf12-a7e1-4300-981d-bda93dcc6f7f.png) | 使用方向框 | 地图展示优化项 |
| 29 | 宠物 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/925d99e5-55ed-4856-84a4-5f28be2e15ea.png) | 使用方向框 | 地图展示优化项 |
| 30 | 人物 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/9fc53a56-689b-4c18-9bd2-a0fac50d29f8.png) | 使用方向框 | 地图展示优化项 |

### 3.1 自定义图标规则

| **项** | **规则** |
| --- | --- |
| 数量口径 | 不计入 30 个默认图标 |
| 入口 | 选择图标弹窗中的自定义图标区域 |
| 地图展示 | 使用方向框 |
| 上传后状态 | 回显到自定义图标区域，并自动选中 |
| 操作 | 支持查看、删除、重新上传（与系统现有逻辑保持一致） |

## 四、地图展示规则

### 4.1 规则总览

地图展示规则只保留两类：

| **规则** | **说明** | **适用图标** |
| --- | --- | --- |
| 直接展示 | 地图中直接展示图标本体，图标本体承担类型识别 | 小轿车、出租车、警车、越野车、微型车、皮卡、小货车、大货车、牵引车、公交、搅拌车、卡车、农机、装载车、挂车、集装箱、火车、挖掘机、拖拉机、船、摩托车、标记 |
| 使用方向框 | 图标放入方向框，方向由方向框表达，图标承担类型识别 | 自行车、滑板车、电动车、猫咪、狗狗、牲畜、宠物、人物、自定义图标 |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/ecf85b6a-34e5-479d-8d31-69622a5c5be0.png)

### 4.2 地图状态矩阵

| **状态** | **状态含义** | **建议业务 Token** | **展示要求** | 图例 |
| --- | --- | --- | --- | --- |
| 静止 | 设备停车或无移动 | `device/stopped` | 蓝色系，视觉权重低于告警态 | ![static.svg](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/0aa79eb9-56e6-4b5e-b8a2-1ef70ceb3fb6.svg) |
| 行驶 | 设备正在移动 | `device/moving` | 绿色系，图标或方向框保持清晰方向 | ![moving.svg](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/f9479bc0-8abd-4ba4-a55f-7b21ff991257.svg) |
| 怠速/未定位 | 设备怠速或定位不可用 | `device/idle` | 黄色系，提示但不压过严重告警 | ![idle-unlocated.svg](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/7ab10571-e57d-40fc-8bc0-94d336464cca.svg) |
| 离线/断油电 | 设备离线或不可用 | `device/offline` | 灰色系，降低视觉权重 | ![offline.svg](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/9863f91c-b9aa-4525-b0b6-30e3dc0a19b4.svg) |
| 超速 | 严重告警或高风险状态 | `alarm/critical` | 红色系，保持最高提醒权重 | ![poweroff-overspeed.svg](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/37736e0d-6529-42de-98b4-1b3a3a50f38c.svg) |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/227a5afe-3e9a-4e94-91de-8afd16b1f199.png)

### 4.3 直接展示规则

| **项** | **规则** |
| --- | --- |
| 图标尺寸 | 默认展示尺寸为：42\*42px；<br>需保证小尺寸可识别； |
| 方向表达 | 有方向属性的图标按设备方向旋转或展示对应方向 |
| 状态表达 | 图标主体或承载底色按 5 类状态切换 |
| 锚点 | 锚点应落在图标视觉中心或业务定位点，避免缩放时偏移（以现有逻辑为准） |
| 叠加 | 多设备聚合、选中、hover、告警叠加时不遮挡图标主体（以现有逻辑为准） |

### 4.4 方向框规则

| 项 | 规则 |
| --- | --- |
| 导出画布 | 使用 64px \* 64px 的透明正方形画布导出 |
| 可视方向框 | 方向框可视区域为 42px \* 54px |
| 旋转锚点 | 取圆形底座圆心，不取外接框几何中心 |
| 锚点位置 | 圆形底座圆心需对齐 64px \* 64px 画布中心点 32,32 |
| 图标位置 | 图标在方向框内居中展示，整体随圆形底座圆心对齐画布中心 |
| 展示方式 | 地图中使用完整 64px \* 64px 画布展示，方向框在画布内表达方向 |
| 适用范围 | 自行车、滑板车、电动车、猫咪、狗狗、牲畜、宠物、人物、自定义图标 |
| 状态表达 | 按静止、行驶、怠速/未定位、离线/断油电、超速 5 类状态展示 |

方向框状态图标只允许修改颜色和状态样式，不允许改变圆形底座圆心、方向框位置、64px \* 64px 导出画布尺寸。

### 4.5 测试注意事项

| 测试项 | 要求 |
| --- | --- |
| 跨端一致 | Web 端与 App 端（Android、iOS）的设备图标需保持一致 |
| 地图展示规则 | 地图展示时只存在两种规则：直接展示、使用方向框 |
| 车辆顶部视角 | 车辆顶部视角图标尺寸为 42px |
| 方向框画布 | 带方向框展示时，导出画布为 64px \* 64px，且不得裁剪透明区域和阴影 |
| 方向框可视尺寸 | 方向框可视区域为 42px \* 54px |
| 方向框旋转中心 | 圆形底座圆心需对齐画布中心 32,32；地图旋转时以完整 64px \* 64px 画布中心旋转 |
| 方向框状态一致 | 静止、行驶、怠速/未定位、离线/断油电、超速 5 类状态的圆形底座圆心需保持同一位置 |

## 五、设备详情基础信息交互优化

### 5.1 设备信息摘要结构

设备详情页顶部使用设备信息摘要承载图标、设备身份信息和快捷操作。摘要区在 5 类设备状态下保持同一结构，只切换图标状态。

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/a313c88f-93f0-4918-821e-9f10b1d37874.png)

| **区域** | **内容** | **设计规则** | 设计稿 |
| --- | --- | --- | --- |
| 图标区 | 当前设备图标，根据当前设备状态展示 | 图标位于 80px \* 80px 容器内，图标尺寸 56px \* 56px<br>鼠标悬浮支持 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/516db061-0cf2-4456-a035-9b475cf70c42.png) |
| 主标题 | 设备名称 | 默认展示设备名称，最多可展示50个字段，超过则【...】展示，鼠标悬浮展示更多；<br>不展示【设备名称】字段，仅展示：R16L-C（若用户修改字段，则按照用户修改后的字段展示） |  |
| 元信息 | 车牌号码、设备型号、IMEI、复制入口 | 车牌号码：默认展示车牌号码，不展示【车牌号码】字段，仅展示：【粤T160XC】<br>设备型号：默认展示设备型号，不展示【设备信号】，仅展示：R16L-C<br>IMEI+复制：默认展示IMEI，支持复制，不展示【IMEI】，仅展示：868773200197567<br>鼠标悬浮展示对应的字段名称 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/590bd2ad-ee73-42b3-8efe-7083dfcb172b.png) |
| 快捷操作 | 监控、追踪、回放、实时视频、视频回放 | 操作入口位于元信息下方，使用图标 + 文案<br>单行展示不下时，掉到下一行展示 | ![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/dd091ff7-a1c5-4c65-8386-e3609764c385.png)<br>![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/7e589b71-5f3c-471a-ae09-3b2d80ca73e3.png) |

### 5.2 图标与设备详情的关系

| 场景 | 规则 |
| --- | --- |
| 设备摘要展示 | 摘要区展示当前设备图标，并随设备状态切换 |
| 选择默认图标 | 保存后设备摘要区同步展示选中的默认图标 |
| 上传自定义图标 | 保存后设备摘要区同步展示自定义图标 |
| 状态变化 | 设备状态变化时，摘要区图标展示切换到对应状态 |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/03ecb3b9-871a-4f4b-afe4-5a9fd228693b.png)

### 5.3 字段悬浮与复制反馈

| 场景 | 规则 | 展示文案 |
| --- | --- | --- |
| 元信息字段悬浮 | 鼠标悬浮时，展示对应字段所属 | 车牌号码、设备型号、IMEI |
| IMEI 复制成功 | 点击 IMEI 复制后展示成功反馈 | IMEI号复制成功 |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/b39046be-b5a3-4b10-9c70-e8591ba58e32.png)

### 5.4 设备功能统一

整合之前在设备信息中的监控、追踪、回放、实时视频、视频回放功能，层级前移；同时采用 icon + 文字的展示方式，让用户快速获取。

| 设备类型 | 展示功能 | 规则 |
| --- | --- | --- |
| 视频设备 | 监控、追踪、回放、实时视频、视频回放 | 与原逻辑保持一致 |
| 非视频设备 | 监控、追踪、回放 | 与原逻辑保持一致 |

| 状态 | 触发条件 | 展示 |
| --- | --- | --- |
| 默认 | 未悬停、未选中 | icon + 文字常规展示 |
| Hover | 鼠标悬停功能入口 | 展示 hover 态 |
| 选中 | 当前功能被选中 | 展示选中态 |
| 禁用 | 当前功能不可用 | 展示禁用态 |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/9e61a956-d27d-4fa9-85e9-c4ac1b2559b0.png)

### 5.5 Tab 交互样式调整

默认展示 12 个 tab 选项。

| 场景 | 规则 |
| --- | --- |
| 默认 | 展示 12 个 tab 选项 |
| 超过 12 个选项 | 【···】按钮在整个 tab 栏最右侧展示 |
| 浏览器宽度缩小 | 【···】按钮在整个 tab 栏最右侧展示 |
| 鼠标悬浮在蓝色区域 | 可通过鼠标滚轮进行左右滑动展示 |
| 点击右侧【···】 | 展开剩余的 tab，进行选择 |

| 状态 | 展示 |
| --- | --- |
| 默认 | 展示【···】入口 |
| Hover | 展开剩余 tab 下拉列表 |
| 选中 | 展示【···】选中态 |
| 禁用 | 展示【···】禁用态 |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/5501945d-0554-400d-a484-c4e5dbfaeb13.png)

#### 5.6.1 ICCID 字段与查看详情入口

| 场景/状态 | 触发条件 | 展示/结果 |
| --- | --- | --- |
| ICCID 为空 | 字段无值 | 输入框展示 placeholder：请输入；字段右侧保留查看详情 icon |
| ICCID 有值 | 字段有值 | 输入框展示 ICCID 值；字段后展示 SIM 卡状态 icon 和查看详情 icon |
| SIM 卡状态 icon | ICCID 有值且返回 SIM 卡状态 | icon 颜色按 SIM 卡状态颜色规则展示 |
| 默认态 | 未悬停、未选中 | 查看详情 icon 展示默认态 |
| Hover 态 | 鼠标悬停查看详情 icon | 展示 tooltip：查看详情 |
| 选中态 | 点击查看详情 icon 后 | 查看详情 icon 展示选中态，并展示 SIM 卡信息浮层 |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/f8e853d8-24b2-47cc-b177-14fdef4e1fb7.png)

#### 5.6.2 SIM卡信息浮层（样式优化）

| 信息位置 | 字段 | 展示规则 |
| --- | --- | --- |
| 顶部标题 | SIM卡状态 | 左侧展示字段名，右侧展示状态值 |
| 状态值 | 正常、空号、到期停机、超额停机、未开套餐、待复机 | 按 SIM卡状态字段色值对照展示 |
| 内容字段 | 到期时间 | 展示 SIM卡到期日期 |
| 内容字段 | 本月流量 | 展示已用流量/总流量 |
| 内容字段 | 本月短信 | 展示本月短信已用条数 |
| 内容字段 | 开关机 | 展示开关机状态 |
| 内容字段 | GPRS功能 | 展示 GPRS 功能状态 |
| 内容字段 | 卡号 | 展示 SIM卡号 |
| 内容字段 | ICCID | 展示 ICCID |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/e8765236-9f27-42be-bf8b-cfe6bca37eea.png)

SIM卡状态字段色值对照按设计稿执行，不在 PRD 中另行定义具体色值。

| SIM卡状态 | 颜色语义 |
| --- | --- |
| 正常 | 绿色 |
| 空号 | 红色 |
| 到期停机 | 红色 |
| 超额停机 | 红色 |
| 未开套餐 | 蓝灰色 |
| 待复机 | 黄色 |

#### 5.6.3 卫星模组号说明 icon

| 场景/状态 | 触发条件 | 展示/结果 |
| --- | --- | --- |
| 字段展示 | 卫星模组号无值 | 字段按设计稿展示 `-` |
| 默认态 | 未悬停 | 卫星模组号字段右侧展示说明 icon |
| Hover 态 | 鼠标悬停说明 icon | 展示 tooltip：卫星通信模组的唯一标识，设备上报数据自动识别，平台将使用此字段关联设备与卫星套餐（与原逻辑一致） |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/8acd7281-9693-4737-9f42-80dad5fb9dd5.png)

### 5.7 图片上传交互状态

图片上传交互细节调整，逻辑与原有逻辑保持一致。

| 状态/操作 | 触发条件 | 展示/结果 |
| --- | --- | --- |
| 默认 | 未上传、未悬停 | 展示上传占位 |
| Hover | 鼠标悬停上传占位 | 展示 hover 态 |
| 选中 | 上传占位被选中 | 展示选中态 |
| 上传后 | 图片上传完成 | 展示图片缩略图 |
| 悬浮 | 鼠标悬停已上传图片 | 显示查看、删除操作 |

| 项 | 规则 |
| --- | --- |
| 字段 | 图片 |
| 上传说明 | 文件支持 jpg/jpeg/png 格式，大小不超过 1MB |
| 查看 | 点击查看操作，按现有查看图片逻辑展示大图 |
| 删除 | 点击删除操作，删除已上传图片并恢复未上传状态 |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/ccc45dcf-4e85-408f-8b02-db6ecd9ccac1.png)

### 5.8 查看图片弹窗

| 项 | 规则 |
| --- | --- |
| 弹窗标题 | 查看图片 |
| 展示内容 | 大图预览 |
| 关闭方式 | 点击右上角关闭图标或底部【关闭】按钮 |
| 查看逻辑 | 与现有查看图片逻辑保持一致 |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/0ef59199-a421-4b7b-a0c0-7373fce35207.png)

## 六、图标选择与自定义上传流程

### 6.1 设备图标替换/预览入口

| 入口 | 触发方式 | 打开内容 |
| --- | --- | --- |
| 设备简要-图标 | 鼠标悬浮 | 预览/编辑 |

注： APP仅做图标替换和地图展示规则，其余保持现状

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/0ea87129-ae61-4af5-90a5-9c08d3ccc7de.png)

### 6.2 编辑图标弹窗

| 区域 | 内容 | 规则 |
| --- | --- | --- |
| 默认图标库 | 30 个默认图标 | 按表格排序展示 |
| 地图效果预览 | 当前选中图标在地图中的效果 | 选择变化后实时更新 |
| 自定义图标 | 上传入口或已上传图标 | 上传后自动选中 |
| 自定义图标说明 | 上传格式和大小限制 | 文件支持 jpg/jpeg/png 格式，大小不超过 1MB |
| 底部操作 | 取消、保存 | 保存后回到设备详情页 |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/52281d5b-251a-45e1-b087-054a38852521.png)

### 6.3 默认图标状态

| 状态 | 触发条件 | 展示 |
| --- | --- | --- |
| 默认 | 未悬停、未选中 | 常规图标 |
| Hover | 鼠标悬停 | 展示 hover 背景或边框，可出现图标名称气泡 |
| 点击 | 鼠标按下 | 展示按下态 |
| 选中 | 当前选中图标 | 使用主色边框或选中标识 |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/423e07d6-16f6-49ae-9a5b-10eda00955de.png)

### 6.4 自定义图标状态

| 状态 | 触发条件 | 展示 |
| --- | --- | --- |
| 默认/未上传 | 尚未上传 | 加号上传占位 + 文件格式说明 |
| Hover/未上传 | 鼠标悬停上传占位 | 上传占位高亮 |
| 点击/未上传 | 点击上传占位 | 打开系统文件选择 |
| 裁剪中 | 选择本地图片后 | 打开图标裁剪页面 |
| 上传后 | 裁剪确认后 | 回显缩略图，自动选中，右侧展示【替换】【删除】 |
| 已上传/选中 | 当前自定义图标已上传且被选中 | 缩略图展示选中描边，右侧展示【替换】【删除】 |
| 替换 | 点击【替换】 | 打开系统文件选择，并进入裁剪流程 |
| 删除后 | 点击【删除】 | 删除自定义图标，回到默认/未上传状态，与原有逻辑一致，选中默认图标第一个【小轿车】 |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/460483a3-884c-493a-b22b-87a9ba3e04f8.png)

### 6.5 自定义图标上传规则

| 项 | 规则 |
| --- | --- |
| 文件格式 | jpg、jpeg、png |
| 文件大小 | 大小不超过 1MB |
| 裁剪比例 | 圆形裁剪预览，输出用于地图方向框 |
| 裁剪页层级 | 在【选择图标】弹窗内下钻，不新增弹窗 |
| 裁剪页内容 | 图片裁剪区、右侧预览、缩放控制、取消、确定 |
| 保存方式 | 点击确定后回到【选择图标】弹窗 |
| 回显 | 将用户上传的图片带入自定义图标中回显，并自动选中当前用户上传的图标 |
| 取消 | 取消裁剪不改变原图标，返回【选择图标】弹窗 |
| 替换 | 点击替换后重新选择本地图片，并进入裁剪流程 |
| 删除 | 删除后恢复未上传状态 |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/bf223599-2e48-44ea-90aa-f2c4efe98b40.png)

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/5f14f51a-962a-47cc-ad6a-02db7f155ce2.png)

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/ba04c2cf-514a-4e19-85ca-4f7b432b3aa9.png)

### 6.6 文件限制

| 场景 | 触发条件 | 处理方式 | 提示文案 |
| --- | --- | --- | --- |
| 文件格式错误 | 上传非 jpg/jpeg/png | 阻止上传 | 仅支持 jpg、jpeg、png |
| 文件过大 | 文件大于 1MB | 阻止上传 | 图片需小于 1MB |

## 七、保存规则

| 场景 | 规则 |
| --- | --- |
| 选择默认图标 | 保存当前选择的默认图标 |
| 选择自定义图标 | 保存当前上传并裁剪确认的自定义图标 |
| 未点击保存关闭弹窗 | 不更新设备图标 |
| 保存成功 | 设备详情、地图预览、设备摘要同步更新 |

## 八、功能指引

此版本上线后，用户首次打开页面时，展示：

| 步骤 | 指引对象 | 标题 | 副文案 | 操作按钮 |
| --- | --- | --- | --- | --- |
| 1/3 | 设备图标 | 图标入口已调整 | 悬浮设备图标后，可切换默认图标或上传自定义图标 | 下一步 |
| 2/3 | 设备功能 | 常用操作已前置 | 监控、追踪、回放等功能现在可快速使用 | 下一步 |
| 3/3 | 更多标签页 | 标签浏览更灵活 | 滚动鼠标可左右浏览，点击【···】可展开更多标签页 | 知道了 |

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/52eea5b9-e8bb-4669-934a-420faf11fc96.png)

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/fae09a59-f538-46b9-85ee-d06892f21ab0.png)

![image.png](https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/ABmOoWbyMQ4W2Oaw/img/67c5ea5f-c734-4000-b65a-9ca49a1fe042.png)

## 九、验收标准

| 模块 | 验收条件 | 优先级 |
| --- | --- | --- |
| 默认图标库 | 展示 30 个默认图标，顺序与 PRD 清单一致 | P0 |
| 新增图标 | 8 个新增图标在图标库中可选择、可预览、可保存 | P0 |
| 地图规则 | 地图展示只存在直接展示、使用方向框两种规则；每个图标只命中其中一类 | P0 |
| 地图尺寸 | 车辆顶部视角图标尺寸为 42px；带方向框展示时导出画布为 100px \* 100px，方向框可视区域为 42px \* 54px | P0 |
| 跨端一致 | Web 端与 App 端（Android、iOS）的设备图标保持一致 | P0 |
| 方向框 | 使用方向框的图标在地图中方向清晰，图标居中 | P0 |
| 状态展示 | 5 类状态在地图、设备摘要、预览中一致 | P0 |
| 设备详情 | 5 类状态下摘要区结构一致，图标、设备名称、车牌号码、设备型号、IMEI、复制入口、快捷操作完整展示 | P0 |
| 设备功能统一 | 功能入口层级前移，采用 icon + 文字；视频设备展示监控、追踪、回放、实时视频、视频回放，非视频设备展示监控、追踪、回放 | P0 |
| 功能入口状态 | 监控等功能入口具备默认、hover、选中、禁用状态 | P0 |
| Tab 交互 | 默认展示 12 个 tab；超过 12 个或浏览器宽度缩小时，【···】固定在 tab 栏最右侧；点击后可选择剩余 tab | P0 |
| Tab 滚动 | 鼠标悬浮在蓝色区域时，可通过鼠标滚轮左右滑动展示 tab | P0 |
| ICCID 查看详情 | ICCID 为空时保留查看详情 icon；ICCID 有值时展示 SIM卡状态 icon 和查看详情 icon；查看详情 icon 具备默认、hover、选中状态；hover 展示“查看详情”；点击后展示 SIM卡信息浮层 | P0 |
| SIM卡信息浮层 | 浮层展示 SIM卡状态、到期时间、本月流量、本月短信、开关机、GPRS功能、卡号、ICCID；SIM卡状态 icon 与状态值按正常、空号、到期停机、超额停机、未开套餐、待复机对应颜色展示 | P0 |
| 卫星模组号说明 | 卫星模组号右侧说明 icon hover 时展示指定 tooltip 文案 | P0 |
| 图片字段状态 | 图片上传占位具备默认、hover、选中状态；上传后展示图片缩略图；悬浮已上传图片展示查看、删除操作 | P0 |
| 图片查看与删除 | 点击查看操作按现有查看图片逻辑展示大图；点击删除操作删除已上传图片并恢复未上传状态 | P0 |
| 查看图片弹窗 | 查看图片弹窗展示大图预览，可通过右上角关闭图标或底部【关闭】按钮关闭 | P0 |
| 图标入口 | 图标切换仅保留设备图标一个入口；设备详情字段中的图标切换入口移除 | P0 |
| 功能指引 | 功能指引集中在文档最后维护，包含“图标入口已调整”“常用操作已前置”“标签浏览更灵活”三条；每条均为标题 + 副文案 + 操作按钮 | P0 |
| 自定义上传 | 上传、替换、裁剪、确认、回显、自动选中、删除流程闭环 | P0 |
| 图标裁剪 | 裁剪页在【选择图标】弹窗内下钻展示，不新增弹窗；确定后回到上一层并自动选中上传图标 | P0 |
| 保存 | 保存成功后设备详情和地图展示同步更新 | P0 |
| 文件限制 | 文件格式错误、文件过大时阻止上传并提示 | P0 |
| 国际化 | 图标名称、按钮、提示文案进入多语言词条 | P1 |