# Architectural Zone Designer — Development Roadmap

## Project Vision

Architectural Zone Designer is a lightweight, canvas-first architectural
space-planning application intended for rapid early-stage design development.

The application should allow architects to develop spatial arrangements while
simultaneously considering:

- Space programming
- Room dimensions and areas
- Adjacency
- Circulation
- Building-code requirements
- Setbacks
- Structural coordination
- Daylight
- Views
- Natural ventilation
- Outdoor access
- Gross and net area calculations
- Repetitive/modular planning
- Reference drawings and precedents

The application should remain fast, simple and visually unobtrusive.

The interaction philosophy should be closer to lightweight canvas applications
such as PureRef than to a full BIM authoring platform.

The goal is NOT to reproduce Revit, AutoCAD, Rhino or structural-analysis
software.

The goal is to create an intelligent architectural planning environment.

---

# CURRENT DEVELOPMENT PHILOSOPHY

For the current development stage:

- Keep the entire application inside a single `index.html`.
- Use vanilla HTML, CSS and JavaScript.
- Avoid external frameworks unless explicitly approved.
- Maintain offline capability.
- Preserve existing functionality whenever adding features.
- Preserve compatibility with older project files whenever practical.
- Integrate new features with existing Undo/Redo.
- Support multi-selection where appropriate.
- Do not redesign unrelated UI while implementing a feature.
- Do not perform large refactors unless explicitly requested.
- Implement features incrementally and test them before moving forward.

The single-HTML architecture is intentional during prototype development.

A future desktop version may reorganize the code internally while preserving
the lightweight/offline philosophy.

---

# LONG-TERM DESKTOP APPLICATION

The eventual goal is a lightweight offline desktop application.

Desired characteristics:

- Very fast startup
- Lightweight installation
- Offline operation
- Minimal interface
- Canvas-first workflow
- Native file open/save
- Drag-and-drop
- Clipboard integration
- Autosave/recovery
- Recent projects
- No mandatory cloud dependency
- No mandatory account/login
- Minimal visual clutter

The mature HTML/JavaScript application may eventually be packaged using an
appropriate lightweight desktop technology.

The current single-HTML prototype should therefore avoid unnecessary
dependencies that make this transition difficult.

---

# CORE DATA-MODEL PRINCIPLE

Project information should increasingly be stored as structured project data
rather than existing only as canvas graphics.

Long-term conceptual structure:

Project
├── Stories
├── Rooms
├── Room Categories
├── Room Boundary Segments
├── Entrances
├── Groups / Modules
├── Reference Images
├── Structural Grids
├── Conceptual Columns
├── Structural Joints
├── Setbacks
├── Code Configurations
├── Compliance Warnings
└── Analysis Results

Canvas graphics should represent project data rather than being the only
source of that data.

This is important for future analysis, compliance checking and migration to
a desktop application.

---

# 1. ROOM EDITING AND BASIC PLANNING

Continue improving the existing room-planning workflow.

Features include:

- Create rooms
- Move rooms
- Multi-selection
- Resize rooms
- Rename rooms
- Move room tags independently
- Duplicate rooms
- Undo/Redo
- Room properties
- Room colors
- Room schedules
- Story management
- Project save/open

Additional editing improvements:

- Swap Width / Length
- Multi-room Width / Length swap
- Architectural color swatches
- Apply color to multiple selected rooms
- Custom/favorite color swatches
- Room transparency
- Lock room dimensions
- Alignment tools
- Distribution tools
- Match properties
- Match room size
- Rotate rectangular rooms
- Mirror rooms
- Duplicate-in-place

These should remain lightweight and CAD-like.

---

# 2. ROOM CATEGORIES

Introduce formal Room Categories.

Examples:

- Bedroom
- Living
- Dining
- Kitchen
- Bathroom
- Corridor
- Lobby
- Stair
- Service
- Storage
- Mechanical
- Electrical
- Office
- Laboratory
- Treatment
- Circulation
- Outdoor
- Other

Room categories should eventually drive:

- Code requirements
- Area calculations
- Environmental requirements
- Room styles
- Compliance checking
- Reporting
- Excel export
- Analysis

Room Category should be separate from Room Name.

Example:

Room Name:
Master Bedroom

Category:
Bedroom

This allows differently named rooms to inherit the same rules.

---

# 3. SEMANTIC ROOM BOUNDARIES

Room boundaries should become individually identifiable architectural objects.

