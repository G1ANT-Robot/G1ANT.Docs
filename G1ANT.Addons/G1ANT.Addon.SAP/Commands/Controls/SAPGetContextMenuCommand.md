# sap.getcontextmenu

## Syntax

```G1ANT
sap.getcontextmenu component ⟦sapcomponent⟧
```

## Description
Gets context menu of SAP component. Currently handled components are SAP tree (`GuiShell`)
and tree node (`TreeNode`).

Use `sap.getchild` to get specific context menu item and then `sap.click` it.


## Arguments

| Argument         | Type                                                              | Required | Default Value   | Description                                                  |
| ---------------- | ----------------------------------------------------------------- | -------- | --------------- | ------------------------------------------------------------ |
| `component`        | [sapcomponent](../../../Structures/SapComponentStructure.md)   | **yes**  |                | The component that owns a context menu. This parameter must contain SAPComponent that owns a context menu. |
| `result`        | [variable](../../G1ANT.Language/Structures/VariableStructure.md)  | no       | `♥result`     | Name of a variable where the command's result will be stored ([sapcomponent](../../Structures/SapComponentStructure.md) structure with component that is `GuiContextMenu`). |
| `if`            | [bool](../../G1ANT.Language/Structures/BooleanStructure.md)        | no       | true           | Executes the command only if a specified condition is true. |
| `timeout`       | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md)  | no       | [♥timeoutcommand](../../G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed. |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                | Name of a procedure to call when the command throws an exception or when a given `timeout` expires. |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md)         | no       |                | Name of the label to jump to when the command throws an exception or when a given `timeout` expires. |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md)           | no       |                | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified. |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md)   | no       |                | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure. |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage`
and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.


## Result
Returns context menu of `GuiContextMenu` type with tree-type nested children
of the same (`GuiContextMenu`) type. Returned context menu is just a container,
its children are the ones that are visible items thus being the ones you want to click.
Children might contain other children.
You can also view the collection of children via `Items` property.