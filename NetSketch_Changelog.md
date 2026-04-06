### Version 1.2

Bug Fixes

**Issue:** Text in text boxes was not appearing in exported PNG, PDF, or SVG files, even though it displayed correctly in the app on non-iPad Pro devices.

**Root Cause:** The `ImageRenderer` used for exporting shapes was not properly rendering text due to:

1. Problematic `.fixedSize()` modifier on text
2. Missing explicit background for `ImageRenderer`
3. No opacity configuration for text boxes

**Issue:** Export window does not automatically close after sharing/exporting.

**Fix:** Added an onDisappear to the export function to detect when the user finishes sharing/exporting the file.

Changes

Added export to SVG to start testing with Microsoft Visio importing.


### Version 1.3

- Added Draw tool as an alternative to the standard connection line too for better integration of Apple Pencil.
- Refined and simplified the orthogonal routing algorithm to prevent lines going thru objects.
- Restructured network shapes and labels to optimize line connectors and sizing issues in relation to connecting lines. Removed all padding from network shapes.
- Adding connector line labels
- Adding 3 new icons - AP, Printer, Internet (alternate cloud symbol)
- Undo/Redo functionality

### Version 1.4

**Fix:** Text and text boxes was not formatted correctly when exporting diagrams.
**Fix:** Autosaving was not correctly triggering on document close. A 5 second autosave was added in addition to a Save button in the top function bar. Like most software, always make sure to save before exiting the application.