A user should be able to select an individual room boundary segment and assign
a Boundary Type.

Initial boundary types:

- Wall
- Glazing
- Virtual / Open

Future types may include:

- Door / Opening
- External Wall
- Internal Wall
- Curtain Wall
- Screen
- Railing
- Other

## Virtual / Open Boundary

A Virtual boundary means two architectural spaces are separate rooms/zones
for programming and area calculations but have no physical wall between them.

Example:

Living Room | Virtual Boundary | Dining Area

Both remain independently identifiable spaces.

## Glazing Boundary

A glazing boundary represents a glazed portion of the room perimeter.

This information should eventually support:

- Daylight analysis
- View analysis
- Natural ventilation analysis
- External exposure
- Façade analysis
- Code compliance

Boundary semantics must be stored as project data, not merely represented by
different line styles.

---

# 4. ROOM ENTRANCES

Allow symbolic entrances to be placed on room boundaries.

A room may have:

- No entrance
- One entrance
- Multiple entrances

Each entrance should be an actual project object.

Initial entrance information may include:

- ID
- Associated room
- Associated boundary
- Position along boundary
- Width
- Entrance type

The first implementation may use a simple symbolic marker rather than a full
architectural door representation.

Future uses:

- Circulation analysis
- Accessibility
- Egress
- Travel distance
- Adjacency
- Route finding
- Code compliance
- Entrance-count requirements

---

# 5. REFERENCE IMAGE / TRACING SYSTEM

Provide a lightweight architectural tracing workflow.

Users should be able to insert reference images into the design canvas.

Reference images may include:

- Existing floor plans
- Hand sketches
- Precedent plans
- Site drawings
- Structural layouts
- Screenshots
- Design studies

## Basic Reference Image Features

- Insert image
- Move image
- Delete image
- Show / Hide
- Lock / Unlock
- Freeze / Unfreeze
- Opacity control
- Per-story reference images
- Save reference-image settings with project

Frozen images should remain visible but should not interfere with room
selection.

---

# 6. REFERENCE IMAGE CALIBRATION

Provide a simple CAD-like scale calibration workflow.

Example:

1. Insert image.
2. Select "Calibrate Scale".
3. Pick Point 1.
4. Pick Point 2.
5. Enter known real-world distance.
6. Application calculates image scale.

Additional capabilities:

- Free resizing using grips
- Preserve aspect ratio
- Numeric scaling
- Rotation
- Numeric rotation
- Position controls

The workflow should remain simple enough for rapid tracing.

---

# 7. ROOM TRANSPARENCY

Allow room fills to have adjustable transparency.

Purpose:

When tracing over reference drawings, the user should be able to see the
reference image beneath rooms.

Transparency should affect room fill without making room boundaries and tags
unreadable.

---

# 8. REFERENCE IMAGE CROPPING / MASKING

Advanced reference-image functionality.

Allow users to isolate only useful portions of reference images.

Prefer non-destructive cropping/masking.

The original image should remain available.

Example:

A user finds a floor-plan precedent containing a useful hotel suite.

The user should be able to isolate only the suite and ignore the rest of the
image.

---

# 9. HYBRID REFERENCE COMPOSITIONS

Support multiple reference images or cropped image fragments on the same
canvas.

Users should be able to:

- Position fragments
- Rotate fragments
- Scale fragments
- Duplicate fragments
- Combine fragments
- Lock fragments
- Hide fragments

Example workflow:

1. Crop a useful suite from Reference A.
2. Duplicate the suite several times.
3. Bring in a corridor/stair reference from Reference B.
4. Position the corridor.
5. Arrange suite fragments around it.
6. Use the resulting composition as a hybrid design reference.

This is intended as a design-thinking tool, not an image editor.

---

# 10. REUSABLE ROOM GROUPS / DESIGN MODULES

Allow collections of rooms and associated planning objects to become reusable
design modules.

Example:

Hotel Suite Type A

may contain:

- Bedroom
- Bathroom
- Entrance
- Internal boundary relationships
- Glazing information
- Room positions
- Room dimensions

The module can then be instantiated multiple times.

---

# 11. DYNAMIC MODULE TYPES

Modules should eventually behave similarly to reusable component/group types.

Example:

Hotel Suite Type A
├── Instance 01
├── Instance 02
├── Instance 03
└── Instance 04

Editing the module definition should be capable of updating other instances.

Users should also be able to duplicate a module type:

