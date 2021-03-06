# ie.runscript

## Syntax

```G1ANT
ie.runscript script ⟦text⟧ nowait ⟦bool⟧
```

## Description

This command executes script on the currently attached Internet Explorer instance. After successful evaluation, its result is stored in a variable.

Please be aware that only the first called function of the script might be evaluated as a result. If you want to get multiple results, compose script, which returns all values as JSON or other single string solution in one function.

| Argument | Type | Required | Default Value | Description |
| -------- | ---- | -------- | ------------- | ----------- |
|`script`| [text](../../G1ANT.Language/Structures/TextStructure.md) | yes|  | Script to be evaluated in a browser |
|`nowait`| [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no | false | If set to `true`, the script will continue without waiting for a webpage to respond to the the script that was run |
|`result`| [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no | `♥result` | Name of a variable where the script result will be stored |
| `if`           | [bool](../../G1ANT.Language/Structures/BooleanStructure.md) | no       | true                                                        | Executes the command only if a specified condition is true   |
| `timeout`      | [timespan](../../G1ANT.Language/Structures/TimeSpanStructure.md) | no       | [♥timeoutcommand](../../G1ANT.Addon.Core/Variables/TimeoutCommandVariable.md) | Specifies time in milliseconds for G1ANT.Robot to wait for the command to be executed |
| `errorcall`    | [procedure](../../G1ANT.Language/Structures/ProcedureStructure.md) | no       |                                                             | Name of a procedure to call when the command throws an exception or when a given `timeout` expires |
| `errorjump`    | [label](../../G1ANT.Language/Structures/LabelStructure.md) | no       |                                                             | Name of the label to jump to when the command throws an exception or when a given `timeout` expires |
| `errormessage` | [text](../../G1ANT.Language/Structures/TextStructure.md) | no       |                                                             | A message that will be shown in case the command throws an exception or when a given `timeout` expires, and no `errorjump` argument is specified |
| `errorresult`  | [variable](../../G1ANT.Language/Structures/VariableStructure.md) | no       |                                                             | Name of a variable that will store the returned exception. The variable will be of [error](../../G1ANT.Language/Structures/ErrorStructure.md) structure  |

For more information about `if`, `timeout`, `errorcall`, `errorjump`, `errormessage` and `errorresult` arguments, see [Common Arguments](../../../appendices/common-arguments.md) page.

## Example

In the following example the robot opens Internet Explorer, focuses on its window, then runs a simple script that displays a message:

```G1ANT
ie.open
window ‴✱internet explorer✱‴
ie.runscript ‴alert("Hello world!");‴
```

> **Note:** Before using this command, the [`ie.attach`](IEAttachCommand.md) or the [`ie.open`](IEOpenCommand.md) command has to be executed.

