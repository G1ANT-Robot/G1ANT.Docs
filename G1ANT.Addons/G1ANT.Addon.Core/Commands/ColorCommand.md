# color

## Syntax

```G1ANT
color position ⟦point⟧
```

## Description

The `color` command retrieves the red, green and blue (RGB) color values of the pixel at the specified coordinates and returns these values as a hexadecimal number in a RRGGBB format. The coordinates can be typed in or inserted automatically by the robot with the [Mouse Position](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/g1ant.robot-window/auxiliary-windows/mouse-position.md) tool.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`position`| [point](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/PointStructure.md)) | yes |  | X,Y coordinates given in a `x⫽y` format (the `⫽` character called the [Point Separator](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/special-characters/point-separator.md) is available with the **Ctrl+?** keyboard shortcut) |
|`relative`| [bool](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md)) | no | false | Coordinates can be provided in an absolute (`relative false`) or relative (`relative true`) position to the active window |
|`result`| [variable](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md)) | no | ♥result  | Name of a variable, where the returned value will be stored as a hexadecimal number in a RRGGBB format |
| `if`           | [bool](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md)) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TimeSpanStructure.md)) | no       | [♥timeoutcommand](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md)) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ProcedureStructure.md)) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/LabelStructure.md)) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TextStructure.md)) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md)) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ErrorStructure.md)) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/common-arguments.md) page.

## Example

This example checks color of the provided pixel (the one from our green G1ANT logo) and displays its value stored in the default `♥result` variable in a dialog box.

```G1ANT
color position 88⫽92 relative true
dialog ♥result
```

