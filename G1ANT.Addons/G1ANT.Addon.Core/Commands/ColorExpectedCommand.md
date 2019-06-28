# color.expected

## Syntax

```G1ANT
color.expected position ⟦point⟧ color ⟦text⟧
```

## Description

The `color.expected` command waits until a given RGB color appears at the specified coordinates of the screen. The coordinates can be typed in or inserted automatically by the robot with the [Mouse Position](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/g1ant.robot-window/auxiliary-windows/mouse-position.md) tool.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`position`| [point](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/PointStructure.md)) | yes |  | X,Y coordinates given in a `x⫽y` format (the `⫽` character called the [Point Separator](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/special-characters/point-separator.md) is available with the **Ctrl+?** keyboard shortcut) |
|`color`| [text](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TextStructure.md)) | yes |   | Expected color as a hexadecimal number in a RRGGBB format |
| `if`           | [bool](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md)) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TimeSpanStructure.md)) | no       | [♥timeoutcommand](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md)) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ProcedureStructure.md)) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/LabelStructure.md)) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/TextStructure.md)) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md)) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](](https://manual.g1ant.com/link/G1ANT.Language/G1ANT.Language/Structures/ErrorStructure.md)) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/common-arguments.md) page.

## Example

This example shows how to check if a color of the specified pixel is exactly as expected. If it is, the `errorcall` argument will be skipped and a *“Color found”* message box will be displayed. This argument will be executed only when the command result is false — in case of this example, if a pixel of the given color does not exist at the specified location. Then, a dialog box with *“Color not found”* message will be displayed.

```G1ANT
color.expected position 88⫽92 color 06914C relative true errorcall notFound
dialog ‴Color found‴

procedure notFound
    dialog ‴Color not found‴
    stop silentmode true
end
```

