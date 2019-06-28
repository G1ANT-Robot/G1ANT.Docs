# color.find

## Syntax

```G1ANT
color.find color ⟦text⟧ position ⟦point⟧ direction ⟦text⟧
```

## Description

The `color.find` command allows to capture the first pixel in the specified direction, starting from the predefined position, that matches the specified color.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`color`| [text](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TextStructure.md)) | yes |   | Expected color as a hexadecimal number in a RRGGBB format |
|`position`| [point](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/PointStructure.md)) | yes |  | X,Y coordinates given in a `x⫽y` format (the `⫽` character called the [Point Separator](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/special-characters/point-separator.md) is available with the **Ctrl+?** keyboard shortcut) |
|`direction`| [text](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TextStructure.md)) | yes |  | Direction of search: `down`, `up`, `right` or `left` |
|`relative`| [bool](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md)) | no | false | Coordinates can be provided in an absolute (`relative false`) or relative (`relative true`) position to the active window |
|`result`| [variable](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/master/G1ANT-Language/Special-Characters/variable.md) | no | ♥result  | Name of a variable, where the returned position will be stored as a value of [point](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/PointStructure.md)) structure. If not found, value of `-1⫽-1` will be returned |
| `if`           | [bool](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md)) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TimeSpanStructure.md)) | no       | [♥timeoutcommand](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md)) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ProcedureStructure.md)) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/LabelStructure.md)) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TextStructure.md)) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md)) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ErrorStructure.md)) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/common-arguments.md) page.

## Example

This example shows how to find the first pixel that has the required color (`FFFFFF`, which is pure white), starting from the position X=50, Y=500 and going down.

```G1ANT
color.find color FFFFFF position 50⫽500 direction down relative false
dialog ♥result
```

The dialog box will show the result *“50⫽500”*, because the first pixel in the specified position is white.