Hotel Suite Type A
→ Hotel Suite Type A1

and modify the new type independently.

Potential uses:

- Hotel rooms
- Apartments
- Hospital departments
- Patient rooms
- Classrooms
- Office modules
- Residential units
- Repeated service cores
- Repeated planning bays

The purpose is rapid modular design development.

---

# 12. CONCEPTUAL STRUCTURAL COORDINATION

Introduce a lightweight structural-planning layer.

IMPORTANT:

This is NOT structural-analysis software.

The purpose is to allow architectural planning and structural logic to evolve
together during early design.

The architect should be able to understand structural implications before the
architectural plan becomes highly developed.

---

# 13. STRUCTURAL GRID SYSTEM

Allow creation of conceptual structural grids.

Initial scope:

- Orthogonal grids
- Vertical grid lines
- Horizontal grid lines
- Automatic naming
- Vertical grids: A, B, C...
- Horizontal grids: 1, 2, 3...
- User-defined spacing
- Move individual grid lines
- Rename grids
- Delete grids
- Add grids
- Show / Hide
- Lock / Unlock
- Snap to grid
- Save/Open
- Undo/Redo

Grid lines should be real project objects.

Future capabilities:

- Rotated grids
- Multiple grid systems
- Grid presets
- Radial grids if required
- Grid dimensioning

---

# 14. CONCEPTUAL STRUCTURAL COLUMNS

Allow simple conceptual columns.

Initial column types:

- Rectangular
- Circular

Properties may include:

- Column ID
- Width
- Depth
- Diameter
- Rotation
- Position
- Associated grid intersection

Columns should preferably be placeable at grid intersections but may be moved
independently.

No structural loading or reinforcement calculations are required.

---

# 15. ROOM / COLUMN COORDINATION

Detect basic spatial conflicts between conceptual columns and rooms.

Example warning:

"Column C12 intersects Bedroom 03."

Potential visualization:

- Highlight column
- Highlight affected room
- Warning marker
- Warning list entry

The application must NOT automatically assume whether the room or column is
incorrect.

The designer decides whether to:

- Move the room
- Reshape the room
- Move the column
- Change the grid
- Accept the condition

This supports early architectural/structural coordination.

---

# 16. STRUCTURAL JOINTS

Introduce conceptual structural/movement joints.

Examples:

- Expansion joint
- Separation joint
- Movement joint
- Other conceptual structural joint types

Structural joints can materially affect architectural planning and therefore
should exist during concept development.

Users should be able to:

- Draw/place joint
- Select joint
- Move joint
- Delete joint
- Name joint
- Assign type
- Set conceptual width / joint zone
- Show / Hide
- Lock / Unlock

Joints should be visually distinct from ordinary lines.

---

# 17. STRUCTURAL JOINT COORDINATION

Future coordination should detect elements crossing structural joints.

Potential affected elements:

- Rooms
- Room modules
- Corridors
- Room boundaries
- Entrances
- Planning zones
- Other design objects

Example:

"Suite Module Type A crosses Structural Joint SJ-01."

The system should warn the architect rather than automatically resolve the
condition.

Repeated design modules should eventually understand structural-joint
boundaries.

---

# 18. CENTRAL WARNING SYSTEM

Introduce a unified project warning system.

Warnings from different systems should appear in one location.

Potential sources:

- Building-code violations
- Setback violations
- Structural-column conflicts
- Structural-joint conflicts
- Missing required entrances
- Missing external openings
- Area requirement violations
- Environmental-analysis issues

Example:

Warnings (7)

CODE
⚠ Corridor C03 below minimum width.

SETBACK
⚠ Bedroom 07 crosses required setback.

STRUCTURE
⚠ Column C14 intersects Bathroom 02.

ENVIRONMENT
⚠ Bedroom 05 has no qualifying external opening.

Warnings should be selectable so the user can locate the affected element.

Warnings should clear automatically when the underlying condition is fixed.

---

# 19. BUILDING-CODE CONFIGURATION ENGINE

Allow architectural code requirements to be configured inside the
application.

The system should NOT hard-code one jurisdiction.

Instead, provide configurable Code Presets.

Examples:

- Dubai Building Code (DBC)
- Abu Dhabi Building Code (ADBC)
- Custom Office Standard
- Client Standard
- User-defined code

Code data must be user-configurable.

---

# 20. GLOBAL CODE RULES

Allow global project rules.

Example:

Minimum corridor width = X

