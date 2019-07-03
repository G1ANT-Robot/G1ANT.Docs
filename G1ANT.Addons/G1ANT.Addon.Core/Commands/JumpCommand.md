# jump

## Syntax

```G1ANT
jump label ⟦label⟧
```

## Description

The `jump` execution flow control command moves the robot to a defined label in a script, where the process is continued until its end. Please note that all lines between the line from which the jump was performed and the labeled line will be skipped (if the jump is “forward” in a script) or repeated (if the jump is “back” in a script). If you want to execute some code — a repetitive set of commands, for example — and then return to the previous point in a script to continue the process, use procedures and the  [`call`](CallCommand.md) commands.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`label`| [label](../../G1ANT.Language/Structures/LabelStructure.md) | yes| | Label name to jump to |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../../../appendices/common-arguments.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

```G1ANT
program notepad
jump start
keyboard ‴Jump over this text‴

label start
keyboard ‴Congratulations! You've made a jump!‴
```

In the example above, the robot opens Notepad, then, instead of typing *“Jump over this text”*, it types *“Congratulations! You've made a jump!”*, because of the `jump` command, which tells the robot to move to the `start` label and skip the lines in between.
