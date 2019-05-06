# mouse.click

## Syntax

```G1ANT
mouse.click position ⟦point⟧ button ⟦text⟧ relative ⟦bool⟧ type ⟦text⟧ count ⟦integer⟧ mousedelay ⟦integer⟧
```

## Description

This command moves mouse cursor to the required position and performs a mouse button action.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`position`| [point](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/master/G1ANT-Language/Structures/point.md) | yes |  | Screen coordinates of a mouse cursor position before executing a button click |
|`button`| [text](G1ANT.Language/G1ANT.Language/Structures/TextStructure.md) | no | left | Mouse button to be pressed: `left`, `middle`, `right`, `xbutton1` or `xbutton2` |
|`relative`| [bool](G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md) | no | true | If set to true, the mouse position is relative to the active window |
|`type`| [text](G1ANT.Language/G1ANT.Language/Structures/TextStructure.md) | no | press | Button action type: `down`, `up` or `press` |
|`count`| [integer](G1ANT.Language/G1ANT.Language/Structures/IntegerStructure.md) | no | 1 | Number of button clicks |
|`mousedelay`| [integer](G1ANT.Language/G1ANT.Language/Structures/IntegerStructure.md) | no | [♥mousedelay](G1ANT.Language/G1ANT.Addon.Core/Variables/MouseDelayVariable.md) | Determines the time value (in ms) for mouse actions (moves or clicks) |
| `if`           | [bool](G1ANT.Language/G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](G1ANT.Language/G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](G1ANT.Language/G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](G1ANT.Language/G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](G1ANT.Language/G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](G1ANT.Language/G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](G1ANT.Language/G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](G1ANT.Language/G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](G1ANT.Manual/appendices/common-arguments.md) page.

## Example

This example shows how to use the `mouse.click` command to perform a drag and drop action on the Windows Desktop:

```G1ANT
keyboard ⋘WIN+D⋙
mouse.click 664⫽346 relative false type down
mouse.click 1362⫽671 relative false type up mousedelay 500
```

