# sap.findbyname

## Syntax

```G1ANT
sap.findbyname name ⟦text⟧ type ⟦text⟧ parent ⟦sapcomponent⟧
```

## Description
Returns the list of all components from current window or from `Parent` children 
with name equal to value of parameter `Name` and type equal to value of parameter `Type`.

## Arguments

| Argument         | Type                                                              | Required | Default Value   | Description                                                  |
| ---------------- | ----------------------------------------------------------------- | -------- | --------------- | ------------------------------------------------------------ |
| `parent`        | [sapcomponent](../../../Structures/SapComponentStructure.md)      | no       |               | Optional component which is one of parents of components to be found. This parameter must contain SAPComponent that is a container. |
| `name`          | [text](../../G1ANT.Language/Structures/TextStructure.md)           | **yes** | Name of component (i.e. "tblMyTable"). |
| `type`          | [text](../../G1ANT.Language/Structures/TextStructure.md)           | **yes** | One of values from the list:<table>            <tr><td>GuiUnknown</td></tr>            <tr><td>GuiComponent</td></tr>            <tr><td>GuiVComponent</td></tr>            <tr><td>GuiVContainer</td></tr>            <tr><td>GuiApplication</td></tr>            <tr><td>GuiConnection</td></tr>            <tr><td>GuiSession</td></tr>            <tr><td>GuiFrameWindow</td></tr>            <tr><td>GuiMainWindow</td></tr>            <tr><td>GuiModalWindow</td></tr>            <tr><td>GuiMessageWindow</td></tr>            <tr><td>GuiLabel</td></tr>            <tr><td>GuiTextField</td></tr>            <tr><td>GuiCTextField</td></tr>            <tr><td>GuiPasswordField</td></tr>            <tr><td>GuiComboBox</td></tr>            <tr><td>GuiOkCodeField</td></tr>            <tr><td>GuiButton</td></tr>            <tr><td>GuiRadioButton</td></tr>            <tr><td>GuiCheckBox</td></tr>            <tr><td>GuiStatusPane</td></tr>            <tr><td>GuiCustomControl</td></tr>            <tr><td>GuiContainerShell</td></tr>            <tr><td>GuiBox</td></tr>            <tr><td>GuiContainer</td></tr>            <tr><td>GuiSimpleContainer</td></tr>            <tr><td>GuiScrollContainer</td></tr>            <tr><td>GuiListContainer</td></tr>            <tr><td>GuiUserArea</td></tr>            <tr><td>GuiSplitterContainer</td></tr>            <tr><td>GuiTableControl</td></tr>            <tr><td>GuiTableColumn</td></tr>            <tr><td>GuiTableRow</td></tr>            <tr><td>GuiTabStrip</td></tr>            <tr><td>GuiTab</td></tr>            <tr><td>GuiScrollbar</td></tr>            <tr><td>GuiToolbar</td></tr>            <tr><td>GuiTitlebar</td></tr>            <tr><td>GuiStatusbar</td></tr>            <tr><td>GuiMenu</td></tr>            <tr><td>GuiMenubar</td></tr>            <tr><td>GuiSessionInfo</td></tr>            <tr><td>GuiShell</td></tr>            <tr><td>GuiGOSShell</td></tr>            <tr><td>GuiSplitterShell</td></tr>            <tr><td>GuiDialogShell</td></tr>            <tr><td>GuiDockShell</td></tr>            <tr><td>GuiContextMenu</td></tr>            <tr><td>GuiVHViewSwitch</td></tr></table> |
| `result`        | [variable](../../G1ANT.Language/Structures/VariableStructure.md)  | no       | `♥result`     | Name of a variable where the command's result will be stored ([list](../../G1ANT.Language/Structures/ListStructure.md) structure of [sapcomponent](../../../Structures/SapComponentStructure.md) structure with components) |
| `if`            | [bool](../../G1ANT.Language/Structures/BooleanStructure.md)        | no       | true           | Executes the command only if a specified condition is true. |
| `timeout`       | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md)   | no      | [♥timeoutcommand](../../G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed. |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                | Name of a procedure to call when the command throws an exception or when a given `timeout` expires. |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md)         | no       |                | Name of the label to jump to when the command throws an exception or when a given `timeout` expires. |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md)           | no       |                | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified. |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md)   | no       |                | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure. |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage`
and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.


## Result
Returns all matching components in a form of a [list](../../G1ANT.Language/Structures/ListStructure.md) 
structure of [sapcomponent](../../../Structures/SapComponentStructure.md) structures.
If nothing is found returned list will be empty.

Properties of each component may vary, therefore no list will be presented here.


##### Note
`Variables` panel does not show details of the list, it just shows names of classes
that contain implementation of models. Don't worry, you can view details of specific 
component on `Variables` panel if you assign a component from list of matching
components to a variable.