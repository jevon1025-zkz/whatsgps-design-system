# Global Search Pattern

## Product Model

Use progressive disclosure:

1. Top-bar quick search for fast, high-confidence retrieval.
2. 查看全部结果 opens the full-screen search workspace.
3. The workspace supports category-specific filtering, browsing, comparison, and return to the originating context.

Do not wait for an empty result before exposing 查看全部结果. Prefer 查看全部结果 over the user-facing label 高级搜索.

## Search Objects And Fields

Primary result objects:

- 设备
- 客户
- 账号, only when it is a separately permissioned entity
- 功能

IMEI, device name, plate number, SIM/card number, ICCID, device remark, account name, aliases, and historical function names are matching fields, not peer object categories. Return one entity once and explain the matched field.

Example device result:

    京A·12345  在线
    IMEI: 8680...7890  所属客户: XX物流
    匹配字段: 设备备注“老板用车”

## Quick Search

- Placeholder: 搜索设备、客户、账号或功能. Do not enumerate every field in it.
- Group a small number of high-relevance results by object.
- Keep 查看全部结果 visible when a query has searchable meaning.
- Chinese names may request after two characters; pure numeric identifiers normally request after four digits; a complete pasted identifier searches immediately.
- Support keyboard navigation, Enter to open the selected result, and Escape to close while restoring focus.

## Full-Screen Workspace

- Categories: 全部 / 设备 / 客户 / 账号 / 功能, omitting unavailable objects.
- Device filters may include matched field, state, owner/customer, and group.
- Customer filters may include name/account and customer level where permissions allow.
- Function filters may include module and formal/historical name.
- Returning to the source page preserves query, filters, selection, and scroll position.
- Results use dense rows/lists, not an app-icon grid.

## Ranking And Deduplication

Default precedence:

1. Exact stable identifier match.
2. Exact name/account match.
3. Prefix match.
4. Name fuzzy match.
5. Remark/content fuzzy match.

Lower the weight of noisy remarks. Deduplicate by canonical entity ID across matched fields, retain the strongest score, and expose the relevant match reason/snippet.

## Permission And Data Logic

Permission filtering is part of retrieval, not a UI cleanup step:

- Apply tenant, role, organization/customer tree, and feature permission before result count, grouping, highlighting, or suggestions.
- Do not reveal that a hidden device, customer, account, or feature exists.
- Route every selected result through the destination's existing permission and availability guard.
- Search history and analytics must not retain unauthorized result labels.

Recommended query architecture:

- Normalize each searchable object into a common result contract: entity type, canonical ID, title, subtitle, status, matched field, snippet, destination, rank, and permission scope.
- Use object-specific adapters/indexes behind one search orchestration layer.
- Normalize identifiers for spaces, case, separators, IMEI/card formatting, and localized aliases without changing displayed source values.
- Keep feature aliases and historical names mapped to the current destination.
- Support request cancellation and stale-response rejection as the query changes.
- Return per-source status so partial failure does not erase successful categories.
- Log latency, zero-result rate, selected rank, matched field, category/filter use, and destination success without unnecessarily logging sensitive raw queries.

## States

- Default/recent search, only when permitted.
- Focused but empty.
- Loading and incremental results.
- Result groups and total-result entry.
- No result.
- No result within current permissions.
- Partial source failure with other results still usable.
- Full failure and retry.
- Destination unavailable, deleted, expired, or permission changed since retrieval.

## First-Version Boundary

Do not require AI search. Exact lookup, normalized prefix matching, controlled fuzzy matching, function aliases, permission filtering, and useful match explanations are the baseline.

