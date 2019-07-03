# process.enqueue

## Syntax

```G1ANT
process.enqueue processname ⟦text⟧
```

## Description

This command enqueues a robot script from a specified file. The script will be executed after the current process and all processes added with any previous `process.enqueue` commands are finished.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`processname`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes |  | File path to a robot script to be enqueued |
| `result`       | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       | `♥result`                                                   | Name of a variable where the command's result will be stored |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

The example below shows how process queuing works. First, the script from the *robot1.g1ant* file is queued, then Notepad is opened, another 2 script files are queued and finally two sentences are sent to Notepad. When this example process finishes, the robot starts executing queued processes: *robot1*, then *robot2* and finally *robot3*:

```G1ANT
process.enqueue robot1.g1ant
program notepad
process.enqueue robot2.g1ant
process.enqueue robot3.g1ant
keyboard ‴I'm about to finish‴
keyboard ‴And start other processes‴
```
