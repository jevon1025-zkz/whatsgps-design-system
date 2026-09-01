# Version 3.0 Manifest

## 2.0 Baseline Retained

- Two-layer color-token governance and CSS output.
- Global field-copy and i18n guidance.
- Product domain model, route inventory, component/page patterns, workflows, review checklist, and quality gates.
- Device-detail workbench as a primary hardware-operation surface.
- Vue/Element UI implementation context.

## 3.0 Material Added Or Revised

| Area | 3.0 source | Result |
|---|---|---|
| PC navigation | Final navigation Figma and navigation PRD | Navigation grouping, top-bar concentration, message center, track-playback changes, and unchanged-logic boundaries. |
| Global search | Final Figma page and prior product discussion | Quick search to full-result workspace, entity/field model, ranking, permissions, states, and backend/query implications. |
| Reminder copy | APP.xlsx, sheets 报警信息 and 站内信息 | Complete raw source rows, role variants, bilingual copy, and PC/mobile consistency rule. |
| Function inventory | LBS function-menu workbook | PC menu hierarchy and role/permission-column interpretation. |
| Device icons | Device-detail/icon Figma, PRD, prior icon workflow and feedback | 30-icon inventory, eight additions, status/display rules, creation principles, small-size QA, customer-feedback lessons, and a Figma-only final-asset gate. |
| Device detail | Device PRD and final Figma | Summary/quick actions, tab overflow, icon flow, and vertical PC form direction. |
| Personas | Prior user research discussion | Only three role distinctions retained; no APP IA or feature plan. |
| PC system framework | Consolidated 3.0 scope | Experience shell, domain/permission, interaction/component, design-system, retained stack, and explicit non-goals. |

## Explicit Exclusions

- APP functions and APP page design.
- APP total information architecture or information-architecture rewrite notes.
- The 68-alarm taxonomy and full mapping.
- Unapproved mobile workflows inferred from PC behavior.

## Source Notes And Resolved Decisions

- Navigation Figma: https://www.figma.com/design/22NZxadyfNoSAvFTBmAaLu/导航优化?node-id=0-1. It contains pages for phase-one navigation and phase-two global search, but its Variables panel reports No variables created in this file.
- Device-detail Figma: https://www.figma.com/design/txoCSedmKc5MTzYF2wJSlD/设备详情?node-id=74-843. The confirmed node is 图标更新; the file also contains 设备详情优化, 图标替换/pc, and 传感器二期优化 sections.
- Final device-icon source: Figma section `图标替换/pc` is node `48:8443`. Verified instance `929:866` is `离线状态 / 摩托车 / 42 x 42px`.
- The former 150 local PNG files have been withdrawn from the formal-delivery definition. Version 3.0 is a specification-only Skill package and intentionally contains no complete device-icon PNG library.
- [device-icon-asset-manifest.md](device-icon-asset-manifest.md) preserves the Figma source rule and provides a provenance template for future asset-export tasks; it is not a missing-asset checklist for this Skill release.
- Final direction-frame decision: Figma annotation is authoritative. Export no-shadow SVG/PNG on a transparent 64 x 64px canvas, keep the visible frame at 42 x 54px, and align the circular-base center to 32,32.
- Bundled final direction-frame handoff: [direction-marker-no-shadow-handoff-20260706-173945.zip](../assets/direction-marker-no-shadow-handoff-20260706-173945.zip).
- Alarm/reminder source includes inconsistent placeholders and suspected wording errors. Preserve them as source text and raise them for product confirmation rather than silently correcting them.
