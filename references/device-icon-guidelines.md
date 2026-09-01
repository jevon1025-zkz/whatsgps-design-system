# Device Icon Guidelines

## Sources

- Final design: https://www.figma.com/design/txoCSedmKc5MTzYF2wJSlD/设备详情?node-id=74-843
- PRD: [device-icon-and-detail-prd.md](../assets/source-materials/device-icon-and-detail-prd.md)
- Prior workflow: [device-icon-workflow.md](../assets/source-materials/device-icon-workflow.md)
- Figma export manifest: [device-icon-asset-manifest.md](device-icon-asset-manifest.md)
- Bundled final direction-frame handoff: ../assets/direction-marker-no-shadow-handoff-20260706-173945.zip

Use the current final Figma instances for approved icon assets. Historical local folders, the former 150-PNG archive, candidates, and contact sheets are evidence only; they are not final assets and must not be resized or repackaged for delivery.

## Asset Source And Release Gate

- This Skill package delivers rules and source-of-truth constraints, not the complete device-icon PNG library. Absence of the 150 historical PNG files is intentional and does not block Skill release.
- Formal PNG/SVG files must be exported from the final instances under Figma section `图标替换/pc` (`48:8443`) or from another explicitly verified final instance in the same file.
- Verified sample: instance `929:866`, properties `离线状态 / 摩托车`, Figma dimensions `42 x 42px`.
- Do not claim that the Skill contains a complete formal icon library. When a separate asset-delivery task is requested, each delivered file must be exported from Figma and recorded in a manifest.
- The manifest must record Figma file key, section/node ID, instance node ID, state, icon type, Figma width/height, export format, and export time.
- If an instance has no export setting, use a non-mutating Figma export/copy path. Do not add settings to the shared design file or substitute a canvas screenshot.

## Inventory

The default library contains 30 icons. Eight are new: 越野车、微型车、皮卡、牵引车、卡车、挂车、集装箱、拖拉机.

Direct display:

小轿车、出租车、警车、越野车、微型车、皮卡、小货车、大货车、牵引车、公交、搅拌车、卡车、农机、装载车、挂车、集装箱、火车、挖掘机、拖拉机、船、摩托车、标记.

Direction frame:

自行车、滑板车、电动车、猫咪、狗狗、牲畜、宠物、人物 and all custom icons.

Each icon must match exactly one map-display rule.

## Status Semantics

| State | Meaning | Token direction | Rule |
|---|---|---|---|
| 静止 | Stopped/no movement | device/stopped blue | Lower urgency than alarms. |
| 行驶 | Moving | device/moving green | Direction remains legible. |
| 怠速/未定位 | Idle or location unavailable | device/idle yellow | Attention without critical weight. |
| 离线/断油电 | Offline or unavailable | device/offline grey | Reduced visual weight. |
| 超速 | Serious/high-risk state | alarm/critical red | Highest visual urgency. |

Do not show a separate red cut-power state on the map. Cut-power uses the grey offline display. The historical folder name 断油电:超速 does not override this product rule; asset mapping must distinguish business state from legacy naming.

## Map Geometry

- Direct-display icon: use the current Figma instance dimensions. The verified `离线状态 / 摩托车` instance is `42 x 42px`; do not extrapolate unverified dimensions to every icon.
- Direction-frame export canvas: transparent 64 x 64px.
- Visible direction frame: 42 x 54px.
- Direction-frame visual: no shadow. Both final SVG and PNG assets use the same no-shadow geometry.
- Align the circular-base center to canvas center (32, 32).
- Rotate around that base center, not the visible bounding-box center.
- Keep canvas, anchor, frame position, and geometry identical across states; change only state styling/color.
- Do not crop the transparent 64 x 64px canvas.

This is the final approved specification. Use the Figma annotation and final handoff assets as the only implementation basis.

The Figma side-test annotation explicitly covers 猫咪、狗、宠物、牛、电动车、自行车、滑板车. Apply the same final direction-frame asset and geometry to every icon classified under the direction-frame rule, including other approved direction-frame/custom icons.

## Creation Direction

- Working source format for future creation: 512 x 512 RGBA PNG, transparent background, centered, no scene/background. This is not the current Figma deliverable size.
- Core acceptance size: the actual Figma map instance, currently verified at 42px for one sample; 512px is only a creation source.
- Style: consistent light 3D miniature, rounded volume, soft highlight/shadow, crisp transparent edges. Avoid photorealism, flat illustration, plastic, jelly, or arbitrary material changes.
- Vehicle icons use strict top view with front facing up. Keep angle, proportion, glass, tires, lights, and highlight system consistent.
- Recognition beats decorative detail. Define the three features that must survive at 42px and how the icon differs from similar device types before drawing.
- Do not use tiny text or thin lines as the only identifying feature.
- Define state-color regions and protected regions before generating variants.

## State Variant Workflow

1. Confirm use scene, display size, neighboring/similar icons, recognition features, view, and state-color coverage.
2. Create and approve the blue stopped master only.
3. Inspect both 512px detail and a true 42px rendering.
4. Generate other states from the same approved master.
5. Change target color regions only; preserve geometry, luminance structure, highlight, shadow, material, alpha, glass, tires, mechanical parts, expressions, and protected details.
6. Inspect individual PNGs plus a five-state contact sheet and 42px sheet.
7. Verify output path, names, dimensions, RGBA/alpha, and cross-platform asset mapping.

Do not regenerate a merely similar icon for a state change. Do not use a whole-image filter that recolors glass, tires, faces, chassis, or mechanical components.

## Lessons From Customer Feedback

### Small/Large Truck And Mixer

At 512px, a colored cab appeared sufficient; at 42px, the large grey cargo box or mixer drum dominated and state was hard to read. Include the principal visible body/cargo/drum surfaces in the state-color region while preserving structure and light 3D shading. State color must occupy enough of the 42px silhouette to be seen immediately.

### Motorcycle

The old top-view silhouette became a vertical line at map size. Do not solve this by horizontally stretching the whole bitmap. Redesign useful transverse features such as tank/side body, handlebar, and mirrors while preserving wheel axis and believable top-view proportion. Verify type recognition and clickability at 42px before creating all states.

## Device Detail And Cross-Platform Rules

- Web, Android, and iOS use consistent icon assets, status semantics, and map-display rules.
- Device summary: icon in an 80 x 80px container, rendered at 56 x 56px.
- Saving a default/custom icon updates device summary and map preview/display together.
- Custom upload supports jpg/jpeg/png, at most 1MB, circular crop preview, replace/delete, cancel without mutation, and automatic selection after successful crop.
- Deleting a custom icon restores the unuploaded state and selects the first default icon, 小轿车, according to the current PRD.
- The icon-replacement flow is a drill-in inside the selection dialog, not an additional nested modal.

## Asset QA

- Type and state are independently recognizable at 42px.
- No state has geometry, scale, anchor, or transparency drift.
- Direction-frame assets have no shadow and remain exactly 64 x 64px with a 42 x 54px visible frame.
- State color is not confined to a negligible patch.
- No residual blue pixels or protected-region miscoloring.
- Vehicle families remain distinguishable: small/large truck, tractor/trailer/container, agricultural/loader/excavator, and similar types.
- Final delivery includes independent assets exported from Figma plus a node manifest; contact sheets and resized historical PNGs do not replace them.
