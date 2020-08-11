# sap.getchild

## Syntax

```G1ANT
sap.getchild name ⟦text⟧ index ⟦integer⟧ parent ⟦sapcomponent⟧
```

## Description
Get child of parent by its name or index. If component is not found, name or index is incorrect
or there's any other problem an error is raised.

Similar to [`sap.find`](SAPFindCommand.md) except that 
* it works with any component including tree nodes, 
* does not search for nested children so you can't use the path as a `Name`,
* allows to get child by index.

## Arguments

| Argument         | Type                                                              | Required | Default Value   | Description                                                  |
| ---------------- | ----------------------------------------------------------------- | -------- | --------------- | ------------------------------------------------------------ |
| `index`          | [integer](../../G1ANT.Language/Structures/IntegerStructure.md)   | no       |                 | The index of child component within parent's children (starting from 1). `Index` or `Name` must be set. |
| `name`          | [text](../../G1ANT.Language/Structures/TextStructure.md)          | no       |                 | The name or relative slash-separated path of child component. `Index` or `Name` must be set. |
| `parent`        | [sapcomponent](../../../Structures/SapComponentStructure.md)      | **yes**  |                | The component that is a parent of children. This parameter must contain `sapcomponent` that is a container. |
| `result`        | [variable](../../G1ANT.Language/Structures/VariableStructure.md)  | no       | `♥result`     | Name of a variable where the command's result will be stored ([sapcomponent](../../Structures/SapComponentStructure.md) structure with component found). |
| `if`            | [bool](../../G1ANT.Language/Structures/BooleanStructure.md)        | no       | true           | Executes the command only if a specified condition is true. |
| `timeout`       | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md)  | no       | [♥timeoutcommand](../../G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed. |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                | Name of a procedure to call when the command throws an exception or when a given `timeout` expires. |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md)         | no       |                | Name of the label to jump to when the command throws an exception or when a given `timeout` expires. |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md)           | no       |                | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified. |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md)   | no       |                | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure. |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage`
and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.


## Result
Returns child component found by name or index.

Properties of child component may vary, therefore no list will be presented here.