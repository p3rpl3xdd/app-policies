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
