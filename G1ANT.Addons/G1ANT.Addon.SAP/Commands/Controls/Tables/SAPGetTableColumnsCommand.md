# sap.gettablecolumns

## Syntax

```G1ANT
sap.gettablecolumns table ⟦sapcomponent⟧
```

## Description
Returns columns of table as a `list` structure with `sapcomponent` structures filled 
with column data (`GuiTableColumn`). You can access specific column by index (i.e. `♥columnList⟦1⟧`),
you can also iterate over the list:
```g1ant
foreach ♥column in ♥columnList
    dialog ♥column⟦text⟧
end
```


## Arguments

| Argument         | Type                                                              | Required | Default Value   | Description                                                  |
| ---------------- | ----------------------------------------------------------------- | -------- | --------------- | ------------------------------------------------------------ |
| `table`         | [sapcomponent](../../../Structures/SapComponentStructure.md)      | **yes**  |                 | Source table. |
| `index`        | [integer](/G1ANT.Addons/G1ANT.Language/Structures/integerStructure.md)     | **yes**  |                 | Index of desired coumn. |
| `result`        | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md)  | no       | `♥result`     | Name of a variable where the command's result will be stored ([list](/G1ANT.Addons/G1ANT.Language/Structures/ListStructure.md) structure of [sapcomponent](../../../Structures/SapComponentStructure.md) structure with column components) |
| `if`            | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BooleanStructure.md)        | no       | true           | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](/G1ANT.Addons/G1ANT.Language/Structures/TimeSpanStructure.md)   | no       | [♥timeoutcommand](/G1ANT.Addons/G1ANT.Addon.Core//Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](/G1ANT.Addons/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](/G1ANT.Addons/G1ANT.Language/Structures/LabelStructure.md)         | no       |                | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)           | no       |                | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md)   | no       |                | Name of a variable that will store the returned exception. The variable will be of [error](/G1ANT.Addons/G1ANT.Language/Structures/ErrorStructure.md) structure |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](/appendices/common-arguments.md) page.

# Result

Collection of columns, each containing of:

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Selected` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BooleanStructure.md) | True if the column is selected. Read-write. |
| `IsFixed`  | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BooleanStructure.md) | Some columns may be fixed, which means that they will not be scrolled with the rest of the columns. Read-write. |
| `Title`    | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md) | This is the caption of the column. Read-only. |
| `Width`    | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Width of the column. Read-only. |
| `Count`    | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Number of cells in the column. Read-only. |

Returned properties also contain all properties of GuiComponent and GuiVComponent, 
including `Text` property which serves as caption of the column.

##### Note
`Variables` panel does not show details of the list, it just shows names of classes
that contain implementation of models. Don't worry, you can see all the details
of your column on the `SAP UI object tree`.
Also, you can view details of specific column on `Variables` panel if you assign
column from column list to a variable.