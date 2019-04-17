# waitfor.color

## Syntax

```G1ANT
waitfor.color position ⟦point⟧ color ⟦text⟧ relative ⟦bool⟧
```

## Description

This command waits for a specified color to appear at a defined position.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`position`| [point](G1ANT.Language/G1ANT.Language/Structures/PointStructure.md) | yes |  |XY coordinates of a pixel where a given color is expected|
|`color`| [text](G1ANT.Language/G1ANT.Language/Structures/TextStructure.md) | yes |  | Expected color value in hex RRGGBB format |
|`relative`| [bool](G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md) | no | true | If set to `true`, the coordinates are relative to the active window |
| `if`           | [bool](G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](G1ANT.Language/G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutwaitforcolor](G1ANT.Language/G1ANT.Addon.Core/Variables/TimeoutWaitForColor.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](G1ANT.Language/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](G1ANT.Language/G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](G1ANT.Language/G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](G1ANT.Language/G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](G1ANT.Manual/appendices/common-arguments.md) page.

## Example

In the script below the robot waits couple seconds (the default time defined by the `♥timeoutwaitforcolor` special variable) for a white pixel to appear at X=300, Y=300 coordinates relative to the active window. If the color is found, a dialog box is displayed. If not, an error message appears.

```G1ANT
waitfor.color position 300⫽300 color FFFFFF relative true
dialog ‴Color found!‴
```

