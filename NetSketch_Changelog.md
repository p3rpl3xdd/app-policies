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

# NetSketch — What's New

---

## Version 2.0

*Released June 2026*

---

### Multi-Selection & Group Operations

**Rubber-band selection**
Draw a selection rectangle across the canvas by dragging on empty space. Any shapes and connections inside the box are selected together — no need to tap each device individually.

**Group drag**
Move multiple selected shapes at once. Everything in the selection travels together, preserving relative positions.

**⌘-tap multi-select (Magic Keyboard)**
On iPad with a hardware keyboard, hold ⌘ while tapping shapes to add or remove them from the selection individually. Tapping without ⌘ still replaces the selection as before.

---

### Network Zones

**Zones — Visio-style containers**
A new Zone tool lets you draw labelled, coloured regions on the canvas — ideal for representing VLANs, data-centre racks, cloud regions, security perimeters, or any logical grouping. Zones render behind devices with a semi-transparent tinted fill and a dashed border.

**Smart zone drag**
Dragging a zone moves everything inside it automatically. Devices contained in the zone travel with it — no need to select them separately.

**Zone resize handles**
Eight resize handles appear when a single zone is selected, letting you freely resize the region by dragging any corner or edge. The opposite corner stays fixed as you drag.

**Zone labels**
Each zone has a customisable label displayed in the top-left corner. Tap the zone to rename it in the Properties panel.

**Zone snapping**
Zones participate in snap-to-align alongside regular device shapes. Drag one zone near another and they snap to matching edges.

---

### Arrangement Tools

**Make Row / Make Column**
Select multiple shapes and use the Properties panel to instantly arrange them in a clean row or column. Shapes are evenly spaced and aligned on a shared axis.

**Spacing slider**
After arranging in a row or column, a spacing slider appears in the Properties panel. Drag it to increase or decrease the gap between shapes in real time.

---

### Connection Styles

**Solid, Dashed, and Dotted lines**
Connections now support three line styles — solid, dashed, and dotted. Choose the style before drawing using the picker in the connection toolbar, or change an existing connection's style in the Properties panel.

This follows standard network diagramming convention: solid for physical links, dashed for logical or virtual links, dotted for management paths.

**Styles in all export formats**
Connection styles are fully preserved in PNG, PDF, and SVG exports.

---

### Inline Label Editing

**Double-tap to rename a device**
Double-tap any network device shape — router, switch, firewall, server, cloud, laptop, desktop, access point, printer, or multi-port switch — to edit its name inline. A text field appears directly below the icon, pre-filled with the current name. Press Return or tap the canvas to confirm.

**Double-tap to label a connection**
Double-tap any connection line, or an existing connection label, to edit it inline. The text field appears at the midpoint of the line. Previously this required opening the Properties panel and scrolling to the label field.

---

### Canvas & Toolbar Improvements

**Label visibility toggle**
A new toolbar button hides or shows device name labels across the entire canvas. Useful for cleaning up complex diagrams for screenshots or presentations. Zone labels, text boxes, and connection labels are always visible — only the device icon labels are affected.

**Full keyboard shortcut support**
Hardware keyboard shortcuts are now available for all tools:

| Shortcut | Action |
|---|---|
| `⌘V` | Select tool |
| `⌘D` | Duplicate selection |
| `⌘Z` | Undo |
| `⌘⇧Z` | Redo |
| `⌘+` / `⌘−` | Zoom in / out |
| `⌘0` | Reset zoom |
| `⌘S` | Save |
| `⌘?` | Help |
| `R` | Router tool |
| `S` | Switch tool |
| `F` | Firewall tool |
| `C` | Connection tool |
| `D` | Draw tool |
| `T` | Text Box tool |
| `Z` | Zone tool |

---

### SVG Export Improvements

**Proper shape icons in SVG**
SVG exports now include proper vector icons for each device type — router, switch, firewall, server, cloud, laptop, desktop, access point, printer, and internet. The previous export used Unicode emoji characters that rendered inconsistently across platforms and did not display in Visio. Each device now exports a clean SVG path icon in the shape's colour.

---

### Connection Routing Improvements

