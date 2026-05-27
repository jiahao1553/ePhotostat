# Graph Report - .  (2026-05-27)

## Corpus Check
- Corpus is ~4,098 words - fits in a single context window. You may not need a graph.

## Summary
- 53 nodes · 57 edges · 11 communities (6 shown, 5 thin omitted)
- Extraction: 95% EXTRACTED · 5% INFERRED · 0% AMBIGUOUS · INFERRED: 3 edges (avg confidence: 0.82)
- Token cost: 0 input · 0 output

## Community Hubs (Navigation)
- [[_COMMUNITY_VS Code Theme Settings|VS Code Theme Settings]]
- [[_COMMUNITY_Crop & Capture Core|Crop & Capture Core]]
- [[_COMMUNITY_Crop Interaction Handlers|Crop Interaction Handlers]]
- [[_COMMUNITY_Camera Stream Control|Camera Stream Control]]
- [[_COMMUNITY_PDF Export & Card Layout|PDF Export & Card Layout]]
- [[_COMMUNITY_Sharpness Auto-Capture|Sharpness Auto-Capture]]
- [[_COMMUNITY_Claude Code Hooks|Claude Code Hooks]]
- [[_COMMUNITY_Dev Tool Configuration|Dev Tool Configuration]]
- [[_COMMUNITY_VS Code UI Customization|VS Code UI Customization]]
- [[_COMMUNITY_Crop Release Handler|Crop Release Handler]]
- [[_COMMUNITY_Torch Toggle|Torch Toggle]]

## God Nodes (most connected - your core abstractions)
1. `workbench.colorCustomizations` - 12 edges
2. `doCapture` - 8 edges
3. `Application State (front/back images)` - 6 edges
4. `applyCrop` - 5 edges
5. `startAnalysis` - 5 edges
6. `updatePreview` - 5 edges
7. `openCropModal` - 4 edges
8. `startStream` - 4 edges
9. `updateStatus` - 4 edges
10. `downloadPDF` - 4 edges

## Surprising Connections (you probably didn't know these)
- `Claude Settings Hooks` --rationale_for--> `Graphify Usage Rules`  [INFERRED]
  .claude/settings.json → CLAUDE.md

## Hyperedges (group relationships)
- **Image Capture Pipeline: Camera → Crop → State → Preview/PDF** — index_docapture, index_applycrop, index_state, index_updatepreview, index_downloadpdf [INFERRED 0.95]
- **Camera Analysis Loop: startAnalysis → computeSharpness → drawViewfinder → doCapture** — index_startanalysis, index_computesharpness, index_drawviewfinder, index_docapture [EXTRACTED 1.00]
- **Crop Modal Interaction: down/move/up → drawCropFrame → applyCrop** — index_oncropdown, index_oncropmove, index_oncropup, index_drawcropframe, index_applycrop [EXTRACTED 1.00]

## Communities (11 total, 5 thin omitted)

### Community 0 - "VS Code Theme Settings"
Cohesion: 0.15
Nodes (12): workbench.colorCustomizations, activityBar.background, statusBar.background, statusBar.debuggingBackground, statusBar.debuggingForeground, statusBar.foreground, statusBar.noFolderBackground, statusBar.noFolderForeground (+4 more)

### Community 1 - "Crop & Capture Core"
Cohesion: 0.36
Nodes (10): applyCrop, closeCropModal, doCapture, manualCapture, removeImage, Application State (front/back images), updateAngle, updatePreview (+2 more)

### Community 2 - "Crop Interaction Handlers"
Cohesion: 0.29
Nodes (7): cropHitTest, drawCropFrame, getEventPos, handleFile, onCropDown, onCropMove, openCropModal

### Community 3 - "Camera Stream Control"
Cohesion: 0.33
Nodes (6): closeCamera, flipCamera, openCamera, resetProgress, startStream, stopStream

### Community 4 - "PDF Export & Card Layout"
Cohesion: 0.40
Nodes (5): ID Card Aspect Ratio (85.6/54 ISO 7810), downloadPDF, drawViewfinder, jsPDF Library (cdnjs), Watermark Stamp Overlay

### Community 5 - "Sharpness Auto-Capture"
Cohesion: 0.67
Nodes (4): Auto-Capture on Sharpness Threshold, computeSharpness, Laplacian Variance Sharpness Detection, startAnalysis

## Knowledge Gaps
- **23 isolated node(s):** `PreToolUse`, `activityBar.background`, `titleBar.activeBackground`, `titleBar.activeForeground`, `titleBar.inactiveBackground` (+18 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **5 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `doCapture` connect `Crop & Capture Core` to `Crop Interaction Handlers`, `Camera Stream Control`, `Sharpness Auto-Capture`?**
  _High betweenness centrality (0.207) - this node is a cross-community bridge._
- **Why does `startAnalysis` connect `Sharpness Auto-Capture` to `Crop & Capture Core`, `Camera Stream Control`, `PDF Export & Card Layout`?**
  _High betweenness centrality (0.139) - this node is a cross-community bridge._
- **Why does `openCropModal` connect `Crop Interaction Handlers` to `Crop & Capture Core`, `PDF Export & Card Layout`?**
  _High betweenness centrality (0.121) - this node is a cross-community bridge._
- **What connects `PreToolUse`, `activityBar.background`, `titleBar.activeBackground` to the rest of the system?**
  _26 weakly-connected nodes found - possible documentation gaps or missing edges._