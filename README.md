# Electroprint-Releases
Electroprint is a software designed to merge 3D files with EDA (Kicad) netlists to 3D print objects with integrated electronics

## Operation:
(Perform in this order)
- The "Import STEP" button allows you to import a .step file (no shit, Sherlock).
- The "Import netlist" button allows you to select a KiCad netlist (preferably version 8.0 or 9.0; earlier versions have not been tested).
- The "Orient face" button allows you to choose a face to orient towards the build plate.
- "Select footprint folder" allows you to locate the KiCad footprints folder. This enables the software to associate the footprints found in the imported netlist. 
Currently, it is not possible to associate footprints individually, so footprints not available in the standard library cannot be used.
- After clicking the routing button, you must click on the starting pad.
While routing, the 'B' key switches to vertical routing mode. Clicking while in vertical routing mode confirms the vertical path and automatically switches back to horizontal routing.
While in vertical routing mode, pressing the 'N' key snaps the cursor to the nearest net pad.

- The right-hand section (in component selection mode) allows you to modify: footprint name, footprint type, footprint file path, and the size of the rectangular block (used to cut the shape out of the main body for "print-in-place" functionality)...
- Tracks can be dragged.
- Track dimensions can be modified (currently the entire track at once).
- You can obtain an estimate of a track's equivalent resistance.


<img width="938" height="853" alt="Capture d&#39;écran 2026-06-25 131815" src="https://github.com/user-attachments/assets/7d021a39-6e53-4755-b274-91f9de8cea88" />
