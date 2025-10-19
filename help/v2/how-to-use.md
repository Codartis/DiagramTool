# Codartis Diagram Tool - Using the Diagram Tool

Learn how to use the features of the Codartis Diagram Tool to visualize and explore your code.

---

**Help Topics**
* [Getting Started](getting-started.md)
* Using the Diagram Tool
* [Diagram Elements and Notation](diagram-notation.md)
* [Troubleshooting](troubleshooting.md)

---

**Page Overview**
- [Controls at a Glance](#controls-at-a-glance)
- [Saving and Loading Diagrams](#saving-and-loading-diagrams)
  - [Opening and Saving](#opening-and-saving)
  - [File Format](#file-format)
  - [Reconnecting Items on Load](#reconnecting-items-on-load)
- [Navigating and Viewing the Diagram](#navigating-and-viewing-the-diagram)
  - [Pan](#pan)
  - [Zoom](#zoom)
- [Adding and Removing Diagram Items](#adding-and-removing-diagram-items)
  - [Adding Diagram Items from the Source Code Editor](#adding-diagram-items-from-the-source-code-editor)
  - [Adding Diagram Items from Solution Explorer](#adding-diagram-items-from-solution-explorer)
  - [Adding Related Nodes](#adding-related-nodes)
  - [Adding Notes](#adding-notes)
  - [Removing Items](#removing-items)
- [Undo and Redo](#undo-and-redo)
- [Selecting and Arranging Diagram Items](#selecting-and-arranging-diagram-items)
  - [Automatic Layout and Manual Adjustments](#automatic-layout-and-manual-adjustments)
  - [Selecting Items](#selecting-items)
  - [Dragging Nodes](#dragging-nodes)
  - [Resizing Nodes](#resizing-nodes)
  - [Pinning Nodes](#pinning-nodes)
  - [Opening and Closing the Member Lists](#opening-and-closing-the-member-lists)
  - [Changing Member Order](#changing-member-order)
  - [Showing or Hiding Type Comments](#showing-or-hiding-type-comments)
  - [Customizing Connector Routes](#customizing-connector-routes)
  - [Customizing Label Positions and Sizes](#customizing-label-positions-and-sizes)
  - [Changing Node Colors](#changing-node-colors)
  - [Changing Item Z-Order](#changing-item-z-order)
  - [Aligning and Distributing Nodes](#aligning-and-distributing-nodes)
    - [Aligning Nodes to Each Other](#aligning-nodes-to-each-other)
    - [Aligning Nodes to a Grid](#aligning-nodes-to-a-grid)
    - [Distributing Nodes Evenly](#distributing-nodes-evenly)
    - [Setting Nodes to Matching Sizes](#setting-nodes-to-matching-sizes)
- [Integrating with Source Code](#integrating-with-source-code)
  - [Jumping from Diagram to Source Code](#jumping-from-diagram-to-source-code)
  - [Updating the Diagram from Source Code](#updating-the-diagram-from-source-code)
- [Exporting a Diagram as an Image](#exporting-a-diagram-as-an-image)
- [Diagram Options](#diagram-options)
- [Monitoring and Canceling Background Tasks](#monitoring-and-canceling-background-tasks)

---

## Controls at a Glance

You can access diagram features from the toolbar, the context menu, or from buttons that appear on diagram items when you hover over them.

<div align="center"><img src="images/ControlsAtAGlance.png" alt="Codartis Diagram Tool window with help text"></div>

## Saving and Loading Diagrams

Diagram saving and loading are integrated with Visual Studio. Diagram files (`*.codartis`) behave like regular project files.

### Opening and Saving
* **Open**: Use **Solution Explorer** or **File → Open → File...**
* **Save**: Use Visual Studio's standard toolbar buttons, or **File → Save / Save As / Save All**, or press **Ctrl+S**
* **Create new:** In Solution Explorer, right-click a project and choose **Add → New Item → Codartis Diagram**

**Note**: The **Codartis Diagram** file type appears in the **Add New Item** dialog only when adding items to a **C# project**. You can work around this limitation by:
* Adding the new diagram to a **C# project**, then moving it to the desired location in **Solution Explorer**.
* Creating an **empty text file** and **renaming its extension** to `.codartis` — it will be recognized as a Codartis Diagram file.

### File Format
Diagrams are saved as **text files in JSON format**, making them easy to include in source control systems.

### Reconnecting Items on Load
When a diagram is loaded, the tool automatically tries to reconnect each item to its corresponding symbol in the current solution.
* Items that no longer exist (e.g. deleted or renamed) appear with a **broken link** icon.
* Use the **broom** toolbar button to remove all unlinked items.

## Navigating and Viewing the Diagram

### Pan
* **Mouse**: Hold the **left button** on the background and drag.
* **Keyboard**: Use the **arrow keys** (when the diagram window has focus).
* Or use the **Pan and Zoom control**.

### Zoom
* **Mouse**: Scroll the **mouse wheel**.
* **Keyboard**: Press the **+ or – keys** (when the diagram window has focus).
* Or use the **Pan and Zoom control**.

## Adding and Removing Diagram Items

### Adding Diagram Items from the Source Code Editor

In a source code editor window:

* **Context Menu**: 
  * Right-click a type or member name and select one of:
    * **Add to Codartis Diagram**
    * **Add to Codartis Diagram With Hierarchy**
* **Keyboard Shortcuts**:
  * Add an item: **Ctrl+Shift+D, Ctrl+Shift+A**
  * Add a hierarchy: **Ctrl+Shift+D, Ctrl+Shift+H**

### Adding Diagram Items from Solution Explorer

* Context Menu:
  * Right-click a file, folder, project, solution folder, or solution node and select **Add to Codartis Diagram**.

* Drag-and-Drop:
  * Drag items from Solution Explorer into the diagram.
    * **C# file (.cs)**: adds the namespaces and types.
    * **Folder**: adds all C# files in the folder.
    * **Project**: adds the project’s output assembly.
    * **Solution Folder**: adds all projects in that folder.

> **Note:** The solution node cannot be dragged, but can be added via the context menu.

> **Tip**: Avoid adding too many items at once (e.g., entire projects), as diagrams may become cluttered or slow. Around 50 items is a practical limit.

### Adding Related Nodes

* **Context Menu**: Right-click a node → **Add Related Items.**
* **Buttons on Node**: Hover over a node to reveal Related Items buttons.
  * Select from a list of related items.
  * **Double-click** the button to add **all** related items.

> **Note**: Buttons with no related items are disabled.

> **Tip**: Nodes with related items display small dots (related item cues).  

### Adding Notes
* **Add a note to a node**: Right-click a node and choose **Add Note**.
* **Edit a note’s text**: Select the note, then click inside to edit.
* **Link an existing note**: Select both the note and node → right-click node → **Add Note**.

> **Tip**: To keep a note unlinked, delete its connector (select it and press **Delete**).

### Removing Items
* Click the **Close** button on a node to remove it.
* Click the **Clear** button on the toolbar to remove all items.
* Right-click → **Remove Item**
* Or press **Delete / Backspace**.

> **Note**: Connectors have no Close button — select them and press **Delete or Backspace**.

## Undo and Redo
* Use the **Undo / Redo** toolbar buttons, or press **Ctrl+Z / Ctrl+Y.**
* Undo and Redo automatically disable Auto Layout, so the layout remains unchanged when reverting.

> **Note:** Undo/Redo is not linked to Visual Studio’s global Undo/Redo. Use the **diagram window’s toolbar** or **keyboard shortcuts**, with focus on the diagram.

> **Tip:** Some operations — such as undoing large layout changes — may take noticeable time. Interaction is temporarily disabled during these operations.

> **Tip:** If undoing an Auto Layout seems to do nothing, keep pressing Undo — the change may have been minor.

## Selecting and Arranging Diagram Items

### Automatic Layout and Manual Adjustments
The diagram automatically arranges nodes for clarity. The layout updates dynamically as the diagram changes.

You can toggle automatic layout anytime using the **Auto Layout** toolbar button.

Manual adjustments:
* Drag or resize nodes — they automatically become **pinned**.
* Pinned nodes remain fixed during layout.
* You can unpin nodes or change auto-pinning behavior in **Options**.

Layout rules:
* Nodes never overlap.
* Inheritance and implementation hierarchies are arranged **top-down**.
* Sibling nodes are ordered **alphabetically left to right**.
* Assembly references are arranged **top-down**.
* Pinned nodes move only to avoid overlaps.

> Want better auto layout? Suggest improvements here: [Enhance automatic diagram layout](https://github.com/Codartis/DiagramTool/discussions/4)
 
### Selecting Items
* **Click** a node, connector, or label to select/unselect.
* **Ctrl+Click or Shift+Click** adds/removes from selection.
* Drag to select multiple items:
  * **Ctrl+Drag**: select multiple
  * **Shift+Drag**: add to selection
* **Context Menu**: Select All Items (**Ctrl+A**)

> Visual cues:
> * Selected nodes – thicker border
> * Selected connectors – thicker line
> * Selected labels – thin boundary box

### Dragging Nodes
* Drag a single node, or all selected nodes together.

> **Note**: Child nodes cannot be dragged outside their parent’s rectangle.

### Resizing Nodes
* Drag a **corner handle** to resize.
* **Double-click a handle** or use **Reset Size** from the context menu to restore default size.

### Pinning Nodes
Prevent nodes from moving during Auto Layout.
* Click a node’s **Pin** button to toggle its state.
* Toolbar: **Pin All Nodes / Unpin All Nodes**.

### Opening and Closing the Member Lists
* Click the **Show/Hide Members button** to toggle member lists.

> **Note**: Disabled if the node has no members.

### Changing Member Order
* Drag and drop members to reorder.
* Or use **Alt + Up/Down Arrow.**

### Showing or Hiding Type Comments
* Nodes display `<summary>` comments from source code (if available).
* Toggle visibility using the **Show/Hide Type Comments** toolbar button.

### Customizing Connector Routes
Hover over a connector to show route points. You can:
* **Drag points** to change the path.
  * Dragging the **first** or **last** point away from its node adds a new point.
  * Dragging the **next-to-first** or **next-to-last** point into its node removes it.
* **Drag segments** to adjust the path.
* Right-click → **Add Route Point** or **Remove Route Point**.
* Right-click → **Reset Route** to restore defaults.

### Customizing Label Positions and Sizes
* **Move**: Drag a label.
* **Resize**: Drag a corner.
* Reset: Right-click → **Reset Size** or **Reset Position**.

> **Note**: When you drag a label far from its origin, a dashed line appears to indicate its original position.

> **Note**: Selected labels show a border that disappears when deselected.

### Changing Node Colors
* Right-click a node → **Custom Color** to choose a background color.
* Applies to all selected nodes.
* To revert, right-click → **Reset Color**.

### Changing Item Z-Order
Change item stacking order via **Right-click → Z-Order**:
* **To Front** – bring to top
* **To Back** – send to back
* **Bring Forward** – move up one layer
* **Send Backward** – move down one layer

### Aligning and Distributing Nodes

#### Aligning Nodes to Each Other
Select nodes → right-click the one you want to align to → choose:
* **Left / Center / Right** (vertical alignment)
* **Top / Middle / Bottom** (horizontal alignment)

#### Aligning Nodes to a Grid
* Toggle grid visibility: **Options → Show Grid**
* Snap selected nodes: **Right-click → Align → Snap to Grid**
* Snap all movement: **Options → Snap to Grid**

#### Distributing Nodes Evenly
Select three or more nodes → right-click → **Space Evenly → Horizontal / Vertical**

> **Note**: Only nodes at the same hierarchy level (same parent or no parent) can be evenly spaced.

#### Setting Nodes to Matching Sizes
Select nodes → right-click the reference node → **Size →**
* **Make Same Size**
* **Make Same Width**
* **Make Same Height**

## Integrating with Source Code

### Jumping from Diagram to Source Code
* **Double-click** a diagram node to open its source definition.
* Works only for symbols defined in source code (not for metadata).

### Updating the Diagram from Source Code
Keep your diagram in sync with the latest source code:
* Update a **single item** (and its relationships) using its **Update** button.
* Update the **entire diagram** using the **Update** toolbar button.

> **Note:** For large solutions, updating the whole diagram can be slow — prefer updating individual items.

Update rules:
* Items with matching fully qualified names are refreshed.
* Missing items show a **broken link** icon.

Remove all broken items using the **Broom** toolbar button.

> **Note**: Renamed items are treated as new symbols — the tool cannot track renames automatically.

## Exporting a Diagram as an Image

Export the current diagram as a `.PNG` file, use the toolbar buttons:
* **To clipboard**: Use **Export Image to Clipboard**
* **To file**: Use **Export Image to File...**

## Diagram Options

Change settings using the **Options** toolbar button:
* Show or hide grid points
* Snap dragging and resizing to grid
* Automatically pin nodes after moving or resizing
* Show pin icons for pinned items
* Highlight all related nodes or only hovered nodes
* Automatically add connectors when applicable
* Automatically remove redundant connectors

## Monitoring and Canceling Background Tasks
The Codartis Diagram Tool builds its code model by querying Visual Studio’s C# parser.
These background queries can take time, especially right after opening large solutions.

All queries run as **background tasks** to keep the tool responsive.
* The **status bar** displays progress for active tasks.

<div align="center"><img src="images/BackgroundTaskStatus.png" alt="Displaying background task status"></div>

You can cancel background tasks anytime:
* Right-click the **spinning circle icon** on the left side of the status bar → select **Cancel All Tasks**.

<div align="center"><img src="images/CancelAllTasks.png" alt="Canceling background tasks"></div>