Other possible future rules:

- Minimum room dimension
- Minimum room area
- Minimum entrance width
- Maximum travel distance
- Minimum circulation width
- Required number of exits
- Accessibility requirements
- Daylight requirements
- Ventilation requirements

Rules should be associated with relevant room categories or project
conditions.

---

# 21. ROOM-CATEGORY CODE RULES

Room categories should inherit relevant requirements from the selected code.

Example:

Category:
Corridor

Rules:
Minimum width = X

Category:
Bedroom

Rules:
Minimum area = X
Minimum dimension = Y
External opening required = Yes

Category:
Bathroom

Rules:
Minimum area = X
Ventilation requirement = Y

Actual code values should be configured through code presets rather than
hard-coded into application logic.

---

# 22. DEFAULT PROJECT CODE

Allow a project to define its governing/default code.

Example:

Project Code:
Dubai Building Code

The application should continuously evaluate relevant design conditions
against this code where possible.

---

# 23. CROSS-CODE COMPLIANCE CHECKING

Allow temporary checking against another configured code without changing the
main governing code.

Example:

Governing Code:
DBC

Check Against:
ADBC

Result:

✓ 42 checks pass
⚠ 5 conditions require review
✕ 2 conditions fail

This allows architects to understand how a design would perform under another
code or standard.

---

# 24. SETBACK SYSTEM

Allow project setbacks to be defined.

Setbacks may eventually derive from:

- Selected building code
- Plot configuration
- Road condition
- Building type
- User-defined rules

Setback lines/zones should be visible on the canvas.

---

# 25. SETBACK COMPLIANCE

Detect when rooms or relevant design elements cross required setback
boundaries.

Potential feedback:

- Red warning outline
- Warning marker
- Warning-list entry
- Optional warning tint

Example:

"Bedroom 04 exceeds North Setback by 0.45 m."

Warnings should update dynamically as the design changes.

---

# 26. AREA CLASSIFICATION

Formalize area classification so rooms/spaces contribute correctly to project
area calculations.

The exact classification system should remain configurable.

Room/category data should determine whether an area contributes to relevant
metrics.

---

# 27. GA / NA / BUA CALCULATIONS

Calculate project area metrics including:

- GA
- NA
- BUA

Calculations must be based on properly assigned room/space categories and
project rules.

Do not rely purely on room names.

Area calculations should update dynamically as the design changes.

---

# 28. AREA SUMMARY PAGE

Provide a dedicated project area dashboard.

Potential information:

Project Area Summary

BUA
GA
NA

Breakdown by:

- Story
- Room category
- Department
- Unit
- Building
- Zone

Potential additional metrics:

- Efficiency ratio
- Net-to-gross ratio
- Circulation percentage
- Service percentage

---

# 29. EXCEL / ROOM DATA EXPORT

Room-data exports should eventually include relevant area classifications and
calculated metrics.

Potential columns:

- Room Number
- Room Name
- Category
- Story
- Width
- Length
- Area
- Area Classification
- GA Contribution
- NA Contribution
- BUA Contribution
- Parent Unit
- Department
- Code Status
- Warning Count

Project-level area summaries should also be exportable.

---

# 30. BUILDING / EXTERNAL BOUNDARY

Allow the building envelope or qualifying external boundaries to be
identified.

This may be:

- Manually drawn
- Derived from room geometry
- Assigned using boundary semantics

The system should distinguish between:

- Internal boundaries
- External boundaries
- Glazing
- Open boundaries
- Building perimeter

This becomes the foundation for environmental analysis.

---

# 31. EXTERNAL EXPOSURE ANALYSIS

Determine whether rooms have qualifying exposure to the exterior.

Example:

Bedroom 01
External Boundary: Yes

Store
External Boundary: No

This information can feed multiple analysis systems.

---

# 32. VIEW ANALYSIS

Use external boundaries and glazing information to determine potential view
access.

Initial analysis may simply classify:

- Has potential external view
- No external view

Future versions may evaluate:

- View direction
- View quality
- Obstructions
- Desired orientation

Keep early implementation simple.

---

# 33. DAYLIGHT ANALYSIS

Use room geometry, external boundaries and glazing semantics to estimate
daylight potential.

Initial implementation should be conceptual rather than physically simulated.

Possible classifications:

- Good daylight potential
- Limited daylight potential
- No direct daylight potential

Future versions may incorporate:

