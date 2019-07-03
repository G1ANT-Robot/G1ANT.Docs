# delay

## Syntax

```G1ANT
delay ⟦integer⟧
```

## Description

The `delay` command allows to suspend robot for a specified time in seconds and milliseconds before it proceeds to the next action.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`seconds`| [integer](../../G1ANT.Language/Structures/IntegerStructure.md) | no | 1 | Time in seconds for a robot to wait before it proceeds to the next line of code |
|`milliseconds`| [integer](../../G1ANT.Language/Structures/IntegerStructure.md) | no | 0 | Time in milliseconds added to the previously specified time in seconds for a robot to wait before it proceeds to the next line of code |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../../../appendices/common-arguments.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

This example launches Notepad and writes *“Hello”* after 4 seconds and 500 milliseconds.

```G1ANT
program notepad
delay 4 milliseconds 500
keyboard Hello!
```

