# sap.gettablerows

## Syntax

```G1ANT
sap.gettablerows table ⟦sapcomponent⟧
```

## Description
Returns rows of table as a `list` structure with `sapcomponent` structures filled 
with row data (`GuiTableRow`). You can access specific row by index (i.e. `♥rowList⟦1⟧`),
you can also iterate over the list:
```g1ant
foreach ♥row in ♥rowList
    dialog ♥row⟦count⟧
end
```


## Arguments

| Argument         | Type                                                              | Required | Default Value   | Description                                                  |
| ---------------- | ----------------------------------------------------------------- | -------- | --------------- | ------------------------------------------------------------ |
| `table`         | [sapcomponent](../../../Structures/SapComponentStructure.md)      | **yes**  |                 | Source table (`sapcomponent` with GuiTableControl or `text` with path). |
| `result`        | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md)  | no       | `♥result`     | Name of a variable where the command's result will be stored ([list](/G1ANT.Addons/G1ANT.Language/Structures/ListStructure.md) structure of [sapcomponent](../../../Structures/SapComponentStructure.md) structure (GuiTableRow) with row components) |
| `if`            | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BooleanStructure.md)        | no       | true           | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](/G1ANT.Addons/G1ANT.Language/Structures/TimeSpanStructure.md)   | no       | [♥timeoutcommand](/G1ANT.Addons/G1ANT.Addon.Core//Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](/G1ANT.Addons/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](/G1ANT.Addons/G1ANT.Language/Structures/LabelStructure.md)         | no       |                | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](/G1ANT.Addons/G1ANT.Language/Structures/TextStructure.md)           | no       |                | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](/G1ANT.Addons/G1ANT.Language/Structures/VariableStructure.md)   | no       |                | Name of a variable that will store the returned exception. The variable will be of [error](/G1ANT.Addons/G1ANT.Language/Structures/ErrorStructure.md) structure |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](/appendices/common-arguments.md) page.

# Result

Collection of rows, each containing of:

| Property name         | Type                                                         | Description                                                  |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `Selected`   | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BooleanStructure.md) | This property is true if the row is selected. Read-write. |
| `Selectable` | [bool](/G1ANT.Addons/G1ANT.Language/Structures/BooleanStructure.md) | This property is true if the row can be selected. Read-only. |
| `Count`      | [integer](/G1ANT.Addons/G1ANT.Language/Structures/IntegerStructure.md) | Number of cells in the row. Read-only. |

`GuiTableRow` is not a visible component, so it does not derive from GuiVComponent, it also 
does not inherit from nor GuiComponent and therefore all other properties exist just for compatibility
with Addon internals and do not contain valuable data.

##### Note
`Variables` panel does not show details of the list, it just shows names of classes
that contain implementation of models. Don't worry, you can view details of specific
row on `Variables` panel if you assign row from row list to a variable.
