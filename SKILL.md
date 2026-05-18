---
name: whatsgps-design-system
description: Use when designing, generating, implementing, reviewing, or documenting UI/UX for the WhatsGPS/Justrack/立即定位 PC hardware device management platform, especially Vue/Element UI pages, Figma restoration, design token output, interaction design, UI consistency checks, and requirement design drafts.
---

# WhatsGPS Design System

## Overview

Use this skill for the WhatsGPS/Justrack PC web platform. The product is a B-end hardware device operations system centered on devices, IMEI, SIM/ICCID, customer ownership, service expiry, location, video, commands, renewal, transfer, alarm settings, and maintenance.

Default implementation target: Vue 2 style SPA with Element UI conventions. Use the platform's existing visual language: dense operational layouts, deep-blue navigation, light blue-gray workspace background, white rounded surfaces, blue primary actions, and high-scannability tables/forms.

## Task Workflow

1. Classify the task:
   - **Design token output**: read `references/design-tokens.md` and `references/design-tokens.css`.
   - **Frontend page generation**: read `references/design-workflows.md`, `references/product-domain-model.md`, `references/component-patterns.md`, and the relevant page pattern in `references/page-patterns.md`.
   - **Route/page coverage**: read `references/route-inventory.md` when the task depends on a real product route, menu module, or page family not already shown in screenshots.
   - **PM/prototype handoff**: read `references/pm-requirement-handoff-guidelines.md` when the user needs a deliverable requirement/prototype guideline, product-manager checklist, or do/don't rules.
   - **UX/interaction design**: read `references/ux-interaction-guidelines.md` when improving user flows, prototype completeness, interaction states, accessibility, error prevention, or usability.
   - **UI/UX quality gate**: read `references/ui-ux-quality-gates.md` before final handoff, generated UI review, accessibility checks, responsive/layout checks, chart/report checks, or interaction-state QA.
   - **Device detail modal/workbench**: always read `references/device-detail-workspace.md`.
   - **UI review or consistency check**: read `references/review-checklist.md` and `references/product-domain-model.md`.
   - **Requirement design draft**: read `references/requirements-design-doc-template.md`.
   - **Figma restoration**: inspect the Figma node when available, then read `references/design-workflows.md` and map spacing, colors, typography, and components back to these references instead of inventing a new style.
   - **Figma Variables setup**: read `references/figma-variable-system.md` before producing JSON, tables, or import instructions.

2. Prefer source of truth in this order:
   - Current product page or Figma frame for the target feature.
   - `references/product-domain-model.md` for entity names, fields, statuses, and workflow semantics.
   - `references/route-inventory.md` for observed routes, page families, tabs, tables, and inaccessible routes.
   - `references/pm-requirement-handoff-guidelines.md` for PM-facing requirement completeness, do/don't rules, and sensor-demand checklists.
   - `references/ux-interaction-guidelines.md` for user flow, information architecture, feedback, error prevention, accessibility, and UX review.
   - `references/ui-ux-quality-gates.md` for adapted `ui-ux-pro-max` quality checks: accessibility, interaction, layout, tables, forms, charts, loading, and motion.
   - `references/design-tokens.md` for colors, typography, spacing, radius, shadow, and sizes.
   - `references/device-detail-workspace.md` for hardware device management workflows.
   - `references/component-patterns.md` for Element UI component composition and states.
   - `references/page-patterns.md` for dashboard, device list, map, video, and trip-image pages.
   - `references/review-checklist.md` for temporary anti-patterns and consistency review.

3. When generating UI:
   - Build the actual operational interface first, not a marketing or landing page.
   - Use Element UI mental models: `el-table`, `el-form`, `el-input`, `el-select`, `el-tabs`, `el-dialog`, `el-radio`, `el-checkbox`, `el-switch`, `el-pagination`.
   - Keep device/customer pages table-first and batch-operation friendly.
   - Preserve dense B-end scanning behavior; avoid oversized cards, hero sections, decorative gradients, or illustrative empty layouts unless the existing page pattern already uses them.
   - Use icons for tools and commands where possible; text-only buttons are acceptable for clear business actions such as 查询, 重置, 详情, 更多, 续费, 转移.
   - Preserve core identifiers and operational context before adding polish: device name, IMEI, SIM, ICCID, model, customer, status, service version, and expiry.

4. When reviewing UI:
   - Lead with concrete inconsistencies against tokens, layout density, table/form behavior, or device-management workflow needs.
   - Check interaction completeness before cosmetic polish: entry, default state, happy path, error path, save feedback, return path, and recovery.
   - Treat the device detail workbench as a primary product surface, not a generic modal.
   - Call out missing states for loading, empty, disabled, validation error, offline/expired device, and batch selection.

## Core Rules

- **Business identity**: This is a hardware device operations platform. IMEI, SIM, ICCID, device model, device status, service version, expiry dates, customer ownership, and last position are core data, not secondary metadata.
- **Visual identity**: Primary blue `#0068FF`; deep-blue sidebar; page background `#F4F7FE`; white rounded content surfaces; text primary `#1B2559`; muted text `#707EAE`; border `#E9EDF7`.
- **Density**: PC-first, 1920 and 1440 widths. Prefer tables, tree panels, toolbars, and two-column forms over low-density card grids.
- **Component shape**: Controls use 8px radius; major cards and workbench modals use 20px radius; table cells are compact and scan-friendly.
- **Device detail workbench**: Wide multi-tab dialog with fixed header tabs and footer actions. Its tabs include detail, service version, customer, tracking, commands, configuration, renewal, transfer, alarms, maintenance, scheduled tasks, reminders, and sensor labels. It must support dense forms and hardware-specific controls.

## Resources

- `references/design-tokens.md`: Figma-variable-ready tokens and naming guidance.
- `references/design-tokens.css`: CSS variable output for frontend/Cursor/Codex use.
- `references/figma-variable-system.md`: Figma variable import, collection structure, and style setup notes.
- `references/route-inventory.md`: Observed route map, page families, accessible pages, and unverified/404 routes.
- `references/pm-requirement-handoff-guidelines.md`: PM-facing current-version requirement/prototype handoff rules, including sensor-demand requirements.
- `references/ux-interaction-guidelines.md`: WhatsGPS-specific UX interaction rules for flows, IA, feedback, error prevention, accessibility, and PM review.
- `references/ui-ux-quality-gates.md`: Adapted UI/UX Pro Max quality gates for accessibility, interaction, layout, table/form, chart, loading, and motion checks.
- `references/product-domain-model.md`: Platform domain entities, field priorities, statuses, and route map.
- `references/component-patterns.md`: Element UI component patterns and state rules.
- `references/design-workflows.md`: Task recipes for page generation, Figma restore, review, token output, and HTML prototype work.
- `references/page-patterns.md`: Layout patterns for dashboard, device list, map, realtime video, trip image, and organization pages.
- `references/device-detail-workspace.md`: The core hardware-device management modal/workbench pattern.
- `references/review-checklist.md`: UI review checklist and temporary anti-patterns.
- `references/requirements-design-doc-template.md`: Structure for writing requirement design drafts.
