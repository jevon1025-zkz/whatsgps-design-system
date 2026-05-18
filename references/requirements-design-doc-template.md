# Requirement Design Draft Template

Use this template when asked to write a requirement design draft for WhatsGPS/Justrack UI.

## Output Structure

```markdown
# [Feature Name] 需求设计稿

## 1. 背景与目标
- 业务背景：
- 目标用户：
- 目标页面/入口：
- 本次要解决的问题：

## 2. 适用范围
- 涉及角色：
- 涉及设备/客户/服务对象：
- 涉及路由或页面：
- 不包含范围：

## 3. 信息架构
- 页面结构：
- 主要区域：
- 字段清单：
- 表格列：
- 操作入口：

## 4. 交互流程
- 默认进入状态：
- 查询/筛选流程：
- 新增/编辑/提交流程：
- 批量操作流程：
- 弹窗/抽屉/工作台流程：

## 5. 状态与规则
- 加载：
- 空数据：
- 禁用：
- 校验错误：
- 成功/失败反馈：
- 权限或不可操作状态：

## 6. 视觉与组件规范
- 页面模式：
- 使用组件：
- 关键 token：
- 表格/表单密度：
- 与现有页面保持一致的点：

## 7. 异常与边界
- 长文本：
- 大数据量：
- 离线/过期/未激活设备：
- 网络失败：
- 权限不足：

## 8. 验收标准
- 功能验收：
- 视觉验收：
- 状态验收：
- 数据验收：
```

## Writing Rules

- Always identify whether the feature is device-centered, customer-centered, map-centered, video-centered, finance/service-centered, or organization-centered.
- For hardware device features, list the relevant identifiers explicitly: IMEI, SIM, ICCID, model, status, service version, expiry, customer.
- For pages related to `/device/index`, mention the device detail workbench when the flow needs deep device editing or configuration.
- For list pages, specify toolbar, table columns, operation column, pagination, selected count, and empty state.
- For form-heavy pages, specify label alignment, required markers, validation timing, disabled/read-only behavior, and footer actions.
- Do not write vague visual copy such as "make it beautiful"; map each visual requirement to tokens or page patterns.
