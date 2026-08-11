# Changelog

This project follows a lightweight form of [Keep a Changelog](https://keepachangelog.com/):
completed work is recorded under **Unreleased**, then moved into a numbered
version section when a release/version is intentionally created.

## Unreleased

### Added

- Saved View slider for global room-fill opacity, allowing reference images to remain visible beneath rooms without fading boundaries or tags
- Toolbar selection filter for rooms, room edges, drafting lines, outdoor boundaries and images
- Generic Rotate Selected command for rooms, drafting lines, outdoor boundaries and unlocked images
- Shift-click and window/crossing multi-selection for unlocked reference images, including group move/delete
- Unified hover, click and window/crossing selection for unlocked reference images
- Persistent, Undoable reference-image Lock/Unlock controls
- Collapsible Story → Apartment/Department → Room tree with direct room selection
- Quick room creation dialog with pointer-attached, snapped canvas placement
- Formal Room Categories stored separately from Room Name
- Standard category choices, custom categories and multi-room category assignment
- Room Category columns in the room schedule and CSV export
- Semantic room-boundary types: Wall, Glazing and Virtual / Open
- Shared and partial boundary-segment data with multi-selection and Undo/Redo
- Dedicated room-boundary and outdoor-boundary selection tools
- Automatically derived and editable outdoor/building boundary
- Graphical outdoor-boundary offset controls
- Printable, draggable and resizable canvas legend with optional two-column room list
- Architectural color swatches with color copy/paste
- Same-name room color synchronization
- Save and Save As using persistent file handles where supported
- Recent-project history and last-used Open/Save location
- Saved canvas zoom and pan restoration
- Collapsible and resizable side panels
- Window and crossing selection for rooms, drafting lines and boundaries
- Adjustable multiline room-tag width
- Contextual status bar with cursor coordinates and command guidance
- Per-story reference images with placement, selection, move and resize grips
- Reference-image visibility, deletion, project persistence and Undo/Redo
- Proportional reference-image grip resizing, numeric scaling and two-point distance calibration
- Reference-image source display and replacement by pasted path or file browser
- Reference-image duplication and copy/paste across stories
- Non-destructive rectangular and polygonal image crops with live closure preview
- Free-canvas rectangle/circle drafting and Shift-constrained angular snapping
- Numeric and 90-degree reference-image rotation with horizontal/vertical mirroring
- Reference-image copy, paste, duplicate, transform and delete context-menu commands
- Drafting-line move, endpoint editing, copy/paste, duplication and context-menu commands

### Changed

- Hovering manipulation grips now shows directional resize or move cursors
- The left sidebar is split into focused Rooms and Settings tabs
- Apartment/Department tree rows now show both room count and total room area
- Room, room-edge, drafting-line and outdoor-boundary selection now share one hover-aware selection tool
- The canvas legend now lives in drawing space, follows pan/zoom, and has font-size controls plus draggable corner width grips
- Cropped reference images now use crop-fitted selection and manipulation bounds
- Zooming and middle-button panning preserve active crop and drafting previews
- Shared-boundary conditions now affect only the actual overlapping segment,
  rather than the complete room edge
- Room-property changes apply automatically without an Apply button
- Room duplication drag shortcut changed to Ctrl+Alt to avoid Shift-selection conflicts
- Project file data advanced to version 38 while retaining older-project fallbacks

### Fixed

- Room-edge hover, click and window/crossing selection now split edges at every adjacent-room intersection instead of treating the entire source edge as one selectable segment
- Window/crossing-selected room edges now open their configuration controls in the right panel
- Line and Chain Line geometry now participates in project Undo/Redo history and unified selection
- Preserved boundary styles when room geometry is redrawn or refreshed
- Reconciled semantic boundaries after rooms are moved, resized or edited
- Corrected stale selection state when switching or deleting stories
- Added outdoor-boundary operations to Undo/Redo history
- Removed a duplicated legacy resize patch that could cause a startup error
- Prevented folded side panels from collapsing the canvas
- Prevented deleted stories from leaving orphan outdoor-boundary data

## v37

- Added multi-room color editing from the Properties panel
- Preserves each room's other properties and supports Undo

## v36

- Added Swap Width/Length for selected rectangular rooms
- Supports multi-selection and Undo

## v35

- Previous baseline
