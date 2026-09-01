# PC Navigation Guidelines

## Sources And Boundary

- Final design: https://www.figma.com/design/22NZxadyfNoSAvFTBmAaLu/导航优化?node-id=174-17739
- PRD: [navigation-prd.md](../assets/source-materials/navigation-prd.md)
- Full PC inventory: [lbs-function-menu.xlsx](../assets/source-materials/lbs-function-menu.xlsx)

This release changes grouping, placement, visual states, and specified copy. It does not change existing permissions, data relationships, API contracts, destination pages, or internal page functions. Anything not shown or adjusted in Figma keeps existing behavior.

## Sidebar

- Regroup and order primary/secondary entries according to final Figma.
- Expanded: brand, menu icons, names, secondary hierarchy, and disclosure arrows.
- Collapsed: brand icon and primary icons only; labels remain available through accessible tooltip behavior.
- Implement default, hover, active, expanded, and secondary-active states from Figma.
- Keep route and permission checks attached to the same business capabilities after regrouping.
- Use lbs-menu-inventory.md to check whether an entry exists and which roles may see it; visual presence in a design frame does not grant permission.

## Top Bar

- Left: sidebar toggle and current page title.
- Global actions: user feedback, search, language, messages, and account.
- Account: avatar, account name, disclosure, and approved product/push/password/logout entries.
- Keep existing language-switch, account-action, feedback, and destination logic unless a requirement explicitly changes it.
- Search follows global-search-pattern.md.

## Messages

### Unread Popover

- Triggered from the top message icon.
- Contains title 未读消息, a 更多 entry, and unread items with title, date, and summary.
- 更多 enters the existing message center.

### Message Center

- Categories: 报警信息, 站内信息, 系统公告, 活动公告, each with unread-count treatment.
- Actions: 全部已读, 标记已读, 删除.
- Filters: date range and device-name search.
- Update list/table states and pagination styling according to Figma.
- 全部已读 affects only the current category.
- Reading, filtering, deleting, detail navigation, read-state persistence, and pagination keep existing business logic.
- Alarm and in-system wording follows system-reminder-copy.md.

## Track Playback

- Use the new sidebar/top-bar shell and final Figma layout for query, map, playback controls, and lower data area.
- Date input displays a date only, without hour/minute/second.
- Merge old 详情 and 速度 entries into 轨迹数据.
- 轨迹数据 opens the existing lower panel and retains its four tabs: 详情, 速度, 行程, 任务列表.
- Device selection, trajectory query, map rendering, playback, and lower-panel content remain unchanged unless explicitly specified.

## Navigation Tokens

The navigation Figma has no local Variables. Use the global token guide:

| Component token | Palette alias | Value |
|---|---|---|
| sidebar/bg-start | dark-blue/6 | #1C2758 |
| sidebar/bg-end | dark-blue/7 | #111835 |
| sidebar/menu-bg | grey/9 | #202020 |
| sidebar/submenu-bg | grey/8 | #333333 |
| sidebar/menu-text | grey/5 | #A2A2A2 |
| sidebar/menu-active-bg | brand/5 | #3370FF |
| sidebar/menu-active-text | white | #FFFFFF |

These are project-token mappings, not Variables extracted from the navigation file.

## Acceptance

- Grouping, order, spacing, icons, text, active/hover/expanded states, and top-bar placement match final Figma.
- Every route remains permission-correct after regrouping.
- No hidden feature becomes visible through search, collapsed navigation, counts, or message previews.
- 全部已读 is category-scoped.
- Track-playback date and 轨迹数据 behavior match the PRD.
- Unshown pages and underlying business behavior remain unchanged.
