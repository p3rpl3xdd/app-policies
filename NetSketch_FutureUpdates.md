In the next versions of NetSketch, I am planning to add Export to SVG functionality to allow the diagrams to be imported into Visio in 2 different ways:

**Method 1: Direct Import (Windows Desktop)**

1. Export from NetSketch → Choose SVG
2. Save .svg file to device
3. Open Microsoft Visio (Windows)
4. File → Open → Select SVG file
5. Visio imports and displays diagram

**Method 2: Insert into Existing Document**

1. Export from NetSketch → Choose SVG
2. Open existing Visio document
3. Insert → Pictures → Select SVG file
4. Diagram appears as editable object

## Visio Limitations When Importing SVG

Based on research, here are the some possible limitations:

### 1. **Visio Web Does Not Support SVG Import** 

SVG import is only supported in Visio desktop app on Windows

**Impact:**

- Users MUST have Visio Desktop (Windows)
- Mac users need Windows VM or Parallels
- Visio for Web users cannot import SVG

### 2. **Shapes Become Groups** 

When importing SVG, shapes are imported as grouped objects

**Impact:**

- Shapes are not "native" Visio shapes
- To edit: Select All → Right-click → Ungroup
- After ungrouping, elements are individually editable

**User Process:**

1. Import SVG
2. See entire diagram as one group
3. Ungroup once (Ctrl+Shift+G)
4. All elements now individually selectable

### 3. **No Automatic Connection Intelligence** 

**Impact:**

- Lines imported as paths, not Visio "connectors"
- Lines won't automatically re-route if shapes are moved
- Users must manually convert to Visio connectors if they want dynamic behavior
- 
**Workaround in Visio:**

1. Delete imported connection line
2. Use Visio's Connector tool
3. Reconnect shapes with native Visio connectors

### 4. **Limited Shape Data** 

**Impact:**

- Custom properties/metadata won't transfer
- Shapes have visual appearance only
- No connection to Visio shape databases

**Depending on how well the app does, I may look into mapping Visio's format directly as an export. This is a considerable amount of work due to the undelying xml formatting to export it to VSDX.**
