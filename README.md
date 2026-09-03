# Electroprint-Releases
Electroprint is a software designed to merge 3D files with EDA (Kicad) netlists to 3D print objects with integrated electronics

The code will be open source before the end of August 2026

## Changelog (v1.4.0):
- Adding a board explorer
- Changes to STEP and 3mf export to improve quality

## Changelog (v1.3.0):
- Routing rules are now editable in "Edit" -> "Routing rules": track width, track height, clearance between tracks of different nets, and clearance between a track and a pad of another net. The rules are saved **inside the project** (.epr), so a project routes the same way on any machine; a checkbox additionally stores them as the defaults for new projects. They never resize the tracks already drawn — those are edited by selecting them, from the right-hand panel.
- Ratsnest system has been reworked to be more like EDA softwares. A link disappears as soon as copper actually connects its two pads, directly or through a chain of tracks and T-junctions. The status bar shows the progress ("12/37 links routed") and "Ratsnest Info" details the nets left to route.
- "Help" window now provide a link to this github.
- New "Pad XY scale (%)" property per component: enlarges or shrinks the pads in the XY plane only (100 % = footprint size), to compensate for the tolerance of your printer. The Z thickness is never affected.

### Fixes (v1.3.0):
- Footprints were mirrored top/bottom, and extruded pads rotated the wrong way (KiCad Y-down vs. 3D Y-up). Both are fixed — check the orientation of components generated with an earlier version.
- The two 90° rotation buttons in selection mode were inverted.
- Footprints whose name contains dots are now resolved correctly, and "Browse footprint..." loads a file even when it sits outside the configured footprint folders.
- Tracks lying outside the default Z plane can now be selected and dragged.
- The missing-footprints window is readable under a dark theme.

## Changelog (v1.2.0):
- You can now export 3mf who can be opened as a project in Prusaslicer. The pause(s) (M601) are already included in the project to allow inclusion of your electronic components. (**3mf export can take up to 1 minute and can cause a temporary freeze of the app**)
- 3mf exports now create forms who don't trigger an alert for non closed geometry in Prusaslicer.
- 3mf exports include special instructions for a high number of perimeters (default 4, adjustable from 1 to 20 in the export dialog) for conductive elements. It avoid the risk of hollow conductive tracks who would be underperforming.
- Language change is now available for English and French through 'Help'>'Language'. It will trigger a re-launch of the app so make sure you saved your project.
- Improved ratsnest visibility
- Color change for the conductive tracks. Now dark blue.

## Changelog (v1.1.5):
- Both selection modes (component and route) are now fused together.
- Selection of the footprint folder is now done through "Edit" "Footprint folder". The folders listed stay between session. No need to find the folder after every re-launch.
- 3MF export optimized for PrusaSlicer, featuring pre-configured settings for multiple perimeters and 90% infill for the conductors.

## Operation:
(Perform in this order)
- The "Import STEP/ STL" button allows you to import a .step/.stl file.
- The "Import netlist" button allows you to select a KiCad netlist (preferably version 8.0 or 9.0; earlier versions have not been tested).
- The "Orient part" button allows you to choose a face to orient towards the build plate.
- "Edit" -> "Footprint folders..." allows you to locate the KiCad footprints folder(s). This enables the software to associate the footprints found in the imported netlist. The list is kept between sessions.
Currently, you can still assign individually a footprint after the component generation. You will just get an alert if the footprint don't exist in the standard library.
- The "Generate 3D components" button builds the pads and the bodies of the components from the netlist.
- "Follow surface" makes the generated components follow the surface of the part instead of staying on the build plate ("Plane mode" switches back).
- After clicking the routing button, you must click on the starting pad.
While routing, the 'B' key switches to vertical routing mode. Clicking while in vertical routing mode confirms the vertical path and automatically switches back to horizontal routing.
While in vertical routing mode, pressing the 'N' key snaps the cursor to the nearest net pad.
- T-junction: while routing, a click on a track already drawn **of the same net** ends the route on it (the end point is snapped onto the axis of the target track). In horizontal mode you must be at the level of the target track; in vertical mode aim at its level with the mouse ('N' snapping keeps priority when active).
- Routing warns you when a track comes closer than the clearances set in "Edit" -> "Routing rules".

### Editing
- The right-hand section allows you to modify, for a selected component: footprint name, footprint type, footprint file path, pad thickness, undercut, pad XY scale, the size of the rectangular block (used to cut the shape out of the main body for "print-in-place" functionality) and its Z offset, plus manual movement in XY / Z and rotation around Z with an adjustable step.
- Tracks can be dragged.
- Track dimensions can be modified (currently the entire track at once) from the right-hand panel, by selecting the track.
- You can obtain an estimate of a track's equivalent resistance ("Resistance probe"). The resistivity used is adjustable (Ω·cm) and remembered between sessions. T-junctions are taken into account; deleting or moving a host track leaves the junction dangling, and the probe then reports that no path exists.
- "Burial analysis" shows, for each component, the buried and the protruding part of its body relative to the imported part.
- Undo / Redo are available in "Edit" (Ctrl+Z / Ctrl+Y), along with "Clear history".

### Saving and exporting
- Projects are saved and reopened as .epr files ("File" -> "Save project" / "Open a project"), with a "Recent projects" submenu.
- "File" -> "Print layout" gives the pause report: at which layer to pause and which components to insert, with heights measured from the bottom of the part. The layer height is adjustable in the window and remembered, and the report can be exported as text or CSV.
- "File" -> "3D Export" offers three exports, the 3MF ones sharing an options dialog (conductor perimeters + checkboxes to attach the pause plan as .txt and/or .csv):
    - "Export STEP" : the geometry alone.
    - "Export 3MF part" : part + conductors as a single multi-volume object, with per-volume PrusaSlicer settings (perimeters and 90 % infill on the conductors). The pauses only travel as readable notes.
    - "Export 3MF project" : same, plus the pauses written in the native format. Opening the 3MF **as a project** in PrusaSlicer already shows every component insertion on the layer bar as an M601 pause with an LCD message listing the components to place — no manual entry. Slice at the layer height of the plan, without rotating the part.
- The application remembers your environment between sessions: window size and position, last folder used by each dialog, footprint folders, probe resistivity, layer height and export options.

<img width="938" height="560" alt="Interface_v1-2-0" src="https://github.com/user-attachments/assets/93705297-2f6b-4203-aaea-f0d20dd7b7a4" />
<img width="955" height="524" alt="result_exp_proj_prusaslicer" src="https://github.com/user-attachments/assets/f316d2b1-5c3d-4b6d-872c-63a867428e3f" />



## Video tutorial and demo (start at 4:25):
[[https://youtu.be/1-gWeTOcZFc](https://www.youtube.com/watch?v=1-gWeTOcZFc)](https://www.youtube.com/watch?v=1-gWeTOcZFc)
[![Video on Youtube](https://img.youtube.com/vi/1-gWeTOcZFc/0.jpg)](https://www.youtube.com/watch?v=/1-gWeTOcZFc)


<img width="2000" height="1498" alt="1782315349131" src="https://github.com/user-attachments/assets/4684d749-29ab-48f9-9aee-6ad04a2d3a67" />
