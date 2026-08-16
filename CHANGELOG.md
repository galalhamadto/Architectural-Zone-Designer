# Changelog

This project follows a lightweight form of [Keep a Changelog](https://keepachangelog.com/):
completed work is recorded under **Unreleased**, then moved into a numbered
version section when a release/version is intentionally created.

## Unreleased

### Added

- Shared advanced line-pattern library with double-dash, dash-dot, dash-dot-dot, long-dash and center-line styles, plus precise negative-cross thickness and dash-size controls
- Saved negative-room cross-line color, weight and solid/dashed/dotted pattern controls in Settings
- Persistent negative rooms for voids, shafts, lifts and other deductions, with white default fill, corner-cross graphics, signed area schedules/exports and net project-area checks
- Connected-loop property boundaries with shared vertex editing, individually controlled setback distances, clickable per-segment dimensions, double-click floating numeric editing, linked setback regeneration, site-line styles, grouped movement and optional neighbour/street labels
- Line-to-Curve drafting command with graphical signed peak-offset preview, click-to-commit, Escape cancellation, persistence and Undo/Redo
- Interactive Fillet and Chamfer workflow for room boundaries and free/room drafting lines, with unified line picking, live graphical preview, floating numeric entry, click-to-apply, Enter confirmation and Escape cancellation
- Drag-and-drop reference-image placement directly on the canvas, with a live image footprint, drop-point marker and filename feedback
- Standard Ctrl/Cmd+Z Undo, Ctrl/Cmd+Y Redo and Ctrl/Cmd+Shift+Z Redo shortcuts
- Generic Delete Selected toolbar command for rooms, groups, drafting lines, outdoor boundaries and reference images
- Generic Mirror Selected toolbar command with horizontal and vertical choices for rooms, groups, drafting lines, outdoor boundaries and unlocked reference images
- Room Groups selection-filter category, group-wide hover feedback and double-click entry into Edit Group mode
- Story → Groups → Group Instance → Room hierarchy in the Rooms tree; grouped rooms no longer duplicate under department branches
- Revit-style linked group instances: grouped rooms select and move together, while Edit Group isolates member editing and Save propagates changes to every instance
- Discard Group Edit restores the complete pre-edit room state; saved group-edit sessions remain a single Undo/Redo operation
- Persistent room groups created from multi-selection through the toolbar or context menu
- Room Groups management panel with selectable layout thumbnails, group duplication and ungrouping
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

- Replaced available generated toolbar symbols with the prepared SVG icon pack, including mirror direction choices and reference calibration/cropping controls
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
- Project file data advanced to version 45 while retaining older-project fallbacks

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
