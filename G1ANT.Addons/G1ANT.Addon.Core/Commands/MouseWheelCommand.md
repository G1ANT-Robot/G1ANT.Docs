# mouse.wheel

## Syntax

```G1ANT
mouse.wheel position ⟦point⟧ horizontalsteps ⟦integer⟧ verticalsteps ⟦integer⟧ relative ⟦bool⟧ mousedelay ⟦integer⟧
```

## Description

This command moves a mouse cursor to the specified position and performs a vertical or horizontal wheel action.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
| `position`        | [point](../../G1ANT.Language/Structures/PointStructure.md) | yes      |                                                              | XY coordinates of a pixel to move a mouse cursor to          |
|`horizontalsteps`| [integer](../../G1ANT.Language/Structures/PointStructure.md) | no | | Number of horizontal mouse wheel steps in pixels; positive value — right, negative — left |
|`verticalsteps`| [integer](../../G1ANT.Language/Structures/PointStructure.md) | no |  | Number of vertical mouse wheel steps in pixels; positive value — down, negative — up |
|`relative`| [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no | true | if true position is relative to active window |
| `mousedelay`      | [integer](../../G1ANT.Language/Structures/IntegerStructure.md) | no       | [♥mousedelay](../Variables/MouseDelayVariable.md) | Determines the time value (in ms) between the consecutive mouse clicks |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

In the following example specify the name of a window (replacing `windowTitle` value), which can be scrolled — your browser, for example — and run the script to see how the page scrolls down:

```G1ANT
window windowTitle
mouse.wheel 200⫽200 verticalsteps 500
```