- Glazing length
- Glazing ratio
- Room depth
- Orientation
- Solar direction

---

# 34. NATURAL VENTILATION ANALYSIS

Use external openings/glazing and room geometry to determine potential for
natural ventilation.

Possible early checks:

- External opening exists
- No external opening
- Multiple external openings
- Potential cross ventilation

Future versions may use opening orientation and area.

---

# 35. DIRECT OUTDOOR ACCESS

Identify rooms with direct physical access to outdoor areas.

This should be distinguished from simply having an external wall or glazing.

A room may therefore have:

External exposure: Yes
View: Yes
Daylight: Yes
Outdoor access: No

or:

External exposure: Yes
View: Yes
Daylight: Yes
Outdoor access: Yes

Entrance/opening data should eventually support this analysis.

---

# 36. FUTURE ANALYSIS DASHBOARD

Provide a consolidated design-analysis view.

Possible categories:

AREA
✓ BUA
✓ NA
✓ GA

CODE
⚠ 4 warnings

STRUCTURE
⚠ 2 conflicts

DAYLIGHT
✓ 84% qualifying rooms

VIEW
✓ 76% qualifying rooms

VENTILATION
⚠ 6 rooms require review

SETBACK
✓ No violations

This should remain understandable to architects rather than becoming a
complex engineering dashboard.

---

# IMPLEMENTATION ORDER

The roadmap describes long-term intent.

DO NOT IMPLEMENT ALL FEATURES AT ONCE.

Recommended sequence:

## Phase A — Room Intelligence

1. Room categories
2. Boundary semantics
3. Room entrances
4. Improved room editing
5. Room transparency

## Phase B — Conceptual Structure

6. Structural grids
7. Conceptual columns
8. Room/column conflict detection
9. Structural joints
10. Structural-joint conflict detection

## Phase C — Reference / Tracing

11. Reference images
12. Image calibration
13. Freeze/visibility/opacity
14. Cropping/masking
15. Multiple reference fragments
16. Hybrid reference compositions

## Phase D — Modular Planning

17. Basic room grouping
18. Named module types
19. Module instances
20. Dynamic module updates
21. Module variants

## Phase E — Area Intelligence

22. Area classification
23. GA / NA / BUA calculations
24. Area summary page
25. Excel export enhancements

## Phase F — Compliance Foundation

26. Central warning system
27. Code configuration data model
28. Code presets
29. Room-category rules
30. Default project code

## Phase G — Site / Setbacks

31. Site/buildable boundary
32. Setback definitions
33. Setback visualization
34. Setback violation detection

## Phase H — Code Intelligence

35. Live compliance checking
36. Warning navigation
37. Cross-code checking
38. Compliance summary

## Phase I — Environmental Intelligence

39. Building/external boundary
40. External exposure
41. View analysis
42. Daylight analysis
43. Natural ventilation
44. Direct outdoor access
45. Analysis dashboard

---

# CODEX IMPLEMENTATION RULE

This roadmap describes the intended direction of the application.

It DOES NOT authorize implementation of every listed feature.

For every Codex task:

1. Read this ROADMAP.
2. Read PROJECT_RULES.
3. Understand how the requested feature fits into the long-term architecture.
4. Implement ONLY the feature explicitly requested in the current task.
5. Do not pre-implement future roadmap features.
6. Do not perform unrelated refactoring.
7. Preserve existing functionality.
8. Preserve project-file compatibility wherever practical.
9. Integrate with existing Undo/Redo.
10. Test affected existing functionality after implementation.

If implementing a roadmap feature requires a data-model decision that could
materially constrain later roadmap features, identify the issue before making
a large architectural change.

---

# DESIGN PHILOSOPHY

Architectural Zone Designer should encourage architects to think about
multiple design constraints simultaneously during early planning.

A room is not simply a rectangle.

It has:

- Purpose
- Category
- Dimensions
- Area
- Relationships
- Boundaries
- Entrances
- External exposure
- Structural context
- Code requirements

Likewise, structure should not suddenly appear after architecture has already
been designed.

Structural grids, conceptual columns and structural joints should be visible
during architectural planning so architecture and structural logic can evolve
together.

The same principle applies to:

- Code
- Setbacks
- Circulation
- Daylight
- Views
- Ventilation
- Area efficiency
- Repetition/modularity

The application should expose these relationships without becoming heavy or
complicated.

The fundamental product principle is:

**Lightweight interaction with increasingly intelligent architectural
awareness.**