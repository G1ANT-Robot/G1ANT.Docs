# color.expected

## Syntax

```G1ANT
color.expected position ⟦point⟧ color ⟦text⟧
```

## Description

The `color.expected` command waits until a given RGB color appears at the specified coordinates of the screen. The coordinates can be typed in or inserted automatically by the robot with the [Mouse Position](../../../g1ant.robot-window/auxiliary-windows/mouse-position.md) tool.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`position`| [point](../../G1ANT.Language/Structures/PointStructure.md) | yes |  | X,Y coordinates given in a `x⫽y` format (the `⫽` character called the [Point Separator](../../../appendices/special-characters/point-separator.md) is available with the **Ctrl+?** keyboard shortcut) |
|`color`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |   | Expected color as a hexadecimal number in a RRGGBB format |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

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