**Smarter routing around obstacles**
Connections now route around every shape on the canvas, not just the two shapes they connect. On dense diagrams, lines that previously cut through unrelated devices will now detour around them.

**Better fallback paths**
When the standard routing options are blocked, the router now tries a wider detour path before falling back to a direct line. This reduces the number of connections that cross shape bodies on complex diagrams.

**Consistent routing in exports**
PNG, PDF, and SVG exports now use the same fully shape-aware routing as the canvas. Previously, exports used a simpler routing path that ignored shape positions.

---

### Bug Fixes

- Fixed the Properties panel not responding to taps on iPad — color picker, delete button, and all other controls now work correctly
- Fixed connection style changes not rendering on canvas — lines now immediately update to the selected style
- Fixed the Arrange controls displacing device positions when zones were included in a rubber-band selection — Arrange and Spacing controls are now disabled when a zone is part of the selection
- Fixed rubber-band selection not working when starting a drag inside a zone's filled area
- Fixed Make Row / Make Column incorrectly including zones in the arrangement calculation

---

## Version 2.1 — What's New

### Path Simulation

**Simulate a route between any two devices**
Tap the new Simulate button in the toolbar to enter Simulation Mode. Tap any source device, then any destination device — NetSketch finds the shortest path through the diagram's connection graph and highlights it with an animated flowing stroke.

**Animated route highlight**
Each connection on the traced path is overlaid with an animated dashed accent-coloured stroke so the route is unmistakable at a glance. Hop devices pulse with a ring to draw the eye along the path.

**Hop-by-hop result panel**
A result panel slides into the right sidebar showing the full ordered hop list — device icon, name, and type for every step — plus the total hop count. Source and destination are clearly tagged SRC and DST.

**No-path detection**
If the two devices are not connected through the diagram, the panel shows a clear "No path found" message along with the names of both devices.

**Non-intrusive activation**
Simulation Mode is activated exclusively via the toolbar button — it is not a drawing tool and cannot be triggered accidentally while placing shapes or drawing connections. The shape palette dims while the mode is active to make the boundary clear. Tap Exit (or the toolbar button again) to return to normal drawing instantly.

## Version 2.2 — What's New

### Path Simulation — Advanced Analysis

**Connection labels in the hop list**
When connections in your diagram have labels (such as interface identifiers or link descriptions), those labels now appear as a small pill between the corresponding hop entries in the Simulation result panel. At a glance you can read the full trace: device → interface → device → interface → destination — exactly like a real `traceroute` output, without any extra steps.

**"What if this link fails?" re-routing**
Each connection in the hop list now has a small fail toggle. Tap it to mark that link as down — NetSketch immediately re-runs the path search excluding the failed link and shows the fallback route. Excluded links are highlighted in red on the canvas with a strikethrough label, so the topology change is visible while you work. Tap the toggle again to restore the link. Use this to validate redundancy before a maintenance window or to trace what reroutes when an outage occurs.

**Multiple path discovery**
NetSketch now finds up to five distinct paths between the source and destination and presents them as a colour-coded picker at the top of the result panel. The shortest path is always Path 1 (accent colour). Additional paths use orange, purple, teal, and pink overlays. All paths are drawn on the canvas simultaneously — the selected path is shown at full brightness with the animated flowing stroke, while the others appear as thin muted strokes so you can compare routes without losing context. Switch between paths instantly with the picker.

**Step-through hop animation**
A Step Through button in the result panel header activates a presentation mode. Back and Step controls reveal the trace one hop at a time: each Step highlights the next device and the link leading to it, with a bright pulse ring on the frontier node. Previously visited hops stay visible but dim slightly. Use step-through in team walkthroughs, training sessions, or any time you need to walk a stakeholder through exactly where traffic flows — or where it stopped.

---

### Performance & Reliability

- Simulation state is now managed by a dedicated `SimulationViewModel` — reduces re-evaluation overhead when simulation properties change during path analysis.
- Shape and connection lookups now use dictionary indices instead of linear scans, improving responsiveness on large diagrams.

---

### Bug Fixes

- Fixed an issue where you could not select connector lines inside of a zone. This was due to the zone object becoming a top layer object.

*NetSketch is built for network engineers and IT professionals on iPad.*

**Contact:** netsketch.prowess710@passmail.net

