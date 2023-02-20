# Codartis Diagram Tool Help

Codartis Diagram Tool is a Visual Studio extension that creates interactive diagrams from C# types and members. The diagram can be used to explore code structure and relationships, navigate between code files and export diagram images to be used in documentation.

- [Getting started](#getting-started)
  - [Installing](#installing)
  - [Supported Visual Studio versions](#supported-visual-studio-versions)
  - [Activating the product or starting a trial period](#activating-the-product-or-starting-a-trial-period)
  - [Adding items to diagram from source code](#adding-items-to-diagram-from-source-code)
  - [Adding items to diagram from Solution Explorer](#adding-items-to-diagram-from-solution-explorer)
- [Details](#details)
  - [Controls at a glance](#controls-at-a-glance)
  - [Saving and loading diagrams](#saving-and-loading-diagrams)
  - [Pan and zoom](#pan-and-zoom)
  - [Selecting diagram items](#selecting-diagram-items)
  - [Context menu](#context-menu)
  - [Automatic layout and manual adjustments](#automatic-layout-and-manual-adjustments)
  - [Jumping from diagram to source code](#jumping-from-diagram-to-source-code)
  - [Diagram notation](#diagram-notation)
  - [Updating the diagram from source code](#updating-the-diagram-from-source-code)
  - [Monitoring and canceling background tasks](#monitoring-and-canceling-background-tasks)
- [Troubleshooting](#troubleshooting)
  - [Logging](#logging)
  - [How to set a system environment variable](#how-to-set-a-system-environment-variable)
  - [Codartis Diagram Tool is installed but unavailable](#codartis-diagram-tool-is-installed-but-unavailable)
  - [Double-clicking the VSIX file: "The requested operation requires elevation"](#double-clicking-the-vsix-file-the-requested-operation-requires-elevation)
  - [Diagram update progress gets stuck for a long time without progress](#diagram-update-progress-gets-stuck-for-a-long-time-without-progress)

## Getting started

### Installing
* Download Codartis Diagram Tool as a Visual Studio Extension package (VSIX file) and install it:
  * Download from Visual Studio Marketplace: 
    * [VS 2019 version](https://marketplace.visualstudio.com/items?itemName=FerencVizkeleti.QuickDiagramToolforC)
    * [VS 2022 version](https://marketplace.visualstudio.com/items?itemName=FerencVizkeleti.diagramtool-vs2022)
  * Double-click the downloaded VSIX file and follow the installer's instructions.
  * If getting a permission error then check out the [Troubleshooting](#troubleshooting) section or install from Visual Studio (see below).

Or

* Install Codartis Diagram Tool from within Visual Studio:
  * Go to Main menu > Extensions > Manage Extensions
  * Choose Online and type "Codartis" in the search box 
  * Click Download
  * Codartis Diagram Tool will be installed when you restart Visual Studio.

> You can find older releases [here](https://codartis.com/diagram-tool/releases.html).

### Supported Visual Studio versions
* **Visual Studio 2019**
  * Minimum required version: **16.11+**
* **Visual Studio 2022** 
  * Minimum required version: **17.2+**

> All Visual Studio editions are supported: Community/Professional/Enterprise

### Activating the product or starting a trial period
Make sure that a solution is open otherwise Codartis Diagram Tool may not be available despite being installed. Check the [Troubleshooting](#troubleshooting) section for more details.
 
* Open the Codartis Diagram Tool window 
  * Visual Studio main menu > View > Other Windows > Codartis Diagram Tool
  * Or use the keyboard shortcut: **CTRL+SHIFT+D, CTRL+SHIFT+D** (yes, push the key combination twice)

<div align="center"><img src="images/AboutPanel2.png" alt="About Panel"></div>

* In the About Codartis Diagram Tool panel:
  * If you already have a license key, then click the **Activate** button.
  * If you don't have a license key then start a 30-day trial period by clicking the **Start trial** button.

> To purchase a license key visit: [codartis.com](https://codartis.com/index.html#pricing)

### Adding items to diagram from source code
* In the source code editor window right-click on a type or member symbol
  * In the context menu click **Add to Codartis Diagram** or **Add to Codartis Diagram With Hierarchy**

<div align="center"><img src="images/AddToDiagramFromSourceCode.png" alt="Add to Diagram from source code"></div>

* Or position the caret on the name of a type or member and use the keyboard shortcuts:
  * Adding an item: **CTRL+SHIFT+D, CTRL+SHIFT+A** 
  * Adding an entire type hierarchy: **CTRL+SHIFT+D, CTRL+SHIFT+H** 

### Adding items to diagram from Solution Explorer
* In the Solution Explorer window right-click on a file or folder
  * In the context menu click **Add to Codartis Diagram**

<div align="center"><img src="images/AddToDiagramFromSolutionExplorer.png" alt="Add to Diagram from Solution Explorer"></div>

> Tip: Don't add too many items (eg. whole projects) to a diagram because it will be cluttered and sluggish. About 50 items is a practical limit for both layout speed and comprehension.

## Details

### Controls at a glance

<div align="center"><img src="images/CodartisToolWindowWithHelpTextSmall.png" alt="Codartis Diagram Tool window with help text"></div>

### Saving and loading diagrams
* Use the Load Diagram and Save Diagram buttons on the toolbar of the diagram tool window.
* To save the diagram with a different file name, click the dropdown button next to the save toolbar button, and choose "Save Diagram As...".

<div align="center"><img src="images/SaveLoadButtonsOnToolbar.png" alt="Codartis Diagram Tool window with help text"></div>

* Diagrams are saved into text files, in JSON format, to make it easy to store them in source control systems.
* The default file extension is ".codartis", but it can be anything.
* After loading a diagram, the tool automatically tries to link all diagram items to their corresponding source code symbols in the current solution.
  * Those diagram items that are not found in the current solution (e.g. because they were deleted or renamed) will be marked with a broken link icon.
  * You can remove all unlinked items from the diagram with the "broom" toolbar button. 

Limitations:
* At the moment, only one diagram can be open at a time. 
* Diagram save and load functionality is not integrated with Visual Studio's file handling commands (New/Open/Save) and saved documents don't show up in and cannot be opened from Solution Explorer. 
* You have to use the "Load Diagram" and "Save Diagram" buttons on the Codartis Diagram Tool window's toolbar. 
* If you would like to use multiple diagrams, integrated with Visual Studio's document concept, then please comment/vote on this discussion: [Handling multiple diagrams as Visual Studio documents](https://github.com/Codartis/DiagramTool/discussions/9)

### Pan and zoom
* Use the mouse: 
  * Pan by holding down the left mouse button.
  * Zoom with the mouse wheel.
* Or use the keyboard (only if the diagram window has the focus): 
  * Pan with the cursor keys.
  * Zoom with W and S keys (FPS shooter-style :)
* Or use the pan and zoom control on the diagram.

### Selecting diagram items
* Click a diagram node to select/unselect
* CTRL+Click or SHIFT+Click: add/remove node to/from selection
* CTRL+Drag: select multiple nodes
* SHIFT+Drag: add nodes to selection

### Context menu
Use the context menu to access the following commands:
* Select All Nodes (shortcut: CTRL+A)
* Invert Selection
* Pin Nodes (Selected/All)
* Unpin Nodes (Selected/All)
* Remove Nodes (Selected/All But Selected/This Node/All But This Node)

### Automatic layout and manual adjustments
Codartis Diagram Tool tries to automatically create a layout that is both clear and meaningful. As the diagram changes the layout is continuously adapted.

However, you can manually adjust the layout by moving (dragging) nodes and by pinning/unpinning nodes.
* To move a node drag it using the left mouse button.
* Moved nodes become pinned automatically (so they don't try to move back to wherever they want).
* To pin/unpin a node click its "pin" button, or use the Context Menu to pin/unpin all nodes, or all selected nodes.

The automatic layout follows these rules:
* Nodes must not overlap.
* Inheritance and implementation hierarchies are arranged "top-down", that is, the more abstract types are above the more concrete ones. 
* Siblings in inheritance hierarchies are ordered by name from left to right.
* Pinned nodes are moved only to avoid overlaps.

### Jumping from diagram to source code
* Double-click on a diagram item.
* It works only for those types that were found in the source code (and not in metadata).

### Diagram notation
Codartis Diagram Tool uses a subset of the standard UML class diagram notation with additional visual hints that are familiar for Visual Studio users (eg. icons for class, struct, etc.)

| Class | Interface | Struct | Enum | Delegate |
|-------|-----------|--------|------|----------|
| ![class](images/SampleClass.png) | ![interface](images/SampleInterface.png) | ![stuct](images/SampleStruct.png) | ![enum](images/SampleEnum.png) | ![delegate](images/SampleDelegate.png) |

Additional details:
* Meaning of the different type name formattings:
  * *Italic* means abstract type.
  * **Bold** means that it was found in source code.
  * Normal (non-bold) means that it was found in metadata (referenced assembly).

| Association | Inheritance | Interface implementation  | Other dependencies |
|------------|--------------------------|-------------|--------------------|
| ![association](images/AssociationArrow.png) | ![inheritance](images/InheritanceArrow.png) | ![interface implementation](images/ImplementationArrow.png)  | ![dependency](images/DependencyArrow.png) | 


Additional details:
* The arrow heads always point in the direction of the dependency.
  * That is, A -> B means A depends on B.
* Fields and properties imply associations from the type that contains the field/property to the type of the field/property.
* Assocations can have a label at the "to" side of the relationship that can contain names and multiplicity markers.
  * The name of the label is the name of the field/property that represents the association in the source code, if it differs from the type of the field/property.
  * If there are multiple assocations to the same type then they are listed as multiple labels. In case of more then 2 labels a "..." symbol is displayed and the whole list can be displayed as a tooltip when pointing at the "..." sign.
<div align="center"><img src="images/AssocationLabelTooltip.png" alt="Assocation label tooltip"></div>

* Assocation multiplicities are indicated as one of the following markers.
    * '0..1' means an optional association (a nullable type in source code).
    * '\*' means "many" (a collection in source code).
    * '[key]' means a dictionary with the given key type.
    * No multiplicity marker means a multiplicity of '1'.
* In the case of "other dependencies", the type of the dependency is indicated with a UML stereotype.
  * E.g.&lt;&lt;typeDefinition&gt;&gt;
* For relationships between a constructed generic type and it type definition, the type arguments are indicated as labels at the "to" side of the dependency arrow.
<div align="center"><img src="images/TypeDefinitionRelationship.png" alt="Type definition relationship"></div>

### Updating the diagram from source code
If the source code changes you can update the diagram from the current source code.
* You can update a single item (and its relationships) by clicking the item's update button.
* Or you can update the whole diagram by using the Update button on the Codartis Diagram Tool window toolbar.

> When working with large solutions prefer updating only single items, because updating a whole diagram might take a long time. Even if there are not many items on the diagram, all of their relationships must be searched in the whole solution, that's why the speed of this operation is determined mainly by the solution size.

Diagram item update is based on their fully qualified name (type name + namespace name).
* If a diagram item is found in source code then its relationships and members are updated.
* If a diagram item is not found in source code then it is marked with a broken link icon.
* You can remove unlinked items from the diagram either one-by-one, or all at once with the "broom" toolbar button.

> Unfortunately this feature can't track symbol rename operations so renamed items will not be found, thus they will be marked as unlinked.

### Monitoring and canceling background tasks
Codartis Diagram Tool builds its code model by querying Visual Studio's C# parser. These queries can take a while, especially right after opening a solution when Visual Studio is still busy parsing the entire source code.

To keep the diagram tool responsive these queries are performed as background tasks. The diagram tool's status bar displays the number and progress of currently running background tasks.

<div align="center"><img src="images/BackgroundTaskStatus.png" alt="Displaying background task status"></div>

You can cancel the background tasks by right-clicking on the spinning circle icon on the left side of the status bar and clicking Cancel All Tasks.

<div align="center"><img src="images/CancelAllTasks.png" alt="Canceling background tasks"></div>

## Troubleshooting

### Logging
In order to turn on logging, follow these steps.
> You will need Administrator rights to complete these steps.

> There's a step by step guide below about [How to set a system environment variable](#how-to-set-a-system-environment-variable)

1. Create a folder for the log files, e.g. C:\Temp\CodartisLogs
2. Define a system environment variable called: "CodartisLogFolder". Set its value to the full path of the log folder that you created.
  <div align="center"><img src="images/LogFolderEnvironmentVariable.png" alt="Log folder environment variable"></div>
  


3. Restart Visual Studio so that it picks up the new environment variable.
4. Check the log folder. The log files will be named like this: "qd-&lt;processid&gt;.log"

To turn off logging, delete the "CodartisLogFolder" environment variable.
> Don't forget to turn off logging if you don't need it any more to preserve disk space. 

### How to set a system environment variable

1. Start a command prompt with Administrator rights.
   * Click the Windows Start Menu and type: `cmd`
   * Right-click the "Command Prompt" item and choose "Run as administrator"
   <div align="center"><img src="images/StartCommandPrompt.png" alt="Start Command Prompt"></div>

2. In the Command Prompt window execute this command:
  
   `rundll32.exe sysdm.cpl,EditEnvironmentVariables`

3. The "Environment Variable" window appears. 
   * You can find the "System variables" at the bottom half of the window.
   * Click "New" to create a variable, or click "Edit" to modify an existing one.
   <div align="center"><img src="images/EnvironmentVariablesWindow.png" alt="Start Command Prompt"></div>

4. In both the "New" and the "Edit" cases you have the fill in the "Variable name" and the "Variable value" fields.
   <div align="center"><img src="images/EditSystemVariableWindow.png" alt="Start Command Prompt"></div>

5. Click OK to close the "New System Variable" or "Edit System Variable" window.
6. Then also click OK to close the "Environment Variables" window in order for the changes to take effect.

### Codartis Diagram Tool is installed but unavailable
Symptoms
* Codartis Diagram Tool's menu items don't show up in Visual Studio  Main menu > View > Other Windows and in context menus.
* When you try to activate Codartis Diagram Tool with the keyboard shortcut, Visual Studio displays the following message in the status bar: 
  > The key combination (Ctrl+Shift+D, Ctrl+Shift+D) is bound to command (Codartis Diagram Tool) which is not currently available.

Cause
* Codartis Diagram Tool uses the C# parser's model that is created by Visual Studio for the current solution. If there's no open solution then Codartis Diagram Tool doesn't get loaded by Visual Studio.

Solution
* Open a solution in Visual Studio.
* If Codartis Diagram Tool is still unavailable then wait a few moments until Visual Studio finishes loading it.

### Double-clicking the VSIX file: "The requested operation requires elevation"
Details
* When trying to install the tool by downloading the VSIX file and double-clicking it, the above error message is displayed.

Solution
* Right-click the VSIX file > Open with... > Choose "Microsoft Visual Studio Version Selector" from the list (might need to click "More apps" to find the item in the list).
* When prompted: "Do you want to allow this app to make changes to your device?" > Click "Yes"

### Diagram update progress gets stuck for a long time without progress
Symptoms
* Task Manager > Details shows that a process called ServiceHub.RoslynCodeAnalysisService.exe consumes low CPU but a large (and continously increasing) thread count.

Cause
* This may indicate that Codartis Diagram Tool and Visual Studio's CodeLens feature interfere with each other.

Solution
* Turn off CodeLens: 
  * Visual Studio main menu > Tools > Options > Text Editor > All Languages > CodeLens > Clear the "Enable CodeLens" checkbox
  <div align="center"><img src="images/DisableCodeLens.png" alt="Disable CodeLens"></div>
* Restart Visual Studio.