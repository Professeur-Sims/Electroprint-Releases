# Electroprint-Releases
Electroprint is a software designed to merge 3D files with EDA (Kicad) netlists to 3D print objects with integrated electronics

The code will be open source before the end auf August 2026

## Changelog (v1.2.0):
- You can now export 3mf who can be opened as a project in Prusaslicer. The pause(s) (M601) are already included in the project to allow inclusion of your electronic components. (**3mf export can take up to 1 minute and can cause a temporary freeze of the app**)
- 3mf exports now create forms who don't trigger an alert for non closed geometry in Prusaslicer.
- 3mf exports include special instructions for high (default 8) number of perimeters for conductive elements. It avoid the risk of hollow conductive tracks who would be underperforming.
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
- The "Orient face" button allows you to choose a face to orient towards the build plate.
- "Select footprint folder" allows you to locate the KiCad footprints folder. This enables the software to associate the footprints found in the imported netlist. 
Currently, you can still assign individually a footprint after the component generation. You will just get an alert if the footprint don't exist in the standard library.
- After clicking the routing button, you must click on the starting pad.
While routing, the 'B' key switches to vertical routing mode. Clicking while in vertical routing mode confirms the vertical path and automatically switches back to horizontal routing.
While in vertical routing mode, pressing the 'N' key snaps the cursor to the nearest net pad.

- The right-hand section (in component selection mode) allows you to modify: footprint name, footprint type, footprint file path, and the size of the rectangular block (used to cut the shape out of the main body for "print-in-place" functionality)...
- Tracks can be dragged.
- Track dimensions can be modified (currently the entire track at once).
- You can obtain an estimate of a track's equivalent resistance.

<img width="938" height="560" alt="Interface_v1-2-0" src="https://github.com/user-attachments/assets/93705297-2f6b-4203-aaea-f0d20dd7b7a4" />
<img width="955" height="524" alt="result_exp_proj_prusaslicer" src="https://github.com/user-attachments/assets/f316d2b1-5c3d-4b6d-872c-63a867428e3f" />



## Video tutorial and demo (start at 4:25):
[[https://youtu.be/1-gWeTOcZFc](https://www.youtube.com/watch?v=1-gWeTOcZFc)](https://www.youtube.com/watch?v=1-gWeTOcZFc)
[![Video on Youtube](https://img.youtube.com/vi/1-gWeTOcZFc/0.jpg)](https://www.youtube.com/watch?v=/1-gWeTOcZFc)


<img width="2000" height="1498" alt="1782315349131" src="https://github.com/user-attachments/assets/4684d749-29ab-48f9-9aee-6ad04a2d3a67" />
