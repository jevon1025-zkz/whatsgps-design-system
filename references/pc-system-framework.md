# PC System Framework

## What 3.0 Updates

Version 3.0 updates the PC product experience framework and the design-system operating framework. It does not claim a complete product information-architecture rewrite or a technical-stack migration.

### Experience Shell

- Sidebar navigation: approved grouping, order, expanded/collapsed presentation, and state rules.
- Top bar: page context plus feedback, global search, language, messages, and account entries.
- Global search: quick retrieval followed by a permission-aware full-result workspace.
- Message system: unread popover, category-based message center, role copy, and category-scoped read actions.
- Device workbench: stable device context, task tabs, quick actions, vertical forms, tables, setting matrices, and predictable footer actions.

### Domain And Permission Layer

- Core objects: device, customer, account, service, location, video, command, alarm, renewal, transfer, maintenance, and sensor configuration.
- Core identifiers: device name, IMEI, SIM, ICCID, model, owner/customer, state, service version, expiry, and last position.
- Permission evidence: PC menu inventory and role columns remain the source for capability visibility.
- Search, counts, previews, recent items, and destination links are permission-filtered before display.

### Interaction And Component Layer

- Dense PC operational layouts remain the baseline: tables, trees, toolbars, continuous sections, maps, media grids, and the device workbench.
- New or substantially redesigned PC forms use labels above controls and task-ordered vertical flow.
- Multi-column structures are reserved for repeated setting matrices, tables, or genuine side-by-side comparison.
- Loading, empty, no-permission, partial failure, disabled, validation, success, and recovery states are part of the framework.

### Design-System Layer

- Color architecture: 01 Gradient Palette plus 02 Component Tokens.
- Shared typography, spacing, radius, size, shadow, and motion references remain available.
- Field-copy and i18n governance apply across PC work.
- Final Figma is authoritative for approved visual results; source provenance must remain explicit when a Figma file has no Variables.

## What 3.0 Retains

- Frontend context remains a Vue 2-style SPA with Element UI conventions unless the target repository proves otherwise.
- Existing routes, interfaces, data relationships, permissions, and internal page logic remain unchanged unless an approved requirement explicitly changes them.
- Existing page families remain the organizational baseline; navigation optimization changes grouping and access presentation, not ownership of every underlying feature.

## What 3.0 Does Not Update

- No frontend framework migration, such as Vue 2 to Vue 3 or Element UI to another component library.
- No backend/service architecture rewrite.
- No database, protocol, API, or device-communication architecture redesign.
- No complete PC route or product information-architecture reconstruction beyond the approved navigation, search, message, track-playback, and device-detail scope.
- No APP feature framework, APP total information architecture, or APP navigation definition.

## Claiming Framework Changes

When describing 3.0, use precise language:

- Correct: PC experience shell and design-system framework were updated.
- Correct: navigation, search, messages, device icons, device detail, form direction, permissions, tokens, copy, and QA rules were consolidated.
- Incorrect: the whole product architecture was rebuilt.
- Incorrect: the frontend or backend framework was upgraded.

