# sap.gettablecell

## Syntax

```G1ANT
sap.gettablecell table ### row # column #
```

## Description
`TableCell` derives all properties from `GuiComponent` and `GuiVComponent`
and it does not introduce its own properties.


## Arguments

| Argument         | Type                                                              | Required | Default Value   | Description                                                  |
| ---------------- | ----------------------------------------------------------------- | -------- | --------------- | ------------------------------------------------------------ |
| `table`         | [sapcomponent](../../../Structures/SapComponentStructure.md)      | **yes**  |                 | Source table. |
| `column`        | [integer](../../G1ANT.Language/Structures/integerStructure.md)    | **yes**  |                 | Number of column containing desired cell. |
| `row`           | [integer](../../G1ANT.Language/Structures/integerStructure.md)    | **yes**  |                | Number of row containing desired cell. |
| `result`        | [variable](../../G1ANT.Language/Structures/VariableStructure.md)  | no       | `♥result`     | Name of a variable where the command's result will be stored ([sapcomponent](../../../Structures/SapComponentStructure.md) structure with the cell component, the `Text` property contains value of the cell) |
| `if`            | [bool](../../G1ANT.Language/Structures/BooleanStructure.md)        | no       | true           | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md)   | no       | [♥timeoutcommand](../../G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md)         | no       |                | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md)           | no       |                | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md)   | no       |                | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Result
Example table cell object serialized to json returned by current command.
```json
{
  "Text": "Value",
  "Tooltip": "",
  "IsChangeable": false,
  "IsModified": false,
  "Position": "21, 45, 32, 20",
  "ScreenPosition": "33, 538, 32, 20",
  "Name": "VBAP-POSNR",
  "Type": "GuiTextField",
  "TypeAsNumber": 31,
  "Path": "/app/con[0]/ses[0]/wnd[0]/usr/tabpT\\01/txtVBAP-POSNR[0,0]",
  "RelativePath": "usr/tabpT\\01/txtVBAP-POSNR[0,0]",
  "Id": "/app/con[0]/ses[0]/wnd[0]/usr/tabpT\\01/txtVBAP-POSNR[0,0]",
  "IsContainer": false
}
```

#### Note
You can access table cell also by path:
* absolute, i.e. `/app/con[0]/ses[0]/wnd[0]/usr/tab/txtPOSNR[0,0]`,
* relative, i.e. `usr/tab/txtPOSNR[0,0]`.

Last position of `Path` for other components is the same as `Name`, but for cells it is different 
and it consists of prefix related with `Type` property (i.e. "txt" for `GuiTextField`), `Name` 
and suffix with cell coordinates, for example `txtVBAP-POSNR[0,0]`.
> ###### Example of accessing cell by path
```g1ant
♥sapCell = ⟦sapcomponent⟧‴usr/tab/txtPOSNR[0,0]‴
dialog ♥sapCell⟦text⟧
```

> ###### Example of accessing cell by command
```g1ant
♥sapTable = ⟦sapcomponent⟧‴usr/tab‴
sap.gettablecell table ♥sapTable column 0 row 0 result ♥sapCell
dialog ♥sapCell⟦text⟧
```
